---
layout: post
title:  "Code Cleanliness Ratio"
date:   2018-11-07
categories: post
comments: true
excerpt_separator: <!--excerpt_end-->
image: /assets/images/code1.png
---

Code Cleanliness Ratio (CCR) is the number Domain Words found
in code, file names, and folder names 
divided by the total number of words (including file and folder
names) in a software code repository.

<!--excerpt_end-->
![Required](/assets/images/code1.png)

Software code is filled with words and sentences that don't help
finding what the project is about.

Some examples of this words are: "for", "if", "util", "service",
"processor", "String", "int, and many more.

The main issue with these words is that make difficult to see
the intention of the project itself.

It's more clear to see code like this:

```java
Invoice.ifItWasPaid().then().sendToCustomer()
```

than seeing this

```java
public static void main(String args...) {
  Invoice invoice = new Invoice(input)
  boolean wasPaid = invoice.wasPaid
  if (boolean) {
    invoice.sendToCustomer()
  }
}
```