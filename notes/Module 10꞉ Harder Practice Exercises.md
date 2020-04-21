---
attachments: [Clipboard_2020-04-20-17-44-07.png, Clipboard_2020-04-20-17-49-26.png, Clipboard_2020-04-20-17-51-12.png, Clipboard_2020-04-20-20-10-34.png, Clipboard_2020-04-20-20-13-04.png, Clipboard_2020-04-20-20-14-15.png, Clipboard_2020-04-20-20-27-30.png, Clipboard_2020-04-20-20-34-33.png, Clipboard_2020-04-20-20-35-34.png, Clipboard_2020-04-20-20-36-49.png, Clipboard_2020-04-20-20-37-26.png, Clipboard_2020-04-20-20-39-10.png, Clipboard_2020-04-20-20-45-59.png, Clipboard_2020-04-20-20-51-38.png, Clipboard_2020-04-20-20-54-08.png, Clipboard_2020-04-20-20-55-18.png, Clipboard_2020-04-20-21-03-53.png, Clipboard_2020-04-20-21-14-48.png, Clipboard_2020-04-20-21-15-35.png, Clipboard_2020-04-20-21-26-25.png, Clipboard_2020-04-20-21-29-44.png, Clipboard_2020-04-20-21-30-27.png, Clipboard_2020-04-20-21-31-22.png]
title: 'Module 10: Harder Practice Exercises'
created: '2020-04-20T11:16:46.618Z'
modified: '2020-04-21T01:31:51.764Z'
---

# Module 10: Harder Practice Exercises

## 55 - Face Detection and Censorship 

This exercise is going to be a bit more fun then our previous lessons. We are going to build a face detection that will detect and blur your face from a video element into a canvas element. This exercise is stepping a little bit ahead because there are a couple of things we need to learn a little bit more about, async/await, which is promises. We also need to learn about bundling tools, specifically one called Parcel. 

![](@attachment/Clipboard_2020-04-20-17-44-07.png) 00:22

The first thing we need to check is that we are on a browser that supports face detection. 

At the time of this recording, there is a proposal for an API, meaning it's not finished yet and might change. Ideally it will get into all of the browsers but currently it is only in Chrome and Android. The way you can tell if your browser supports it is you can go to the console on any page and type `FaceDetector`, or `typeof FaceDetector`. 

![](@attachment/Clipboard_2020-04-20-17-49-26.png) 1:40

If you get undefined or an error returned, that means your browser does not support it. If you are on Chrome, you likely have to go to the flags page in Chrome and turn it on. 

Often new features in the browser are not given to the masses because they are not ready yet. In order for us to play with them, we need to enable them. The way you turn flags on in chrome is you navgiate to `chrome://flags`.

![](@attachment/Clipboard_2020-04-20-17-51-12.png) 3:30

This page contains all kinds of features that are still experimental in Chrome. You want to search for "Experimental Web Platform features" and enable it. You will probably have to restart your browser, so go ahead quit it, and restart it, and then you should see `typeof FaceDetector` work. 

If you do all that and still cannot get `typeof FaceDetector` to return "function" it's possible that your computer does not support it. But from everyone Wes has steted with, it works well.

The second thing is we need to use a server in order to run this. That is because accessing a user's webcam is a security issue (you don't want to give everybody access to your web cam), you have to ask the user first for access to their webcam.  

You've probably been to a million websites where they ask for notifications or to know your location, things like that. Those are permission-based APIs in the browser, and accessing someone's webcam is no different than that. That sort of preference, is it allowed or not, is tied to the origin.

An origin in Javascript is just a fancy way of saying a domain name. So in Wes' case, he is currently allowing the camera on localhost, but you might allow the camera on New York Times or Facebook or all these different websites. 

![](@attachment/Clipboard_2020-04-20-20-10-34.png) 3:54

Everytime you visit a new origin, a new domain name, you're going to have to ask the user for access to their webcam and it will pop up. 
So in order for us to do that, we cannot just open up `face.html` (from the  `/53 - Face Detection Censorship` folder) in the browser like we have been doing up until now.

![](@attachment/Clipboard_2020-04-20-20-13-04.png) 4:27

