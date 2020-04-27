---
attachments: [Clipboard_2020-04-20-17-44-07.png, Clipboard_2020-04-20-17-49-26.png, Clipboard_2020-04-20-17-51-12.png, Clipboard_2020-04-20-20-10-34.png, Clipboard_2020-04-20-20-13-04.png, Clipboard_2020-04-20-20-14-15.png, Clipboard_2020-04-20-20-27-30.png, Clipboard_2020-04-20-20-34-33.png, Clipboard_2020-04-20-20-35-34.png, Clipboard_2020-04-20-20-36-49.png, Clipboard_2020-04-20-20-37-26.png, Clipboard_2020-04-20-20-39-10.png, Clipboard_2020-04-20-20-45-59.png, Clipboard_2020-04-20-20-51-38.png, Clipboard_2020-04-20-20-54-08.png, Clipboard_2020-04-20-20-55-18.png, Clipboard_2020-04-20-21-03-53.png, Clipboard_2020-04-20-21-14-48.png, Clipboard_2020-04-20-21-15-35.png, Clipboard_2020-04-20-21-26-25.png, Clipboard_2020-04-20-21-29-44.png, Clipboard_2020-04-20-21-30-27.png, Clipboard_2020-04-20-21-31-22.png, Clipboard_2020-04-21-06-28-28.png, Clipboard_2020-04-21-06-28-56.png, Clipboard_2020-04-21-06-58-49.png, Clipboard_2020-04-21-07-19-00.png, Clipboard_2020-04-21-07-19-53.png, Clipboard_2020-04-21-07-20-57.png, Clipboard_2020-04-21-07-25-23.png, Clipboard_2020-04-21-07-28-44.png, Clipboard_2020-04-21-07-45-14.png, Clipboard_2020-04-21-07-45-43.png, Clipboard_2020-04-21-07-49-15.png, Clipboard_2020-04-21-07-52-21.png, Clipboard_2020-04-21-08-01-54.png, Clipboard_2020-04-21-18-00-57.png, Clipboard_2020-04-21-18-11-21.png, Clipboard_2020-04-21-18-44-26.png, Clipboard_2020-04-21-19-04-01.png, Clipboard_2020-04-21-19-06-41.png, Clipboard_2020-04-21-19-07-31.png, Clipboard_2020-04-21-19-10-48.png, Clipboard_2020-04-21-19-14-30.png, Clipboard_2020-04-21-19-17-06.png, Clipboard_2020-04-21-19-17-53.png, Clipboard_2020-04-21-19-18-32.png, Clipboard_2020-04-21-19-26-08.png, Clipboard_2020-04-21-19-27-29.png, Clipboard_2020-04-21-19-38-17.png, Clipboard_2020-04-21-19-46-53.png, Clipboard_2020-04-22-06-37-18.png, Clipboard_2020-04-22-06-38-44.png, Clipboard_2020-04-22-06-39-50.png, Clipboard_2020-04-22-06-55-58.png, Clipboard_2020-04-22-07-14-34.png, Clipboard_2020-04-22-07-21-16.png, Clipboard_2020-04-22-07-22-44.png, Clipboard_2020-04-22-07-24-48.png, Clipboard_2020-04-22-07-26-09.png, Clipboard_2020-04-22-07-27-16.png, Clipboard_2020-04-22-07-37-32.png, Clipboard_2020-04-22-07-38-43.png, Clipboard_2020-04-22-07-42-12.png, Clipboard_2020-04-22-07-42-55.png, Clipboard_2020-04-22-07-44-12.png, Clipboard_2020-04-22-07-45-16.png, Clipboard_2020-04-22-17-20-49.png, Clipboard_2020-04-22-17-21-57.png, Clipboard_2020-04-22-17-27-58.png, Clipboard_2020-04-22-17-32-28.png, Clipboard_2020-04-22-17-33-36.png, Clipboard_2020-04-22-17-33-53.png, Clipboard_2020-04-22-17-41-21.png, Clipboard_2020-04-22-17-45-30.png, Clipboard_2020-04-23-08-31-55.png, Clipboard_2020-04-23-08-37-40.png, Clipboard_2020-04-23-08-42-16.png, Clipboard_2020-04-23-08-42-37.png, Clipboard_2020-04-27-11-00-37.png, Clipboard_2020-04-27-11-04-47.png, Clipboard_2020-04-27-11-06-05.png, Clipboard_2020-04-27-11-16-04.png, Clipboard_2020-04-27-11-21-34.png, Clipboard_2020-04-27-11-25-30.png, Clipboard_2020-04-27-11-26-43.png, Clipboard_2020-04-27-11-35-40.png, Clipboard_2020-04-27-11-37-15.png, Clipboard_2020-04-27-11-39-20.png, Clipboard_2020-04-27-11-40-58.png, Clipboard_2020-04-27-11-42-16.png, Clipboard_2020-04-27-11-43-52.png]
title: 'Module 10: Harder Practice Exercises'
created: '2020-04-20T11:16:46.618Z'
modified: '2020-04-27T15:47:48.404Z'
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
  const faces = await faceDetector.detect(video);
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
  const faces = await faceDetector.detect(video);
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

One trick you can do is if within our log, we just wrap the items in curly brackets like this, it will actually show us the property names and values.

