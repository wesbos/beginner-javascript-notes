---
attachments: [Clipboard_2020-05-27-06-59-50.png, Clipboard_2020-05-27-07-05-17.png, Clipboard_2020-05-27-07-15-19.png, Clipboard_2020-05-27-07-18-36.png, Clipboard_2020-05-27-07-19-13.png, Clipboard_2020-05-27-07-19-33.png, Clipboard_2020-05-27-07-21-39.png, Clipboard_2020-05-27-07-22-53.png, Clipboard_2020-05-27-07-23-08.png]
title: Module 14 - ES Modules and Structuring Larger Apps
created: '2020-05-27T10:45:39.129Z'
modified: '2020-05-27T11:33:35.784Z'
---

# Module 14 - ES Modules and Structuring Larger Apps


## 78 - Modules 

Let's talk about modules. 

Being able to share code across multiple javascript files and even across multiple projects is an easy thing to do when you start to use modules in Javascript.

So what are they? Modules are a way to structure and organize your Javascript, and it gives us the ability to share functionality and data across multiple files and projects. 

Here are a few things you need to know about modules:
- They have their own scope, similar to how a function has scope.
- They can hold anything (functionality, data, config)

If you recall in the previous lesson where we built a currency converter, we had a variable `currencies` that was a giant object of all the currency codes and names. 

It would be nice if instead of having that object directly in our file, we could put it in a separate module and then import it into the file to use when we need it. That is what modules will allow us to do. 

Another use case for modules is utility functions. In the Dad Jokes lesson that we finished, we had a `randomItemFromArray` method. That method is not specific to our Dad Jokes project, it's just a handy array utility. We could throw that off into a separate file that is used for utilities. 

Let's look at how modules work in the browser, and then we will look at some tooling that will help us work with them. 

You might hear modules referred to as **ESM**, **EcmaScript modules**, or **ES6 modules**. They were added to Javascript a couple of years ago, and they are the best way to organize your javavscript when you have multiple files. 

Let's go into our playground and create a folder called `modules` (it might already be there for you). 

Inside of that let's make the following files: `index.html`, `utils.j`, `handlers.js`, `scripts.js`. Now we have three different javascript files here. 

Let's say we had the following code in `scripts.js`: `const name = 'wes'`. 

In `utils.js`, lets add a simple function. 

```
function returnHi(name){
  return `hi ${name}`;
}
```

So if we are in `scripts.js` and we want to use that `returnHi` function, can we?

Let's try. Modify the code like so. 

```
const name = 'wes';
console.log(returnHi(name)();
```

Now let's go into our `index.html` and add our base HTML if it is not already there. Let's add a script source tag and link it to `scripts.js`, and open it up in the browser.

When you do that, you should see an error that `returnHi` is not defined.  

![](@attachment/Clipboard_2020-05-27-06-59-50.png) 3:58

That makes sense becuase we have not yet put our `utils` on the page. You might think we can just add another script source tag above the one we added and link it to utils.

```
<script src="./utils.js"></script>
<script src="./scripts.js"></script>
```

![](@attachment/Clipboard_2020-05-27-07-05-17.png) 4:27

As you can see, now it works. All we had to do is put one script in front of the other one that we needed it in. This used to be the way we shared code across multiple files. 

That got out of hand pretty quickly because you had all these files that had dependencies and the order of the script tags affected the execution because they all have to load in a waterfall, which means one after the other. Each file is assuming that the other one has access to it. 

If you look at our `scripts.js` file in VS code, ESLint is complaining that `returnHi` is not defined. That is because that function does not exist within the file, so where did it come from? 

The only reason it works is because we have globally scoped the function in another file and we are just assuming that it will be available to us on the page. That is a very brittle way to write javacript. 

The solution to that is to use modules! When you need a function like `returnHi`, we can just import the function from the module, from the file that actually contains that function.

When you do that, you don't really have to worry about things loading before each other, because we will import the valuse we need before hand. 

Let's change this example to a very simple module. 

In our `index.html`, we will just have one script tag and that script tag is going to be your entry point into your Javascript. We will add the `type` attribuet on the script tag and set it to `module` like so:

```
<scripts src="./scripts.js" type="module"></script>
```

Let's modify the code in our `scripts.js` file to contain the following:

```
const name = 'wes';
console.log('Its working...');
```

Let's refresh the HTML page and look at the console you will see a bunch of errors. 

![](@attachment/Clipboard_2020-05-27-07-15-19.png) 7:11


This first one is the CORS issue again. It is giving us trouble because you cannot use modules unless you are running it on a server. 

### Setting up Server 

We cannot use a Parcel server because Parcel also handles modules for us and Wes is trying to show us how they work without using a bundler. We just need a very simple server up and running. 

If you know how to run a server to serve us these files, feel free to skip ahead. (to 10:41)

There are a couple of different ways to do this. 

1. VSCode plugin

If you go to extensions in VS code and search for "Live Server", you should see an extension that matches it and you can click install. 

![](@attachment/Clipboard_2020-05-27-07-18-36.png) 8:13

If you go back to the modules and right click on the `index.html` and click open with Live server, and that will start it up in the browser. 

![](@attachment/Clipboard_2020-05-27-07-19-13.png) 8:26

![](@attachment/Clipboard_2020-05-27-07-19-33.png) 8:34

That will start up a localhost server. The url is `127.0.0.1:5550` which is the equivalent as localhost, it is just the IP address. You can replace it with localhost and it will work just the same `localhost:5550`. 

Now if you open up the dev tools, you will see that it is working. 

2. BrowserSync

Another way to get a server running. Open your terminal and run `npm install -g browser-sync`. 

![](@attachment/Clipboard_2020-05-27-07-21-39.png) 9:16

Then we need to do into our `modules/playground` folder within the terminal and then we just type `browser-sync` and it should start up a server. 

![](@attachment/Clipboard_2020-05-27-07-22-53.png) 8:43

If you 
![](@attachment/Clipboard_2020-05-27-07-23-08.png) 9:47

stoppe at 9:45




---

## 79 -  Currency Module Refactor

---

## 80 - Currency Modules Refactor 2 

---

## 81 - Dad Jokes Modules Refactor

---

## 82 - Bundling and Building with Parcel

---

## 83 - using open source npm packages

---

## 84 - Security


