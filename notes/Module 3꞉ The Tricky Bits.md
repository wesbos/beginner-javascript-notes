---
attachments: [Clipboard_2020-02-03-18-47-58.png, Clipboard_2020-02-03-19-52-11.png, Clipboard_2020-02-03-19-52-56.png, Clipboard_2020-02-03-20-03-38.png, Clipboard_2020-02-03-20-14-11.png, Clipboard_2020-02-03-20-21-45.png, Clipboard_2020-02-03-20-22-13.png, Clipboard_2020-02-03-20-22-53.png, Clipboard_2020-02-03-20-43-38.png, Clipboard_2020-02-03-20-44-06.png, Clipboard_2020-02-03-20-55-28.png, Clipboard_2020-02-03-20-57-52.png, Clipboard_2020-02-03-21-10-13.png, Clipboard_2020-02-03-21-10-48.png, Clipboard_2020-02-04-13-16-53.png, Clipboard_2020-02-04-13-22-11.png, Clipboard_2020-02-04-13-23-59.png, Clipboard_2020-02-04-13-24-16.png, Clipboard_2020-02-05-07-53-19 (2).png, Clipboard_2020-02-05-19-09-28 (2).png, Clipboard_2020-02-05-19-14-46.png, Clipboard_2020-02-05-20-22-15.png, Clipboard_2020-02-05-20-23-42.png, Clipboard_2020-02-05-20-24-02.png, Clipboard_2020-02-05-20-37-58.png, Clipboard_2020-02-05-20-41-03.png, Clipboard_2020-02-05-20-41-31.png]
title: 'Module 3: The Tricky Bits'
created: '2020-02-03T23:25:39.261Z'
modified: '2020-07-29T22:11:29.164Z'
---

# Module 3: The Tricky Bits

## 17 - Scope

We have touched on scope a few times throughout the course already because it's impossible to talk about variables without touching on scope. 

What is scope? Scope answers the question _"where are my variables and functions available to me?"._ 

So far in the course, we have been making functions and variables and they have generally been available anywhere we wanted them. We have also seen some issues like when you create a variable inside of a function, and they're not available outside the function. 

That is what scope is. 

Go to the playground folder and create a new file called `scope.html`, and use your html base inside of it. 

Add a script src to a file called `scope.js` which will live in the same directory. 

```html
<script src="./scope.js"></script>
```

Add a new file `scope.js` in `/playground` and add a `console.log('It works!');`.  

Open the file up in the browser to make sure it works. 


### Global Variables

We will start by taking about the first type of scope which are referred to as **global variables**. 

With global variables, whether you have a script tag, or javascript file, or run it in the console, anytime you declare a variable, it will be available anywhere in the application. 

For example, if you add in `scope.js` `const first = 'wes';` and then in the console type `first`, it will return the value of first. 

Also, if you were to add another script tag in `scope.html` like below 👇, will it work? 

```html
  <script src="./scope.js"></script>
  <script>
    console.log(first);
  </script>    
```

That does work, the console will log "wes". 

Why does it work? 

Because when you just go ahead and create a variable in a javascript file, not inside of a function, not inside of a module, not inside of an if statement, when you just create it out in the open, that is what is referred to as a **global variable**. 

You can access global variables from any other javascript that is running on the page like a script tag or via the console. 

In the browser, the global scope is called the window. 

If you type `window` in the console, you will see every single thing that is attached to the global scope is inside of the window.  

![](@attachment/Clipboard_2020-02-03-18-47-58.png)

That is why sometimes you will see people doing things like `window.setTimeout()`. There is also just regular, old, `setTimeout()`, both are the exact same thing.

Methods that are globally available to us like `setTimeout()` are actually on the window object, and that is what is called global. 

There is one thing to know about `const` and `let`.

Let's say we added this code to `scope.js`.

```js
/*  eslint-disable */
const first = 'wes';
let second = 'bos';
var age = 100;
```

Id you reload `scope.html` in the browser and then in the console type in `first`, `second` and `age`, you will see the following values returned because they are all global variables 👇

![](@attachment/Clipboard_2020-02-03-19-52-11.png)

