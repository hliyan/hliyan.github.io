---
layout: post
title: A Layman's Introduction to Cryptocurrencies
date: 2013-11-28 17:00:00
---

*A plain English explanation of the theory behind Bitcon-like virtual currencies. Some oversimplifications have been made in the interest of clarity and brevity. But if you find outright errors or have suggestions for improvements, let me know!*

#### The perfect currency

Imagine a fantasy society. They have the same exchange problem as us — they can’t barter one tenth of a horse for a mug of beer or half a haircut for a loaf of bread. Our society’s ancestors solved this problem by switching to gold and other precious metals — you can divide it into very tiny units, it doesn’t rot and everybody recognizes its value.

But in this fantasy society, they have alchemy. They can create any metal they want (we’ll get there someday too, through matter transmutation). In this place, a grain of gold is no more valuable than a grain of sand. Yes it’s useful, but nobody will accept it as payment because it’s so abundant. It’s just like you won’t accept air as payment even though it’s technically more valuable to human life than food[^1].

So what do they do? They devise a type of magic coin and a magic wallet (later we will replace this magic with technology). This type of coin is impossible to copy or forge perfectly. It’s not even possible to create it at will, because then everyone will do it and it’ll be about as valuable as sand again. So it has to have a limited supply. The magic works by creating these coins periodically. Who gets the newly created coins? Everybody. Since this is not a finders-keepers scenario like in gold mining, it’s only fair. Newly generated coins periodically appear in everyone’s wallets. And these coins can be neatly split into smaller coins so that they can be spent in any fraction you want.

<!--break-->

Now a human being can’t tell whether one of these coins is the real thing or not by just looking at it. The wallet does it for you. If you receive a fake coin from someone and try to put it in your wallet, your wallet will spit it out immediately. Doesn’t that solve this society’s currency problems? Let’s see:

1. Limited supply.

2. Can be split neatly into small units.

3. Impossible to perfectly forge; forgeries are instantly detectable.

4. No central party mints the coins or has control of them. So no corruption.

#### A somewhat less than perfect currency

Unfortunately, magic doesn’t exist. So let’s dial back the magic a bit. Instead of magic coins and magic wallets, everyone gets an account book, or a *ledger*. Instead of physical coins periodically appearing in a wallet, you periodically receive a unique ‘coin number’ in the mail, from a central exchange/mint, which we will talk about soon. It basically says, “you’re now the owner of a new coin identified by #555″ (that’s just an example). Nobody else get’s that exact number again. It’s just like the serial number on a banknote (or a bill, if you’re American). You write this number down in your ledger. When you spend your coins, you strike it off your ledger. When you receive coins, whether from the mint or as payment from someone else, you add that to your ledger. So you always know your current balance.

Say you want to buy a beer. You go to the bartender and say “I’m giving you #555-1/10, give me a beer” (let’s say that identifies one tenth of the coin #555). If he accepts, you’re supposed to strike one tenth of coin #555 off your ledger and the bartender is supposed to add #555-1/10 to the bar’s ledger.

But is the bartender going to accept your word? You could of course show him the entry in your ledger as proof, but then what if you forged the ledger? Not only could you spend coin #555 ten times over in bars all over town, you could even claim to have coin #556. How will anyone know who has which coin?

#### The problem of the central mint

So the personal ledger or account book is not enough. We need a central ledger. So when you want to buy that beer, the bartender calls the *central* exchange and says “I’m getting #555-1/10 from Mr. Smith”. Someone at the exchange checks the central ledger and verifies that you, Mr. Smith does indeed own at least 1/10th of #555. But they also need to check that the bartender is not cheating. So either you too have to call the exchange and say “I’m giving #555-1/10 to Joe’s Bar,” or the exchange has to call you and ask “Mr. Smith, Joe’s Bar is claiming #555-1/10 from you. Is that legitimate?”. If both sides say yes, the transaction takes place without possibility of fraud. It’s a bit like credit card transactions, right?

Except we’re making some assumptions. We’re assuming that people won’t get fed up of continuously having to call the exchange every time they pay for something. We’re assuming that the exchange is completely honest. That second assumption is very wrong. Even though an economist may have calculated that the exchange (or the “mint”) should mail out no more than coin #1000 this year, the employees of the exchange decide to “mint” a few hundred extra coins and split it amongst themselves. Suddenly, they’ve got money for nothing. No amount of oversight is going to stop this. The power to make money out of thin air is so tempting that even the bosses and the bosses’ bosses will eventually succumb.

