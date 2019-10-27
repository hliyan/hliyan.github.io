---
layout: post
title: You might not need redux
date: 2017-05-08 01:45:00
---

Whenever I start a new front end project using React, I get a lot of helpful suggestions like "Use Redux, it's great!" or "Use Mobx, it's great!" or "Use Redux Saga, it's great!".

"But why would I need Redux (or Mobx or Redux Saga, or whatever state management library that is in vogue as you read this)?" I ask.

"It's the current paradigm," (or something along those lines) is a frequent answer, which is just another way of saying "All the cool kids are doing it." Which is not an answer to the question "why?"

So why do you want to use Redux?

In order to understand why you need Redux, you need to understand why Flux Architecture was needed. In order to understand Flux Architecture, you need to understand why two-way bindings and MVC architecture was needed. In order to understand two-way bindings and MVC, you need to understand plain old DOM manipulations.

So let's start there.

## Plain old DOM manipulation

This is how we used to do it "back in my day":

```javascript
var xhr = new XMLHttpRequest();
 
xhr.onreadystatechange = function() {
  if (xhr.readyState == XMLHttpRequest.DONE && xhr.status == 200) {
    document.getElementById('answer').value = xhr.responseText;
  }
}
xhr.open('GET', 'http://foo.com/bar', true);
xhr.send(null);
```

As you can see, the application code will get out of hand very quickly.

## DOM manipulation with jQuery

When jQuery came along, it got a little better:

```javascript
$.get('http://foo.com/bar', function(data) {
  $("#answer").value(data);
});
```

This made the code a little less verbose, but the fundamental problem remained: your data querying, business logic and your UI rendering (DOM manipulations) code were all mixed in together. Also, you were hand-coding the changes to the view in response to the changes to your data.

## MVC with two-way data binding

Next, we came up with the idea of views bound to data in models in such a way that when controllers change the model, the views "react" and update themselves. And when the user updates the views, the model reacts and updates itself. MVC with two-way data bindings was born.

Here's an example using Angular (I've omitted the Ajax call here and only demonstrated the 2-way data binding between $scope.answer and the answer input field.

```html
<div ng-app="QAApp" ng-controller="QCtrl">
  Answer: <input id="answer" type="text" ng-model="answer"><br>
  <br>
  Answer is: {{answer}}
</div>
 
<script>
var app = angular.module('QAApp', []);
app.controller('QCtrl', function($scope) {
    $scope.answer = "Your answer";
});
</script>
```

So now we cleanly separated the view from the data and the logic. All good, right? Not quite. As applications got larger and models were bound to multiple views and were manipulated by multiple controllers, it became increasingly difficult to follow the execution of the app from the point of data change to the view. It could also potentially result in loops – a model updates the view, which updates another model, which updates the view... so on and so forth. Debugging was a nightmare for large applications with complex logic.

## React

Facebook's React.js library came with one-way data bindings – changes to the data (or "props") caused the view to react and update itself. But changes to the view did not affect data. Instead, such changes had to be notified as events, which the application was expected to capture and change the data. In other words, "data flows down, events flow up". But React.js, being just a view library, was silent about how to do this. Only later did Facebook's developers come up with Flux Architecture. This began a blizzard of competing Flux libraries (names like "Flummox", "Marty", "McFly", "Alt", "Reflux", "Fluxxor" come to mind). Redux, a reducer function based library, seem to have won the war. And that is how we came to be using Redux for the majority of our React apps.

Here's a sufficiently abstract representation of Flux: https://github.com/facebook/flux/tree/master/examples/flux-todomvc 
Redux is not too dissimilar.

## If not Redux, then what?

Say you're to write an app for a simple Todo list. Now assume that the developers of the Todo application backend have provided you with a ready-made JavaScript client that is a very convenient wrapper around the API – the client object encapsulates all the logic, state and fetch actions that are needed to cater to a front end. Then all you need is to map your react component props to data from that client and component event handlers to functions in the client. For asynchronous operations, you subscribe and listen to events emitted by the client.

It kind of sounds like Flux all over again, but note the differences:

```javascript
import Todo from 'todo-client';
  
// initialize todo application client
// this encapsulate all client side state, actions, network calls and logic
Todo.init({
  url: 'http://localhost',
  username: 'bob'
});
  
// stateless view template
// this has only props, no state
const TodoList = (list) => {
};
  
// wrap stateless template around a stateful 'wiring' component
// this has only state, no props
class TodoListView extends React.Component {
  constructor(props) {
    this.setTodos = this.setTodos.bind(this); // would could metaprogram this
    this.onClickNewItem = this.onClickNewItem.bind(this);
  }
 
  componentWillMount() {
    setTodos({list: Todo.getTodoList()}); // initial state
    Todo.on(Todo.events.TODOS_UPDATED, this.setTodos); // subscribe to further updates to state
  }
  
  componentWillUnmount() {
    Todo.off(Todo.events.TODOS_UPDATED, this.onTodosUpdated);
  }
  
  setTodos(list) {
    this.setState({ list: list });
  }
 
  onClickNewItem() {
    Todo.createDraftItem();
  }
  render() {
    return (<TodoList list={this.state.list} onClickNewItem={this.onClickNewItem} />);
  }
}
  
ReactDOM.render(<TodoListView/>, document.getElementById('todo'));
```

That's it – a stateless component wrapped around a state-only component that calls  an business API client. Much of what we put in actions and reducers are encapsulated inside the business API, along with network calls and business logic. The stateless components only contain HTML/JSX and the stateful wrapper component only contains code that wires the stateless component to the application client. This makes the front end extremely thin. I'd actually suggest that the application API client be developed and maintained as a completely separate codebase from the front end.

Deceptively simple, is it not?
