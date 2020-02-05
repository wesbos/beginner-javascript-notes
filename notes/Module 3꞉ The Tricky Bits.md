---
attachments: [Clipboard_2020-02-03-18-47-58.png, Clipboard_2020-02-03-19-52-11.png, Clipboard_2020-02-03-19-52-56.png, Clipboard_2020-02-03-20-03-38.png, Clipboard_2020-02-03-20-14-11.png, Clipboard_2020-02-03-20-21-45.png, Clipboard_2020-02-03-20-22-13.png, Clipboard_2020-02-03-20-22-53.png, Clipboard_2020-02-03-20-43-38.png, Clipboard_2020-02-03-20-44-06.png, Clipboard_2020-02-03-20-55-28.png, Clipboard_2020-02-03-20-57-52.png, Clipboard_2020-02-03-21-10-13.png, Clipboard_2020-02-03-21-10-48.png, Clipboard_2020-02-04-13-16-53.png, Clipboard_2020-02-04-13-22-11.png, Clipboard_2020-02-04-13-23-59.png, Clipboard_2020-02-04-13-24-16.png]
title: 'Module 3: The Tricky Bits'
created: '2020-02-03T23:25:39.261Z'
modified: '2020-02-05T02:21:20.132Z'
---

# Module 3: The Tricky Bits

## 17 - Scope

We have touched on scope a few times throughout the course already because it's impossible to talk about variables without touching on scope. 

What is scope? Scope answers the question where are my variables and functions available to me. 

So far in the course, we have been making functions and variables and they have generally been available anywhere we wanted them. We have also seen some issues like when you create a variable inside of a function, and they're not available outside the function, that is what scope is. 

First, go to the playground folder and create a new file called `scope.html`, and use your html base inside of it. Add a script src to a file called `scope.js` which will live in the same directory. 

```
<script src="./scope.js"></script>
```

Add a new file in `/playground` called `scope.js` and add a `console.log('It works!');`.  Open the file up in the browser to make sure it works. 

We will start by taking about the first type of scope which is what are called **global variables**. Global variables are if you have a script tag, or javascript file, or run it in the console, anytime you declare a variable, it will be available anywhere in the application. 

For example, if you add in `scope.js` `const first = 'wes';` and then in the console type `first`, it will return the value of first. Also, if you were to add another script tag in `scope.html` like so, will it work?

```html
  <script src="./scope.js"></script>
    <script>
      console.log(first);
    </script>    
```

That does work, the console will log "wes". 
Why does it work? Because when you just go ahead and create a variable in a javascript file, not inside of a function, not inside of a module, not inside of an if statement, when you just create it out in the open, that is what is referred to as a global variable. You can access global variables from any other javascript htat is running on the page like a scritp tag or via the console. In the browser, the global scope is called the window. 

If you go ahead in yoru browser and type in Window, you will see every single thing that is attached to the global scope is inside of the window.  

![](@attachment/Clipboard_2020-02-03-18-47-58.png)

That is why sometimes you will see people doing things like `window.setTimeout()`. There is also just regular, old, `setTimeout()`, both are the exact same thing. Methods that are globally available to us like `setTimeout()` are actually on the window object, and that is what is called global. 

There is one thing to know about `const` and `let`.

Let's say we added this code to `scope.js`.

```
/*  eslint-disable */
const first = 'wes';
let second = 'bos';
var age = 100;
```

if you reload `scope.html` in the browser and then in the console type in `first`, `second` and `age`, you will see the following values returned because they are all global variables:

![](@attachment/Clipboard_2020-02-03-19-52-11.png)

However, if you type in `window.first` and `window.second` you will get undefined but when you type in `window.age` it will return 100. 

![](@attachment/Clipboard_2020-02-03-19-52-56.png)

This is because var variables are attached to the window object and they are globally scoped, and const and let variables when declared like the example above are still globally scopped, they are just not attached to the window. That is not really all that important because you shouldn't be making global variables anyway. This was just to demonstrate why sometimes people write `window.` or just type the global variable directly. 


The same thing goes with functions. 
If we make a function `function sayHi(){console.log('hi!');}`, we can call it:

1.  from a script tag on the html page like so: 
```js
  <script src="./scope.js"></script>
    <script>
      sayHi();
    </script>
```

2. typing `sayHi()` in the console
3. typing `window.sayHi()` in the console. 

Why is it available at `window.sayHi()`? Because anything that is in the global scope is attached to the window object with the exception of const and let variables. 

Using global scope is almost never a good idea, but before we learn why that is, we need to learn about how different parts of scope work. 

Let's get rid of the `<script>sayHi();</script>`  code in `scope.html`. Remove everything within `scope.js`. In `scope.js`, add `const age = 100;`. 