```
console.log({width, height, top, left});
```

The reason that works is because you are essentially making an object.

![](@attachment/Clipboard_2020-04-21-07-45-14.png) 30:34

Now we want to draw a box onto our canvas element that is down in the part of the page that is highlighted in the image below.

![](@attachment/Clipboard_2020-04-21-07-45-43.png) 30:47

We are going to overlay it with the video in order to do that. 

Let's set a couple of defaults at the top of the page. 

```
const ctx = canvas.getContext("2d");
ctx.strokeStyle = "#ffc600";
ctx.lineWidth = 2;
```

Now let's go into our `drawFace` function and we will call `ctx.strokeRect()`, which is the API for drawing a rectangle. 

```
function drawFace(face) {
  const { width, height, top, left } = face.boundingBox;
  ctx.strokeRect(left, top, width, height);
}
```

![](@attachment/Clipboard_2020-04-21-07-49-15.png) 31:45

As you can see, it does work. if you move your face around, the boxes should move around as well. 

We need to fix a few things though. One of those things is that our rectangles are not overlaid on top. 

Note: if the rectanges are overlaid for you, you  can ignore these instructions.

Let's take a look at our `face.html`. It seems like it's ignoring our style tag. Let's try moving our styles to the head. 

```html
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

    .wrap > * {
      grid-column: 1;
      grid-row: 1;
    }

    .face {
      position: absolute;
    }
  </style>
</head>

<body>
```

If you refresh the page now, it should work. This likely happened because we are using a beta version of Parcel.

![](@attachment/Clipboard_2020-04-21-07-52-21.png) 32:29 

The next thing to fix is that the stroke that the rectangle is created in is not yellow. Let's try moving where we set the strokeStyle and the lineWidth into the function right before we draw the rectangle like so:

```
function drawFace(face) {
  const { width, height, top, left } = face.boundingBox;
  ctx.strokeStyle = "#ffc600";
  ctx.lineWidth = 2;
  ctx.strokeRect(left, top, width, height);
}
```

The next thing to fix is that they are not clearing. We can fix that by calling `ctx.clearRect` before we draw the rect. 

```
ctx.clearRect(0,0, canvas.width, canvas.height)
```

That clears the amount, the width and the height, based on starting at the top left hand corner, everytime it runs, it clears the canvas for us.

It is working pretty well. It is a bit jumpy right now, it used to be a lot better, they're still working on it. The eyes, nose, and mouth values were working very well for Wes for a while, but currently they're really weird.

The next thing we want to do is pixelate the user's face on top of it. Lets go ahead and do that. 

We will create a function called `censor` which will take in a `face`. In our case, we don't care about anything but the bounding box.  SO instead of doing something like this:


```
function censor(face){
  const faceDetails = face.boundingBox;
}
```

we are going to destructure the bounding box properties directly like so:

```
function censor({boundingBox}){
}
```

Now we just have a variable called `boundingBox`. We could also rename it to a variable called face like so:

```
function censor({boundingBox: face}){
 console.log(face);
}
```

![](@attachment/Clipboard_2020-04-21-08-01-54.png) 35:28

As you can see, we are getting that bounding box. 

Now the question is how do you censor something, right? There are a couple of different ways you can do it. 

The best way Wes has found is to take a snapshot of the user's face, scale it down very very small, and then paint it to the canvas. And then immediately after that, pull it off the canvas, stretch it back up and put it back in. 

So essentially you make it really small and then save it and lose all the pixel quality, and them you take it out, stretch it back up again, and thats how you get the pixelation look. 

Lets first write out comments for what we plan to do. 

```
function censor({boundingBox:face}){
  //draw the small face
  // take that face back out and draw it back normal size
}
```

Now the way we are going to do this is we are going to take our second canvas context, `faceCtx` and call `drawImage()` on it. `drawImage` takes in a lot of arguments, let's look it up on MDN.

![](@attachment/Clipboard_2020-04-21-18-00-57.png) 37:01

So it takes a few set of options. You can either pass in 3 (`image`, `dx`, `dy`), 5(`image`, `dx`, `dy`, `dWidth`, `dHeight`), or it takes 9 (`image`, `sx`, `sy`, `sWidth`, `sHeight`, `dx`, `dy`, `dWidth`, `dHeight`). We will be using all 9, and Wes will do his best to explain what each parameter is.

Let's get started.  The first argument `drawImage` takes is the image you want to draw to it, so we will pass in our `video`, `faceCtx.drawImage(video);`

Then it wants the `x` and the `y` coordinates of where it should start drawing the image so we will pass `0,0`, like so `faceCtx.drawImage(video, 0, 0);`.  Save the file. 

If you just look at the HTML page, it might look like nothing has changed but if you inspect it, you will see that what we are actually seeing is the canvas, not the video. 
If we add a `display:none` css style to the video, you will notice that you can still see yourself. The video is being painted onto the canvas.

![](@attachment/Clipboard_2020-04-21-18-11-21.png) 37:48

Now this isn't exactly what we want to do. We want to take the square that is painting on Wes' face and throw it on there.  Comment out the `faceCtx.drawImage()` line of code for a second to make sure we have the square painting. If you do, that is good.  

Now lets go through every single argument, one by one. 

There are 9 arguments to the function.

