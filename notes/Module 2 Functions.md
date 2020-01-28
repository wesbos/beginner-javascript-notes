---
attachments: [Clipboard_2020-01-28-16-43-12 (2).png, Clipboard_2020-01-28-16-47-39 (2).png, Clipboard_2020-01-28-16-48-49 (2).png, Clipboard_2020-01-28-17-00-34.png, Clipboard_2020-01-28-17-05-22.png, Clipboard_2020-01-28-17-12-10.png, Clipboard_2020-01-28-17-15-30.png, Clipboard_2020-01-28-17-16-18.png, Clipboard_2020-01-28-17-17-04.png, Clipboard_2020-01-28-17-18-49.png, Clipboard_2020-01-28-17-25-44.png, Clipboard_2020-01-28-17-27-44.png, Clipboard_2020-01-28-17-31-06.png, Clipboard_2020-01-28-17-35-06.png, Clipboard_2020-01-28-17-35-44.png, Clipboard_2020-01-28-17-41-21.png]
title: 'Module 2: Functions'
created: '2020-01-28T21:27:12.651Z'
modified: '2020-01-28T22:51:18.993Z'
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

Make a new folder inside of the `/playground` directory and call it `custom-functions`. 
