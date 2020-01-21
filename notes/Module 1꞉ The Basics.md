---
attachments: [Clipboard_2020-01-19-17-07-50.png, Clipboard_2020-01-19-17-09-59.png, Clipboard_2020-01-19-17-25-44.png, Clipboard_2020-01-19-17-52-35.png, Clipboard_2020-01-19-18-07-43.png, Clipboard_2020-01-19-18-09-31.png, Clipboard_2020-01-19-18-23-06.png, Clipboard_2020-01-19-18-25-49.png, Clipboard_2020-01-19-18-26-31.png, Clipboard_2020-01-19-19-18-45.png, Clipboard_2020-01-19-19-19-39.png, Clipboard_2020-01-19-19-19-54.png, Clipboard_2020-01-19-19-40-13.png, Clipboard_2020-01-19-19-45-07.png, Clipboard_2020-01-19-19-45-10.png, Clipboard_2020-01-19-19-45-44.png, Clipboard_2020-01-20-19-31-26.png, Clipboard_2020-01-20-19-39-40.png, Clipboard_2020-01-20-19-47-16.png, Clipboard_2020-01-20-20-17-03.png, Clipboard_2020-01-20-20-19-01.png, Clipboard_2020-01-20-20-23-21.png, Clipboard_2020-01-20-21-30-55.png, Clipboard_2020-01-20-21-36-56.png]
title: 'Module 1: The Basics'
created: '2020-01-19T22:03:47.486Z'
modified: '2020-01-21T03:08:16.031Z'
---

# Module 1: The Basics

---
## 01 - Welcome 

Welcome, and thanks for checking out Beginner Javascript. This is all the stuff Wes wishes he had known over the last 10 years of him doing Javascript, so it's a big course but it does a good job of distilling the information down into the things you need to know and making it easy and fun.
 
 This video is for housekeeping items that need to be addressed before we can get into writing code.

 First one is the starter files for this can be found at beginnerjavascript.com, click through to My Account and there will be a link like this ![](@attachment/Clipboard_2020-01-19-17-07-50.png) to the starter files. There is also a link to the slack channel, where you can jump in and get help, maybe join up with a buddy and do a course together with someone. The starter files link will bring you over to github which has all of the starter files as well as all of the solutions for this course. Please star the beginner-javascript github repo to help Wes up!

 There are three folders in the beginner-javascript repo. 

 ![](@attachment/Clipboard_2020-01-19-17-09-59.png)

 There is a `snippets/` folder that has some base HTML snippets in there with instructions on how to get them into your HTML editor (we will talk about the editor in the next video). 
 
 There is also a `/playground` folder. This folder will have some HTML files where when Wes is trying to explain a concept, he will play around within that file. He will often provide a `-FINISHED.html` file, which will include what Wes has written in the video, whereas the file itself, Wes will either ask you to create it yourself or he will provide an empty state. 

 The `/excercises` folder contains all the proper, full blown excercises that we will be doing throughout the course. 

 Note: sometiemes the numbers are going to be a little off from the video number is, so just make sure to line up the file with the name of the video, not necessarily the number. 

 Another thing is how should you do this course?  Should you watch it, should you code, should you code while you watch? About half the people prefer to watch it and then do it after, and the other half prefer to do it as they watch. Try both methods and see what best works for you! You'll fall into whatever feels best for you pretty quickly. 

 Last thing is grab a buddy if you can. Jump into the slack chatroom and see if there is anyone willing to do it with you, you can team up, or team up with someone in person. It's always better if there is someone to hold you accountable. It's a long course, 28 hours long, you can jump around. 

 If you understand what functions are for example or what parameters are, feel free to skip those videos. The whole idea is that it is referenceable. We are not building a huge app here that be build on in every video, instead, every video pretty much stands on it's own and if we reference something from a previous video, Wes will mention it. 

 ---

 ## 02 - Browser, Editor and Terminal Setup

 Let's talk real quick about setup and the tools you need. 

 You can skip this video if you know the three things: 
 1. Which browser you would like to use (as well as how to open the dev tools)
 2. You already have NodeJS and NPM installed. 
 3. You have an editor that you like (such as VSCode). 

