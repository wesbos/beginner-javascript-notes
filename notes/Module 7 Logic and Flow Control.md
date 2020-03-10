---
attachments: [Clipboard_2020-03-10-07-05-03.png, Clipboard_2020-03-10-07-05-06.png, Clipboard_2020-03-10-07-10-48.png]
title: 'Module 7: Logic and Flow Control'
created: '2020-03-10T11:02:14.437Z'
modified: '2020-03-10T11:27:11.895Z'
---

# Module 7: Logic and Flow Control

## 37 - BEDMAS

If you know what BEDMAS is, skip this video.

![](@attachment/Clipboard_2020-03-10-07-05-06.png) 00:43

This video will be covering BEDMAS And the order of operations in which javascript runs. It is exactly the same as how mathimeticans use it. 

The order in which things run is that things in brackets go first, then we do exponents (which is sort of like the power of). 

We do have exponents in javascript. That looks like `2 ** 2` which is the equivalent of 2 to the power of 2.  `2 ** 10` is 2 to the power of 10.

Next is division, multiplication, addition and subtraction. 

Why is that useful? Open up `bedmas.html` and in the script tag, let's say we have the following..

```
const age = 10 * 5 - 2;
```

That evaluates to 48. Why? First we look for brackets -- there are none, then we move onto exponents, which there are also none of. We go to multiplication next, so 10 * 5 = 50 and then comes addition and subtraction so 50 - 2 = 48. 

Now what if we do..

```
const age2 = 10 * (5-2);
```

So first we evaluate what is in the brackets (5-2 = 3). Then we do exponents (there are none), and next comes multiplication so 10 * 3 = 30. 

This is useful in things like our `calculateBill()` function from previous lessons. 

![](@attachment/Clipboard_2020-03-10-07-10-48.png) 2:51

What is happening there is that all of the functions (`calculateBill(100)`, `calculateBill(20)`, `calculateBill(15)`) run first and equate to a value. 

So the `total` variable declaration is actuall evaluating the following:

`const total = 128 + (25.6 - 19.2)`

Because `calculateBill(100)` = 128 and `calculateBill(20)` = 25.6 and `calculateBill(15)` = 19.2

So in this case, the subtraction happens first (25.6 - 19.2) and then it's added to 128. 

That is order of operations. Next we will get into logic and flow control. If statements, truthy or falsy, equality using and and or, ternarry, switch statements, timers and intervals. 

--- 

## 38 - Flow Control - If Statements, Function Returns, Turthy, Falsy

If statements are the foundation of all logic in javascript. They expect Booleans, which are always either true or false, or they expect some sort of condition that is evaluated to true or false or truthy and falsy. 

First we will explain the mechanics of if statements using greater or less than operators firts, and the we will get deeper into other operators shortly.

At it's most basic, we have an if statement that looks like the following:

```
if( 10 > 2){
  console.log('Yep');
}
```

That is saying if 10 is greater than 2, console log "Yep". 

`if(10>2){console.log('Yep`);}` is the if statement. 

`(10 > 2)` is what is referred to as the **condition**. The condition is going to be evaluated to true or false. By evaluated, what we mean is that if you were to run that in the console (10 > 2) it would evaluate to true or false. 

There are the curly brackets which are opening and closing the block `{}`. Any code that needs to happen when the condition is true need to go within the block. 

We can also add an else if like so:

```
if( 10 > 2 ){
  console.log('Yep');
}
else if( 11 > 10){
  console.log('Yep')
}
```
You can also chain these else ifs as many times as you want. However, if the first one is true, even if the later ones are also true, they will never run. 

```
if( 10 > 2 ){
  console.log('Yep');
}
else if( 11 > 10){
  console.log('Yep')
}
else if (3 > 1) {
  console.log('Yep');
}
```

Although all three conditions above are true, the second and third blocks will never run because the first condition evaluates to true and runs. 

stopped @ 2:32
