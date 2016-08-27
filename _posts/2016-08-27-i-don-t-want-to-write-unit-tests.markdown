---
layout: post
title:  "I don't want to write unit tests"
date:   2016-06-4 18:00:56 -0500
categories: post
---

Have you ever felt that good sensation when you fix duplicate code?

I am sure you have felt that satisfaction when you know that you did 
the right thing and you know that everybody is going to be happy and 
will see the great developer you are.

Have you ever felt the same satisfaction when you create a unit test? 
Probably not.

Why don’t we feel the same satisfaction given that the creation of the 
unit test is probably more important that elimination duplicate code?

Maybe you think that fixing duplicate code is much more important than 
the creation of a unit test. And even more important when we know that 
the method is already working. You also may think that this process is 
tedious and a waste of time even though we know it’s important. 
But, what's the reason for that?

The reason could be that refactoring is something we can feel proud 
about, something we can show to our team, and is something that makes 
us feel good when our team leader learns of this great achievement.

Creating a unit test is not something you can feel proud about. It’s 
not something you can brag about to your teammates or something that 
makes your team leader proud of you.

Maybe this is because most of the time the execution of this unit test 
is hidden until you or some other developer breaks it. One of the uses 
for a unit test is the ease of refactoring tasks, which by the way, 
sometimes these are not wanted because they also are a “waste of time”. 
There are more software bugs related to a missing unit test than to a 
missing refactoring.

We first need a well unit test suite before doing a bug-free refactor. 
This could mean that unit tests could be even more important that 
refactoring.

Unit and functional tests are the specifications and design of our 
system. We cannot develop a system without requirements, thus, unit 
and functional tests are more important than our production code. 
Designing a system is an engineering task. Developing the production 
code is a technical task.

Unit and functional tests represent the description of our system, 
they tell us what the system does, how we can use it and what the 
business rules and use cases are. Why do we hate them so much and try to 
avoid them?

Software companies see tests as a quality control tool which process is 
executed at the end of the SDLC. This tests should be defined before 
start the code development and they should be executed every time the 
system is built or compiled.

Let’s give unit tests the place they deserve in our code, which is the 
base for requirements and the description of our system.