Create a function called `go()`, and we will `console.log(age); console.log(hair);` further down the page.  

```js
const age = 100;
function go(){
  const hair = 'blonde';
}
console.log(age);
console.log(hair);
```

When we `console.log(age)`, is it going to be 100? When we `console.log('hair')`, will it be blonde?

![](@attachment/Clipboard_2020-02-03-20-03-38.png)

Age returns 100, but hair throws a reference error. Maybe that is because we did not run the `go()` function, we just defined it? Let's try runnin to go function so that variable gets declared. Before `console.log(age);` add `go();`. If you refresh the page and look at the console, we will still see the error. Why?

This is the next type of scope which is called **function scope**. What function scope is, is when variables are created inside of a function, those variables are only ever available inside of that function. That means that anything we create inside of the `go()` function, is not available outside of that function, unless we were to explicitly return it and put it into it's own variable when that function is run. 

If you modify the `console.log(hair)` to be within the `go()` function, it will log.

```
function go(){
  const hair = 'blonde';
  console.log(hair);
}
```

You can think of the curly brackets in functions as gates. They keep the variables in and do not allow them to leak out. 

Now is that the same for the opposite? If we were to `console.log(age)` from within the `go()` function, would that work? If variables can't leak out, can they go in? If you refresh the page and look at the console, you will see it worked.

This is an interesting thing about javascript and most programming languages. Variables, if they are not found inside of a function, will go up a level higher and look for a variable n that scope. If it's not available in that scope, it will go up a level higher. We will talk about multiple nested scope in just a second. 

So what is happening is inside the `go()` function the code is saying, "there is no variable inside of this function called age, so I will go up one more level and look up". 

Now if we added as the first line of the `go()` function, `const age = 200;` and refresh the page, is that going to error? Is that going to be 200 or 100? It's will be 200. 

Two things: is that allowed? and why it is 200?

It's 200 because it looks in the local function first and it does find a variable called age. However, if it is not found, it will go one level higher and look for it at that level. Why is this allowed? Why is it not breaking? If you however over the variable in VSCode, you will see an error in ESLint that says 
> 'age' is already declared in the upper scope.

![](@attachment/Clipboard_2020-02-03-20-14-11.png)

That is what is referred to as shadow variables. You can name variables the same thing, if they are not in the same scope. However, its not a good idea because if you name a variable something that is the same as in another scope, you limit yourself to being able to access that. 

In this example:

```
const age = 100;
function go(){
  const age = 200;
  const hair = 'blonde';
  console.log(age);
  console.log(hair);
}
```
If we wanted to access the `age = 100;` from the `go()` function, there is absolute no way to do that because the variable has been shadowed (meaning it has been over-written).

A tip is that if you ever have a variable inside of a function that is very similar to a variable outside of a function, name the variable inside of the function more specifically so you have access to both. In this case, inside of the function you could declare a variable like `const myAge = 200;` instead of just calling it `age`. 

The next type of scope is **block scope**.

We will start by talking about `var`, `let`, and `const` variables and how they are scoped differently. `const` variables cannot be reassigned, and `let` and `var` variables can be re-assigned. They have a different way of how they are scoped. 

Let's do an example. 

Will this code work?
```js
if(1 === 1){
  const cool = true;
}
console.log(cool);
```

No, it throws the following error: 
![](@attachment/Clipboard_2020-02-03-20-21-45.png)

What if we make it a `var` variable instead?

```js
if(1 === 1){
  var cool = true;
}
console.log(cool);
```

It works! ![](@attachment/Clipboard_2020-02-03-20-22-13.png)

What if we make it a `let` variable?

```js
if(1 === 1){
  let cool = true;
}
console.log(cool);
```

It doesn't work.
![](@attachment/Clipboard_2020-02-03-20-22-53.png)

What is hapepning there is whenever you have a set of curly brackets like in the if statement above, that is what is referred to as a block. (Blocks will be showing up in most places, the most common is probably an if statement. We will have lots more examples throughout the course.)

You can think of those brackets are gates. Those gates keep variables in. Anytime something that was created inside of these gates, they are not allowed to leave the gates. If you need to access a variable that was created inside of the gates, outside of the gates, you are not allowed to do it. 

There are a few solutions to that because every now and then you run into a situation where you do need a variable to be available outside of a block. 

What happens is you have to create the variable above it, as we will demonstrate in this example:

```js
let cool;
if(1 === 1){
   cool = true;
}
console.log(cool);
```

In this example, we have declared a variable cool without assigning anything to it, and then on the line that previously had `let cool = true;`, we do not declare the cool variable, we simply update it. 

What that does it creates it's in the higher scope (in this example it is a global variable but if this was created inside of a function it would be function scoped). Then, we update the variable, and then it's available to us outside of the function. 

