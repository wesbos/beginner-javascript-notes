---
attachments: [Clipboard_2020-01-28-16-43-12 (2).png, Clipboard_2020-01-28-16-47-39 (2).png, Clipboard_2020-01-28-16-48-49 (2).png, Clipboard_2020-01-28-17-00-34.png, Clipboard_2020-01-28-17-05-22.png, Clipboard_2020-01-28-17-12-10.png, Clipboard_2020-01-28-17-15-30.png, Clipboard_2020-01-28-17-16-18.png, Clipboard_2020-01-28-17-17-04.png, Clipboard_2020-01-28-17-18-49.png, Clipboard_2020-01-28-17-25-44.png, Clipboard_2020-01-28-17-27-44.png, Clipboard_2020-01-28-17-31-06.png, Clipboard_2020-01-28-17-35-06.png, Clipboard_2020-01-28-17-35-44.png, Clipboard_2020-01-28-17-41-21.png, Clipboard_2020-01-28-19-48-01.png, Clipboard_2020-01-28-19-54-21.png, Clipboard_2020-01-28-19-59-14.png, Clipboard_2020-01-28-20-05-33.png, Clipboard_2020-01-28-22-28-03.png, Clipboard_2020-01-28-22-28-19.png, Clipboard_2020-01-29-15-31-21.png, Clipboard_2020-01-29-15-31-32.png, Clipboard_2020-01-29-15-32-16.png, Clipboard_2020-01-29-15-50-59.png, Clipboard_2020-01-29-15-55-38.png, Clipboard_2020-01-29-15-57-14.png, Clipboard_2020-01-29-16-43-59.png, Clipboard_2020-01-29-16-44-48.png, Clipboard_2020-01-29-16-45-24.png, Clipboard_2020-01-29-16-50-48.png, Clipboard_2020-01-29-16-55-56.png, Clipboard_2020-01-29-16-57-30.png, Clipboard_2020-01-29-17-00-53.png, Clipboard_2020-01-29-17-01-04.png, Clipboard_2020-01-29-18-48-01.png, Clipboard_2020-01-29-18-48-13.png, Clipboard_2020-01-29-18-51-05.png, Clipboard_2020-01-29-18-51-45.png, Clipboard_2020-01-30-17-50-07.png, Clipboard_2020-01-30-17-51-04.png, Clipboard_2020-01-30-17-52-26.png, Clipboard_2020-01-30-19-48-27.png, Clipboard_2020-01-30-19-58-43.png, Clipboard_2020-01-30-20-06-08.png, Clipboard_2020-01-30-20-07-35.png, Clipboard_2020-01-30-20-25-18.png, Clipboard_2020-01-30-20-26-46.png, Clipboard_2020-01-30-20-27-19.png, Clipboard_2020-01-30-20-30-25.png, Clipboard_2020-01-30-20-43-26.png, Clipboard_2020-01-30-20-44-42.png, Clipboard_2020-01-30-20-57-19.png, Clipboard_2020-01-30-20-59-21.png, Clipboard_2020-01-30-21-06-26.png, Clipboard_2020-01-31-17-36-06.png, Clipboard_2020-01-31-17-36-25.png, Clipboard_2020-01-31-17-45-50.png, Clipboard_2020-01-31-17-46-02.png, Clipboard_2020-01-31-17-47-21.png, Clipboard_2020-01-31-17-47-38.png, Clipboard_2020-01-31-17-49-45.png, Clipboard_2020-01-31-17-52-29.png, Clipboard_2020-01-31-17-55-36.png, Clipboard_2020-01-31-17-57-25.png, Clipboard_2020-01-31-17-58-57.png, Clipboard_2020-01-31-18-15-45.png, Clipboard_2020-01-31-18-20-52.png, Clipboard_2020-01-31-18-22-08.png]
title: 'Module 2: Functions'
created: '2020-01-28T21:27:12.651Z'
modified: '2020-01-31T23:22:18.116Z'
---

# Module 2: Functions

## 12 - Functions - Built in

These videos are going to be about functions. They are not going to be exhaustive, because there is so much more we need to learn in order to take advantage of them. We will get a good primer on what functions are, the core concepts, and an overview of the types of functions that you can write. The rest of the course is going to be using functions, since they are like types, a fundamental building block of javascript and we will get good at functions because we will be writing them throughout this entire course.

So, functions, what are they?

They allow us to group together sets of statements. 

As a refresher from previous videos, these are all statements: 
![](@attachment/Clipboard_2020-01-28-16-43-12.png)

If you wanted to group all those statements together (generally they are related to each other and generally they produce some sort of output), you could group them together inside of a function. 

Functions can take in data, those are known as **arguments**. We will discuss the difference between arguments and parameters shortly. 
Just know that when you pass data to a function, it is known as an argument. They perform some work (a statement), and sometimes they also return a value.

Let's look at an example in the console, `Math.max()` (this is actually a method, and we will explain the difference between a function and a method shortly, it is not much). 

If you run it in the console, it returns negative infinity. ![](@attachment/Clipboard_2020-01-28-16-47-39.png)
What we want to do is pass it some data, and what it will do is return the maximum value. For example, we pass two numbers, 10 and 12. It will return to us the highest number (which is 12).

![](@attachment/Clipboard_2020-01-28-16-48-49.png)

Now what is going on there? `Math.max(10, 12)` is a javascript statement. The values `10` and `12` that we are passing into the function are called arguments. If you are passing multiple values to a function, you need to separate each value with a comma and it's  best practice to include a space between each. The data that you pass to a function, the data that you give to a function in order for it to run is called an argument. 

Sometimes, functions will return to you some data that is generally the answer or the computed output based on what you passed in. 

For example:
`Math.floor(2.4444)` will return `2`

Here we are passing one argument of `2.4444` and it returns to us the floor of that value which is `2`. 

![](@attachment/Clipboard_2020-01-28-17-00-34.png)

There are a whole bunch of built-in functions in javascript, whether you are using it in the browser or with node. They come with all of these built in things, and we have already been using them because there is no way around it. The one that we have used the most so far is `console.log()`. 