If you already have those things in place, skip this video and move onto the next one. Wes will just be introducing all three of those and talking about his personal choices behind them. 

Let's get into the browser. You can use Firefox, Chrome, any browser you like because we are just writing javascript. The important thing here is that we will be using the developer tools. Both Firefox and Chrome have very good web developer tools, Wes will likely be using Chrome throughout the course. 

Things you need to know how to do is open the dev tools. You can just right click and select "Inspect Element", which will show you the DOM, and you can click over to the console. 

It's worth learning the shortcuts to quickly open up developer tools, inspect element and the console. That way you can really quickly open it. 

To find the shortcuts, in Chrome you go to View -> Developer and then you can see the shortcuts. 

In Firefox, you click on the hamburger menu and go to Web Developer -> and then you will see the shortcuts for Inspector and Web Console, which is the two we will be using. 

Next up, we need NodeJS. In order to install NodeJS, go to NodeJS.org and install the latest version. ![](@attachment/Clipboard_2020-01-19-17-25-44.png)

Don't pay attention to the version numbers, those will change depending on when you take the course. The stuff that we are covering is not dependent on what version of node you use, we aren't writing NodeJS websites in this course, instead a lot of tooling, bundling, formatting etc uses NodeJS under the hood so we need to have that installed.

How do you know if you have it installed or not? You can go ahead and install it again and all that will do is update your NodeJS to the current version if you already had it installed. 

Another way to check is to open up a terminal window. You can use the built in terminal application which on a Mac you can find under Applications -> Utilities -> Terminal. Wes is using a terminal called Hyper to his terminal. You can also use the terminal in VSCode. You can use iTerm. They are all the same terminal at the end of the day. If you want to know what theme Wes is using, you can go to wesbos.com/uses and that will give you the links to all of the different themes and things he is using. 

How do you know once you have a terminal open? You can go ahead and type  `node - v` in the terminal and press enter. That will let you know what version you have installed. You need to also check that you have NPM installed. You can do that using `npm -v`, which will tell you what version of NPM you have installed. As long as you have something greater than 10 for node and 6 for npm, you should be fine. 

On Windows, the terminal is called Command Prompt. You can access this by going to Start -> All Programs -> Accessories -> Command Prompt. There is another terminal for Windows called Cmder.

Wes wants to avoid going down any  rabbit holes regarding complex tooling and best ways to do things. You just need to have it installed and it will be working.

Now we will do some command line basics in case you are not familiar with working in the command line.

There are a couple of commands you need to know in order to run our javascript and bundles. 

Cmd Line Basics

`cd` - this means change directory
`ls -l` (mac) `dir` (windows) - this will list out all of the files and directories under the current directory
`pwd` - print working directory will give you something like `/Users/wesbos/beginner-javascript/excercises`. 
`cd ..` - go up a level in the current directory 

![](@attachment/Clipboard_2020-01-19-17-52-35.png)

In this example, Wes is in the `beginner-javascript` directory, and he uses the command `ls -l` to see what other directories he has nested inside his current directory. Now he can use the `cd` command to change directories into the `/excercises` directory by typing in `cd excercises`.

If you want to learn how to customize your terminal, you can go to https://commandlinepoweruser.com to take a quick course of Wes' to get you up and running with a cool terminal that shows the prompt and current working directory like Wes' does. That is not part of this course, just for those who are curious. 

Other things to know are going up a level in a directory. You can do that using `cd ..` 

That is all we need to know right now. 

If you want to see if your node is working, if you just type `node` that will give you a caret which will oad up a REPL which is a read-eval-print loop. That is essentially the console. You can do 1+1 and press enter and the console will evaluate that to 2. 

To get back to the command line if you have run the `node command` you have to press CTRL + C a few times to exit back into the terminal. 

Other helpul things are:

`cmd + k` or `cmd + r`  (mac) or `ctrl + k` or `ctrl + r` (windows) - will clear out the console. 

(this works in Chrome dev tools console as well)

Finally we are on the topic of the editor. 