5 are source args, which means they are about how we pull data out of this video, and then 4 arguments about how we want to paint it into. We only want the inside of the square to be painted onto it.

The first argument is where does the source come from, which in this case is our video tag. 

The next two are `face.x` and `face.y`, which are where do we start the source pull from? We are trying to pull the square out so we want to start at the top left corner of the square. 

If we have where we start from, we need to know how wide and how high it needs to go, so we pass `face.width` and `face.height`. That is all the pulling out arguments. 


```js
function censor({boundingBox:face}){
  //draw the small face
  faceCtx.drawImage(
    //5 source args
    video, //where does the source come from?
    face.x, //where do we start the source pull from?
    face.y, 
    face.width,
    face.height,
    //4 draw args
  )
}
```

Now the next four arguments are related to drawing it into the face canvas that we have. Now we have to ask "where do we start drawing it at?" The answer is `face.x` and `face.y`. 

The next arguments are how wide and how high should I paint it to? You might think, okay we can just use `face.width` and `face.height`.  However if you try that, you will see a really weird effect where your face is almost delayed. 

What is actually happening there is that its just painting Wes' face to the square, and then everything you see outside of the square is the video element, and then everything inside the square is the canvas. There is a bit of a delay there. 

So the way it will work is we are going to take 10 pixels by 10 pixels and then peel it back up once we have done it. So instead of passing `face.width` and `face.height`, we will pass `10,10`. 

```
//4 draw args
face.x, //where should we start drawing the x and y?
face.y,
10,
10 
```

![](@attachment/Clipboard_2020-04-21-18-44-26.png) 40:29

You can see in the very top corner there is a tiny little Wes. 
Let's make a variable called size instead of hardcoding the values 10,10, so we can quickly reference that whenever we need it.  

Add the following towards the top of the file: `const SIZE = 10;`. Why did we do it in all caps? it's a commomn practice in the graphics canvas world, any variables that are constant throughout the application, they do them in all caps. 
 
```js
faceCtx.drawImage(
  // 5 source args
  video, // where does the source come from?
  face.x, // where do we start the source pull from?
  face.y,
  face.width,
  face.height,
  // 4 draw args
  face.x, // where should we start drawing the x and y?
  face.y,
  SIZE,
  SIZE
);
```

Now we need to draw the small image back on but scaled up. Remember -- the whole reason we draw it small was so we can pull it back out, strech it back up, and then paint it overtop. Saving it small lets us get that pixelated look that we are going for here. 

To do that we will use `drawImage`. 

The source is the faceCanvas itself, and we want to start from the top left corner so we pass `face.x` and `face.y`. 

For how wide and how high we want to go, it's no longer the width of the face, it's the width of the tiny one, so we can pass `SIZE` for both width and height.


Next we have our drawing args. Where should we start drawing the x and the y? `face.x` and `face.y`. And then for how wide and high should we do it, we want `face.width` and `face.height`.

```js
// draw the small face back on, but scaled up
faceCtx.drawImage(
  faceCanvas, // source
  face.x, // where do we start the source pull from?
  face.y,
  SIZE,
  SIZE,
  //drawing args
  face.x,
  face.y,
  face.width,
  face.height
);
```

If you refresh the page, you might notice it's not working. 

Wes spent 20 minutes debugging this to figure out why is it not painting my face once it is scaled up? Wes' debugging mindset went through and said it looks like it's not actually drawing anything there because if you comment that entire small face drawImage, it works the exact same. 

If you give it a separate src, like the `video` to pull from instead of `faceCanvas`, you will see it works. 


```js
// draw the small face back on, but scaled up
faceCtx.drawImage(
  video, // source
  face.x, // where do we start the source pull from?
  face.y,
  SIZE,
  SIZE,
  //drawing args
  face.x,
  face.y,
  face.width,
  face.height
);
```

So why is it not painting to the `faceCanvas`? Wes switched the source back and then went to the element and set `display:none` on the canvas element with class of `face`, and nothing changed. 

So that's when Wes thought maybe we are drawing to the wrong canvas. But then he thought we have two canvases. 
The first canvas is the regular canvas with `ctx`. The second canvas is the canvas with the `faceCtx`.  So what is wrong with the variables?!

It was right here... 

```js
const faceCanvas = document.querySelector(".face");
const faceCtx = canvas.getContext("2d");
```

We grabbed the `faceCanvas` element correctly, but then we assigned `faceCtx` the wrong canvas! We used `canvas` instead of `faceCanvas`.

```
const canvas = document.querySelector(".video");
const ctx = canvas.getContext("2d");
const faceCanvas = document.querySelector(".face");
const faceCtx = canvas.getContext("2d");
```

Modify that code to: 

```
const canvas = document.querySelector(".video");
const ctx = canvas.getContext("2d");
const faceCanvas = document.querySelector(".face");
const faceCtx = faceCanvas.getContext("2d");
```

![](@attachment/Clipboard_2020-04-21-19-04-01.png) 44:27

Now it is finally working! It is taking our faces and spreading it all over. There are few things we can do to fix some of that stuff. 

Let's go into our `censor` function.  In the first line of the function add `faceCtx.imageSmoothingEnabled = false`.  If you don't have that, the image is just kind of blury so what the browser does is it says "oh this is pixelated!, let me try to smooth it out".  But if you turn that off, you get the real pixelated values. 

