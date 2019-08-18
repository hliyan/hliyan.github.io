---
layout: post
title: Things I believe about engineering
date: 2019-08-18 01:00:00
---

## What is the most important thing?

    “The most important property of a program is whether it accomplishes the intention of its user.” ― C.A.R. Hoare

Technology is not an end in itself, but rather a means to an end. The end is that which your software (or even your hardware, your machine or your building) hopes to accomplish for its user. The user depends on you, and you in turn depend on the user, because in the final analysis it is the user who pays your salary. Putting technology before the user is no more sensible than putting medicine before the patient.

## What is engineering?

    “First solve the problem. Then, write the code.” ― Waseem Latif

    “Some of the best programming is done on paper, really. Putting it into the computer is just a minor detail.” ― Max Kanat-Alexander

What sets an engineer apart from a mechanic, a technician or a coder? They all build things, or at least, rebuild things. The difference is that the engineer builds it in his mind first. He is able to do so because he understands the principles underlying the the things he builds. He can predict how something behaves without having to build it first. And this is why design is the thing that sets an engineer apart from non-engineers. And it is also why an engineer must know the principles that govern his domain, for without it he cannot design. One does not become an engineer by googling for code, any more than one becomes a physician by googling for treatments.

## What is hacking?

The value of hacking is speed. It achieves this by sacrificing rigor. When solving problems that don’t have a clear solution path, hacking, or rapidly evolving a solution through trial and error, is desirable. In other words, it is a form of experimentation. But do not experiment on your user. He depends on you. Do your hacking well away from production.

## What is software engineering?

Civil engineering has evolved over millennia; mechanical engineering over centuries; electrical and electronic engineering over decades. Their practitioners have had time to make most of the possible mistakes in their domain, learn from them and solidify those learnings into a discipline. Yet software engineering does not seem to follow this same path. Like a teenager that refuses to grow up, it resists discipline. Perhaps, that is because, like a teenager, it too, is still growing rapidly. The lessons are changing too fast to solidify into industry standards. But this is unlikely to be the case forever. Like the early civil engineering craftsmanship moved from the mythical domain of Masons into the hands of trained professionals, software engineering too, will one day move from the mythical domain of the 10x programmer in to the hands of trained professionals. We should expedite, not resit this. There is no human endeavor that did not benefit from forethought and method. Software engineering is unlikely to be the first exception to this in history. Strive for rigor.

## What is programming? And what is coding?

Programming is the process of converting a requirement into one or more algorithms operating on one or more data structures. It is a process, at its core, that is independent of languages, technologies, platforms or libraries. Coding is the process of encoding said algorithms and data structures into the syntaxes and interfaces provided by the programmer’s languages and technologies of choice. The combination of critical thinking and knowledge of algorithms and data structures makes one a programmer. Knowledge of languages, technologies and their sytnaxes and interfaces does not.

## What is code?

    “Programs must be written for people to read, and only incidentally for machines to execute.” ― Harold Abelson

Machines only require binary. Programming languages exist for human beings, and therefore code written in such languages must be produced with human comprehension in mind. Code that requires the presence of the author for explanation, has failed in its purpose.

## What is technology?

Technology is defined as the application of scientific knowledge for practical purposes. Different applications of the same scientific principles by different commercial entities do not constitute technologies, but products. Technologies must be known by their generic names before their tradenames, just as drugs must have generic scientific names before tradenames. In design, you must first choose the generic technology that meets the needs of your users, and only then search for specific products. Design is not technology shopping.

## Why is programming hard?

Programming is not hard. Programming very large programs is hard. Programming becomes easy when the problem is broken down into small enough pieces the right way. Break it down the wrong way, and you merely shift the difficulty from building to assembling.

## What is design?

Design is the process of determining how something is to be done, before attempting to do it. This is not to be confused with planning, which is the process of determining what is to be done in what order, when and by whom, before starting.

Design is a process of prediction, and therefore requires knowledge of the principles of the domain. Design is also a process of instruction: once the design is complete, the outcome should be a document that instructs either the author or another person on how to go about constructing the intended system.

The design process needs to be structured. Two individuals given the same constraints and tools, should not produce two wildly differing designs. Design documents need to be structured. Two individuals, given the same design, should not produce two wildly differing systems.

Design is needed when the system to be developed is too large or complex to be directly programmed from requirements. Therefore design can be thought of as a process of envisioning the whole system, and then breaking it down into progressively smaller components until each component reaches a level of simplicity that can be directly programmed. In this sense, design is recursive.

Designs need to be simple. The more parts there are in a system, the more parts there are to fail. Fewer parts are better.

## What is a component?

Anything that is a part of a whole is a component. In engineering, the nature of good components is that they are designed, built and verified as if they are systems in themselves: they have their own dimensions, tolerances and specifications. Once integrated into a larger system, the engineers of that largers system need not worry about the internals of the component, and for all intents and purposes, should be able to treat it as a black box that behaves as per specification. A component that fails to meet its specifications, or worse, has no specification to speak of, fails in its purpose.

## What is testing?

All theories except mathematics are approximations of reality. Even programs that are mathematically proven must run on real world hardware that lack mathematical precision or certainty. Therefore the only way erase any doubt that your program works, and does so under all conditions, is to actually subject it to each said condition and compare its behavior against expected behavior. This is the essence of testing.

## Who should test?

The burden of proof generally rests on he who makes the assertion. A mathematician is expected to prove his theorem before it is taken seriously. A scientist is expected to show data before his theory is taken seriously. However, in neither discipline is proof by the author taken at face value. It is reviewed and verified, usually by those who are neither friends nor colleagues of the author, so as to eliminate bias, conscious or otherwise. So it should be in engineering. A programmer must test everything that he has written, and demonstrate that he has done so. It is the job of quality assurance to ascertain that he has done as he has said.