However, if you type in `window.first` and `window.second` you will get `undefined` but when you type in `window.age` it will return `100`. 

![](@attachment/Clipboard_2020-02-03-19-52-56.png)

This is because `var` variables are attached to the `window` object and they are globally scoped, and `const` and `let` variables when declared like the example above are still globally scoped, they are just not attached to the window. 

That is not really all that important because you shouldn't be making global variables anyway. This was just to demonstrate why sometimes people write `window.` or just type the global variable directly. 

The same thing goes with functions. 

If we make a function `function sayHi(){console.log('hi!');}`, we can call it by the following methods:

1.  from a script tag on the html page like so: 👇

```html
  <script src="./scope.js"></script>
    <script>
      sayHi();
    </script>
```

2. typing `sayHi()` in the console
3. typing `window.sayHi()` in the console

Why is it available at `window.sayHi()`? 

Because anything that is in the global scope is attached to the window object with the exception of `const` and `let` variables. 

Using global scope is almost never a good idea, but before we learn why that is, we need to learn about how different parts of scope work. 

### Function Scope

Let's get rid of the `<script>sayHi();</script>`  code in `scope.html`. 

Remove everything within `scope.js` and then add  
```js
const age = 100;

```

Create a function `go()`, and the following logs 👇

```js
const age = 100;
function go(){
  const hair = 'blonde';
}
console.log(age);
console.log(hair);
```


When we `console.log(age)`, is it going to be 100? 
When we `console.log('hair')`, will it be blonde?

![](@attachment/Clipboard_2020-02-03-20-03-38.png)

Age returns 100, but hair throws a reference error. 

Maybe that is because we did not run the `go()` function, we just defined it?

Let's try running the go function so that variable gets declared. Before `console.log(age);` add `go();`. 

If you refresh the page and look at the console, we will still see the error. Why?

This is the next type of scope which is called **function scope**. 

What function scope is, is when variables are created inside of a function, those variables are only ever available inside of that function. 

That means that anything we create inside of the `go()` function, is not available outside of that function, unless we were to explicitly return it and put it into it's own variable when that function is run. 

If you modify the `console.log(hair)` to be within the `go()` function, it will log. 👇

```js
function go(){
  const hair = 'blonde';
  console.log(hair);
}
```

You can think of the curly brackets in functions as gates. 

They keep the variables in and do not allow them to leak out. 

Now is that the same for the opposite? 

If we were to `console.log(age)` from within the `go()` function, would that work? 

If variables can't leak out, can they go in? 

If you refresh the page and look at the console, you will see it worked.

This is an interesting thing about javascript and most programming languages. 

Variables, if they are not found inside of a function, will go up a level higher and look for a variable in that scope. If it's not available in that scope, it will go up a level higher. _(We will talk about multiple nested scope in just a second)._ 

So what is happening is inside the `go()` function the code is saying, "there is no variable inside of this function called age, so I will go up one more level and look up". 

Now if we added as the first line of the `go()` function, `const age = 200;` and refresh the page, is that going to error? 

Is that going to be 200 or 100? 

It's will be 200. 

Two things: 
1. is that allowed? 
1. why it is 200?

It's 200 because it looks in the local function first and it does find a variable called age. 

However, if it is not found, it will go one level higher and look for it at that level. 

Why is this allowed? Why is it not breaking? If you hover over the variable in VSCode, you will see an error in ESLint that says 
> 'age' is already declared in the upper scope.

![](@attachment/Clipboard_2020-02-03-20-14-11.png)

That is what is referred to as **shadow variables**. 

You can name variables the same thing, if they are not in the same scope. 

However, it's not a good idea because if you name a variable something that is the same as in another scope, you limit yourself to being able to access that. 



```js
const age = 100;
function go(){
  const age = 200;
  const hair = 'blonde';
  console.log(age);
  console.log(hair);
}
```

In the example above 👆, if we wanted to access the `age = 100;` from the `go()` function, there is no way to do that because the variable has been **shadowed** _(meaning it has been over-written)_.

A tip is that if you ever have a variable inside of a function that is very similar to a variable outside of a function, name the variable inside of the function more specifically so you have access to both. 