Wes highly recommends you use VSCode because he thinks it's the best editor for writing javascript in. You may have different opinions. In terms of tooling, Wes feels that VSCode is the best. We will be looking at some extensions to use to format Javascript properly. Again if you want to know what theme Wes is using, refer to wesbos.com/uses. 

---

## 03 - Running and Loading JS 

Let's talk about how to actually run Javascript. There are a couple of ways we can run Javascript, we can run it in the console, we can run it in node, we can run it via a script tag, we can also have an external script. We will talk about how we can actually run those. 

The simplest is to open up your dev tools and go to your console. If you want to run some javascript to see how it works, like here Wes has typed 1 + 1 and hit enter and the console returned 2. 

![](@attachment/Clipboard_2020-01-19-18-07-43.png)

This right here is a javascript console and it's a nice way to quickly noodle on some javascript to see how it works, just pop open a console. The neat thing is if you are on any websites, say github.com, the javascript that you type into your console runs on the actual page that is loaded and existing. 

For example Wes types 
`document.querySelectorAll('p')` 
to grab all the paragraphs from the github page that he is currently on. ![](@attachment/Clipboard_2020-01-19-18-09-31.png)
(Don't worry about what `document.querySelectorAll()` does, we will cover that in a future video). The code that runs in your dev tools console is running in the context of the page that is loaded in your browser tab. 

Now let's move into another way. 

Go into the playground folder and create a new file called `running-js.html`. Wes has an Emmet extension so he is going to hit `!` and `Tab` to scaffold out some HTML for us. 

In the body, we can have a script tag in which we will `console.log('hey')` . What that will do is when the HTML is loaded, it's going to say "OH! This is a script tag, I am changing languages from HTML over to Javascript, and it will run any code inside of the opening and closing script tag as javascript. If you go ahead and open the `running-js.html` file in the browser, and open the console, you will see that it says "hey". 
![](@attachment/Clipboard_2020-01-19-18-23-06.png)

Don't sweat this too much, we will be explaining what console.log and everything does shortly. 

One thing to keep in mind is that it's almost always worth running scripts just before the closing body tag. So if we were to modify `running-js` to include a pargraph tag that says Hey right after the body tag, like so: `<body><p>Hey</p>`, and then we wanted to grab that paragrah via javascript, we could if our script is right located right before the closing body tag. 

![](@attachment/Clipboard_2020-01-19-18-25-49.png)

If you were to move the script tag above the paragrah (or move the paragraph below the script tag), and refresh the page, the console will show `null` because that means it found nothing. 

![](@attachment/Clipboard_2020-01-19-18-26-31.png)

That is because in order for your script tag to access the elements on the page, the elements must first be on the page before you select them. 

If we try to select something that doesn't yet exist (because it gets created later), we won't have access to it.

For your own sanity, always put your javascript right below the closing body tag. (We will talk about loading in future videos when we get a little bit more into the DOM). 

Another way we can do it is via an external javascript file. If you go into the playground and make an external javascript file, called `some.js`. In that file, add the following code: `console.log('I am in another file')` and save.

Now in the `running-js.html` file, remove the existing script block and instead add a script tag with a `src` attribute. You do not need a `type=` attribute until we hit modules. Inside of the `src=` attribute, you need to give it a relative path, like so `<script src="./some.js">`. This works because the HTML file is in a folder where the sibling is `some.js`. Dot forward slash `./` means in this folder. Dot dot `../` would mean go up a level. In our case, it's in the same folder so  `./some.js` is the relative path to our file. 

Now if you run that, it will say in the console `I'm in another file`, and it will even show you where that javascript had been run.
![](@attachment/Clipboard_2020-01-19-19-18-45.png)

Again, if you were to put the script inside the HEAD, it will still work. 
![](@attachment/Clipboard_2020-01-19-19-19-54.png)

However, if you were to try to select some things on the page, such as the paragraph tag, you will get null. 

![](@attachment/Clipboard_2020-01-19-19-19-39.png)

Why? Because of the same reason. The script will run before the actual HTML is finished building on the page. Now there are some options like the `async` and `defer` attributes you can add to your script tags that will delay the actual running of the javascript, and it will download it asynchronously and then run it once the HTML has been loaded, however that is a much more advance topic which we will get into once we discuss async. But first we will need to understand what does asynchronous mean, etc. 

Leave the script tag right before the closing body tag for the best performance and to save yourself future debugging headaches. 

Another thing you may have noticed is why is there a closing script tag if there is no content inbetween the opening and closing tag? That is a quirk with the script tag. It cannot be self closed. You also cannot add extra javascript between the script tag like so: ![](@attachment/Clipboard_2020-01-19-19-40-13.png) That will not work. 

You can have multiple script tags, if you like. The only downside to that is that every single time that it hits one of those, it will go off and download and parse that for you. When we hit modules, we will look at how we can bundle those multiple files into one. Or you can do something called code splitting, which is split them into multiple, smaller javascript files, and have them load on demand. 

One more is actually running it in NodeJS. 

If you create another file in the playground called `node-example.js` and add in the following code: `console.log('I'm from node')`. 

NodeJS is javascript that can run in the server. So instead of running javascript on a website, we run it on an actual machine (like many other programming languages do).

The way we do that is we open our terminal and cd into the playground directory. You can run the script in node by entering the following in the terminal: `node node-example.js` and hitting enter. That will run whatever code is in the script file, and once it's done, it will exit out of node and return you to the terminal.

![](@attachment/Clipboard_2020-01-19-19-45-44.png)

That's the short of how to load javascript. We will be using a mixture of running javascript in the console, in a script tag and in external javascript files. 


---

## 04 - Variables and Stateements

This video is going to teach you an introduction to variables. Variables are a building block of javascript, and you can't use javascript without knowing variables so we are going to get a primer on what they are, what the different types of them are, what declaration means as well as what a statement is in javascript.

Go into your `/playground` folder and make a new file called `variables.html`. Use the HTML base snippet and add a script tag within the body. To make sure everything is working, add a `console.log('hey');` within the script tag. Wes will explain the use of the semi colon shortly. 

If you open up the `variables.html` file in the browser, you should see 'hey' in the console. 

![](@attachment/Clipboard_2020-01-20-19-31-26.png) 

There are three different ways to make a variable, which in Javascript we refer to as declaring a variable. They are: `var`, `let` and `const`. 

Let's start with `var`. To make a variable you say `var` and then you make a name of the variable. You can use almost anything for a variable name (we will discuss restrictions shortly)

```javascript
var first = 'wes' 
```

What we have done there is created a new variable called `first` and we set it to a string (we will discuss what that is in a second) of 'wes'.

Now, if you refresh the `variables.html` page, and type into the console `first`, you will see that we actually get the value that is inside of that variable. 

![](@attachment/Clipboard_2020-01-20-19-39-40.png)

You can also do it by doing a console.log like so:

```html
<body>
<script>
  var first = 'wes';
  console.log(first);
</body>
```

The second way to delcare a variable is with `let`.     

Add `let age = 300;` below the declaration of the variable `first`. 

If you refresh `variables.html`, and type in age, you will see 300 returned in the console. 

The third way is with `const`. Below the `age` variable, add the following: `const cool = true;`. That is what is called a constant variable.

The naming of these things aren't great. Const means constant, but it's still called a variable. `var`, `let`, `const` are all different types of variables, and there is different ways to declare the variables and we will talk about the pros and cons to all of them in just a second. 

Before we do that, let's discuss the semi colon Wes is adding after each javascript line. 

![](@attachment/Clipboard_2020-01-20-19-47-16.png)

These semi-colons are used to terminate the line of javascript. 
`var first = 'wes';` is what is refered to as a "statement" in javascript. A statement is an instruction  to the computer, browser, the javascript interpreter to do something. 

This can usually be summarized as a variable was being declared, a variable was being updated, a function was being called, something was console.logged. 

Anytime  you want to do something in javascript, that is referred to as a statement. When you are done your statement, you add a semi-colon to the end of the line. 

```js
var first = 'wes'; //variable declaration statement
let age = 300;
let cool = true;
console.log(first); //function call statement
```

One thing that we will run into in javascript is something called a "code block". 

For example, add the following line of code to `variables.html` and refresh the page

```js
if(age > 10){
  console.log('you are old');
}
```

You should see the message "you are old" in the console. 

The question is how come we didn't put the semi-colons after each line like this: 
```js
if(age > 10){;
  console.log('you are old');
};
```

That is because it's something that is referred to as a code block. Code blocks are things that are bound by these curly brackets `{` and `}`.  

Things like function definitions, if statements, loops do not need a semi-colon at the end because you aren't telling the computer to do something, you are just running some code and you are telling the computer to do something inside of it. 

Throughout the course Wes will continue to mention why we do and do not use the semi-colon so you can get the hang of it.

It is possible to get away without writing semi-colons in javascript because there is something in javascript called ASI, which is automatic semi-colon insertion but we are not cover that because it's a much more advanced topic. Devs use don't use semi-colons know how ASI is working and they take advantage of that. That is totally fine, but it's best to learn javascript with semi-colons. 


Let's talk about the difference between the three types of variables. 

Remove all the extra javascript code within `variables.html` except for:

```js
<script>
  var first = 'wes'; 
  let age = 300;
  let cool = true;
</script>
```

So `var` and `let` can be updated. If you ever want to change what the value is of one of those variables, you can simply just change it. For example, if you add the following line of javascript, refresh `variables.html` in the browser and type `first` in the console, you should see the value `westerhoff` returned. 

```html
first = 'westerhoff';
</script>
```

![](@attachment/Clipboard_2020-01-20-20-17-03.png)

The same can be done with the age variable. 

For example type in the console `age = 400`. That updates the value of the `age` variable. 

![](@attachment/Clipboard_2020-01-20-20-19-01.png)

You can either run the javascript from the `variables.html` page, or you can run them from the console. Because the variables in `variables.html` are global variables (we will cover what that is in a future video), we can modify the either in the script tag within `variables.html` or directly from the console. 

Notice that we do not have to redeclare the variable. We did *not* have to do something like this:

```js
var first = 'wes';   
let age = 300;
let cool = true;

var first = 'westernhoff';
```   

That is actually a bad practice and in most cases, won't even work. You only need to declare the variable with `var`, `let`, or `const`, and then whenever you want to update the value, you don't need to put that infront of it, you can just go ahead and set it to it's new value. 

You CANNOT set a const variable to be something else. If you were to go `cool = false`, you will see the following error: ![](@attachment/Clipboard_2020-01-20-20-23-21.png)

Errors in javascript will tell you what went wrong and where it went wrong. Here it says "Uncaught TypeError: Assignment to constant variable on Line 18.". Now that is exactly what we did, we tried to change a variable that was set to a constant. Constant variables cannot be changed, so think of them like an API key or something that you never want changed. You set those to a constant, and the value of that variable can never be changed. Now, that is not totally true, we will follow up when we hit arrays and objects (meaning that there is a difference between the array or object that it is bound to and the values that live inside of it). What we need to know right now is just that `var` and `let` variables can be changed or updated, and `const` variables cannot. 

The next thing you need to know about variables is this thing called **Strict Mode**. 

TIP: While in your code editor, you can select a block of text and on your keyboard press `Command` + `/` to comment out your code. Commenting out code makes your browser skip that code. It'll still be there, but the browser will not run it. 

If you put this code in the script tag, refresh `variables.html` and write dog in the console, the console will return the value of "snickers". 

```
<script>
    // var first = 'wes';   
    // let age = 300;
    // let cool = true;
    
    // first = 'westerhoff';
    // cool = false;

    dog = 'snickers';
  </script>
```

We made a variable even though we did not `var`, `let`, or `const` it. What is going on? How can that happen? 

Now if we go to the top of our opening script tag, and add `use strict;` and then refresh the page, we will see the error "dog is not defined". 

![](@attachment/Clipboard_2020-01-20-21-30-55.png)

In the early days of javascript, it was possible to create a variable without first declaring it, and the browser would just add the var on behalf of the user. That leads to bad code down the road, it's pretty sloppy and it's not something that you want to do. So what happened? Javascript still supports the old method of not declaring a variable because it has to be backwards compatible with early javascript code. But they can introduce new modes into the browser like strict mode, which will throw an error if you try to do something like not declaring a variable properly. 

```
var dog = 'hugo';
dog = 'snickers';
```

First you are declaring the variable dog and then updating it with the value of snickers. 

Another thing you can do is just declare a variable and then update it on the next line like so: 

```
var dog;
dog = 'snickers';
```
That will work because what happens here is if you comment out the second line so it's just `var dog;` and refresh `variables.html`, when you type dog into the console you will have the value of undefined returned to you. 

![](@attachment/Clipboard_2020-01-20-21-36-56.png)

Strict mode is useful but we won't be typing it every time in this course because we are going to be following best practices and it is enforced by default when you are using javascript modules, and modules are probably how you are going to be writing all of your modern javascript.

Now let's talk about the second difference between `var`, `let`, and `const`, which is scoping. 

Clear your javascript code until it's back to the three variables we had at the beginning.

```
 var first = 'wes';   
 let age = 300;
 const cool = true;
```

Scoping in javascript answers the question "Where are my variables available to me?". We are going to have an entire section of this course focused on scoping because it's such a fundamental part of javascript, but for now we need to know that:

`var` variables are scoped differently than `let` and `const` variables.

`var` variables are what we refer to as function scoped variables. 

`let` and `const` variables are what we refer to as block scoped variables. 

What does this mean?!

We are going to learn what blocks and functions are in the future. Since we haven't covered that yet, just put that on ice temporarily. Just know that var variables are function scoped (they are only available within the parent function), and `let` and `const` are block scoped {}. We will continue on in the functions and block video about this. 

The question is, what are we going to be using in this course?
They are all valid. `let` and `const` were introduced as part of what is called es6, which is only a couple of years old. `var` has been around since javascript has been invented. 

You may sometimes see people say `var` variables are old or deprecated, but they are not. It's just that some developers (Wes included) prefer to use `let` and `const` because the block scoping makes more sense as well the benefit of assigning a constant value to these constants and not accidentally overwriting a variable which can lead to bugs. 

Here is how Wes' approaches deciding which of the three to use:

- He uses `const` by default. Anytime he is assigning a new variable, he just defaults it to `const` because he doesn't know if he'll need to be updating that or not. 
- If he needs to change a value of a variable, he will use a `let`. Sometimes he will make a variable `const` and then realize he needs to update it so he will make it a `let`.
- Wes almost never uses a `var` variable. There are some exceptions like when declaring a variable outside of a block but we will go into more detail about that shortly. 

Last thing we need to talk about is **naming conventions**.

What can you call your variables? As a convention, variables should not start with a capital. For example `const Dog = 'bowser';` will work in the browser, it's not wrong, it's not broken javascript, but it's convention that variables should not start with a capital unless they are a class (we will get into that once we get into classes, prototypes and things like that). 

Variables must start with either an a-Z letter (a,b,c,d etc). They can also start with or contain an underscore `_` or dollar sign `$`. 

For example you could do `const $$$$$$$$ = 100;` and it would work. A variable like `$_$` would also work. 

`$` and `_` are the only non a-Z characters that can be used inside of variables. 

The `_` is sort of synonymous with a library called lowdash, and the $ is sort of synonymous with a library called jQuery so you don't normally make your variables called $ or _ because they have sort of been taken as a convention. You can however certainly include them if you want.

If a variable is made up of two words, for example `const iLovePizza`. This is referred to as camel case. With camel case, every word inside of your variable will contain an uppercase except for the first one, for the reasons we just talked about. Upper camel case is where you do start it with a capital (ILovePizza), however that is almost never used in Javascript unless you are defining a class. 

 There is also something called Snake Case. Instead of using capitals between words, you use underscores. For example `const this_is_snake_case = 'cool';`.

 There is also something called kebab case, for example `const this-is-kebab-case` but this is **not** allowed in javascript. 

 Most developers will always use camel case, UpperCamelCase if you are building a class, some people like underscores and kebab case is not allowed. 
 
  





















































