![](@attachment/Clipboard_2020-04-21-19-06-41.png) 45:04
![](@attachment/Clipboard_2020-04-21-19-07-31.png)

We also want to clear the canvas before we do any of this so underneath that smoothing line, add `faceCtx.clearRect(0, 0, faceCanvas.width, faceCanvas.height)`.

Now the canvas should clear when we move. 

One other thing is it doesn't do a great job at getting Wes' whole face. So what Wes will do is go to the top of the file and create a scale variable like so `const SCALE = 1.5;`

![](@attachment/Clipboard_2020-04-21-19-10-48.png) 45:33

Now let's go to our second draw and make a few variables that are scaled up. 

First we will make a width and height:

```
const width = face.width * SCALE;
const height = face.height * SCALE;
```

Then we will go down to our `drawImage` function and replace the last two values with our `width` and `height` variables like so: 


```
// draw the small face back on, but scaled up
const width = face.width * SCALE;
const height = face.height * SCALE;

faceCtx.drawImage(
  faceCanvas, // source
  face.x, // where do we start the source pull from?
  face.y,
  SIZE,
  SIZE,
  // drawing args
  face.x,
  face.y,
  width,
  height
);
```

![](@attachment/Clipboard_2020-04-21-19-14-30.png) 46:18

That makes a bigger scaled up face. Now we need to move the canvas over a bit based on the scale. For that we need a bit of math. 

We will take our drawing args from `faceCtx.drawImage()` and do 

```
// Drawing args
face.x - (width - face.width) / 2,
face.y - (height - face.height) / 2,
```

![](@attachment/Clipboard_2020-04-21-19-17-06.png) 46:51

Now you can play around with the size and scale variables. If you change the size to `const SIZE = 100;`, you will see something like 

![](@attachment/Clipboard_2020-04-21-19-17-53.png) 47:11
![](@attachment/Clipboard_2020-04-21-19-18-32.png)

You can feel free to stop the video here, but if you want to continue, we will create some sliders that will change these `SIZE` and `SCALE`  values. 

Let's make an options variable that is an object with properties of `SIZE` and `SCALE` like so:

```
const options = {
  SIZE: 10,
  SCALE: 1.35
}
```

Then everywhere in the code we are calling those variables, modify the code so instead of passing just `SIZE` we pass `options.SIZE`.

For example

```js
// draw the small face back on, but scaled up
const width = face.width * options.SCALE;
const height = face.height * options.SCALE;
```

Now let's go back to the `face.html` and make some controls. 

Let's give ourselves an input of type "range", with a minimnum value of 0.3 and a max of 3 and the step will be 0.1. Then we need to add a label. 

```html
<div class="controls">
  <label for="SCALE">
    SCALE:
    <input type="range" name="SCALE" min="0.3" max="3" step="0.1" />
  </label>
</div> 
```

![](@attachment/Clipboard_2020-04-21-19-26-08.png) 50:05

Let's make the defaults line up with what we set.  Let's add `value="1.35"` to the input range. 

![](@attachment/Clipboard_2020-04-21-19-27-29.png) 50:18

As you can see now the default value is set on the scale slider. 

Duplicate that code and let's do the same for size. Size will start at 10 and go from 1 all the way to 100, and the step will go up by 1. 

```
<label for="SIZE">
  SIZE:
  <input type="range" name="SIZE" min="1" max="100" step="1" value="10" />
</label>
```

Now we need to add some event listeners. We need to select the inputs first. We will select every input within the `controls` class with a type of "range": 

```
const optionsInputs = document.querySelector('.controls inputs[type="range"]);
console.log(optionsInputs);
```

If you refresh the page and inspect the console, there is nothing! We did make a mistake, we should have used `querySelectorAll` so modify that code but it still doesn't give us anything. 

![](@attachment/Clipboard_2020-04-21-19-38-17.png) 51:46

Oh we have a typo! It should be `.controls input[type="range"]` not inputs plural. Modify the code accordingly. 

Now we can make an event listener for each of those. we will add the event listener on the `input` so it will run whenever the input changes and then we will call `handleOption`. 

```
optionsInputs.forEach(input => input.addEventListener('input',  handleOption));
```

Above that let's add the `handleOption` function.

```
function handleOption(event){
  console.log(event.currentTarget.value);
}
```

Now when you move the slider, you should see the values changing in the console. 

Now what we need to do is pull out the value and the name of the input. Add `console.log(event.currentTarget.name);` as well. 

![](@attachment/Clipboard_2020-04-21-19-46-53.png) 53:07

Let's destructure those `value` and `name` variables. 

```js
function handleOption(event){
  const { value, name } = event.currentTarget;
  options[name] = value;
}
```

Now inputs always come in as strings so we need to conver that back to numbers like so:

```
options[name] = parseFloat(value);
```

 Now you can play with the inputs and scale and resize up and down!

 That was a long video, but hopefully it was fun for you. 

---

## 56 - Sarcastic Text Generator

This is a quick and fun exercise. You can try this yourself to see how you would structure it.

What we will be doing is building a sarcastic text generator where you can enter some text and then select one of three options: sarcastic, funky, or unablet o structure a sentence. Based on your selection, the text you entered will be modified to match the style option you selected.

