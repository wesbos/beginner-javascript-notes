---
attachments: [Clipboard_2020-04-20-17-44-07.png, Clipboard_2020-04-20-17-49-26.png, Clipboard_2020-04-20-17-51-12.png]
title: 'Module 10: Harder Practice Exercises'
created: '2020-04-20T11:16:46.618Z'
modified: '2020-04-20T21:57:01.633Z'
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

stopped at 3:40


## 56 - Sarcastic Text Generator
