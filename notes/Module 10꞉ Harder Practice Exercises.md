---
attachments: [Clipboard_2020-04-20-17-44-07.png, Clipboard_2020-04-20-17-49-26.png, Clipboard_2020-04-20-17-51-12.png, Clipboard_2020-04-20-20-10-34.png, Clipboard_2020-04-20-20-13-04.png, Clipboard_2020-04-20-20-14-15.png, Clipboard_2020-04-20-20-27-30.png, Clipboard_2020-04-20-20-34-33.png, Clipboard_2020-04-20-20-35-34.png, Clipboard_2020-04-20-20-36-49.png, Clipboard_2020-04-20-20-37-26.png, Clipboard_2020-04-20-20-39-10.png, Clipboard_2020-04-20-20-45-59.png, Clipboard_2020-04-20-20-51-38.png, Clipboard_2020-04-20-20-54-08.png, Clipboard_2020-04-20-20-55-18.png, Clipboard_2020-04-20-21-03-53.png, Clipboard_2020-04-20-21-14-48.png, Clipboard_2020-04-20-21-15-35.png, Clipboard_2020-04-20-21-26-25.png, Clipboard_2020-04-20-21-29-44.png, Clipboard_2020-04-20-21-30-27.png, Clipboard_2020-04-20-21-31-22.png, Clipboard_2020-04-21-06-28-28.png, Clipboard_2020-04-21-06-28-56.png, Clipboard_2020-04-21-06-58-49.png, Clipboard_2020-04-21-07-19-00.png, Clipboard_2020-04-21-07-19-53.png, Clipboard_2020-04-21-07-20-57.png, Clipboard_2020-04-21-07-25-23.png, Clipboard_2020-04-21-07-28-44.png]
title: 'Module 10: Harder Practice Exercises'
created: '2020-04-20T11:16:46.618Z'
modified: '2020-04-21T11:29:06.901Z'
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
  const stream = navigator.mediaDevices.getUserMedia({
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

That will store it in a global variable called `temp1`. If you try calling `temp1()`, you will see something returned to us called a **promise**.  

![](@attachment/Clipboard_2020-04-20-21-30-27.png) 16:57

There are a couple things going on here. First, it might show you a little recording icon on the chrome tab (it might not, we will go over that in a sec.). 

![](@attachment/Clipboard_2020-04-20-21-31-22.png) 17:03

As mentioned, we are returned a promise when we call `temp1()` in the console (which is our `populateVideo()` function stored as a global variabe). 

What that means is we have not been returned the actual stream of video, instead it's just something called a promise that it will get the stream of the webcam eventually. 

We will get more into promises in future videos, but for now just know that `navigator.mediaDevices.getUserMedia()` is a special kind of function that returns this thing called a promise.

In order for us to wait for the stream to come back from the webcam, because that takes some time, we need to first mark the function a `async` by typing the word `async` in front of it, and add the keyword `await` before we call `navigator.mediaDevices.getUserMedia()`. 

We will also add a call to `populateVideo()` where we used to log it.


```
async function populateVideo() {
  const stream = await navigator.mediaDevices.getUserMedia({
    video: { width: 1280, height: 720 },
  });
  console.log(stream);
}
populateVideo();
```

If you refresh the page and look at the console, you may see the following:

![](@attachment/Clipboard_2020-04-21-06-28-28.png) 18:09

If you do not, you may see a little red X on your video camera icon in the browser tab. 

To fix that, you need to click on it and select "continue" or "always allow access". Click done, then reload the page, and then you should see a media stream in the console.

![](@attachment/Clipboard_2020-04-21-06-28-56.png) 18:18

How is what is returned to us via the `MediaStream` useful?

We can now put the stream into our video which we have already selected. You would normally pass the video something like `video.srcObject = "dog.mp4";` but we will be passing the video the stream instead and then calling `play()` on it. We will put an `await` infront of where we call `video.play()` because sometimes it takes a few seconds to start playing and that will wait for it.

```
video.srcObject = stream;
await video.play();
```

If you refresh the page, you should see it worked. 

So what did we do there? We made a function called `popuateVideo()`, we grabbed the feed off the user's webcam, and then we set the object to be the stream, and then played it. 

Another thing we need to do is size the canvases to be the same size as the video.

If we were to add a `console.log(video.videoWidth, video.videoHeight);` we should get 1280 x 720. 

If we change one line of code from `navigator.mediaDevices.getUserMedia({video: { width: 1280, height: 720 }});` to `navigator.mediaDevices.getUserMedia({video: true});`, and refreshed the page, we should see the sixes 640 x 480. Let's switch that back.

Note: these sizes might not be the same on your computer, depending on your webcam. 

So we need to size the canvases to match the video, which we can do like so:

```
canvas.width = video.videoWidth;
canvas.height = video.videoHeight;

faceCanavs.width = video.videoWidth;
faceCanvas.height = video.videoHeight;
```

Now we have two canvases that are the same size as the video feed.

The next thing we need to do is work with the FaceDetection API. We will call it `detect` and it also needs the `async` keyword in front of it (we will cover why in future video). 

Now we want to go ahead and detect faces that are in the shot.

Next we will use the `faceDetector` variable we created earlier and call `.detect()` on it. You pass `detect()` reference to three things:
- an image
- a video
- or a canvas

In our case we are going to pass it access to the video. 

```
async function detect(){
  const faces = await faceDetector.detect(video);
  console.log(faces);
}
```

Now, we need to run our `detect()` function once, but after the video has been populated. If you run `detect()` when there is no video, it will not find any faces.

The way we can do that is by tagging a `.then()` onto `populateVideo` like so:

```
populateVideo().then(detect);
```

This is promise based, which we will cover in more detail in future videos. 

If you refresh the page and open the console now, you should see a face detected. IT will tell you exactly where the eyes, the nose, and the mouth are. 

![](@attachment/Clipboard_2020-04-21-06-58-49.png) 23:24

It also gives us the `boundingBox` which is the square around the user's head.

The way we are calling `detect()` right now, it will only run once after `populateVideo()` is done playing.

So what we need to do is call `detect()` over aned over again. You might be thinking we can use an interval for this. That is the way we used to do this stuff, but there is a better way, that allows you to do stuff as fast as possible, is to use something called **request animation frame**.

Request animation frame allows the browser to tell us when we should repaint or redo something. Instead of us trying to do something every 60 miliseconds, because some people's computers vary in speed, request animation frame will repaint or rerun the stuff on the screen a lot less frequently on a computer that isn't as fast. 

So what we will do is ask the browser when the next animation frame is, and then tell it to run detect for us. 

```
async function detect() {
  const faces = await faceDetector.detect();
  console.log(faces);
  // ask the browser when the next animation frame is and tell it to run detect for us
  requestAnimationFrame(detect);
}

populateVideo().then(detect);
```

If you refresh the page, you should see lots of DetectedFaces logged in the console. 

Let's look at what is happening there..

Instead of calling `requestAnimationFrame(detect)`, we could have just called `detect()` and that works pretty well, but because of performance reasons, it's better to call `requestAnimationFrame()`.

What we have just done there is a concept called **recursion**. Recursion is when a function calls itself. It will run forever, and ever, until something stops it, such as an exit condition.

Recursion is when a function calls itself, inside of itself. Detect is being called from `detect` which allows us to run it infinitely.

Let's take a look at the DetectedFace. 

![](@attachment/Clipboard_2020-04-21-07-19-00.png) 26:24

As you can see, it gives us an array with one item. So let's `console.log(faces.length);`.

![](@attachment/Clipboard_2020-04-21-07-19-53.png) 26:44

As you can see, it only logs one face until Wes holds up the queens face on a dollar bill. 

![](@attachment/Clipboard_2020-04-21-07-20-57.png) 27:35

When Wes holds up a picture, FaceDetection detects all four faces.

Next up, we need to do two things:
- we need to draw triangles around the faces that are found
- we need to censor the face by pixelating the area that is around their face.

We will make a function called `drawFace` which will take in the user's face. We need a couple of pieces of information. 

We need to know how wide and high is the user's face, because the further away the subjects are from the camera will affect that. 

We also need the X and Y coordinate from the top. For example over 400 pixels and down 300 pixels is where the head starts.

Let's start by just logging the faces and calling `drawFace()`.  We will loop over all the faces in a `.forEach` and call `drawFace` for each. 

```
async function detect() {
  const faces = await faceDetector.detect();
  console.log(faces);
  // ask the browser when the next animation frame is and tell it to run detect for us
  faces.forEach(drawFace);
  requestAnimationFrame(detect);
}

function drawFace(face) {
  console.log(face);
}

populateVideo().then(detect);
```

When you refresh the page and look at the console, you should see many faces logged. 


Let's get the bounding box from one of those. We need the `top` and `left`, `width`, and the `height`. 

![](@attachment/Clipboard_2020-04-21-07-25-23.png) 29:17


```
function drawFace(face) {
  const { width, height, top, left } = face.boundingBox;
  console.log(width, height, top, left);
}
```

If you refresh the page, you should see lots of logs like the following: 

![](@attachment/Clipboard_2020-04-21-07-28-44.png)

stopped at 30:05

## 56 - Sarcastic Text Generator