The sarcastic option gives us sponge bob case as it's often called, which is depicted in the image below. 

![](@attachment/Clipboard_2020-04-22-06-38-44.png) 00:34

![](@attachment/Clipboard_2020-04-22-06-37-18.png) 00:26

![](@attachment/Clipboard_2020-04-22-06-39-50.png) 00:45

Note: the funky option gives us those weird characters but you should never use these charactres in a real world situation because they are inaccessible to someone with a screen reader.

We will be working out of the `56 - Sarcastic Text` folder. Open up `index.html`. 

The page already contains some base styles so we can center it on the page, then we have a div with a bunch of inputs.

```html
<body>

  <div class="typer">
    <label for="sarcastic">
      <input type="radio" value="sarcastic" id="sarcastic" name="filter" checked>
      Sarcastic
    </label>
    <label for="funky">
      <input type="radio" value="funky" id="funky" name="filter">
      Funky
    </label>
    <label for="unable">
      <input type="radio" value="unable" id="unable" name="filter">
      Unable to Structure a Sentence
    </label>
    <textarea name="text">so I was thinking about going to the store.</textarea>
    <p class="result"></p>
  </div>

  <script src="./text.js"></script>
</body>
```

The only thing we need to know about the inputs is they all have the same `name` attribuet value. That allows us to only select one of the radio buttons at a time. We are going to be using their values (sarcastic, funky, or unable) to pull the specific filters. 

First thing we want to to do is select a few things. We need the text area that the person will input heir text into, the paragraph where we display the result and then all the inputs.

Let's grab the text area. Let's use an attribute selector to specify the textarea in case in the future we add more than one to the page.

```
const textarea = document.querySelector('[name="text"]');
```

Then we need the result.

```
const result = document.querySelector('.result');
```

Then we need the inputs. We will use `querySelectorAll` for these. We will select all the inputs with a name of "filter" on them. 

```
const filterInputs = document.querySelectorAll('[name="filter"]');
```

Let's log them all the make sure they are working.

![](@attachment/Clipboard_2020-04-22-06-55-58.png) 2:50

Next we need a handler that will output the text. We will make a new function called `transformText`. It will take in some text and then output the result.

We will add an event listener on the input event and call `transformText` everytime the event fires. 

To get the text out of the text area to pass to our function we can use `e.target.value`. 

```
function transformText(text){
  result.textContent = 'Transformed Text';
}
textarea.addEventListener('input', e => transformText(e.target.value));
```

Let's check that it is working by simply logging the text within the transformText function. When you refresh the html page, open the console and type into the text area, you should see the text you are typing being logged. 

Now we need to write some filters. We have three filters, and we will start by writing the sarcastic filter. 

One thing Wes likes to do when we have a few related things like these filters is to stick them in an object instead of having them all as their own function.

Let's call the object `filters` and each property will be the filter name like so:

```js
const filters = {
  sarcastic: function(){

  },
  funky: function(){

  },
  unable: function(){

  },
}
```

You will notice when you save the file that it refactors the object to this, which is just a shortcut. It's not the same thing as an arrow function, it's just a shorter way to write functions in objects. 

```
const filters = {
  sarcastic() {},
  funky() {},
  unable() {},
};
```

So what we need to do is take the text and loop over every letter, because for "sarcastic text", every other letter is a different case. 

```
const transformText(text){
  //take the text, and loop over each letter
  const mod = Array.from(text);
  console.log(mod);
  result.textContent = text;
}
```

Now everytime you type, we should get an array of every single letter that the person has in there. 

![](@attachment/Clipboard_2020-04-22-07-14-34.png) 5:54

Now we want to loop over that array and every other one we want to uppercase and every other one we want to lowercase. We can use `map` for that, and we will pass `map` our `filtres.sarcastic` function. 

Since this is just a map function, our sarcastic method on the filters can take in all the arguments that a regular map can do. Let's use the parameters `letter` and` index` and log those to make sure it's working correctly like so: 

```


const filters = {
  sarcastic(letter, index) {
    console.log(letter, index);
    return letter;
  },
  funky() {},
  unable() {},
};

function transformText(text) {
  // take the text, and loop over each letter
  const mod = Array.from(text).map(filters.sarcastic);
  console.log(mod);
  result.textContent = text;
}

textarea.addEventListener("input", (e) => transformText(e.target.value));
```

![](@attachment/Clipboard_2020-04-22-07-21-16.png) 6:54

Now when you type, as you can see, we are logging the letter and the index. What we can do is say if it's an even number, let's lowercase it, and if it's an odd number, uppercase it. 

How do you know if a number is even or odd? There is a neat way of doing that with the **modulo** operator.  Let's do a little aside to go over how the modulo operator works. 

![](@attachment/Clipboard_2020-04-22-07-22-44.png) 7:41

Let's say Wes he has a pack of 10 smarties (which are a candy in Canada) and three kids. 

If we try to divide 10 by 3 we get `10 / 3 = 3.33333333335`. Well you can't really split a smartie into thirds. You might think we can use `Math.floor(10/3)` which does return 3. 

![](@attachment/Clipboard_2020-04-22-07-24-48.png) 8:21

So each kid gets 3 smarties. If we have a pack of 10, each kid gets three, if we had a pack of 20, each kid will get six. Now the question is, how many are leftover that Wes gets? 

