---
layout: post
title:  "I don't want to write unit tests"
date:   2016-06-4 18:00:56 -0500
categories: post
comments: true
---

Have you ever felt that good sensation when you fix **duplicate code**?
I am sure you have felt that satisfaction when you know that you did 
the right thing and everybody is happy about it.

![Required](/assets/images/winter.jpg)

Have you ever felt the same satisfaction when you create a **unit test**? 

_Probably not._

The creation of a unit test may be more important than duplicate code 
elimination.

You may think this process is a waste of time and we shouldn't bother
to create unit tests for code that is already working.

_But - is it really a waste of time?_

Refactoring a piece of code is something we can feel **proud** 
about, something we can show off to our team, and something that makes 
us **feel good**.

Creating a unit test is not something you can feel proud about. It’s 
not something you can brag about to your teammates or something that 
makes your team leader proud of you.

Maybe this is because most of the time the **execution** of this unit test 
is hidden until you or some other developer **breaks it**. 

The **truth** is that _unit tests_ make refactoring much **easier**. 
There are more software bugs related to a missing unit test than bugs 
related to missing refactorings.

We need a well suite of unit tests before doing a **bug-free** refactor. 
Thus, unit tests are even **more important** that refactoring.

Unit tests and functional tests are the **specifications** and design of our 
**system**. We cannot develop a system without requirements. 

_**Unit and functional tests are more important than the production code.**_
 
Writing the production code is a **technical** task. 
Designing a system is an **engineering** task.

Unit and functional tests represent the description of our system, 
they tell us what the system **does**, how we can **use** it and what the 
business rules and use cases are. 

*Why do we hate them so much and try to avoid them?*

Software companies use tests as a **quality control** which has to be executed 
executed at **the end** of the SDLC. 

Functional tests should be defined **before** starting the code development 
and they should be executed **every time** the system is compiled.

Let’s give unit tests the place they deserve in our code, which is the 
**base for the requirements** and the **description of our system**.