Here is another example that is a more realistic, where we are getting into two different kinds of scopes:

```
function isCool(name){
let cool;
if(name === 'wes'){
   cool = true;
}
console.log(cool);
return cool;
}
```

So what is going on here is we have one scope, which is the function scope (`function isCool(name){...}`). One thing that can get cnofusing is that a function also has a block, so any let, var of const variables are automatically scoped to a function, because regardless if its a function or a block, it's a set of curly brackets so it's scoped to that. 

And then we have blocked scope which is within the `if(name === 'wes'){...}`. 

Again to demonstrate, if we changed the `cool` variable within the if statement to a const variable, like in this example, it would not work:

```
function isCool(name){
let cool;
if(name === 'wes'){
   const cool = true;
}
console.log(cool);
return cool;
}
```

However, the example below does work:

```
function isCool(name){
let cool;
if(name === 'wes'){
   cool = true;
}
console.log(cool);
return cool;
}
```

Although we went over how to solve the fact that variales are blocked scope, in most cases that is not something you need fixed, and it is actually really nice to have blocked scope because you don't have to variables leaking out of it. 

In the past, we have had for loops such as the following:

```
 for(var i = 0; i < 10; i++) {
   console.log(i);
}
```

That will log 0 -9 like so ![](@attachment/Clipboard_2020-02-03-20-43-38.png)

If you type i in the console, it will return 10

![](@attachment/Clipboard_2020-02-03-20-44-06.png)

We have this random variable that is out floating called `i`, which should have been contained within the for loops but because it's a var, it has leaked outside. By simply making it a `let` variable, that random `i` variable will no longer be floating because it will be scoped to the curly brackets. 

Block scoping is one of the reasons people say use `const` by default, `let` when you want to re-assign it and don't use var unless there is a specific use case for it. 

To go back to our example earlier with `isCool()`, we could have also solved it by changing the cool variable to a var like so

```
function isCool(name){
if(name === 'wes'){
   var cool = true;
}
console.log(cool);
return cool;
}
```
Why does that work? Because it's a `var` variale. `var` variables are not block scoped, they are function scoped. So they are available outside of the if statement block, but they are only available inside of the `isCool()` function. 

We will do another example of scope look-up to solidify that concept. 

```js
const dog = 'snickers';

function logDog() {
  console.log(dog);
}

function go() {
  const dog = 'sunny';
  logDog('sunny');
}

go();
```

What is going on here? We have a variable `dog` which is set to `"snickers"`. We have a function that will log a variable called dog, `logDog()`, and then we have a function called `go()` that creates a variable named `dog` again that is set to the value of `"sunny"`, and then we run that `logDog()` function, and then we run `go();`. 

When we call the `logDog()` function, is it going to log "sunny" or is it going to log "snickers"?

You may think it will log `sunny` because we declare the dog in the function scope, so when the function runs, shouldn't it look in it's own scope for that? Or you might think it may run snickers becaue the function is declared within a dog variable inside of it so it will look up for that variable. 

What does it log? snickers! ![](@attachment/Clipboard_2020-02-03-20-55-28.png)

Even though we ran the `logDog()` function within the `go()` function and that function has a locally scoped variable called "sunny", it's still logging "snickers". 

That is because javascript is what is referred to as **lexical scoping** or **static scoping**. (those are buzz words in javascript). What that means is the way that variable look-up or scope look-up happens, is where the functions are defined, not where they are run.  So even though the `logDog()` function is run inside of another function which has a locally scoped `dog` variable, it doesn't care about where it's run, it cares about where it is defined.

Because `logDog()` is defined where it is, since it doesn't have a local variable named dog, it will just go up one level.

![](@attachment/Clipboard_2020-02-03-20-57-52.png)

Ideally the function `logDog()` would take a parameter of `dog` and then log whatever parameter value it is passed like so:

```js
const dog = 'snickers';

function logDog(dog) {
  console.log(dog);
}

function go() {
  const dog = 'sunny';
  logDog('Rufus');
}

go();
```

Now that console will show "Rufus". Why? Because when a function takes in an argument, it will make local variables inside of that function named whatever you named the parameter, and then that is availble to them. 

It is the same as doing:

```
function logDog(dog){
  const dog = whateverYouPassedInAsTheFirstArgumentToTheFunction;
  console.log(dog)
}
```

That is what javascript is essentially doing behind the scenes. It is taking the value that you pass the first parameter and making a local variable for the function. 

So if you did 
```js
function go() {
  const dog = 'sunny';
  logDog(dog);
}
```

The code doesn't care what you called the variable that you as passing in, it just cares about the value. 

The example above is the same thing as just passing in a string of sunny like so:
```js
function go() {
  const dog = 'sunny';
  logDog('sunny');
}
```

