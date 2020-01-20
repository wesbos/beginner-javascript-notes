---
attachments: [Clipboard_2020-01-19-17-07-50.png, Clipboard_2020-01-19-17-09-59.png, Clipboard_2020-01-19-17-25-44.png, Clipboard_2020-01-19-17-52-35.png, Clipboard_2020-01-19-18-07-43.png, Clipboard_2020-01-19-18-09-31.png, Clipboard_2020-01-19-18-23-06.png, Clipboard_2020-01-19-18-25-49.png, Clipboard_2020-01-19-18-26-31.png, Clipboard_2020-01-19-19-18-45.png, Clipboard_2020-01-19-19-19-39.png, Clipboard_2020-01-19-19-19-54.png]
title: 'Module 1: The Basics'
created: '2020-01-19T22:03:47.486Z'
modified: '2020-01-20T00:28:22.611Z'
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


stopped @ 5:54 of 03 - Running & Loading JS 





