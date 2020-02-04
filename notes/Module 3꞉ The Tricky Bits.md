---
attachments: [Clipboard_2020-02-03-18-47-58.png]
title: 'Module 3: The Tricky Bits'
created: '2020-02-03T23:25:39.261Z'
modified: '2020-02-04T00:05:25.700Z'
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
/* eslint-disable */
const first = 'wes';
let second = 'bos';
var age = 100;
```

if you reload `scope.html` in the browser and then in the console type in `first`, `second` and `age`.

stopped @ 3:21 of 17