For example if you `console.log('hey`)`, it will return hey. 

Interestingly enough, it also returns undefined. ![](@attachment/Clipboard_2020-01-28-17-05-22.png) That is because the console.log function logs to the console, it does not return a value. Not all functions are meant to return a value, sometimes they just go off and do things without returning a value.

Tip: You can tell in the console if something is a return or a statmeent by the `>` and `<.` arrows next to the line in the console. `>` indicates that it's a statement and `<.` indicates that it's the response to the statement. 

![](@attachment/Clipboard_2020-01-28-17-12-10.png)

Some other built in functions we can use are:

`parseFloat("20.34543543")` which takes in a string and returns a number. This is about switching types. 
![](@attachment/Clipboard_2020-01-28-17-15-30.png)

`parseInt("20.3243423")` takes in a string and returns a number `20` without a decimal. 
![](@attachment/Clipboard_2020-01-28-17-16-18.png)

We looked at `Math.round()`, `Math.floor()`, `Math.ceil()`.

If you type `Date.now()` in the console it will return..
![](@attachment/Clipboard_2020-01-28-17-17-04.png)

`Date.now()` is a function that does not take in any arguments. What it returns to us is the number of miliseconds since January 1 1970. If you go to https://epoch.now.sh, it's a tool that you can use to convert the milisecond value to a datetime. You can also do the opposite -- pick some date and time in the future and then it will return the milisecond value. 

![](@attachment/Clipboard_2020-01-28-17-18-49.png)

That is dates, we will go deeper into dates in future videos. 

We also have functions that will work with something called the DOM, which are the HTML elements that are on the page. 

Make a new file called `functions.html`, and we will use our html base snippet. Add a paragraph tag inside of the body that says "hey, how ya doin?" and then add an empty script tag below. Open that up in the browser.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1.0" />
    <title>Functions!!</title>
    <link rel="stylesheet" href="../base.css" />
  </head>

  <body>
    <p>Hey How ya doin?</p>
    <script>
    </script>
  </body>
</html>
```

Now, if in the script section of `functions.html`, you added the following code, what we would be doing is running a function called `document.querySelector()`, in which we are passing it a selector (`p`), and then what it does is it finds something that matches that selector and puts it into a variable, and we console log that variable.

```html
<script>
  const p = document.querySelector("p");
  console.log(p);
</script>
```

![](@attachment/Clipboard_2020-01-28-17-25-44.png)

There are a lot of other functions built in, some are mobile specific like `navigator.vibrate()`. 

![](@attachment/Clipboard_2020-01-28-17-27-44.png)

Another useful thing is if you are not sure what arguments a function should take, you can refer to the Mozilla developer docs, in order to see what is going on. In google, type `Navigator.vibrate()`. Usually you will need to look for the Mozilla developer. (A tip is to include `mdn` at the end of your search so the Mozilla docs float to the top).

The docs should explain what the method is, how it can be used, and what it returns. 

![](@attachment/Clipboard_2020-01-28-17-31-06.png)

Let's look at a couple of more. Clear the console. In `functions.html`, add a lot of text, such as a few paragraphs of Lorem Ipsum. Wes is using the Emmet extension for VS Code which allows him to type `lorem400` and hit tab to expand 500 words of lorem ipsum. (You can manually search for a Lorem Ipsum generator online if do not have the Emmet extension). 

Now if you refresh `functions.html` you will see a lot of text on the page. 

![](@attachment/Clipboard_2020-01-28-17-35-44.png)

Add enough text so you can scroll on `functions.html`. 
Now you should be able to type in the console `window.scrollTo(0, 600)`, and that should cause your window to scroll down 600 pixels. 
If we search for `scrollTo` on mozilla docs, it says it accepts argumenst of a x and y coordinate, or you can pass it an options object. 

The docs say that "options is a ScrollToOptions dictionary", dictionary is a word we use in javascript to represent an object, it's an object that has a number of set properties on it. 

![](@attachment/Clipboard_2020-01-28-17-41-21.png)

```
window.scrollTo(0, 1000);
```
```
window.scrollTo({
  top: 100,
  left: 100,
  behavior: 'smooth'
});
```

This is a great example of how you can pass any type to a function. In the first example, we are passing two numbers but it's also an option to pass an object which has properties inside of it like `top`, `left`, `behaviour`. 

Try typing into the console
```js
scrollTo({top:500, left:0, behavior: 'smooth})
```
The page should scroll down 500 pixels. 

`scrollTo` is an example of a function that does return anything, instead it just goes off and does some work for us. 

---

## 13 - Functions - Custom

In this video we will get into making our own custom functions. 

Make a new folder inside of the `/playground` directory and call it `custom-functions`. Inside of that, create two files, `index.html` and `cf.js`. 

Add `console.log('it works!');`.
In `index.html`, add the HTML base snippet. We will need to modify the base.css path because we made a folder so the path should now be `../../base.css` because we have to go up two levels to get to it. 
Right before the closing body tag, add a script src tag `<script src="./cf.js">`. Open the page in a browser and you should see `It works!` in the console. 

The real power of javascript comes when you want to define your own functions. Functions can do anything. They group together a set of instructions, often taking in values (we talked about arguments earlier), doing some work and then returning value or set of values to the person that requested in. 

We are going to create a function called Calculate Bill. 

Calculate Bill is a western gentlemen who is very good at going to restaurants and calculating what the bill would be regarding what the bill was, how much tip was, how much tax is. 

There are going to be a few buzzwords as we go through, which we will explain as we go. 

The first one is functions are created or defined, and they are later called.

When you make a function, when you author what it does, that is called a **function definition**. 
Later on, when you want to run that function, that is called **calling** or **running** of a function. 

There are a few ways to define a function. We are going to go over all the different approaches in the next videos but for now, we will go over the basic. 

First you type `function` and then the name of the function. Function naming follows the exact same rules as variable naming which we went over previously. 

We are going to call it `calculateBill`

```js
function calculateBill(){
//this is a function body
}
```