The reason for that is the file path that you see in the url browser above is not an origin. If security stuff is tied to an origin, it won't be able to do it from a local file.

You might notice the X next to the camera. If you take a look, you will see that the camera is blocked.

![](@attachment/Clipboard_2020-04-20-20-14-15.png) 4:35

If you try to allow it by clicking "always allow", it still won't work. 

So you cannot open the HTML file directly in your browser, it must run through a server. So how do we run a server? 

One server that Wes likes is a bundler, called Parcel, which we will learn more about when we get to the modules section. 

Parcelo will give us a little development server where when we change something on the page, it will automatically refresh the page for us. If we change any of our CSS, it will automatically re-load the CSS on the page without actually having to do a full page refresh. 


To get that running, we neeed to open up a terminal. If you need a refresher, go back to video 2 where Wes goes over the different types of terminals. 

Once we have the terminal open, we need to get into the folder that contains our `face.html` file. 

To do that, you need to use the command `cd` to go into the correct directory.

If you don't know where you are starting in the terminal, you can type `pwd` and it will tell you where you are on your computer. 

![](@attachment/Clipboard_2020-04-20-20-27-30.png) 6:11

What is probably easier than that is if you are using VSCode, you can just right click the folder and select "Open in Terminal". 

![](@attachment/Clipboard_2020-04-20-20-34-33.png) 6:20

That opens the terminal up in the built in terminal in VSCode.

![](@attachment/Clipboard_2020-04-20-20-35-34.png) 6:23

In the second video, Wes had us install node and NPM, and you can check if you have both by typing `node -v` and `npm -v` in the terminal, which will tell you what versions you have installed.

![](@attachment/Clipboard_2020-04-20-20-36-49.png) 7:01

If you need to check what the latest node version is, you can go to `nodejs.org` and find the LTS version which stands for long term support -- that is the most stable version. 

![](@attachment/Clipboard_2020-04-20-20-37-26.png) 7:04

Once you have confirmed you have both of those and yo uare in the right directly, go ahead and type `npm install`.

Wes will cover this all more in the  future, but what that does is it will take all our dependencies and install them for us. In our case we are installing Parcel. 

![](@attachment/Clipboard_2020-04-20-20-39-10.png) 7:45

You should completely ignore the versions in this file, because that will likely change in the future and Wes will be keeping the files up to date. 

While we wait for that to finish installing, lets take a look at the `face.html` structure to see what we are working with. 


```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>Censorship</title>
  <link rel="stylesheet" href="../../base.css">
</head>

<body>
  <div class="wrap">
    <video class="webcam"></video>
    <canvas class="video"></canvas>
    <canvas class="face"></canvas>
  </div>
  <script src="./pixelated-face.js"></script>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
    }

    .wrap {
      position: relative;
      min-height: 100vh;
      display: grid;
      justify-content: center;
      align-items: center;
    }

    .wrap>* {
      grid-column: 1;
      grid-row: 1;
    }
    
    .face {
      position: absolute;
    }
  </style>
</body>
</html>
```

We have our base css which is just the blue background. Then we have our wrapper, which has a video element,  a canvas element, and then another canvas element. One canvas is for the video and one is for our face.

Then we are linking up the `pixelated-face.js`. (Note: Wes is using a different file than us so he can demonstrate how the finished result works). After that we have a few styles that just center things on the page, nothing too interesting. 

If we look at the terminal, the package should be done installing. 

![](@attachment/Clipboard_2020-04-20-20-45-59.png) 8:56

You may notice in the terminal something like "found 39 high severity vulnerabilities". That will pop up when you `npm install` things. What happens there is that some dependencies have security vulnerabilities that need to be fixed and what happens is the people who create Parcel will fix that eventually. So if you see that, don't freak out. It's totally fine, hopefully NPM will hopefully find a better way to deal with those warnings. 

We need to create a new file in our folder called `pixelated-face.js`. Inside of it add a `console.log("it works!");`.  

Next go back to the terminal and in the same directory type `npm start`. What that will do is it will run Parcel against our `face.html` file and it will run our server at some URL. 

![](@attachment/Clipboard_2020-04-20-20-51-38.png) 10:45

If you go to that URL in the browser and open the console, you should see "it works!". 

