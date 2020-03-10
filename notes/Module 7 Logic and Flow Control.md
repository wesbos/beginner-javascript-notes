---
attachments: [Clipboard_2020-03-10-07-05-03.png, Clipboard_2020-03-10-07-05-06.png, Clipboard_2020-03-10-07-10-48.png, Clipboard_2020-03-10-19-08-05.png]
title: 'Module 7: Logic and Flow Control'
created: '2020-03-10T11:02:14.437Z'
modified: '2020-03-10T23:20:21.715Z'
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

Although all three conditions above are true, the second and third blocks will never run because the first condition evaluates to true and runs. An if statement will look for the first condition that evaluates to true and then it only runs that block, it will skip the rest. 

If you wish to check for whether multiple things are true, you'd have to have three separate if statements rather than one big if else statement, like so:

```
if( 10 > 2 ){
  console.log('Yep');
}
if( 11 > 10){
  console.log('Yep')
}
if (3 > 1) {
  console.log('Yep');
}
```

Additionally, if nothing is matched, you can chain a `else{}` onto the if statment like so:

```
if ( age > 70){
  console.log('In your seventies');
}
else if ( age > 60){
  console.log('In your sixties');
}
else if (age > 50){
  console.log('In your 50s');
}
else {
  console.log("nothing was true");
}
```

"nothing was true" will be logge if age is less than 50. 

Notice that the `else` statement does not have parenthesis () like the if and else if statements. That is because else never has a condition. It is a catch all which runs if none of the conditions are true. It's similar to the default that we learne about in the switch statement. 

Let's say we take the following code :

```
const age = 100;
if ( age > 70){
  console.log('In your seventies');
}
else if ( age > 60){
  console.log('In your sixties');
}
else if (age > 50){
  console.log('In your 50s');
}
else {
  console.log("nothing was true");
}

```

If you run that in the console, what would you see? You should see "in your seventies". 

![](@attachment/Clipboard_2020-03-10-19-08-05.png) 4:39

Even though that the rest of the conditions are true, because the first condition is true, none of the other conditions are evaluated or run. That is important to keep in mind if you're working with multiple things that could be true. You need to be aware of the order of which you check your if statements. 

Now we will talk about if statements inside of a function, which is likely something you will come across and use to return different values. 

```
  function slugify(sentence, lowercase) {
      if(lowercase){
        return sentence.replace(/\s/g, '-').toLowercase();
      }
      else {
        return sentence.replace(/\s/g, '-');
      }
    }
```

We have this slugify function, which takes in a sentence and then takes in a Boolean, which is either going to be true of false based on whether we should lowercase it or not, and then we return that sentence but we call the .replace() method on it. 

You may be wondering about this line of code:

```
sentence.replace(/\s/g, '-').toLowercase();
```

This is a **regex**, which stands for regular expression. A regular expression is a way to match characters in a string. 

A regex always starts and closes with a forward slash `/` and then you type in different characters. 

In our case, we want to pass the space character which is `\s`. `g` stands for global, which means find them all, not just the first one. Then we replace it with the dash and call toLowercase. 

If you open the html page in a browser and type into the console `slugify('I am very cool')`, it will return "I-am-very-cool".  It puts dashes where spaces were. 

If you were to run that same code but pass a second argument of true, it will lowercase it as well and return "i-am-very-cool". 

6:28