In this case, inside of the function you could declare a variable like `const myAge = 200;` instead of just calling it `age`. 

### Block Scoping 

The next type of scope is **block scope**.

We will start by talking about `var`, `let`, and `const` variables and how they are scoped differently.

`const` variables cannot be reassigned, and `let` and `var` variables can be re-assigned. They have a different way of how they are scoped. 

Let's do an example. 

Will the code below work 👇?

```js
if(1 === 1){
  const cool = true;
}
console.log(cool);
```

![](@attachment/Clipboard_2020-02-03-20-21-45.png)

No, it throws the error shown above 👆
>Uncaught ReferenceError: cool is not defined

What if we make it a `var` variable instead? 

```js
if(1 === 1){
  var cool = true;
}
console.log(cool);
```

It works! 

![](@attachment/Clipboard_2020-02-03-20-22-13.png)

What if we make it a `let` variable?

```js
if(1 === 1){
  let cool = true;
}
console.log(cool);
```

It doesn't work, we get the same error. 

![](@attachment/Clipboard_2020-02-03-20-22-53.png)

What is hapepning there is whenever you have a set of curly brackets like in the if statement above, that is what is referred to as a **block**. _(Blocks will be showing up in most places, the most common is probably an if statement. We will have lots more examples throughout the course.)_

You can think of those brackets are gates. Those gates keep variables in. 

Anytime something that was created inside of these gates, they are not allowed to leave the gates. If you need to access a variable that was created inside of the gates, outside of the gates, you are not allowed to do it. 

There are a few solutions to that because every now and then you run into a situation where you do need a variable to be available outside of a block. 

What happens is you have to create the variable above it, as we will demonstrate in this example 👇

```js
let cool;
if(1 === 1){
   cool = true;
}
console.log(cool);
```

In that example, we have declared a variable `cool` without assigning anything to it. 

On the line that previously had `let cool = true;`, we do not declare the cool variable, we simply update it with `cool = true`. 

What that does it creates it's in the higher scope _(in this example it is a global variable but if this was created inside of a function it would be function scoped)_. 

Then, we update the variable, and then it's available to us outside of the function. 

Here is another example that is a more realistic, where we are getting into two different kinds of scopes 👇

```js
function isCool(name){
let cool;
if(name === 'wes'){
   cool = true;
}
console.log(cool);
return cool;
}
```

So what is going on here is we have one scope, which is the **function scope** (`function isCool(name){...}`). 

One thing that can get confusing is that a function also has a block, so any `let`, `var` of `const` variables are automatically scoped to a function, because regardless, if its a function or a block, it's a set of curly brackets so it's scoped to that. 

And then we have **blocked scope** which is within the `if(name === 'wes'){...}`. 

Again to demonstrate, if we changed the `cool` variable within the if statement to a const variable, like in this example, it would not work 👇

```js
function isCool(name){
let cool;
if(name === 'wes'){
   const cool = true;
}
console.log(cool);
return cool;
}
```

However, the example below does work 👇

```js
function isCool(name){
let cool;
if(name === 'wes'){
   cool = true;
}
console.log(cool);
return cool;
}
```

Although we went over how to solve the fact that variables are blocked scope, in most cases that is not something you need fixed, and it is actually really nice to have blocked scope because you don't have variables leaking out of it. 

In the past, we have had for loops such as the following:

```js
 for(var i = 0; i < 10; i++) {
   console.log(i);
}
```

That will log 0 - 9 as shown below 👇

![](@attachment/Clipboard_2020-02-03-20-43-38.png)

If you type `i` in the console, it will return 10.

![](@attachment/Clipboard_2020-02-03-20-44-06.png)

We have this random variable that is out floating called `i`, which should have been contained within the for loops but because it's a `var`, it has leaked outside. 

By simply making it a `let` variable, that random `i` variable will no longer be floating because it will be scoped to the curly brackets. 

Block scoping is one of the reasons people say use `const` by default, `let` when you want to re-assign it and don't use `var` unless there is a specific use case for it. 