![](@attachment/Clipboard_2020-04-20-20-54-08.png) 11:03

Sometimes you will see weird warnings like the yellow one above, and that is related to a Chrome extension that you have installed, and that is annoying because it gets in the way of writing our actual code. 
That can be annoying because there is no way to get rid of them. One trick Wes has found it typing into the Filter `-DevTools` like so: 

![](@attachment/Clipboard_2020-04-20-20-55-18.png) 11:20

Now that we have everything up and running, lets dig into some code.

The first thing we want to do is select all the elements that are on our page. We have our video, our canvas, and then another canvas.

We are going to access the user's webcam, dump it into the canvas element with the class of video, and then we are going to take the frames of that video, put a square around the person's face and then in the canvas element with class of face, we will pixelate the persons page. The canvas element work could be done on one canvas, but Wes prefers to keep them separate in case he ever wants to only pull one of those images out.

Let's go ahead and grab those three classes (`webcam`, `video`, and `face`). Let's page them into our `pixelate-face.js` file. 

Note: in the video, at this section, Wes is able to paste all three classes like this on the page
```
webcam
video
face
```
In VSCode, he is able to press the shortcuts `CMD + A` and then `CMD + Shift + L`, and that gives him a cursor on every single line. 

![](@attachment/Clipboard_2020-04-20-21-03-53.png) 12:35

Add the following code:

```
const video = document.querySelector(".webcam");
const canvas = document.querySelector(".video");
const faceCanvas = document.querySelector(".face");
```

We need to pull the context out of each canvas element now. We talked about that in our Etch-a-Sketch exercise but that is where we do the drawing. 

Modify the code like so to add the following: 

```
const video = document.querySelector(".webcam");

const canvas = document.querySelector(".video");
const ctx = canvas.getContext("2d");

const faceCanvas = document.querySelector(".face");
const faceCtx = canvas.getContext("2d");
```

Now we need to make a new face detector, and then let's log everything we have so far. 

```js
const faceDetector = new FaceDetector();
console.log(video, canvas, faceCanvas, faceDetector);
```

![](@attachment/Clipboard_2020-04-20-21-14-48.png) 14:12

Note: you might notice in VSCode that it says "FaceDetector is not defined" if you hover over `new FaceDetector()`. 

![](@attachment/Clipboard_2020-04-20-21-15-35.png) 14:18

That is because it is looking for a function called `FaceDetector`. The way we can solve that is to say `const faceDetector = new window.FaceDetector()`. THat is fine to do (Wes told us not to do it in looping) here beause this FaceDetector API does not exist in NodeJS land.

The next thing we need to do is write a function that populates the user's video. 

To do that we need to grab the stream from the user's webcam. 

```
function populateVideo(){
  const stream = navigator.mediaDevices.getUserMedia();
}
```

We need to pass `getUserMedia()` some options, saying if you want video or audio (we just want video). You can just say `video:true` or you can ask for a specific size from it. 

Modify the code like so and get rid of the log we had added earlier.

```
function populateVideo() {
  const stream = navigator.mediaDevices.getUserMeda({
    video: { width: 1280, height: 720 },
  });
  console.log(stream);
}
```

If you refresh the HTML page and try to run `populateVideo()`, you will see an error like so:

![](@attachment/Clipboard_2020-04-20-21-26-25.png) 15:50

Now that we are running thing through a bundler, we no longer have the ability to access our functions globally via the console. 
If you ever do want to do that, you can do `window.populateVideo = populateVideo;`. That will surface it for you, but that is not a great way to do it. 

The best way to do it would just be to add a log in your javascript file and you can see it. If you do ever need to access it from the chrome dev tools, you can right click it, and click store as global variable.

![](@attachment/Clipboard_2020-04-20-21-29-44.png) 16:48

That will store it in a global variable called `temp1`. If you try calling `temp1()`, you will see something returned to us called a **promiose**. 

![](@attachment/Clipboard_2020-04-20-21-30-27.png) 16:57

There are a couple things going on here. First, it might show you a little recording icon on the chrome tab (it might not, we will go over that in a sec.). 

![](@attachment/Clipboard_2020-04-20-21-31-22.png) 17:03

stopped at 17:10


## 56 - Sarcastic Text Generator
