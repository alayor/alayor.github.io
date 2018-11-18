---
layout: post
title:  "Code Cleanliness Ratio"
date:   2018-11-07
categories: post
comments: true
excerpt_separator: <!--excerpt_end-->
image: /assets/images/code1.png
---

Code Cleanliness Ratio (CCR) is the total number `Domain Words` found in a 
software code repository divided by the total number of words
in the repository.

<!--excerpt_end-->
![Required](/assets/images/code1.png)

Most of the time software projects are filled up with words and sentences that don't help
to figure out what the projects are about.

Some examples of these words are: `for`, `if`, `util`, `service`,
`processor`, `String`, `int`, and many more.

These words make it difficult to find out the intention of the project.

For instance, it's more clear to see code like this:

```java
Invoice.ifItWasPaid().then().sendToCustomer()
```

than seeing this

```java
public static void main(String args...) {
  Invoice inv = new Invoice(input)
  boolean wasPaid = inv.wasPaid
  if (boolean) {
    inv.sendToCustomer()
  }
}
```

The formula to calculate the Code Cleanliness Ratio is:


CCR = &#x2211;DW / &#x2211;W


where &#x2211;DW is the number of words that belong to the `Domain Words`
and &#x2211;W are the total number of words.

We consider "words" as all the variables, sentences, signs,
file names, folder names, etc.

The `Domain Words` are the words related to the domain of the
software application or solution.

Examples of `Domain Words` in a Travel Software Application are:

* `Flight`
* `Origin`
* `Destination`
* `Reservation`
* `Booking`
* `Check-in Date`
* `Check-out Date`

Naturally, we do need to write language-specific words like `if`, `for`, `while`, etc. in order
to build our system. However, we can sometimes hide them behind reusable libraries.

Let's calculate the CCR of our previous code. 

Suppose the `Domain Words` are the following:

* `Invoice`
* `Paid`
* `Send`
* `Customer`

Let's analyze the first example.

```java
Invoice.ifItWasPaid().then().sendToCustomer()
```

If we consider camel case names as separate words.
The Total Words &#x2211;W would be <b>9</b>. (`Invoice`,`If`,`It`,`Was`,`Paid`,`then`,`send`,`To`,`Customer`) 

Given that only `Invoice`, `It`, `Send`, and `Customer` belong to the
`Domain Words` the &#x2211;DW would be <b>4</b>.

So, the Code Cleanliness Ratio of this code is

```javascript
CCR = 4 / 9 = 0.44444
```

Let's analyze our second example using the same Domain Words list.


```java
public static void main(String args...) {
  Invoice inv = new Invoice(input)
  boolean wasPaid = inv.wasPaid
  if (boolean) {
    inv.sendToCustomer()
  }
}
```

&#x2211;DW is <b>6</b> and &#x2211;W is <b>23</b>.

So, the Code Cleanliness ratio of this code is

```javascript
CCR = 6 / 23 = 0.26086
```

We can improve the CCR of our latest code by changing the 
variable name `inv` to `invoice`, resulting in &#x2211;DW = <b>9</b> 
which it would result in a CCR of `0.391304`

```javascript
CCR = 9 / 23 = 0.391304
```