To go back to our example earlier with `isCool()`, we could have also solved it by changing the `cool` variable to a `var` as shown below 👇

```js
function isCool(name){
if(name === 'wes'){
   var cool = true;
}
console.log(cool);
return cool;
}
```

Why does that work? 

Because it's a `var` variable. 

`var` variables are not block scoped, they are function scoped. 

That means they are available outside of the if statement block, but they are only available inside of the `isCool()` function. 

We will do another example of scope look-up to solidify that concept. 👇

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

What is going on here? 

We have a variable `dog` which is set to `"snickers"`. 
We have a function `logDog` that will log the `dog` variable. 
We also have a `go()` function that creates a variable named `dog` again, and sets it to the value of `"sunny"`.
Then we run that `logDog()` function, and then we run `go();`. 

When we call the `logDog()` function, is it going to log Sunny or Snickers?

You may think it will log Sunny because we declare the dog in the function scope, so when the function runs, shouldn't it look in it's own scope for that? 

Or you might think it may log Snickers becaue the function is declared within a `dog` variable inside of it so it will look up for that variable. 

What does it log? Snickers! 

![](@attachment/Clipboard_2020-02-03-20-55-28.png)

Even though we ran the `logDog()` function within the `go()` function and that function has a locally scoped variable set to the value of Sunny, it's still logging Snickers. 

### Lexical and Static Scoping

That is because javascript is what is referred to as **lexical scoping** or **static scoping** _(those are buzz words in javascript)_. 

What that means is the way that variable look-up or scope look-up happens, is where the functions are defined, not where they are run.  

So even though the `logDog()` function is run inside of another function which has a locally scoped `dog` variable, it doesn't care about where it's run, it cares about where it is defined.

Because `logDog()` is defined where it is, since it doesn't have a local variable named `dog`, it will just go up one level.

![](@attachment/Clipboard_2020-02-03-20-57-52.png)

Ideally the function `logDog()` would take a parameter of `dog` and then log whatever parameter value it is passed like so 👇

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

Now that console will log "Rufus". 
Why? 

Because when a function takes in an argument, it will make local variables inside of that function named whatever you named the parameter, and then that is availble to them. 

It is the same as doing the following 👇

```js
function logDog(dog){
  const dog = whateverYouPassedInAsTheFirstArgumentToTheFunction;
  console.log(dog)
}
```

That is what javascript is essentially doing behind the scenes. It is taking the value that you pass the first parameter and making a local variable for the function. 


```js
function go() {
  const dog = 'sunny';
  logDog(dog);
}
```

The code  doesn't care what you called the variable that you as passing in, it just cares about the value. 

The example above  👆 is the same thing as just passing in a string of Sunny, as shown below 👇

```js
function go() {
  const dog = 'sunny';
  logDog('sunny');
}
```

We will go over best practices and many more examples in the course. 

**Best Practices**

1. Try not to create global variables 
    - it is fine for us to create them while doing these examples and when we get into modules, it is almost impossible to create global variables unless you explicitly do something like `window.IAMGlobal = 'wes'`. 
    - Unless you explicitly attach it to the window, with a module, it is very hard to create a global variable which is intentional.  


2. Functions are scoped the exact same as variables
  - You can create functions inside of other functions. _We will look at examples of why you might want to do that later_. 
  Here is an example in the meantime 👇

    ```js
    function sayHi(name){
      function yell(){
        console.log(name.toUpperCase());
      }
      yell();
    }
    ```

If you were to write `sayHi('wes')` in the console, it will return WES. 

![](@attachment/Clipboard_2020-02-03-21-10-13.png)

However if you try to call the `yell` function futside of `sayHi()`, as shown below, it will throw an error 👇

```js
function sayHi(name){
  function yell(){
    console.log(name.toUpperCase());
  }
  yell();
}

yell();
```

What is happening there is just like variables, functions are scoped to the parent function. 

If you create a function inside of another function, that function will only ever be available inside of that. 

That is starting to open up what is referred to as a **closure**, which is a more advanced example we will go over in the future. 

It is possible to do a function inside of a function, but generally, you won't be doing that. 

---

## 18 - Hoisting

