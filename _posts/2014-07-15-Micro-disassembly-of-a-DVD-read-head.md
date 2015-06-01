---
layout: post
title: Micro-disassembly of a DVD read head
---

Armed with a Phillips screwdriver, a pair of tweezers and a 300x digital microscope, I decided to delve into the innards of this three year old Chinese-built DVD player. What follows are some of the interesting things I found inside.

![1](/public/images/2014-07-15-dvd/1.jpg)

I'll be concentrating on the read head (1) below, which slides back and forth along the metal rod (2) as the disc turns:

![2](/public/images/2014-07-15-dvd/2.jpg)

Removing the plastic cover:

![3](/public/images/2014-07-15-dvd/3.jpg)

Here's a closeup. You can see two magnets (1), (2) on either side of the lens/laser and two pairs of tiny cables (3), (4) doing, well, *something* (which we will discover next):

![4](/public/images/2014-07-15-dvd/4.jpg)

Time has now come to pull out the big gun, namely the microscope. Training it on one of the magnets on either side of the lens (see (2) in the last image), I get this:

![5](/public/images/2014-07-15-dvd/5.jpg)

Fancy, isn't it? Right next to the permanent magnet (1) are two electromagnets (2) and (3). Notice the extremely fine gap between the magnet and the electromagnets. The magnification here is around 200x:

![6](/public/images/2014-07-15-dvd/6.jpg)

What do the electromagnets do? Following the copper wire lead me to the cable coming from the main board. Conclusion: I think this is the mechanism that compensates for the dumb drive motor. The drive motor gets the read head in the general neighborhood. Then small regulated currents to the electromagnets do fine-grained positioning. The suspension system probably also helps absorb vibrations that might cause the head to lose its place. Ingenious.

And here's the laser emitter -- a tiny chip hiding beneath the lens:

![7](/public/images/2014-07-15-dvd/7.jpg)

So after stripping away everything else, we find that this tiny little piece is the heart of the entire device. It emits the laser and almost certainly contains the sensor that detects the beam reflected off the DVD too. The sensor can't be far away. The beam displacement caused by the marks on a DVD's surface is very tiny (see the first image on [this How Stuff Works article](http://electronics.howstuffworks.com/dvd-player1.htm) for a schematic version). So let's look at the thing closer:

![8](/public/images/2014-07-15-dvd/8.jpg)

There you have it. It's hard to imagine that such a small thing can do such a big job. That black thing to the upper right is a strand of my hair, for comparison. There are 11 inputs/outputs. So I'm guessing it contains both the laser and the sensor. Quite frankly, I couldn't find anything else that could possibly house either.

Some of the optics that guide the laser:

![9](/public/images/2014-07-15-dvd/9.jpg)