What we have done is defined it, given it parenthesis (that's not calling it, that is defining it) and then you open and close a function block. Anything that goes between the opening and closing function block is called the function body and is part of the function. 

For now, add `console.log('Running Calculate Bill!!!')` in the function body. 

Now to go ahead and run a function, we simply take the function name. 

First let's look at something.  View `index.html` in the browser and open the console. With functions, it works just like a variable in that you can call them by the name of it, it's almost the exact same thing. However when you put the name of the function, you see the entire code. 

![](@attachment/Clipboard_2020-01-28-19-48-01.png)

Now if we want to run the function we would enter into the console `calculateBill()`, which will log `Running Calculate Bill!!!!` in the console. 

Add the following to `cf.js`

```js
// Function Definition
function calculateBill() {
  // this is the function body
  console.log('Running Calculate Bill!!');
}

//Function Call or **Run**
calculateBill();
```

Now, let's talk about returning values. You noticed when we called `calculateBill()` it returned undefined. ![](@attachment/Clipboard_2020-01-28-19-54-21.png)

It does the work we asked it to do, and then it returns undefined. Often, functions will do a bunch of work and then return to you the result. 

What we are going to do in our function is we will take in arguments like how much the dinner was, the tax rate and how much you want to tip, and it will return to us the total value. 

The way that works is we will assume the meal is 100 dollars, and we will multiply it by 1.13 because in Ontario the tax rate is 13%. Now we can console log the total value. 

```js
// Function Definition
function calculateBill() {
  // this is the function body
  console.log('Running Calculate Bill!!');
  const total = 100 * 1.13;
  console.log(total);
}

//Function Call or **Run**
calculateBill();
```

![](@attachment/Clipboard_2020-01-28-19-59-14.png)
(This is a perfect example of the issue with floating point numbers); 

You might be thinking "oh, now i have this nice total variable which I can just quickly access. If you type `total` in the console, it will return undefined. 

If below `calculateBill();` in `cf.js` you add `console.log('total')`, and refresh the page in the browser, you will see an error that `total is not defined` as well as an eslint warning. This is something that we will get into called scope. 

Variables that are created inside of a function are only available within that function. It is not available outside of it. So how do we store the result of the calculation so we can access it using a variable? 

That is with returning. When we called `calculateBill()` earlier, we got undefined returned in the console. So what we need to do is from the function, we will return total (return is a keyword in javascript) like so:

```js
  const total = 100 * 1.13;
  console.log(total);
  return total;
}

//Function Call or **Run**
calculateBill();
```
Now when you call it in the console, you will see it returns the value. 

![](@attachment/Clipboard_2020-01-28-20-05-33.png)

Now the question is how can we store that value? The total variable is still not available to me. That is because we need to capture (another buzz word) the result of the function or capture the returned value of the function into a variable. Modify the line of javascript with `calculateBill()` to:
```js
const myTotal = calculateBill();
console.log(myTotal);
```

In the console, you can now access the variable `myTotal`. 
We can modify the console.log to be `console.log($\`Your total is $${myTotal}\`);`
That will print out the value and message in the console. 

Couple things to review. The `total` variable within the `calculateBill()` function and the `myTotal` variable below the function, you might be asking why do we have two variables for the exact same value? The reason is that `total` variable is a temporary variable. 

That variable, because it has been created inside of hte function, it is only ever available inside of that function, and when that function is done running, that variable is cleaned up (or what is called garbage collected in javascript nad it's no longer needed).  So if you ever want to capture the value returned from `calculateBill()`, you have to stick it into a variable before you can go ahead and display it. 

Another cool thing you can do with interpolation strings is you can actually run the function from within the console.log statement. Javascript is going to run the function first, and then whatever the return result is it will immediately be interpolated into that string.

```js
console.log(`Your total is $${calculateBill()}`);
```

---

## 14 - Functions - Parameters and Arguments

This video will focus on arguments and parameters. In the `calculateBill()` function from the previous video, we hardcoded the tax amount. 

A best practice in javascript is to keep your code DRY, which stands for Don't Repeat Yourself. If you are making a function called `calculateBill()` and asumming that the bill is 100 dollars and 15%, that is not good because it is not very reusable. 

So what we could do is above the calculateBill function, we can declare the following variables, and modify the code like so:

```js
const bill = 100;
const taxRate = 0.13;

function calculateBill(){
  console.log('Running calculate bill!!');
  const total = bill * taxRate;
  return total;
}
```
This will work, but that is not the best way to do it. Why? Because the function calculateBill is relying on something called "global variables". 

For right now, what we need to know is that this is a function that needs some data, and when it is not passed data, it instead is reaching outside of the function in order to look up that data in a higher scope.
 
 It's not great to reach outside of a function in order to get your data. 

 In `cf.js`, remove the last console.log and add the following:

 ```
 const myTotal = calculateBill();
 const myTotal2 = calculateBill();
 console.log(myTotal, myTotal2);
 ```

TIP: you can console log as many pieces of data as you want by separating the values with commas like in the example above. 

The console.log will return the same value: 100.13.

Now what if we wanted a different value?
Could we do something like this? 
(Note: you need to change the `bill` variable that is declared in `cf.js` to a `let` instead of a const so we can reassign it)

 ```
 const myTotal = calculateBill();
 bill = 200;
 const myTotal2 = calculateBill();
 console.log(myTotal, myTotal2);
 ```
If you refresh it, now it works. 
However, all the of work we did like changing a variable in between running the code and yanking the variable from outside into the function to use. This is bad practice and it is how you get very brittle applications.

What we want to do is instead of reaching out, we want to pass into our functions the pieces of data that we need. 

Let's do a bit of cleanup. Get rid of the `let bill` and `const taxRate` variables. 

Get rid of lines of code where we are reassigning variables and declaring myTotal2 (`bill = 200; const myTotal2 = calculateBill()`) and the last console log. 

Now we should have 

```js
// Function Definition
function calculateBill() {
  // this is the function body
  console.log("Running Calculate Bill!!");
  const total = bill * 1 + taxRate;
  return total;
}

const myTotal = calculateBill();
```
Now we want to take the variables bill and tax rate and we want to make them into something called params for your function.

When you define your function and say when someone calls it, I am going to expect someone to pass me some data, so we put in params (Wes likes to think of them as placeholders). 

```js
function calculateBill(billAmount, taxRate){
  ...
}
```

Now, inside of the function body, we will have access to the two variables that were passed: `billAmount` and `taxRate`. 

It's kinda confusing because there is no like creation of the param variables, but Wes will explain it in just a second. 

```
// Function Definition
function calculateBill(billAmount, taxRate) {
  // this is the function body
  console.log("Running Calculate Bill!!");
  const total = billAmount * (1 + taxRate);
  return total;
}

const myTotal = calculateBill(100, 0.13);
console.log(myTotal);
```

That will give you 100.13. 

But now we are able to make a myTotal2 really quickly:

```
const myTotal = calculateBill(100, 0.15);
const myTotal2 = calculateBill(200, 0.13);
console.log(myTotal, myTotal2);
```

It works without having to reassign because when you define a function, you can place parameters. P = placeholder is one way to remember it. 

When you call the function, you pass it arguments. 

![](@attachment/Clipboard_2020-01-28-22-28-03.png)

Here is a quick cheatsheet Wes has put together. 

![](@attachment/Clipboard_2020-01-28-22-28-19.png)

When we define the function name, we put what are called parameters. Parameters are what are called placeholders (we will talk about default values for parameters shortly). When you call, run or invoke (all 3 mean the same thing), and you actually pass it the data, that will take place of the variables (for example meal will be 100 and taxRate will be 10.13), those will be called arguments. 

People incorrectly use those terms interchangably but one way to remember is that parameters are placeholders. The things that you pass in are arguments that are "actual values". 

Bringing it back to `const myTotal = calculateBill(100,0.13)`, here we are running the function and as arguments we are passing straightaway numbers. However, the values that get passed into a function can be in a variable as well.  This is a common thing people get hung up on when learning how functions work is how they sort of get renamed. 

Let's take a look at code we wrote for `calculateBill()`.

WHen we have a function called calculateBill(), when the data gets passed in, there are going to variables that are going to be available inside of the calculateBill function, they are going to be what is called scoped to tis function and they are only available in this function as to what they are passed in. 

If we add a console.log within calculateBill like so ->

```
// Function Definition
function calculateBill(billAmount, taxRate) {
  console.log(billAmount, taxRate);
  // this is the function body
  console.log("Running Calculate Bill!!");
  const total = billAmount * (1 + taxRate);
  return total;
}
const myTotal = calculateBill(100, 0.15);
```

That will print to the console ![](@attachment/Clipboard_2020-01-29-15-31-32.png)

We can run that function from the console but pass it different values for the arguments, it will console log the values of the arguments that we passed, like so ![](@attachment/Clipboard_2020-01-29-15-32-16.png)

Why? Because javascript will take whatever you write as an argument, and then when you call the function it will make it sort of temporarily available and make them available to you via the names that you put in your parameters. 

What gets a little bit confusing to people is if we declare two variables before we call the function like so:

```
const wesTotal = 500;
const wesTaxRate = 0.3;
const myTotal = calculateBill(100, 0.15);
```

We can actually pass those variables into the function like this:

```
const wesTotal = 500;
const wesTaxRate = 0.3;
const myTotal = calculateBill(wesTotal, wesTaxRate);
```

Now the big confusion is, if they are variables outside of the function, and we pass them into the function, when it's called inside of the function, is the first parameter called `billAmount` or is it called `wesTotal`? Will it even work if you pass in a variable that does not have the same name as the parameter? Try by refreshing `index.html` in the browser.

It works just fine!

So -- when you run a function in javascript, what happens is javascript takes in whatever you have pass it, whether you have passed it that value directly (as a number or string for example), or if you pass it in via reference meaning that you just passed a reference to a variable which in turn will hold a value). At the end of the day we are still passing values, whether you pass it directly or whether you pass it a reference to a variable that holds a value.  Javascript doesn't care about how you are passing them in and as soon as the function runs, it doesn't care whether you passed a variable or value because it just knows that you passed in a value.

What javascript does is say okay, take whatever they passed in the first argument amd just make a variable called billAmount that is available inside of the confines of the curly brackets.

When the function is running, it does not care about anything else that is going outside of this function. It just knows it's doing it's job, it's been pased in the two little pieces of data that it needs, it does the math and returns it's value from within the function. 
 

When values get passed into a function, they sort of get renamed into whatever it is that you have defined your function parameters as.

Let's do another example!

Comment out `const myTotal = calculateBill...`. 
Add the following function to your code, which just returns hello and which we will pass in someone's first name. 

```js
function sayHiTo(){
 return `Hello ${firstName}`; 
}
const greeting = sayHiTo();
console.log(greeting);
```

Let's run the code as is, even though it will break, to see why. 
 
In the console you should see an reference error in the console. ![](@attachment/Clipboard_2020-01-29-15-50-59.png)

What happens is this function, first it loosk inside of it's own function scope, and it will look for a variable named firstName that has been passed in. If there is not, what it will start to do is go up to a high level of scope and look there. 

let's say there was a firstName variable like so:

```js
const firstName = 'wes';
function sayHiTo(){
 return `Hello ${firstName}`; 
}
const greeting = sayHiTo();
console.log(greeting);
```

it would actually work, because the function will reach outside for that data if nothing is found within the scope of that function. So what we want to do is modify the function definition to set it to take in one parameter (`firstName`). And then when we run the function, we actually have to pass it a string (we will use `Wes`), and then we will have our greeting.


```js
const firstName = 'wes';
function sayHiTo(firstName){
 return `Hello ${firstName}`; 
}
const greeting = sayHiTo('Wes');
console.log(greeting);
```

What is nice about this is now we can use that function to print out any first name like so
![](@attachment/Clipboard_2020-01-29-15-55-38.png)

As long as we pass in an argument (in this case "Wes"), it is going to have a variable inside of that function that is referenced to whateer the person has passed in. 

If we don't run it with anything, you will see... ![](@attachment/Clipboard_2020-01-29-15-57-14.png)  
The reason that happens is when a functoin runs, it will create the variable for us (`firstName`) and set it to whatever was passed in. But if it creates a variable and someone doesn't pass in anything, then it will just be set to undefined which is exactly how variables work. 

Now let's go over a few more examples. 

Let's go back to passing expressions. For this example we will go back to calculateBill.  

```
// const greeting = sayHiTo('Wes');
// console.log(greeting);
const myTotal3 = calculateBill(100, 0.15);
```

we know the code above works but what if instead we do 

`const myTotal3 = calculateBill(20 + 20 + 30 + 20, 0.15);`

Is that going to work? If you load `index.html` in the broswer you will see `103.4999999999`. 

(If you followed Wes too closely, you may have gotten the value of 90.5. If that is the case, the line of code that calculates the total within `calculateBill`. It should be `const total = billAmount * ( 1 + taxRate);`. This is because of bedmas, we need the paranthesis)

That works. Why? Because the only thing that a function can take in is a value, and whether you pass that value directly, as in a number, whether you pass that value in as av ariable which holds a value, that works,  and then you can also pass in expressions. 

In this example we are not actually passing an expression, we are actually running an expression and that will first run (`20 + 20 + 30 + 20`) and add it up to $90, and then we pass that raw value of 90. 
It is absolutely fine to do something that like, in fact it is pretty common. You can even mix and match. Let's say we have a variable `const kait = 100;` and then we want to add another $50 ontop of that. You can do something like.. 

```
const kait = 100;
const myTotal3 = calculateBill(kait + 50, 0.15);
```
It will still work if you mix and match. 


Let's remove `myTotal3` example, and do another example where we pass functions as arguments.

We will make a function called `doctorize` that will take in a `name` argument and return the name with Dr. infront like so

```js
function doctorize(name){
  return `Dr. ${name}`;
}
```

 And we will make another function called `yell` that also takes in a name and returns HEY with the variable name uppercased like so:

 ``` 
function yell(name){
  return `HEY ${name.toUpperCase()}`;
}
```

You might have noticed that both functions are using the variable name, While it's not okay to reuse variables in the same scope multiple time, it is okay to reuse parameters. Why? because when arguments are passed in, the paraemters are only available within that function so you will never run into a collision where the name that you pass into one function is going to overwrite it in the other function. That will not happen because parameters are scoped to the confines of their own functions.

The name parameter that is used in the `doctorize()` method will never collide with the variable within the `yell()` method. 

Let's go ahead and run it in the console. 

![](@attachment/Clipboard_2020-01-29-16-43-59.png)

What is kind of cool is you can pass the output of doctorized, into yell. 
In the console, do the following `yell(doctorize('wes))`;

![](@attachment/Clipboard_2020-01-29-16-44-48.png)

How that works is brackets go first, so anything inbetween the yell paranthesis, ![](@attachment/Clipboard_2020-01-29-16-45-24.png)  the code says "okay, I need to first run this function" , and hopefully that retursn a value (which it does, it returns Dr.Name), and then the value that is returned from doctorize immediately gets passed into yell as an argument and then that will in turn return "Hey  Dr. Wes". 

So to recap -- another way we can pass a value to a fucntion is the output of a function is just a value at the end of the day, and you can run that directly.

**Default Values**

Now let's talk about default values. 

If we were to take our `yell` function and instead of passing it "Wes", we do not pass an argument, it will error out. 
What is happening is that the `toUpperCase()` function (it's technically a method), it's trying to run it against something that didn't get passed in. So let's say someone forgets to pass a value to the yell function, our program will break. 

![](@attachment/Clipboard_2020-01-29-16-50-48.png)

What we can do is we can set something called defaults. When you define your function, inside of your function definition, you can set a default by saying name is equal to 'Silly Goose'.

```
function yell(name = 'Sily Goose'){
  return `HEY ${name.toUpperCase()}`;
}
```
If you run it an pass an argument, it will still work. However when you run it without an argument, the function will no longer error out and instead will fall back to the default value for the parameter and output `HEY SILLY GOOSE`. 

 So as you define your function, yo ucan say if soeone does not pass this paramenter here called name, just dfault it. 


Let's go back to our calculateBill function. You may be thinking that it's a bit silly to have to pass in the the tax rate every single time.  We will use a default value to set a default tax rate of 0.13. 

```
// Function Definition
function calculateBill(billAmount, taxRate = 0.13) {
  // this is the function body
  console.log("Running Calculate Bill!!");
  const total = billAmount * (1 + taxRate);
  return total;
}
```

What that allows us to do is call `calculateBill(100)` and only pass the value for the billAmount. 

![](@attachment/Clipboard_2020-01-29-16-55-56.png)

Wes often likes to set default values when he is creating functions. Even just adding a default value for a string variable of an empty string. 

```
function yell(name = ''){
  return `HEY ${name.toUpperCase()}`;
}
```

That will make sure the function doesn't error out, it just won't show a name like so ![](@attachment/Clipboard_2020-01-29-16-57-30.png)
That is just a safeguard. 

Let's take it one step futher and modify calculateBill to also take in a tip rate. 

Add another argument with a default value `tipRate = 0.15`. 

```
// Function Definition
function calculateBill(billAmount, taxRate = 0.13, tipRate = 0.15) {
  // this is the function body
  console.log("Running Calculate Bill!!");
  const total = billAmount * (1 + taxRate);
  return total;
}
```

Now we will change the way we calculate total to `const total = billAmount + (billAmount * taxRate) + (billAmount * tipRate);`

You may notice that as you save the file, prettier will remove the paranthesis if they are not needed (the bedmas rules are not needed here)
![](@attachment/Clipboard_2020-01-29-17-00-53.png) ![](@attachment/Clipboard_2020-01-29-17-01-04.png)

Now if we run calculateBill and pass it 100 dollars, it will return 128.

Now one little sort of gotcha that happens here is what if you want to use the defaultTax rate but not the default tipRate?
If you try to do `const myBill4 = calculateBill(100, ,0.2);` it will break. The error returns unexpected token `,`. 

So that only thing that you can pass into a function to make it kickback to it's original value is undefined. Meaning that functions will onl yever fall back to the defaults if nothing is passed. Remember when a variable is not set to anyting, it's value is undefined. So you cannot go ahead and pass zero here and expect it to false back to the deault. 

You have to actually pass it undefined. `const myBill4 = calculateBill(100, undefined, 0.2);` and it works like we wanted. 

It's very infrequently that you have to pass undefined like that but it's worth knowing that s how the function will define whether to fall back on a default value or not. It's nothing to do with trutjhy or falsey which we will be learning soon. 

---

## 15 - Different Ways to Declare Functions

One thing you're goin to hear a lot when you're getting into javascript is that javascript functions are "First class citizens". 

That means javascript functions  are values in themselves, they can be stored in variables and passed into other functions. 

What is a value in javascript?  We know that in the examples below `true` and `100` are values.
```
const age = 100;
const cool = true;
```
Those are values that are numbers, or strings or booleans.
What is cool about javascript is that functions can be passed into other functions. Functions can be stored in variables, they can be moved around like any other piece of data in JavaScript. That is not true for every other languages.

For now, we will talk about the ability to put functions into variables.  And this video will go over all the different ways to declare functions. 

Create a new file in our `custom-functions` directory called `ways-to-make-a-function.js`.  Add `console.log('it works')` and go back into the `index.html` file and change the path in the `src` attribue on the script tag to `<script src="./ways-to-make-a-function.js"></script>`. Refresh the browser to ensure that it works. 


We already know one way to declare a function and that is through the function keyword. 

```js
function doctorize(firstName){
  return `Dr. ${firstName}`;
}
```

Now let's see how we can actually declare that, in other ways. Comment that out. 

The next way to create a function is an anonymous function, which is a function without a name. 

To make `doctorize` an anonymous function, you would modify it like this:

```js
function(firstName){
  return `Dr. ${firstName}`;
}
```
However, it's not actually valid javascript in this case. If you try running it in the console you will see an error that says
>Function statements require a function name
However they are valid in many other use cases, specifically using them in callbacks (we will learn about that) as well as in an IIFE (immediately involved function expression). However in this examlpe it is not valid javascript.

Why would you ever want an anoymous function? The next way to declare a function will help explain that.

Add a comment `//AnonFunction` above that function, copy it and then comment it out. Paste the copied code below the commented out function. 

The next way to declare a functino is a function expression. A function expression is when you store a function as a value in a variable. 

```js
//Function Expression
const doctorize = function(firstName){
  return `Dr. ${firstName}`;
}
```

What we did above is we took an anonmyous function and stuck it in a variable. If you refresh the page, you will see that in the console, we have doctorize available to us, and we can call it like we did in previous videos.

![](@attachment/Clipboard_2020-01-29-18-48-13.png) 

That is what people mean when they say functions are first class citizens. WWhat we are doing there is we are creating a variable and then storing the function in that variable name.

You may come across developers who say to not use function expressions because it gives bad errors. Here is an example that demonstrates what they mean by that:

```js
//Function Expression
const doctorize = function(firstName){
   doesntExist();
  return `Dr. ${firstName}`;
}
```
![](@attachment/Clipboard_2020-01-29-18-51-45.png)

What used to happen is the error would just tell you that it occured in an anonymous function and you'd have no clues to lead you to where the error is happening. In our case, it does now tell you it happens inside of doctorize on line 12. 

Although the function is technically an anonymous function without a name, the browsers will now infer the name of the function from the variable name and use that in the errors.

What is the difference between doing a function declaration and a function expression? Why would you want to use one over the other?

There is only one real difference (beside error handling which isnt really an issue anymore) is how they operate how they operate in something called **hoisting**. We will go over this in a future video but we will go over it quickly now.

Add to the .js file a `doctorize2` function. 
```js
const doctorize = function(firstName){
  return `Dr. ${firstName}`;
}
function doctorize2(firstName){
  return `Dr. ${firstName}`;
}
```

If on the line before the first `doctorize` function, we were to add `doctorize("wes")`, do you think that it will run? If you run a function before you define it, does it work? 

Nope! You get an error like:

>Uncaught ReferenceError: Cannot access 'doctorize' before initialization
>    at ways-to-make-a-function.js:78
>(anonymous) @ ways-to-make-a-function.js:78

What about doctorize2? 

```js
console.log(doctorize2("wes"));

const doctorize = function(firstName) {
  return `Dr. ${firstName}`;
};
function doctorize2(firstName) {
  return `Dr. ${firstName}`;
}
```

It does work! The function declaration works, but the function expression does not work if you call it before you define it. Why?

Even though those are the exact same functions we have created, because you define a regular function with a function keyword and the other one with a variable, functions that are declared with the fucntion keyword are called hoisted.

That means that javascript takes all functions and hoists them up, up, up and says you're a function, you belong at the top of the file so that anywhere that you call the function it will be available to you. Javascript does **not** hoist variable functions. 

Why is that useful? Very rarely, Wes has never used that in his entire career except tiny use cases. 

Hoisting is more of an interview question that you may be asked. 
Essentially it means that javascript will take functions and bring them up before the yare called. You can technically run a function before it is defined with that ability. 

In `ways-to-make-a-function.js`, clear out the second doctorize2 function and just leave the function expression. 

**Arrow Functions**

The next way to make a function is using an arrow function. Arrow functions themselves have a few different ways of being declared. We will go over those now. 

Arrow functions are an addition to javascript which was addedi n the last couple of years.

They offer a couple of things. 

First, they have a concise syntax and are shorter. Often with tings like callbacks, its simpler to use an arrow function to write a one liner function. 

Another benefit is that they do not have their own scope in reference to the `this` word (we will go over `this` in more depth in the future).

Arrow functions are anonymous functions, which means there is no way to declare an arrow function the way we do a function declaration `function doctorize(){..}`. You always have to stick it into a variable.

To illustrate this, we will begin by writing a regular function. 

```js
function inchToCM(inches){
  const cm = inches * 2.54;
  return cm;
}
```

This function will take in inches and return centimeters. Let's try it ion in the browser. 

![](@attachment/Clipboard_2020-01-30-17-50-07.png)

This is a pretty simple function, but it still takes up four lines of code. We can make it a bit shorter by instead of creating a variable and then returning a variable, you can just return the calculation itself. 

![](@attachment/Clipboard_2020-01-30-17-52-26.png)
Note: you may notice in the screenshot that the return cm is now greyed out. That is because that code is unreachable which happens because we are returning on the line above, and when you return from a function, that function is finished running.

```js
function inchToCM(inches){
  return inches * 2.54; 
}
```

Now we can convert it to an anonymous function as a step on the way to making it an arrow function.

```js
const inchToCM = function(inches){
  return inches * 2.54; 
}
```

Refresh the page to check that it still works (it does!).  It still works in the same way, now we just have made it an anonymous function and stored it in a variable. 

Now we will go ahad and convert that function over to an arrow function. 
There are a couple of different ways we can do that, which we will go over now. 

Instead of writing the word function, we will delete it like so:

```js
const inchToCM = (inches){
  return inches * 2.54; 
}
```

Now we will go to the right of the paranthesis and add what is called a fat arrow `=>`.

In programming, `->` is referred to as a skinny arrow and `=>` is referred to as a **fat arrow**. 

```js
const inchToCM = (inches) => {
  return inches * 2.54; 
}
```

You might notice if you save, prettier will modify the function and remove the paranthesis which we do not want because we want to change it to an arrow function in steps. To disable that, add `/* eslint-disable */` right above the function. 

Note: the spaces between `(inches) => {` does not have to be there, `(inches)=>{` still works, but it's more readable with spaces.

If you refresh the page and run it in the console, you will see that it still works.

The next thing we will do is what is called an **implicit return**. 

An explicit return is when you type the return keyword, like in `return inches * 2.54`. That is an explict return meaning that we explicitly return the value there. 

And implict return is returning it without actually having to type the keyword return. Arrow functions allow us to return a value without having to type the keyword `return`. 

First, we will put the function on one line like so: 

```js
const inchToCM = (inches) => { return inches * 2.54;};
```

To get rid of the explicit return, first you put it on one line, delete the curly brackets`{` `}` and delete the keyword. 

`const inchToCM = (inches) =>  inches * 2.54;`

So what we did there is we made an arrow function called inchTocM which takes in one argument called `inches`, and then it implicitly returns the value. 

The way we can tell this is an implicit return is that:
1. it's all on one line
2. there is no return keyword
3. there are no curly brackets. 

If you refresh in the browser, you will see that it still works.

To recap: what we did there is we removed the function block, modified the code to be on one line, and removed the explicit return. 

Finally, and this is more of a stylistic choice, if there is only ever one parameter for your function, you can actually get rid of the paranthesis around the parameter as well, like so

```
const inchToCM = inches =>  inches * 2.54;
```

That is still your arrow function, we have just taken the paranthesis off because if there is only one parameter in your function, you can remove them no problem. 

Let's do another example!

Make a function called `add`, that takes in two parameters (first one `a` and second one`b`), we have set a default value of 3 in b. Then we make a temporary variable called total which we return.

```js
function add(a, b = 3) {
  const total = a + b;
  return total;
}
```
Pause the video now, try to convert it to an arrow function yourself and then come back to the video.

Let's first see if it works as it originally was. Save the code from above and refresh `index.html` in the browser. Open the console and test the function.

![](@attachment/Clipboard_2020-01-30-19-48-27.png)

You might notice that dev tools is giving us an annotation (?b), and that little question mark infront of b is telling us that the argument is optional. (`b` if optional because there is a default value to fall back on)

First thing we will do is stick the function in a variable calld add and remove the function name. `const add => function(a, b = 3) }`

Next we will convert it to an arrow function. Get rid of the keyword function and add a fat arrow to the right of the paranthesis. 

```js
const add = (a, b = 3) => {
  const total = a + b;
  return total;
}
```

Next we will return just `a + b` and get rid of the total variable. 

```js
const add = (a, b = 3) => {
  return a + b;
}
```

The next thing is put it on it's own line.

```
const add = (a,b = 3) => { return a + b; }
```

Then we can get rid of the function block and return keyword. 

```js
const add = (a, b = 3) => a + b;
```

Now we have a short arrow function! You may have noticed that we did not get rid of the parentheses, and that is because there is more than one parameter. 

There are a couple of other gotchas with arrow functions that we need to know about. Let's go over them now.

**Returning an object**

let's make a function called `makeABaby()` that will take in the babies first and last name. Inside of the function we will have an object call baby, with a name and age.

```js
function makeABaby(first,last){
  const baby = {
    name: `${first} ${last}`,
    age: 0
  }
  return baby;
}
```


It works!

![](@attachment/Clipboard_2020-01-30-19-58-43.png)

How would we convert this to an arrow function? First we will stick it in a variable, and convert it to an arrow. 

```js
 const makeABaby = (first,last) => {
  const baby = {
    name: `${first} ${last}`,
    age: 0
  }
  return baby;
}
```

If your function needs to do some stuff inside of the block, you can leave it as is. This is a perfectly valid arrow function. If the only thing you're using the arrow for is the ablity to type less as well as some of the benefits of not scoping this, this is totally valid.  However we can take it a bit further. 

Instead of declaring the baby variable we will just return the object directly.

```js
 const makeABaby = (first, last) => {
     return {
       name: `${first} ${last}`,
       age: 0
     };
  };
```

Now the question is... how would we do the implicit return?
We can put it on one line, no problem. (Objects can be put on one line).
But how would we return it. Let's try it. 

First put it on one line.

```js
const makeABaby = (first, last) => {return { name: `${first} ${last}`, age: 0}};
```

Now if we want to make it an implicit return, we get rid of the curly brackets and the return. 

```js
const makeABaby = (first, last) => { name: `${first} ${last}`, age: 0};
```

However, you will see this error if you try to run the code like that.
![](@attachment/Clipboard_2020-01-30-20-06-08.png)

Whats happening there is it thinks that the curly bracket from the baby object is actually the curly object from the block of the function. Curly brackets in javscript can be creation of an object, or a block of code. So how do you implicitly return an object when it gets confused about what it actually is. 

If you want to implictly return an object in javascript, you just pop a set of parentheses around the thing that you are returning and that will contain it and it won't think it's the block fo the function. 

```js
const makeABaby = (first, last) => ({ name: `${first} ${last}`, age: 0});
```

If you try it in the code, it still works.

Now is there a benefit of having the function this way or how we did it originally? Wes doesn't think so. Youre not really getting much benefit, in fact the way we had it originally was a bit more readable. 

There is nothing wrong with doing a regular function, because you want to think about your future self. Let's say you come back to the code in 6 months, what will be easier for you to read? Don't always go to making an arrow function by default, and hopefully throughout this course it will become more clear when you should reach for an arrow function (specifically with arrays and doing maps and reduce and filters).

**IIFE**
The next way to clear a function is using an IIFE (pronounced iffy). 
That is an immediately invoked function expression. 

We will do an example to demonstrate was an IIFE is. 

Add this function to our code (comment out the other code) and refresh `index.html`.

```js
function(){
  console.log('Running the Anon function');
  return `Your are cool`;
}
```

Nothing happens when you refresh `index.html` because it's not allowed to. We talked about how you can stick a function in a variable and that is okay. Another way to run this function is what is called an immediately invoked functional expression. 

What you can do is wrap that function in a parantheses, (parentheses always run first in javascript), and what that will do is return a function value and you can immediately run that function by putting paranthesis on the end like so:

```js
(function(){
  console.log('Running the Anon function');
  return `Your are cool`;
})();
``` 

Now, if you refresh the page, you will see the console.log which means that our function expression was immediately invoked. It was immediately run. 

What is the benefit of doing something like that? It used to be very popular before we had modules and block scope, you will realize when we get into scoping that a function declares its own scope and its often handy to even declare functions inside of the thing, and it will provide us a sheltered space where the variables can't leak inside. We will go over that later in the course. 

For now, just know that it's an immediate invoked function. 

One last thing is what if the function took an age? You would pass it like so:

```
(function(age){
  console.log('Running the Anon function');
  return `Your are cool and ${age}`;
})(age)
```

That isn't something you will be using that often, but it does come up when you need to create something like a closure (epxlained in future video). 

**Methods**

Next type of function we have is called methods. 

Wes has so far sort of been saying that methods and functions are the same thing and we have a video coming up that focused entirely on creating your own methods.  

A method is simply a function that lives inside of an object. 

If we take a look at the function `console.log` in the browser, so far Wes has been telling us that `console.log()` is a function. But he has been lying to us.   

`log()` is actually the functino that lives inside of console, and console is actually an object. If you type `console` into the console and open it up, you will see that there are all kinds of things within it.

![](@attachment/Clipboard_2020-01-30-20-26-46.png)

Scroll down to log, and the little f ![](@attachment/Clipboard_2020-01-30-20-27-19.png) you see means that it's actually a function.

So `console` is the object and `log()`, `count()` or any of the other functions listed under the console object are the functions. 

We have a special word to describe functions that live inside of an object and we call those methods. 

So we can actually do something like this..

```js
const wes = {
  name: 'Wes Bos',
  sayHi: function(){
    console.log('Hey wes!');
    return 'Hey Wes!';
  }
}
```

Try it in the browser, first type `wes` and hit enter and next type `wes.sayHi()` and hit enter. You should see the following:
![](@attachment/Clipboard_2020-01-30-20-30-25.png)

Wes.sayHi() is a method. You make it a property on your object and you set it to a function.

Those functions can also have names. Sometimes you will see something like this:

```js
const wes = {
  name: 'Wes Bos',
  sayHi: function sayHi(){
    console.log('Hey wes!');
    return 'Hey Wes!';
  }
}
```

Wes doesn't see the point of doing something like that, but it is technically allowed. 

There is also a new shorthand method. 

```js
const wes = {
  name: 'Wes Bos',
  // Method!
  sayHi: function sayHi(){
    console.log('Hey Wes!');
    return 'Hey Wes!';
  },
  //Short hand Method
  yellHi(){
    console.log('HEY WESSSSS');
  }
}
```

If you refresh the browser and type `wes.yellHi()`, it will work.  

What we did there is instead of writing `sayHi: function()`, which will work, we can get rid of the function keyword and the colon and what that will do is make a property called `yellHi()` set to a function `yellHi`. It's just a shorthand way to write methods inside of an object.

There is another way, which is an arrow function. 

```sj
const wes = {
  name: 'Wes Bos',
  // Method!
  sayHi: function sayHi(){
    console.log('Hey Wes!');
    return 'Hey Wes!';
  },
  //Short hand Method
  yellHi(){
    console.log('HEY WESSSSS');
  }
  //Arrow functino
   whisperHi: () => {
     console.log('hiii wess im a mouse');
   }
```

`whisperHi()` is an arrow function that doesn't take any arguments, but it could take in arguments if you wanted.

Those are three different ways to do methods and the short hand is the most common way.
The only reason you would do an arrow function is because you don't want to access this.

The only reason you would do an arrow function is because you don't want to access this. We will go over that when we get to objects but really quickly Wes will show us. 

If you modify the `sayHi()` method to add `console.log(this);` and ran it in the browser

```js
 sayHi: function sayHi(){
    console.log(this);
```
You will see that on the line in our code that we console logged, we will see the value of `this` returned. 

![](@attachment/Clipboard_2020-01-30-20-43-26.png)

`this` is equal to the object that it was called against. That is cool because you could actually do something like this:

```js
const wes = {
  name: 'Westopher Bos',
  // Method!
  sayHi: function sayHi(){
    console.log(`Hey ${this.name}`);
    console.log('Hey Wes!');
    return 'Hey Wes!';
  },...
```

You would see it immediately fulls the value of the name property. 

![](@attachment/Clipboard_2020-01-30-20-44-42.png)

That will not work in an arrow function because they take the parent scope of this. We will explain that in the future. 


**Callback Functions**
The final thing Wes wants to talk to us is something called callback functions.

So a callback function is just a regular function, but we sort of use that name for something that will happen when something is done. The easiest way to define a callback function is either when someone clicks something, run this. Or when this amount of time has passed, run this.

Let's look at both of those examples.

**Example 1**

We will do a click callback. 

Go into our `index.html` file and give ourselves a button that say click me and give that a class of `clickMe`.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1.0" />
    <title></title>
    <link rel="stylesheet" href="../../base.css" />
  </head>

  <body>
    <button class="clickMe">Click Me!</button>
    <script src="./ways-to-make-a-function.js"></script>
  </body>
</html>
```

Go back to the javascript file. 

We will select the element (we will go over in depth more about the DOM later) like so

```
const button = document.querySelector('.clickMe');
console.log(button);
```
Refresh the page and open the console to see that it works.

![](@attachment/Clipboard_2020-01-30-20-57-19.png)

Now we are goign to listen for a clikc on that button like so:  

```
const button = document.querySelector('.clickMe');
button.addEventListener('click', wes.yellHi());
```

When that click hapens, we can pass it to any function that we want. in this case, we chose `sayHi()` from our `wes` object from a previous example. 

Now, everytime you click it, it will say HEY WESSSS

![](@attachment/Clipboard_2020-01-30-20-59-21.png)


What is happening there is that `.addEventListener()` is an event listener that we are listening for a click on, and the callback function is `wes.sayHi()`. 

It's a functino that we give it access to. Notice that we are not running it there, we are just saying here is the function dear browser, when someone clicks that button please be a dear and calll that function. That is what is referred to as a callback function.

Callback functions can be declared outside of the handler, so making a function like

```js
function handleClick(){
  console.log('Great clicking!!');
}
button.addEventListener('click', handleClick);
```

What we are telling the browser to do here is that when someone clicks the element with the class '.clickMe`, run the functino called `handleClick`. 

 The other option, that is probably half as common, where you define the function outside and then pass in the reference to the function. 
Another thing you can do is just pass it an anonymous function. You can do this

```

button.addEventListener('click', functino(){
  console.log('nice Job!');
});
```

![](@attachment/Clipboard_2020-01-30-21-06-26.png)

And it works just fine when you press it. 

What we have done there is we have passed it an anonymous function as a value directly and the browser will know to call this function itself. There are upsides and downsides of doing it that way which we will get into another time. 

What you need to know is that a callback function is a function that gets passed into another function and then it is called by the browser at a later point in time.

The other example we have is a timer callback. There are a couple way to do timers (we will go over all of them in the future) but the simplest is `setTimeout()`.

```
setTimeout();
```

It takes two things:
1. a function to call after a certain amount of time
2. a duration in milliseconds (after how long should I run this)


So let's do `1000` milliseconds which is one second later. If we run the page after one second, it will run 

```js
setTimeout(wes.yellHi(), 1000)
```

If we run the page after one second, it will run HEY WES. 

You can also pass it an anonymous function.

```
setTimeout(function(){
  console.log('DONE TIME TO EAT');
}, 1000);
```
After a second that will console log DONE TIME TO EAT.

You can pass those as arrow functions as well.


```js
setTimeout(() => {
  console.log('DONE TIME TO EAT');
}, 1000);
```

That will work the same!

---

## 16 - Debugging Tools

There are two parts of debugging: 
1. there are tools you can use to get info when things go wrong
2. the right mindset to be a good problem solver

This video will focus on the tools. What Wes' hopes for is that as you go through the course, anytime we start to hit a roadblock, Wes won't cut it out of the video, he will leave it in and show us his thought process.

Go into the exercises folder, there is a folder 16 called Debugging and then inside of that there is a file called `debugging-START.js` and `debugging.html`. 
If you open `debugging.html`, you will see that it's just a basic html file where we are loading base css, we have a button that says make me bigger and then a script tag that is loading `debugging.js` which doesn't exist yet. Make a copy of the `debugging-START.js` file and save it as `debugging.js`. 

This file contains a bunch of stuff we haven't learned yet: arrays of objects, loops, functions, event listeners, etc. It doesn't matter that we don't know what all those different things do yet, Wes will explain that later and we will learn how to build our own. This is more so we can test different types of debugging. 

We will start with console debugging. 

There is `console.log()` which is the most common one you'll see. 

```
people.forEach((person, index) => {
  console.log(person.name);
});
```

There is `console.info(person.name)` which usually gives you a little eye and cirlce beside the console output but it doesn't seem to be there right now.

There is `console.error(person.name)`. That isn't used for throwing or handling errors (we will learn about that), this just changes what the log looks like in the console. 

![](@attachment/Clipboard_2020-01-31-17-46-02.png)

It also gives you a stack trace:
![](@attachment/Clipboard_2020-01-31-17-47-21.png)

There is `console.warn()` which is very similar to `console.log()` 

![](@attachment/Clipboard_2020-01-31-17-47-38.png)

There is `console.table()`. Anytime you have a list of objects, and the objects have the same property (meaning the objects all have `name`,`cool`, and `country` properties), `console.table()` will format that into a nice little table.

```
console.table(people);
```
![](@attachment/Clipboard_2020-01-31-17-49-45.png)

There is `console.count()`. This is useful if you want to know how many times a function is being run. If we go into the `doctorize()` function in `debugging.js` and add a `console.count('runinng doctorize');`, and then refresh the html page, now everytime you type `doctorize('wes');` in the console, the console will log a count. 

![](@attachment/Clipboard_2020-01-31-17-52-29.png)

That is useful in a scenario where you aren't sure if a function is running twice, or somethings you are working with hover elements and it's getting triggered way too often. `console.count()` will show you how many times it's actually running. 

You can also pass variables to `console.count()`. If you were to change the example to backticks

```
function doctorize(name) {
  console.count(`running Doctorize for ${name}`);
  return `Dr. ${name}`;
}
```

Now if you type in the console `doctorize('wes')`, it will show the count, but if you run `doctorize('snickers');`, it goes back to one. 

![](@attachment/Clipboard_2020-01-31-17-57-25.png)

But if you call `doctorize('wes');` again, it maintains that. 

![](@attachment/Clipboard_2020-01-31-17-58-57.png)

So it's based on what strings you pass to the console.count().

Next we have `console.group()`, that can be helpful if you have a bunch of stuff to console.log(). 

We will make a function `doALotOfStuff` to demonstrate. Comment out all of the example consoles we have gone over so far. 


Add `console.group("Doing some stuff")`, and then underneath it add a few more consoles such as log, warning, error. Then add `console.groupEnd()` and pass it the same string we had passed to `console.group()`. 

```js
function doALotOfStuff() {
  console.group("Doing some stuff");
  console.log("Imone");
  console.warn("watch out!");
  console.error("hey");
  console.groupEnd("Doing some stuff");
}
```

![](@attachment/Clipboard_2020-01-31-18-15-45.png)

What it does is it groups together all of `console.log()` into a groupable thing, and that can be very helpful. We will do another example in the `people.forEach()` method. 

```
people.forEach((person, index) => {
  console.group(`${person.name}`);
  console.log(person.country);
  console.log(person.cool);
  console.log("DONE!!");
  console.groupEnd(`${person.name}`);
});
```

![](@attachment/Clipboard_2020-01-31-18-20-52.png)

It nicely organizes the people into their separate collapsable section.

You can actually also do `console.groupCollapse()` which will by default collapse all the groups. 
![](@attachment/Clipboard_2020-01-31-18-22-08.png)

stopped @ 6:57