You could try to figure it out using math but it's not the best way. 
[](@attachment/Clipboard_2020-04-22-07-26-09.png) 8:50

What you can do is you can use the modulo operator. Let's say you have 10 smarties, and three kids. The modulo operator will tell us after they are evenly divided, how many are left? 

`10 % 3` = 1.

![](@attachment/Clipboard_2020-04-22-07-27-16.png) 9:17

So if we have 10 smarties that we divide by 3, there will be one leftover. 
If we have 6 smarties, there will be none leftover.

The modulo operator is great for knowing how much is left after you have evenly divided. 

We can use this operator to check if something is even or not. `10 % 2` will be 0, because 10 is event. If you do `11 % 2` you will get 1 returned. So anytime that 1 is returned with the modulo operator you know it's odd and if 0 is returned, then it's even. 

We can use this to upper/lowercase every other letter in our sarcastic filter. 

```
const filters = {
  sarcastic(letter, index) {
    // if it is od, it will return 1 which is truthy.
    if (index % 2) {
      return letter.toUpperCase();
    }
    // if it is even, it will return 0 and we will lowercase it.
    return letter.toLowerCase();
  },
```

If you refresh the page and start typing, you will see that every other leter is uppercased. 

![](@attachment/Clipboard_2020-04-22-07-37-32.png) 12:02

What we can do is set the result to be `mod.join(' ')`. 

```
function transformText(text) {
  // take the text, and loop over each letter
  const mod = Array.from(text).map(filters.sarcastic);
  console.log(mod);
  result.textContent = mod.join("");
}
```

Now if you type in the textarea and select the sarcastic filter, you should see something like this:

![](@attachment/Clipboard_2020-04-22-07-38-43.png) 12:15

So that is our first filter, and we are just hardcoding it in our transformText function right now. But it would be great if we can use it based on the radio selection that we have.

How could we  do that? 

The first like of our `tranformText` could be grabbing the filter. We want to find the input with name of filter that is also checked, and we want to grab it's value. 

```
const filter = document.querySelector('[name="filter"]:checked').value;
console.log(filter);
```

![](@attachment/Clipboard_2020-04-22-07-42-12.png) 13:04

Now when we type in it, we get the selected filter type logged in the console. 

![](@attachment/Clipboard_2020-04-22-07-42-55.png) 13:19

Another way we could have done the filter is because we already have the inputs, we could use the find method to find the input that is checked like so:

`filterInputs.find(input => input.checked)`

![](@attachment/Clipboard_2020-04-22-07-44-12.png) 13:49

If you try that, you should notice an error in the console that says
>filterInputs.find is not a function. 

That is because `filterInputs` is a nodelist, not an array. We could wrap it in Array.from and then call find like so:

```
Array.from(filterInputs).find(input => input.checked);
```

![](@attachment/Clipboard_2020-04-22-07-45-16.png) 14:05

This is actually a better approach because why rerun the query selector if we have already selected all of the inputs. Let's change the code to use that instead. 

```
function transformText(text) {
  const filter = Array.from(filterInputs).find((input) => input.checked).value;
```

With the way the code is written now, we will be transforming our filterInputs into an array every time the person types. That is not ideal. Let's instead turn it into an array once on pageload because it is unnecessary to have to keep doing that. 

Modify the code like so:
```
const filterInputs = Array.from(document.querySelectorAll('[name="filter"]'));
```

Let's do some cleanup and get rid of the console logs within our `transformText` function. 

Now what we can do is take the filter variable and use it as a property lookup instead of hardcoding the value.

Replace this line of code:  `const mod = Array.from(text).map(filters.sarcastic);`
With this: `const mod = Array.from(text).map(filters[filter]);`

Because filter is stored in a variable, we need to use square brackets to look up the property. 

If you refresh the page, the sarcastic option should still work but nothing should happen when you select the other two options because we haven't hooked them up yet.

Let's do funky now. Add the parameter `letter` to the function, like so:

```
funky(letter){},
unable() {},
};
```

We need some sort of dictionary or lookup of funky letters. If you open the `text-DEMO` or `text-FINISHED` file, you will see an object of funky letters. Copy that variable along with the `/* eslint-disable */` and `/* eslint-enable */` commens into our text.js file.  Paste it towards the top of the file, after our `filterInputs` declaration. 

![](@attachment/Clipboard_2020-04-22-17-20-49.png) 16:15

This object is just a lookup of letters that match to funky letters. 

We kept the eslint disable comments because otherwise when you save the javascript file, it formats the object so each property is on it's own line, which makes it hard to work within the file because it becomes so long. 

Back to our funky function logic, we need to do the following:
1. Check if there is a funky letter for this case
2. If there is no funky letter for this case, check if there is a lowercase version. 
3. If there is nothing, return the regular letter

So we have our letter argument, which we can use to look up inside of `funkyLetters`. So for example if someone types `T`, we now there is a t for us. 

![](@attachment/Clipboard_2020-04-22-17-27-58.png) 17:43

Add the following code:

```
let funkyLetter = funkyLetters[letter];
```

What we are doing there is we are looking up the letter in our `funkyLetter` object and assigning the value to our `funkyLetter` variable. 
If there is a funkyLetter, we will return it. 
If there is not, we will return the original letter. 

