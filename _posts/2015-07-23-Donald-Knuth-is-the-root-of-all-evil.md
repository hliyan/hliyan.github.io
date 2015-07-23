---
layout: post
title: Donald Knuth is the root of all evil
---

Trying to optimize your code before you know which parts of it consume the most time and resources, or worse yet, doing so even before you know whether  your code runs slowly at all, is bad. But so is dismissing preperation, precaution and diligence with a pithy one-liner you picked up from a paper you haven't read, written by an author whose original meaning you don't seem to have deciphered.

I speak, of course, of the notorious:

> "Premature optimization is the root of all evil." - Donald Knuth

<!--break-->

Or, one of the very few phrases you may not utter in my presence without risking being told to "get out" in a very Jobs-like fashion. I have heard this phrase being used by developers for everything from justifying their sloppy implementation to silencing someone who has pointed out a bottleneck in the code. Every single time a developer (including a younger version of myself) tried to follow this "advice", it has ended up making my job harder (often *much harder*), not easier.

Here is the full quote:

> "Programmers waste enormous amounts of time thinking about, or worrying about, the speed of noncritical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%." - Donald E. Knuth, *Structured Programming With Go To Statements* [^1]

This is a quote from, if I may say so, a more civilized age (1974) when programmers worked much, much closer to the hardware and almost always had more formal training than their modern counterparts. Cautioning them against too much caution made sense. To take a part of this statement, drop the qualification that comes immediately after it and then quote it *ad nauseam* in a condescending tone is enough to get even the likes of me riled.

I don't know the size, performance expectations or the language of the types of programs Knuth was referencing here. I confess I haven't had the time to read the 40-page paper in full (although perhaps someday I should set aside the time). But I don't think one needs to do so to know that the quote, in the spirit it is used today (which roughly translate to "implement now, optimize later") is no longer universally applicable (if it were ever applicable at all).

A better alternative: be mindful of *Amdahl's Law* [^2] and the cost of I/O:

![cost of IO](public/images/2015-07-23-knuth/cost-of-io.png)

[^1]: [Structured Programming With Go To Statements](http://web.archive.org/web/20130731202547/http://pplab.snu.ac.kr/courses/adv_pl05/papers/p261-knuth.pdf), Computing Surveys, Vol. 6, No. 4, December 1974, p268

[^2]: [Amdahl's Law](https://en.wikipedia.org/wiki/Amdahl%27s_law)