We talked about this a little bit before. 

Now we will get into the details about what it is, when you can use it and why you might want to use it. 

**Hoisting** in javascript allows you to access functions and variables before they have been creatd.

There are two things in javascript that are hoisted: 
1. function declarations
2. variable declarations. 

### Hoisting Function Declarations

We will focus on function delcarations first. 

Make a `hoisting.html` file in the `/playgrounds` directory and give it the base html. 

Add a script source of `./hoisting.js` and create a new Javascript file with that name.  

Do our usual `console.log('It works!');` to check that it works.

Next, make a function `sayHi();`. 

If you try to run this function before it  exists, will it work? 

You can see ESLint is complaining with warning of:
>`sayHi` was used before it was defined. eslint(no-use-before-define)


```js
sayHi();

function sayHi() {
  console.log('hey!'); 
}
```

If you open `hoisting.html` in the browser, does it work? 

It does. 

Why is that?

When you run your javascript file, the Javascript compiler will take all of your function declarations and move them to the top of the file so they are all available before you use them. 

Because of hoisting, you can technically run a function before it exists. 

Let's do another example. 

Add the following function 👇

```js
function add(a,b){
  return a + b;
}
```

Now use that function within `sayHi()`, like so 👇

```js
sayHi();

function sayHi() {
  console.log('hey!'); 
  console.log(add(10,2));
}
function add(a,b){
  return a + b;
}
```

Is that going to work? 

It does. 

![](@attachment/Clipboard_2020-02-04-13-16-53.png)

That is because hoisting moves them to the top before it will actually run anything.

So javascript rearranges the file and puts all the variable and function declarations at the top of the file. 

Why does that functionality exist? 

Wes hardly ever uses hoisting, he prefers to declare his functions before using them. 

When we get into modules, he prefers to put his separate functions in a module like util functions or math functions, and then import them as he needs them.

One argument Wes has heard for hoisting being useful is people often prefer when opening up a file, say you open up `hoisting.js`, they much prefer to first be able to see _what_ does this file do, and then _how_ does this file do it. 

That way if you are quickly jumping into a file, you can quickly see from the first couple of lines "what does this file do". 

If you do care about how it does it, you can go a bit further down into the file and see what it does, as shown below 👇

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

### Variable Hoisting 

The other type of hoisting is called **variable hoisting**. 

If you were to go the top of the file and add 👇

```js
console.log(age);
var age = 10;
```

What will happen? Is it going to error? Undefined? 10?

The value is undefined. 

![](@attachment/Clipboard_2020-02-04-13-23-59.png)

If you try to log another varaible that does not exist, you will get an error 👇

![](@attachment/Clipboard_2020-02-04-13-24-16.png)

Why is that? 

What is happening is that javascript will hoist the variable declarations but it will not actually hoist the setting of the values. 

So if after the page is loaded, you type `age` into the console, it wil be set to 10. 

So what Javascript does is it says before everything runs, I am going to make my variables and then I'm just going to go ahead and update them. 

It is basically doing the equivalent of the following 👇

```js
var age;
console.log(age);
age = 10;
```

You can use hoisting to figure out if variables are created but not what their values are later in the file.

Hoisting is when variable declarations and function declarations that are hoisted to the top of the file. 

Only function declaration types of functions are hoisted, **not** function expressions (when you put a function in a variable). 

Same thing goes with arrow function or any other type of function. 

---

## 19 - Closures

**Closures** is one of the scariest words in javascript and a concept that comes up all the time in javascript, especially in interviews.

It's a hard  concept to get, but it can be relatively simple to understand. We will tackle now understanding of the basics of what a closure is. 

As we build stuff, Wes will mention when something is a closure to give us more context and examples of when closures are used.

Create a new file  `closures.html` in the `playground` directory and add our HTML base.

Open up a set of script tags. Our examples will go within the script tags, like so 👇

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title></title>
  <link rel="stylesheet" href="../base.css">
</head>

<body>
  <script>
  //examples go in here
  </script>