#### A global ledger instead of a central one

So how do we keep the central exchange honest? We don’t. We get rid of it. We don’t trust any single person to hold that central ledger, which is the account book that lists every single coin number or partial coin number against someone’s name and is updated with every transaction. We give it to *everybody*. Instead of a list of just your coins, now your personal ledger contains a list of all coins ever, with names of owners. Now when you go to the bartender, he doesn’t have to trust you or even a central exchange, he can look up the last owner of #555-1/10 from his own ledger. So you strike it off your ledger and the bartender adds it to his own. You enjoy your beer.

Now we have two problems. Were both of you honest in your book updates? And how is everyone else going to know about this transaction? If it’s just a few people in a room, it’s easy. You just stand up and announce “#555-1/10 from Mr. Smith to Joe” and everyone will update his/her book. Since everyone knows the total number of coins in existence, it’ll be a trivial matter to add up the accounts and check if you and Joe are both telling the truth. There’s no chance of fraud. The moment you try to spend a coin you don’t have, the books will not balance and everyone will scream fraud. That solves the problem of the corrupt central exchange, right?

Wrong. We only solved one problem (double spending), ignored another (who mints the coin numbers now?) and introduced a new problem (the whole world now knows your private financial details).

#### Making numbers scarce

Let’s take the minting problem. We have to make sure these ‘coins’ have a limited supply. But if there is no central exchange controlling the issuing of these numbers, we have a problem. Anyone can write up a new number. And numbers are infinite. We need that magic back. Even though we don’t have magic, we have something close: mathematics.

The math problem 3 x 2 = 6 is no more easier or difficult than it’s reverse, which for the sake of this discussion, we will consider to be 6 / 2 = 3. Unless of course you’re bad at division, but that’s a different story. Most math calculations take a similar amount of effort whether you do it one way or the other. Most but not all. There is a certain types of mathematical function, called a hash function[^2], that is very easy to do in the forward direction, but extremely time consuming to reverse.

How does this help us limit the supply of coin numbers? We decree that all valid coin numbers must produce a specific pattern when run through a hash function. The only way to do that is to keep trying random numbers until you accidentally stumble upon one that gives you a hash that matches the required pattern. The first person do discover and announce a given number, gets to keep it (or spend it). It’s kind of like prospecting for gold and finding a nugget. Of course, now pen and paper won’t be enough. The calculations are tough. Fortunately we have computers. We also have the Internet. So the problem of broadcasting transactions to a large number of people gets solved too. Now we have a limited supply of coin numbers that everyone can verify as authentic, and a global ledger that prevents people from spending money they don’t own.

#### Privacy

Now we’ve nailed it, right? Not quite. We just solved fraud and oversupply. But what about privacy? That’s easy. Why does your ledger have to carry your name at all? It can just be a number. And you can have as many ledgers as you like. It’s just like you opening many bank accounts. Want to get paid a salary? You just tell your company accountant “Here’s my coin account number. Send my salary here”. Is he going to object? No. It’s your money, so it’s your choice where you send it.

But wait, you say. Now the company knows that you’re the owner of that account. If your boss is a creep, he could study the global ledger and track the coin he paid you all the way to a seedy bar in a disreputable part of town. And you don’t want that. What can you do?

Just create any number of new accounts and split up the money among them. Spend using those. Now your creepy boss doesn’t know whether those new accounts belong to your or to someone else you made a payment to. He can suspect, but he’ll never know for sure. If you’re really paranoid, you can even exchange your coins with friends. Your boss will be very surprised when your coin is used to buy diapers in London when he knows for a fact you live in Los Angeles and have no children. With billions of people using these coins dozens of times a day, at some point the creeps and spooks are going to have to give up. They can always suspect, but they won’t be able to prove anything.

Okay, now we’ve got it, right? This new virtual currency is perfectly divisible, cannot be counterfeited without everybody crying foul, cannot be created on a whim so as to cause oversupply and cannot be reliably tracked to a person.

#### Authentication

Still no. When we went from announcing transactions to a roomful of people to using the Internet to broadcast them, we introduced a new problem: authentication. In the room, people will identify you by your face. But on the Internet, you’re just an account number. When you (or anyone else) in the coin network receives a broadcast saying “#555-1/10 from account X to account Y”, how do you know that it’s an authentic broadcast from the owner of account X? Note that Y (the receiver) doesn’t need to prove himself — you don’t need to prove anything to receive money if someone is willing to just hand it to you.

