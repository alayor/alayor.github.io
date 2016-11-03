---
layout: post
title:  "I Don't Want To Write Unit Tests"
date:   2016-06-4 18:00:56 -0500
categories: post
image: /assets/images/required.png
---

Have you ever felt that good sensation when you fix duplicate code?
I am sure you have felt that satisfaction when you know that you did 
the right thing and everybody is happy.

Have you ever felt the same satisfaction when you create a unit test? 
Probably not.

The creation of a unit test may be more important than duplicate code 
elimination. However, You might think this is wrong. 

You may also think this process is tedious and a waste of time 
because the code is already working and why shouldn't bother.
But, is that really a waste of time?

The reason could be that refactoring is something we can feel proud 
about, something we can show off to our team, and is something that makes 
us feel good when our team leader learns of this great achievement.

Creating a unit test is not something you can feel proud about. It’s 
not something you can brag about to your teammates or something that 
makes your team leader proud of you.

Maybe this is because most of the time the execution of this unit test 
is hidden until you or some other developer breaks it. Unit tests make
refactoring much easier. 
There are more software bugs related to a missing unit test than bugs 
related to missing refactorings.

We first need a well unit test suite before doing a bug-free refactor. 
This means that unit tests are even more important that refactoring.

Unit and functional tests are the specifications and design of our 
system. We cannot develop a system without requirements. Unit 
and functional tests are more important than our production code. 
Designing a system is an engineering task and developing the production 
code is a technical task.

Unit and functional tests represent the description of our system, 
they tell us what the system does, how we can use it and what the 
business rules and use cases are. Why do we hate them so much and try to 
avoid them?

Software companies see tests as a quality control tool which process is 
executed at the end of the SDLC. These tests should be defined before 
starting the code development and they should be executed every time the 
system is built or compiled.

Let’s give unit tests the place they deserve in our code, which is the 
base for requirements and the description of our system.