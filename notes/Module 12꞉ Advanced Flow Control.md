---
attachments: [Clipboard_2020-05-07-19-46-46.png]
title: 'Module 12: Advanced Flow Control'
created: '2020-05-07T23:18:40.737Z'
modified: '2020-05-07T23:49:33.928Z'
---

# Module 12: Advanced Flow Control 

## 66 - The Event Loop and Callback Hell 

Before we get into promises, we need to talk about how Javascript is asynchronous and how the event loop works. 

You may often hear that almost everything in Javascript is non-blocking (asynchronous). What does that mean?

For us to understand that, we need to first talk about how Javascript events work.

Javascript is a single threaded language, meaning that only one thing can be run at a time. Some other languages are multi-threaded, which means they can run multiple processes at once. Because Javascript is single threaded, which means we can only run one thing at a time. 

Let's visualize that with some examples. Open up the `event-loop.html` file within the `exercises/` directory. 

Let's add two logs witin our script tag and then refresh the page to check them. 

```
console.log('Starting');
console.log('ending');
```

![](@attachment/Clipboard_2020-05-07-19-46-46.png) 00:58

No one is surprised by that.

Let's add some code in between the two logs. In this demo we want to wait for two seconds, which we could do with a timeout. 

```
console.log('Starting');
setTimeout(function(){
  console.log('Running');
}, 2000);
console.log('ending');
```

Now if you refresh the page, what will you see? 


stopped at 1:20
































---

## 67 - Promises

---

## 68 - Promises - Error Handling

---

## 69 - Refactoring Callback Hell to Promise Land

---

## 70 - Async Await

---

## 71 - Async Await Error Handling

---

## 72 - Async Await Prompt UI

---

## 73 - Async Typer UI - two ways
