---
layout: post
title: Down the rabbit hole of ORM hate
date: 2015-05-29 12:39:44
---

All I wanted to do was to link to the Wikipedia article on [ORM (Object-relational mapping)](http://en.wikipedia.org/wiki/Object-relational_mapping) in a post contemplating moving from [Sequelize](http://docs.sequelizejs.com/en/latest/), the Node.js ORM we currently use, to [Waterline](https://github.com/balderdashy/waterline), a newer and somewhat fancier looking ORM used in the [Sails.js](http://sailsjs.org/) framework.

Then Google spat out this as the *first search result for "ORM"*: [ORM Is an Offensive Anti-Pattern](http://www.yegor256.com/2014/12/01/orm-offensive-anti-pattern.html) -- a highly opinionated article that seem to be based almost entirely on the author's bad experiences with [Hibernate](http://en.wikipedia.org/wiki/Hibernate_(Java)). I've heard ORM described as the [Vietnam of computer science](http://blogs.tedneward.com/2006/06/26/The+Vietnam+Of+Computer+Science.aspx) about ten years ago (read [Jeff Atwood's much shorter take on it](http://blog.codinghorror.com/object-relational-mapping-is-the-vietnam-of-computer-science/) if you found the original post too wordy), but to see this so high up the search results was a bit jarring.

![ORM Is an Offensive Anti-Pattern](/public/images/2015-05-29-orm.jpg)

<!--break-->

I spent the next hour stumbling from article to article, finally ending up at [Martin Fowler's blog post](http://martinfowler.com/bliki/OrmHate.html) on the subject, which I felt was the most reasonable.

To summarize (if imperfectly) what everyone is saying:

- Perfect object-relation mapping cannot be achieved -- the best way to store the data is never the same as the best way to represent it in your code ([Object-relational impedance mismatch](http://en.wikipedia.org/wiki/Object-relational_impedance_mismatch)) (I agree)
- "the only workable solution to the ORM problem is to pick one or the other: either abandon relational databases, or abandon objects" (I disagree - the mismatch between the two is often manageable)
- It's a "terrible and offensive violation of the object-oriented paradigm" (I don't care. What matters are the practical implications, not the philosophy)
- It hurts performance (I agree, but developer time tends to be more valuable than CPU time, so I'm willing to put up with some performance loss for productivity gain)
- It's easy to map columns to attributes, but trying to handle complex relationships between entities in a generic way quickly gets out of hand (I agree)
- Some developers use an ORM to hide from the database (I agree -- you shouldn't be using a persistence layer if you don't understand it)

I have attempted some form of ORM at least four times in the past twelve years: thrice with statically typed languages (once in Java, twice in C++) and then once in a dynamically typed language (PHP). As bad as the experiences were, they were never as bad as those times I had to hand-code each mapping (down to the SQL queries) within the application code itself. Whatever the flaws of ORMs might be, they are better than writing reams of boilerplate code just to get your data out of the database and into memory.

Then last year, in an attempt to avoid the problem, I considered moving away from relational databases entirely. I evaluated several NoSQL databases only to conclude that none of them could be guaranteed to scale up to the data volumes I needed; none of them could do the sort of complex queries I needed for reports. After about a month, I was back where I started: relational databases were (and still are) the best way to persist large volumes of structured data.

So for my latest project (which is built on Node.js), I picked an ORM -- Sequelize. Six months on, the world hasn't ended. My team and I ran into the usual problems with complex relations and interactions between entities, which we handled on an ad-hoc basis (which is to say we wrote an additional mapping code *only* where the ORM fell short). So it seems I have settled on solution #4 of the Six Solutions to the Problem, as per Ted Neward:

> **4. Acceptance of ORM limitations**. Developers simply accept that there is no way to efficiently and easily close the loop on the O/R mismatch, and use an ORM to solve 80% (or 50% or 95%, or whatever percentage seems appropriate) of the problem and make use of SQL and relational-based access to carry them past those areas where an ORM would create problems.

One final note: I notice that a lot of ORM hate seem to originate from developers who use statically typed languages. This makes sense to me -- one of the things I found infuriating about object relation mapping with Java and C++ was that object structures had to be predetermined at compile time. That usually meant hand-coding the objects or code generation, or worse yet, using arrays of hybrid data structures as objects (which is basically emulating dynamic typing). By comparision, object relation mapping in dynamically typed languages has been relatively pain-free for me.

---

#### References

1. [ORM Is an Offensive Anti-Pattern](http://www.yegor256.com/2014/12/01/orm-offensive-anti-pattern.html), Yegor Bugayenko, 2014
2. [The Vietnam of computer science](http://blogs.tedneward.com/2006/06/26/The+Vietnam+Of+Computer+Science.aspx), Ted Neward, 2006
3. ["OrmHate"](http://martinfowler.com/bliki/OrmHate.html), Martin Fowler, 2012
4. [Thoughts on Vietnam commentary](http://blogs.tedneward.com/2006/06/27/Thoughts+On+Vietnam+Commentary.aspx), Ted Neward, 2006
5. [Object-Relational Mapping is the Vietnam of Computer Science (2006)](https://news.ycombinator.com/item?id=7310077), Hacker News, 2014
6. [ORM Haters Don’t Get It](http://techblog.bozho.net/orm-haters-dont-get-it/), Bozhidar Bozhanov, 2012