</body>
</html>
```

A **closure** is the ability to access a parent level scope from a child scope, even after the parent function has been terminated. 

Normallly, Wes doesn't like examples that are not real world but since this is a tough concept, we will start with a simple example. 

We are going to make a function inside of a function, called `inner` and `outer` to illustrate the concept and then we will get into more fun examples. 

Create a function `outer` and within it set a variable `outerVar` equal to "Hey I am the outer var". 

Now inside of that, make another function called `inner()` and within it declare the following variable 👇

```js
const innerVar = 'Hey I am an inner var";
``` 

In the previous lesson on scope, we learned that within the `inner()` function, we can add a log of the `innerVar` variable like so 👇

```js
console.log(innerVar);
``` 

You can also log the `outerVar` within the `inner()` method because of the scope lookup chain. 

Since there is no variable called `outerVar` in that function, it will go a level up to the `outer()` function and since it finds that variable there, it will use that variable.

```js
  function outer(){
    const outerVar = 'Hey I am the outer Var';
    
    function inner(){
      const innerVar = "hey I am an inner var";
      console.log(innerVar);
      console.log(outerVar);
    }   
  } 
```

Now, let's try calling `inner()` from within `outer()`, and open the browser and console ad run the `outer()` function from the console. 

You should see both the inner and outer variables. 

![](@attachment/Clipboard_2020-02-05-07-53-19.png)

The same thing would happen if you called it from within the html script tag like so 👇

```html
<script>
  function outer() {
    const outerVar = "Hey I am the outer Var";

    function inner() {
      const innerVar = "hey I am an inner var";
      console.log(innerVar);
      console.log(outerVar);
    }
    inner();
  }
  outer();
</script>  
```

The `inner()` function is able to do a scope lookup and see the `outer`. We have already learned about that, and that's not really a closure. 

Now the kind of interesting thing, and this is where closures come into play, is where you don't call the `inner()` function from within the `outer()` function but you call it at a later point in time. 

So let's not call it from within `outer()`, remove that line of code where we are calling `inner()` and also remove the call to `outer()`. 

From the `outer()` function, let's return the `inner` function. You can return it two ways.

The first way is shown below 👇

```html
<script>
  function outer() {
    const outerVar = "Hey I am the outer Var";

      return function inner() {
      const innerVar = "hey I am an inner var";
      console.log(innerVar);
      console.log(outerVar);
    }
  }
</script>
```

The second way is like so 👇

```html
<script>
  function outer() {
    const outerVar = "Hey I am the outer Var";

      function inner() {
      const innerVar = "hey I am an inner var";
      console.log(innerVar);
      console.log(outerVar);
    }
    return inner;
  }
</script>
```

We will go with the second one and after the `outer()` function, we will add 👇

```js
const innerFn = outer();
```

What we are doing there is:
 - we are running the outer function
- it's creating an outer variable (`outerVar`)
-  then we are returning the inner function, which is why we are sticking it in a variable (`innerFn`).

In the console, when you type `innerFn` it will return the `inner` function like so 👇

![](@attachment/Clipboard_2020-02-05-19-09-28.png)

The question is, if you were to run `innerFn()` right below the function expression, is the `outerVar` still going to be accessible or will it be `undefined`?  

```html
<script>
  function outer() {
    const outerVar = "Hey I am the outer Var";

    function inner() {
      const innerVar = "hey I am an inner var";
      console.log(innerVar);
      console.log(outerVar);
    }
    return inner;
  }

  const innerFn = outer();
  innerFn();
  
</script> 
```

We ran the `outer()` function on this line of code `const innerFn = outer();`, which is where it created the variable, and then it returned the inner function. 

Is that still going to be available to us or will it be `undefined`?  

If you try that code, you will see that they both work. 

![](@attachment/Clipboard_2020-02-05-19-14-46.png)

What you can do is stick a function into a variable, and then at a later point in time, you can have access to that function. A closure comes into play because you can access the function even though the outer funciton is done. 

We learned in scoping that when a function is done,  anytime there are scoped variables that aren't returned from the function, they are not accessible. 

Now we get this weird thing where when we run the function outside of it, it's still able to access it. That is what is referred to as a **closure**. 

Javascript is able to create functions inside of functions, and it can still reach outside to the parent scope, and even though the oute`r function is done running, it will still maintain that variable in memory so that we can then access it at a later time. 