Are we going to have to reveal people’s identities again?

No. You don't need to reveal *who* you are. You just need to prove that the person who is trying to spend a coin is the same as the last owner of that coin, regardless of who he or she is.

In the real world, you prove your identity by doing something that only you can do. In most cases, this involves placing your signature on a piece of paper, entering the combination into a safe or inserting your key into a lock. Of course neither method is perfect. A good forger can forge your signature. If someone watches you open the safe, they may see your combination. Someone can duplicate your key. On the Internet, the duplication problem is much, much worse — you can copy anything perfectly because it’s all ones and zeroes (which is why record companies still have such a tough time keeping people from pirating music). So the moment you use a secret number to prove your identity, it becomes useless because now everyone knows it and can easily reproduce it.

#### Digital signatures

What you really need is something a bit like magic: you need to be able to prove you know a number without actually revealing that number. Believe it or not, there is another class of mathematical problem involving prime numbers that can do just this.

Many years ago, three very talented men whose last names begin with the letters R, S, and A figured out a way to use this problem to construct a system like this:

You have two numbers -- a scrambling key and an unscrambling key. You keep the scrambling key secret and tell everyone your unscrambling key. Then you can do this:

    "I am who I say I am" + SCRAMBLING KEY —> scramble —> i3nd93slncek383cekeqnrq
    
You will be the only person in the world who can do this for any given phrase or number. Anybody else in the world can do the reverse (and only the reverse):

    i3nd93slncek383cekeqnrq + YOUR PUBLIC UNSCRAMBLING KEY —> 
      unscramble —> "I am who I say I am"

You just verified your identity to someone by showing him a result that only you could produce (because only you have your secret number). He could verify it because he (and everyone else) knows your public number. You never revealed your secret.

So now you know how we’re going to solve the identity problem on the Internet. Every account will have two numbers — the secret number and the public number. Everyone knows the public numbers and the global ledger contains these numbers too. You keep your secret number very, very safe. Because if you lose it, you have no way of ever spending your coins again. Because you can’t prove who you are. Worse yet, if someone else gets a hold of your secret key, he can spend your money.

When you announce a new transaction, you ‘digitally sign’ the transaction message with your secret key. The message gets published all over the Internet. Everyone in the coin network takes the message, sees the the public account number and uses it to unscramble the message body. If the unscrambling is successful, then the sender is the rightful owner of the account.

#### Voila! Voila?

Finally, it looks like we’ve sorted out all the theoretical problems!

Now we have a few practical problems. First, that global ledger is going to grow huge. Second, what happens if you drop off the Internet for a few hours and come back? Of course, this coin network can be designed so that your “wallet program” can ask anybody and everybody on the network to supply you with the missing transactions in order to catch up. This should take minutes, if not seconds. But what if a fraudster waits for a latecomer just like you and pays you with a coin that belongs to someone else? It’s in the global ledger, but your copy is not yet up to date. If he times it right, by the time your ledger gets updated, you may have already handed over your goods to the fraudster. And the ledger now tells you that the coin belongs to someone else.

#### Archiving old transactions

Let’s take the first problem — the problem of the huge ledger. Do you really need all the transactions from the beginning of time? If it’s a paper ledger book, you would probably finalize it annually and publish an official copy. All the balances at the end of December 31st will be brought forward to the new year’s book. The old books will stored in archives, only to be pulled out if the need arises.

In theory, this is exactly what happens with our digital coin network. The only difference is that instead of a central bank or exchange, this process of archiving and bringing the balance forward is performed by everyone in the network. Every time someone finds a new coin number, he (or rather his wallet program) should announce it in a new 'page' of the leger. This page contains all the transactions between the previous coin discovery and the current one. Everyone else in the network will accept this as the next page of the ledger.

The further in the past a page is, the surer you can be that the transactions on it are authentic. There’s way you can use a hash function to mathematically link pages into a chain so that you can’t change even a single figure on a page without breaking the entire chain. But I’m going to skip that part of the story.

So after a while you can sort of start forgetting about really, really old pages. But remember, you need to know the *current* balance for every account. Your wallet program may not need to know all of it personally, but most of the coin network should (so that wallets that are behind the times can catch up).

#### Catching up