We will go over best practices and many more examples in the course. 

**Best Practices**

1. Try not to create global variables 
    - it is fine for us to create them while doing these examples and when we get into modules, it is almost impossible to create global variables unless you explicitly do something like `window.IAMGlobal = 'wes'`. Unless you explicitly attach it to the window, with a module, it is very hard to create a global variable which is intentional.  


2. Functions are scoped the exact same as variables
-  Can you create a function inside of another function? Absolutely. We will look at examples of why you might want to do that later. Here is an example:

```
function sayHi(name){
  function yell(){
    console.log(name.toUpperCase());
  }
  yell();
}
```

If you were to write `sayHi('wes')` in the console, it will yell `WES`. 

![](@attachment/Clipboard_2020-02-03-21-10-13.png)

However if you try to call the `yell` function outside of `sayHi()`, it will throw an error:

```js
function sayHi(name){
  function yell(){
    console.log(name.toUpperCase());
  }
  yell();
}

yell();
```

What is happening there is just like variables, functions are scoped to the parent function. If you create a function inside of another function, that function will only ever be available inside of that. That is starting to open up what is referred to as a closure, which is a more advanced example we will go over in the future. 

It is possible to do a function inside of a function, but generally, you won't be doing that. 

---

## 18 - Hoisting

We talked about this a little bit before. Now we will get into the details about what it is, when you can use it and why you might want to use it. 

Hoisting in javascript allows you to access functions and variables before they have been creatd.There are two things in javascript that are hoisted: function declarations and variable declarations. 

We will focus on function delcarations first. Make a `hoisting.html` file in the `/playgrounds` directory and give it the base html. Add a script src of `./hoisting.js` and create a new javascript file named `hoisting.js`. Do our usual `console.log('It works!');` to check that it works.

Make a function called `sayHi();`. If you try to run this function before it  exists, will it work? You can see ESLint is complaining with warning of:
>`sayHi` was used before it was defined. eslint(no-use-before-define)


```js
sayHi();

function sayHi() {
  console.log('hey!'); 
}
```
If you open `hoisting.html` in the browser, does it work? it does. Why is that?

When you run your javascript file, javascript hte compiler will take all of your function declarations and move them to the top of the file so they are all available before you use them. 

Because of hoisting, you can technically run a function before it exists. 

Let's make another example. Add the following function:
```
function add(a,b){
  return a + b;
}
```

If you use that function within sayHi(), like so: 

```
sayHi();

function sayHi() {
  console.log('hey!'); 
  console.log(add(10,2));
}
function add(a,b){
  return a + b;
}
```

Is that going to work? It does. 

![](@attachment/Clipboard_2020-02-04-13-16-53.png)

That is because hoisting moves them to the top before it will actually run anything.

So javascript rearranges the file and puts all the variable and function declarations at the top of the file. Why does that functionality exist? 

Wes hardly ever uses hoisting, he prefers to declare his functions before using them. Or when we get into modules, he prefers to put his separate functions in a module like util functions or math functions, and then import them as he needs them.

One argument Wes has heard for hoisting being useful is people often prefer when opening up a file, say you open up `hoisting.js`, they much prefer to have what does this file do ffirst, and the nhow does this file do it. That way if you are quickly jumping into a file, you can quickly see from the first couple of lines "what does this file do". We don't necessarily care how it works, we just want to know how it works. 

If you do care about what it does, you can go a bit further down into the file and see what it does. 

```js
/* What does this file do? */
sayHi();

/* How does this file do it? */
function sayHi() {
  console.log('hey!');
  console.log(add(10, 2));
}
```

Personally, Wes doesn't use this method very much and doesn't like it all that much but that is just his personal opinion.

The other type of hoisting is called **variable hoisting**. 

If you were to go the top of the file and add 

```
console.log(age);
var age = 10;
```

What will happen? is it going to error? Undefined? 10?
The value is undefined. 
![](@attachment/Clipboard_2020-02-04-13-23-59.png)

Now if you try to log another varaible that does not exist, you will get an error 

![](@attachment/Clipboard_2020-02-04-13-24-16.png)

Why is that? 
What is happening is that javascript will hoist the variable declarations but it will not actually hoist the setting of the values. So if after the page is loaded, you type `age` into the console, it wil be set to 10. 

So what Javascript does is it says before everything runs, I am going to make my variables and then I'm just going to go ahead and update them. 
It is basically doing the following:

```
var age;
console.log(age);
age = 10;
```

You can use hoisting to figure out if variables arecreated but not what their values are later in the file.

Hoisting is variable declarations and function declarations that are hoisted to the top of the file. Only function declaration types of functions are hoisted, NOT function expressions (when you put a function in a variable). Same thing goes with arrow function or any other type of function. 

---