The variable is not **cleaned up** or "**garbage collected**" which is a term that is often used. 

Why would that be helfpul? It looks very confusing. 

### Examples of Closures

Let's look at some actual examples.

First, we will go over an example of a closure creating a function which is what we just went over. 

The second example will be how you can use closures to create what are called **private variables**. 

Comment out the previous code we had added in the script tags, and add the following 👇

```js
 function createGreeting(greeting = "") {
    const myGreet = greeting.toUpperCase();
    return function(name) {
      return `${myGreet} ${name}`;
    };
  }
```

This function:
- takes in a greeting, the default of which is an empty string
- assigns it to the `myGreet` variable which takes the greeting that got passed in to the function
- then runs `toUpperCase()` against it.  

From there, we will return a function, which we don't have to name, which will take in the presons name and return a greeting.

Why is that helpful? 

Why did we do this in two separate functions? 

Because you can create functions that are based off whichever greeting you like. 

```js
const sayHello = createGreeting('hello');
const sayHey = createGreeting('hey');
console.log(sayHello('wes'));
console.log(sayHello('kait'));
console.log(sayHey('kait'));
```

If you refresh you will see the following in the console 👇

![](@attachment/Clipboard_2020-02-05-20-22-15.png)

What is happening here is that when we create the outer function `createGreeting(){...}`, we had created a variable inside of that function, which is then accessed at a lower scope. 

We've got inner scope here 👇

![](@attachment/Clipboard_2020-02-05-20-23-42.png)

And we have outer scope here 👇

![](@attachment/Clipboard_2020-02-05-20-24-02.png)

Since our inner scope references a variable that was created in our outer scope, that is what is referred to as **closure**. 

We still are able to access our outer variables inside of the outer function scope, inside of our inner even after the `createGreeting()` function has been closed over. That is the whole idea behind closures, it's been closed. 

That is the first example where you have functions inside of functions and they are able to access the closure data inside of that. 

### Private Variables

The other sort of similar way is to create something called **private variables**. 

We will demonstrate it with another example.

We are going to create a function, `createGame` that will take the name of the game as a parameter. 

Inside of the function we will declare a variable `score` and another function `win` within, in which we will increment the score and return a string with the name of the game and the score. 

Next we will create a variable `hockeyGame` and assign it to the `createGame()` function where we will pass "Hockey" as an argument. 

Add the following code 👇

```js
function createGame(gameName){
    let score = 0;
  return function win(){
      score ++;
      return `Your name ${gameName} score is ${score}`
    }
}
const hockeyGame = createGame('Hockey');
```

_(Note: if you forget to add the `return` keyword that is infront of the `win()` function, when you try to run `hockeyGame()` in the console, it will throw an error saying `hockeyGame is not a function`.)_

Now, whenever we run the hockey game function, a message will be logged in the console showing the incrementing score. 

![](@attachment/Clipboard_2020-02-05-20-37-58.png)

What is happening there is the function that we create is called `win()`, and we are using a `score` variable. 

So whenever we create the game, we create an empty score variable. 

And then the inner function, whenever we actually run it, will increment the score variable that is of the outer scope. 

Why is that helpful?

That allows you to maintain multiple games at once.

Under the `hockeyGame` variable, we will declare another variable, like so 👇

```js
const soccerGame = createGame('Soccer');
```

Now we can do this in the console 👇

![](@attachment/Clipboard_2020-02-05-20-41-03.png)

![](@attachment/Clipboard_2020-02-05-20-41-31.png)

Even though the `score` variable 👆 is the same variable name, because we have created two separate `win()` functions by using the `createGame()` function, they each have their own private variable score. 

Currently there is no way for us to access `score`. 

If you try to access it in the console, you will get an error like the following
> score is not defined

There is no way for us to access that unless we were to explictly return that variable or as we did in this example, by putting it into a string. 

To recap:

Closures are the ability of a child function, or an inner function, to access variables from a higher level scope even after the functions have been called or closed or closed over. 

---