```
funky(letter) {
  // first check if there is a funky letter for this case
  const funkyLetter = funkyLetters[letter];
  if (funkyLetter) return funkyLetter;
  // if there is not, check if there is a lowercase version
  // if there is nothing, return the regular letter
  return letter;
},
```

If you refresh the page and try typing something while selecting the funky radio button, you should see it start working. 

![](@attachment/Clipboard_2020-04-22-17-32-28.png) 18:27

If no `funkyLetter` is returned, we want to check for the lowercase version of it because some letters have a funky version for both lower and uppercase, like `f`.

![](@attachment/Clipboard_2020-04-22-17-33-53.png) 18:37

To do that, we will modify `funkyLetter` to be a let instead of a const, and then after the comment where we check if there is a lowercase version, we will try to grab the lowercase version by lowercasing the letter and looking it up in the `funkyLetters` object and then assigning the value to  `funkyLetter`. If a value is found, we will return it, otherwise we will just return the letter as is. 

```js
funky(letter) {
    // first check if there is a funky letter for this case
    let funkyLetter = funkyLetters[letter];
    if (funkyLetter) return funkyLetter;
    // if there is not, check if there is a lowercase version
    funkyLetter = funkyLetters[letter.toLowerCase()];
    if (funkyLetter) return funkyLetter;
    // if there is nothing, return the regular letter
    return letter;
  },
```

The last one is `unable`. It will take in a letter, and what we will do is one-in-three spaces, we will use the dot dot dot. 

So we need a random number between zero and two, so we need like 1, 2, or 3 or 0, 1, 2. 

The way that we can do that is using `Math.random() * 3`. That returns a number with decimals so we need to wrap it in a `Math.floor()`. 

![](@attachment/Clipboard_2020-04-22-17-41-21.png) 20:06 

Now we will get 0, 1, or 2 returned. So let's grab that random number within the `unable` function. 

```
const random = Math.floor(Math.random() * 3);
```

Next we are going to check whether the letter is equal to an empty sqace, and that the random is equal to 2 (so 1 in 3), then return dot dot dot. 
Otherwise, we just return the letter. 

```
unable(letter) {
  const random = Math.floor(Math.random() * 3);
  if (letter === " " && random === 2) {
    return "....";
  }
  return letter;
},
```

Now if you refresh the page, select the unable option and try typing into the textarea, there is a one in three chance that the space will be turned into a `...` 

![](@attachment/Clipboard_2020-04-22-17-45-30.png) 21:13

The last thing we want to do is when you click on the radio button options, it should trigger that filter and show you the result. 

To do this we can take our `filterInputs`, loop over each one of them, add an eventlistener that listens for the input event, and then when there is an input event, we will call another function which calls `transformText` and passes the text from the textarea. 

```
filterInputs.forEach((input) =>
  input.addEventListener("input", () => {
    transformText(textarea.value);
  })
);
```

Now each of our filter inputs have an event listener that listens to the input event, and when that fires, it triggers the `transformText` event and passes the value of the text. 

Now if you refresh the page, you should be able to select the different radio buttons and the text formatting will change based on the filter you select.

The main thing Wes wanted to get across in this lesson is that you can store methods inside of an object, to keep them together, as well as look them up on that object with a variable that is populated from some external input. 

---

## 57 - Shopping Form with Custom Events, Delegation and localstorage 

In this lesson we will build a shopping list, where you can add items, check them off, and delete them.

![](@attachment/Clipboard_2020-04-23-08-31-55.png) 00:24

Although you may have written something like this before, Wes has baked a lot of things that we need to learn about Javascript into this simple example.  

We will be learning about emitting custom events, such as the one hightlighted in the image below (if you don't know what a custom event is, don't worry, we will be learning about it). 

![](@attachment/Clipboard_2020-04-23-08-37-40.png) 00:40

We will also be learning about event delegation, how do you listen for clicks on things that happen in the future, as well as DOM events, and local storage.

If you open up the `index.html` file in the `exercises/57 - Shopping List` directory let's go over the code that we are starting and working with. We have a div called shoppinglist which contains a form element and an empty ul. Within that ul, we will be outputting our shopping list items. The form has our input and our submit buttons.

```html
<body>
  <div class="shopping-list">
    <form class="shopping">
      <input type="text" name="item" id="item">
      <button type="submit">+ Add Item</button>
    </form>

    <ul class="list"></ul>
  </div>

  <script src="./shopping.js"></script>
</body>
```

With this exercise, you can right-click and open the filter in the browser and everything should still work. However if you do want the live reloading, and instant CSS changes, we can use Parcel, which will give us a server, live reloading and module bundling (which we have yet to learn about). 

There are two ways to install Parcel on your machine. You can install it once, to each project, which is what we did in the last exercise, or you can install it globally on your machine so that anytime you need it you can get a little server up and running. 

The way that you install Parcel globally on your machine is by opening the terminal and typing `npm install -g parcel-bundler` . Now, anytime you are in a terminal, it will be available to you as a command called Parcel. 

![](@attachment/Clipboard_2020-04-27-11-00-37.png) 3:00

If you are on a mac and you have trouble installing global modules on your command line, type `sudo` infront of the command like so `sudo npm install -g parcel-bundler`.  
That will ask you for a password first. You can tell it works if you type `parcel --version` it will tell you what version you have.

