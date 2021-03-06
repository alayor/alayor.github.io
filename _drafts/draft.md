---
layout: post
title:  "Behaviour-Driven Development"
date:   2016-09-24 21:45:00 -0500
categories: post
---

_"This feature is not correct. The process should be done biweekly -- twice
a week,"_ - The analyst said, _"This is totally different from the
feature I requested."_

This was the second demo meeting held with the business analyst to show 
this new feature and it was the second rejection.

_"We thought 'biweekly' meant every two weeks,"_ The programmer said,
_"We tried to follow verbatim every requirement in the user story, but
it seems it has ambiguities in some parts."_

_"Fair enough, I'll revisit it and try to correct any ambiguity"_ - The
analyst agreed.

What's the cost of this kind of misinterpretations? What can we do to
avoid them?

The reason why languages like english or spanish are not used to create
software is because these languages have ambiguities that hinders the
process for an interpreter to read and process.

Software specifications are written mostly in english -- so when 
interpreters (or programmers) try to process them, we sometimes 
end up with a software misbehaviour.

Behaviour-Driven Development is a process that intends to solve this
kind of problems by providing a common language that a business analyst
and a computer can read and process.

There are several frameworks, like Cucumber, that can be used to 
implement BDD.
Cucumber is a framework that provides a common language used to write 
software specifications.

Cucumber allows users to create _feature_ files that analysts can use to
write specifications and define the behaviour of new features as well
as the entire system.

Likewise, these files can be read by a computer and can be used to 
execute functional tests in order to find out if a particular behaviour
is being executed correctly.

BDD's main purpose is to solve communication problems inside a software
development team. However, we can use this tool in an interesting way 
when the specifications are defined prior the development of a new feature.

By having all the specifications defined previously, we can test anytime 
if our current development is meeting these requirements. We can also 
test if we are breaking existing functionality.

By using BDD, software development teams keep one source of truth that
enables the team to agreed on the real intention and purpose of any old 
and new feature. Teams can finally stop having misinterpretations
and communication problems when delivering new functionality.