Now the huge ledger problem is kind of solved. But what about the fraudster who tries to buy something from you using someone else’s coin while your wallet is still catching up after a long hiatus from the Internet? The obvious answer: wait for your wallet to catch up before you consider a payment from someone as final. Even if you were never disconnected from the Internet, still wait a while. The fraudster may be trying to pay using the same coin on opposite sides of the world. It may take a while for whole network to catch up. With the kind of Internet that we have today, this period would probably be in the order of minutes.

So do we have everything in order? Let’s see:

1. A ‘coin’ is a mathematical thing — each represented by a unique coin number (or a string) so you can send it over a data network (like the Internet).

2. Its supply is mathematically limited by the difficulty in computing valid coin numbers.

3. We did away with both individual fraudsters and corrupt central exchanges in one swell swoop by introducing an open, global ledger that anyone can verify.

4. We made the transactions anonymous by giving anybody the ability to open a coin account (it’s just a number).

5. We made sure the transaction announcements were from the real coin owners by making them sign their announcements with their digital signature.

6. We solved the problem of the huge ledger by chunking transactions into pages and letting old pages be forgotten.

7. We solved the problem of who creates these pages by making it part of the math problem that gives you new coin numbers.

8. And of course, we want you to wait until the latest transactions come to your copy of the global ledger before considering any coins you received final.

What I just described isn’t exactly Bitcoin, but the theory is the same. If you understand the logic, you should be able to understand Bitcoin about as much as I have. The real thing only differs in specifics.

#### Appendices

[^1]:
    #### How can something produced out of thin air have value?

    How can something generated in a computer have any value? Let me ask you a question back. What makes a grain of rice different from a grain of sand? What gives the first thing value while the second thing is almost worthless (unless you’re in construction). Is it the fact that you can *eat* rice? Then what about breathable air? That’s a lot more valuable than rice but we seem to care even less about it than we do about sand. That’s because it’s scarce. So something has to have both *utility* and *scarcity* for it to be considered valuable. A uniquely shaped dog turd you see on the way home may be scarce, but that doesn’t make it valuable on its own (I know, that’s a terrible example).

    So what makes Bitcoin valuable? In addition to having mathematically-enforced scarcity, it does in fact have what an economist would call an *intrinsic value*. It has properties that make it a much better medium of value exchange than anything we have. *That’s* it’s utility. If you’re still not convinced, consider what all modern paper money is: it’s just ink on paper. It has value because the government says it has value. Or as an economist would tell you, it’s currency by *fiat*. They used to be backed by gold, but not any more. Many people (at times myself included) dream of returning to the good old days of gold backed currencies where modern inflation rates would be unthinkable. But something like Bitcoin could potentially be even better than gold. Who knows? Even experts have trouble predicting this one. And I’m certainly no expert.

[^2]:

    #### One-way functions

    If someone presents you the problem “what is the number N, when multiplied by two gives you six?”, or N x 2 = 6, you can easily do the reverse calculation and get the answer: 6 / 2 = 3.

    But there are certain calculations where there is no reverse. Consider for example, the problem “add up the alphabetical positions of the letters in the word ‘CAT’, where A = 1, B = 2, C = 3, etc”. The answer is easy: C + A + T = 3 + 1 + 20 = 24.

    But what about the reverse? For example “find a name of an animal so that the letters add up to 100″: ? + ? + ? + … + ? = 100. There is no way to do it except to keep trying different words until you hit upon the right answer.

    ELEPHANT = 81

    RATTLESNAKE = 126

    ANTEATER = 88

    ...

    You’re just going to have to keep guessing until you get 100. However, once somebody finds an answer, it’s extremely easy to verify that it’s correct — just add up the letters.

    At least in the above example you have a hint — you know ANT is too short and HIPPOPOTAMUS is probably too long. But the the type of functions we are talking about, called one-way hashes, give you results that change radically even if a single character in the input is changed. There is absolutely no way to gradually tweak the input until you get the right number. You have to keep guessing wildly. In addition, unlike the ANIMAL = 100 problem above, which can have multiple solutions, these hash functions usually give you a unique result for a given input.

    For example, hashing the line “To be, or not to be, that is the question” using the hash function SHA1 (Secure Hash Algorithm 1), you get the result:

        > f1738b02767494315c0e91503dce14387bf0686c
        
    But if you remove just the first comma, (“To be or not to be, that is the question”), you get:

        > 492f24918f1c8b059e3d532c1c3d9d43e60eac58

    A radically different result. [Try it for yourself](http://www.sha1-online.com/).