Now in the terminal, cd into the Shopping List directory and then type `parcel index.html` in the terminal and hit enter. There will be a message in the terminal telling on which server it is running (usually localhost:1234).

![](@attachment/Clipboard_2020-04-27-11-04-47.png) 3:59

 ![](@attachment/Clipboard_2020-04-27-11-06-05.png) 

 Let's get started. Open the `shopping.js` file, which should contain nothing. 

 There are a couple of things that need to happen...
 - need to listen for when someone types into the input and hits the submit button
 - need to keep track of all of the shopping list items and whether or not they are complete
 - need to render out a list of all of those items

Note: you may notice when you focus into the input to enter a shopping list, all these values show up of everything you have ever typed, like in the picture below. To fix that, you can go to the HTML, you can set autocomplete to false on either the input or the whole form. There is also an `autocapitialize` attribute which you can switch on or off. 

![](@attachment/Clipboard_2020-04-27-11-16-04.png) 5:17

```
<form class="shopping" autocomplete="off">
```

Back to our javascript, lets start by grabbing a few elements: the shopping form and the list. 

```js
const shoppingForm = document.querySelector(".shopping");
const list = document.querySelector(".list");
```

Next we need an array to hold our **state**. 

```
//We need an array to hold our state
const items = [];
```

What does **state** mean? The definition changes from framework to framework, but generally what people are saying is that state is a bunch of data that reflects the state of your application. But what does that mean? Let's use this finished shopping list screenshot as an example. 

![](@attachment/Clipboard_2020-04-27-11-21-34.png) 7:09

State is going to contain a list of all of my items, and a list of all the IDs of each of those items, and whether they have been completed or not. If it was a shopping cart, state would be a list of all the items in the card, how many of each item was in the shopping cart, how expensive is each item, etc. 

You should always be able to recreate the visual part of your application given just the data. All of the current state of your application, meaning how it current is, should always be reflected in some sort of object or array of data and that is what we refer to as **state**. 

Next we need to listen for a submit event on the form. 

If you refresh the page and try to type an item in the input and hit submit, you will notice that the form submits, it puts `?item=Egg` in the URL bar. However that is now what we want. 

![](@attachment/Clipboard_2020-04-27-11-25-30.png) 8:01

![](@attachment/Clipboard_2020-04-27-11-26-43.png) 8:13

Let's make a submit handler for that. The first thing the handler needs to do is prevent the form from submitting so let's add `e.preventDefault()`. 

```
function handleSubmit(e){
  e.preventDefault();
}
```

Now we will grab our `shoppingForm` nad add an event listener on the submit event and pass it the `handleSubmit` callback. Remember, for forms, we don't use click or enter events because it's much easier to just listen to the submit event. That way, if you submit by clicking, you submit by hitting enter, something else triggers a submit of the form, all of those use cases are covered by a single event called submit. 

```
shoppingForm.addEventListener('submit', handleSubmit);
```

Now if you refresh the page, type in eggs and hit enter, nothing should happen, which is good. Let's log "submitted" in our `handleSubmit` function. 

Next we need to pull the data out of the input. How can we get that? Within the `handleSubmit` function, add the following code after we log submitted.

```
function handleSubmit(e) {
  e.preventDefault();
  console.log("Submitted!!!!");
  const name = e.currentTarget.value;
  console.log(name);
}
```

If you refresh the page now, type in eggs and hit enter, you should get something like below in the console. 

![](@attachment/Clipboard_2020-04-27-11-35-40.png) 10:00

Why are we getting undefined? Let's do a bit of debugging. Let's add a log of `e.currentTarget` to our handler. If you do that and then refresh the page, you should see the form element logged. 

![](@attachment/Clipboard_2020-04-27-11-37-15.png) 10:13

The reason we are getting undefined because the currentTarget is the form, not the input. We want to get the text out of the input.  There are a couple ways we could do this. 

We could write another query selector to grab it, however, because the input has a name `<input type="text" name="item" id="item>`, it's actually accessible via the form dot the name of the input. 

![](@attachment/Clipboard_2020-04-27-11-39-20.png) 10:34

If we take the form and store it as a global variable, called `temp1`. We can do `console.dir(temp1)` to get every property inside of it.

![](@attachment/Clipboard_2020-04-27-11-40-58.png) 10:56

Somewhere inside of all thoes properties is `item`. Wes is having trouble finding it but we will demonstrate it with code. Modify the log of `console.log(e.currentTarget)` to `console.log(e.currentTartget.item)`. 

![](@attachment/Clipboard_2020-04-27-11-42-16.png) 11:04

As you can see, we now get the item, not the entire form itself. 

So modify our name declaration to `e.currentTarget.item.value` like so:

```
function handleSubmit(e) {
  e.preventDefault();
  console.log("Submitted!!!!");
  const name = e.currentTarget.item.value;
  console.log(name);
}
```

As you can see, now we can capture the value of eggs. 

![](@attachment/Clipboard_2020-04-27-11-43-52.png) 11:20

Next step is to store the data about the shopping item in the items array, but we cannot just store the straight up string, because we need to be able to store a bit more info about that item. 

The other two things we need to know are:
-  is it completed (have you bought it or not?) 
- what is the ID of the item?  

stopped at 11:44
