---
attachments: [Clipboard_2020-05-21-06-40-48.png, Clipboard_2020-05-21-06-50-00.png, Clipboard_2020-05-21-06-53-48.png, Clipboard_2020-05-21-07-04-16.png, Clipboard_2020-05-21-07-05-02.png, Clipboard_2020-05-21-07-05-42.png, Clipboard_2020-05-21-07-10-24.png, Clipboard_2020-05-21-07-10-55.png, Clipboard_2020-05-21-18-09-08.png, Clipboard_2020-05-21-18-22-56.png, Clipboard_2020-05-21-18-29-13.png, Clipboard_2020-05-21-18-35-48.png, Clipboard_2020-05-21-18-38-59.png, Clipboard_2020-05-21-18-47-00.png, Clipboard_2020-05-21-18-47-30.png, Clipboard_2020-05-21-18-48-38.png, Clipboard_2020-05-21-18-48-54.png, Clipboard_2020-05-21-18-50-37.png, Clipboard_2020-05-22-07-49-00.png, Clipboard_2020-05-22-07-54-59.png, Clipboard_2020-05-22-07-59-32.png, Clipboard_2020-05-22-08-10-11.png, Clipboard_2020-05-23-08-46-00.png, Clipboard_2020-05-23-08-49-00.png, Clipboard_2020-05-23-09-09-31.png, Clipboard_2020-05-23-09-14-45.png, Clipboard_2020-05-23-09-15-26.png, Clipboard_2020-05-23-09-45-11.png, Clipboard_2020-05-23-09-48-29.png]
title: 'Module 13: Ajax and Fetching Data'
created: '2020-05-21T10:25:44.675Z'
modified: '2020-05-23T13:48:46.217Z'
---

# Module 13: Ajax and Fetching Data

## 74 - Ajax and APIs

Using `async/await` and Promises is also very useful when fetching data from an **API**. 

An API is a term that is thrown around a lot but it stands for Application Programming Interface, and it is a way to talk to a machine in a somehwat standardized procedure. 

When you are building any type of app, that app, the client, needs to talk with  server that exists somewhere. It does not matter if you are building a web app, mobile app etc. If you are building a web app, the app (the client) would be the web browswer.

For example if you had a twitter app, you would need to be able to pull down your most recent tweets, send tweets, like tweets, reply to tweets etc. All that functionality is basd upon what is called an API.

Most services with a public facing website will try to surface their data and surface their functionality via an API. 

A lot of work that you will be doing as a web developer will be just pulling down data. We will start by looking at how we can go to another service and pull that data into our application and then display it (Wes will show us two examples, one with a pizza and one with github).

The most popular way to pull data from an existing websites that offers an API, is using a URL that you can hit with some associated data, such as Wes Bso in the Github example below. That API will respond with what is called JSON. 

![](@attachment/Clipboard_2020-05-21-06-40-48.png) 2:27 

We have discussed **JSON** a few times. It stands for Javascript Object Notation, and it is a good way to transport Javascript objects from server to server or server to client. 

Open a browser and navigate to this endpoint: https://api.github.com/users/webbos
That is part of the Github API. 

Note: in the videos, Wes is using a chrome extension that makes viewing JSON files easier called JSONViewer. If you are going to be working with JSON or APIs,Wes recommends downloading it. 

Although what is returned looks like an object, it's actually just a string.

If we copy that string into the console and assign it to a variable called `data`, we can log it and access it from the console like so. 

![](@attachment/Clipboard_2020-05-21-06-50-00.png) 3:33

As you can see, it is just a huge string.

If you do `typeof data` it would return string. 

If you wanted to grab one of the properties from the data returned such as `data.company` it will return undefined because it's just a string. 

So the server will return a string and it's up to the developer to turn it back into a Javascript object. 

To do that, we can wrap `data` in a `JSON.parse()` and that will return to us a proper object, which we can then store in a variable. 

```
const dataObj = JSON.parse(data);
```

Now we can access the object properties using the javascript dot notation. 

![](@attachment/Clipboard_2020-05-21-06-53-48.png) 4:29 

Lots of APIs allow for this functionality that enables you to pull data from their server into your own. 

There are many that do not allow it and many that require API keys, which we will go into later. For now, we will be working with wide open APIs that do not require any authentication. 

In our playground folder and create a new file called `apis.html`. 

Note: You will often referred to what we are doing in this video as **AJAX**, which stands for Asynchronous Javascript and XML. 

We know what asynchronous is and Javascript, but you may not know what XML is. 

XML is another way that you can receive data and it looks a lot like HTML but is not HTML. 

XML was used in the past but has generally been replaced with JSON as the preferred way to send data via APIs, but you might still encounter it. 

Wes has only had to work with XML once during his 12 year career.

So when people say "AJAX" they mean fetching data from an API and displaying it on the page. 

Let's go into our HTML and give ourselves base HTML with a script tag within the body.

```
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title>APIs</title>
  <link rel="stylesheet" href="../base.css">
</head>

<body>
  <script>
  </script>
</body>

</html>
```

The first thing we will do is store the URL in a variable. That is not necessary but is much easier.  

We will call the variable `endpoint`. **Endpoint** is a fancy word for the URL that you need to visit in order to get the data.

```
const endpoint = 'https://api.github.com/users/webbos';
```

In order to get that data, we will use `fetch` which exists within Javascript. (There are some other libaries that are used, specifically Axios but the fetch library is very good and comes built in to all browsers). 

To grab that data we will call `fetch` and then pass it the endpoint that we want to call. That will return a Promise. 

```
const wesPromise = fetch(endpoint);
console.log(wesPromise);
```

![](@attachment/Clipboard_2020-05-21-07-04-16.png) 7:52

The way you can see if it worked is if you go to the network tab and refresh the page, you will see all the requests that have happened on the page.  You can see when it got sent out and that it comes back with all of the data.

![](@attachment/Clipboard_2020-05-21-07-05-42.png) 8:13 

Now if we weant to get that data back into JS, how do we do that? We can use `.then()`. 

Let's make a quick error handler first.

```
function handleError(err) {
  console.log("OH NO!");
  console.log(err);
}

```

Now let's fetch that data and log it to the console. 

```
const endpoint = "https://api.github.com/users/webbos";

const wesPromise = fetch(endpoint);
wesPromise
.then((data) => {
  console.log(data);
})
.catch(handleErro);
```

![](@attachment/Clipboard_2020-05-21-07-10-55.png) 9:15

Now when you refresh the page, we do not get the Promise anymore, instead we get this response object you see above. The response tells us the type is "cors" which we will talk about in a second. 

We have all these properties on the response object but where do we get the data? If you expand the properties like `headers` and `body`, you won't see much. 

![](@attachment/Clipboard_2020-05-21-18-09-08.png) 9:27

As you can see, the data is nowhere to be found. 

There is another step that needs to happen before we can get the data. In the step we just did, we get the data that is steaming into the browser in the variable we have named `response`. The data is not yet fully downloaded and we also do not know what type of data is coming back, you can use `fetch` to fetch any type of data. It is not assumed it is JSON, it could be an image or raw text. 

In order to actually get the data, we need to tell the browser that when the data is finished downloading, go ahead and convert it from JSON to a javascipt object. 

![](@attachment/Clipboard_2020-05-21-18-22-56.png) 10:30

If you look at the prototype of the response object, you will see that there is a number of methods on the response. In our case, we want to use `json()`.  

We will return `response.json()` which will return another promise. 

```
wesPromise
.then((response) => {
  return response.json();
}).catch(handleError);
```
Now we can chain on another `.then()` and then we will have the actual data, which we can log.

After a split second, you should see that we have the full object. There is no need to `JSON.parse()` it because `response.json()` will do it. 

SO you need to use a double promise to actually get the data when you use fetch.
The first one gets the response and the second one gets the response and turns it into JSON for us.

Now we can log information from the data we fetched. 

```
wesPromise
.then((response) => {
  return response.json();
})
.then(data=>{
  console.log(data);
  console.log(data.blog);
  console.log(data.name);
  console.log(data.location)

})
.catch(handleError)
```

![](@attachment/Clipboard_2020-05-21-18-29-13.png) 11:40

Let's now display some info about the user. 

Let's add a paragraph tag in our HTML and give it a class of `user`, then select it in our script tag. 

```
<body>
  <p class="user"></p>
  <script>
    function handleError(err) {
      console.log("OH NO!");
      console.log(err);
    }

    const userEl = document.querySelector(".user");

    const endpoint = "https://api.github.com/users/wesbos";

    const wesPromise = fetch(endpoint);
    wesPromise
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        console.log(data.blog);
        console.log(data.name);
        console.log(data.location);
        userEl.textContent = `${data.name} - ${data.blog}`;
      })
      .catch(handleError);
  </script>
</body>
```

![](@attachment/Clipboard_2020-05-21-18-35-48.png) 12:40

As you can see, it pops up.

One other thing you can do is set the text content of the element as loading before we replace it with the data, so for a split second you will see "loading...". 

```
userEl.textContent = "loading....";
const wesPromise = fetch(endpoint);
```

Now let's refactor this to use `async/await`. 

We will make an async function `displayUser` that takes in a `username`. Let's bring all of the code we wrote after we grab the element with the class of `user` and put it into our `displayUser` function. 

![](@attachment/Clipboard_2020-05-21-18-38-59.png) 13:39

Now let's go line by line. We will leave the first line as is.

The promise where we fetch the endpoint can now be switched to await and that no longer is a Promise but is a response. Then we can get the data by awaiting `response.json()`. 

```
async function displayUser(username) {
  userEl.textContent = 'loading...';
  const response = await fetch(endpoint);
  const data = await response.json();
  console.log(data);
  console.log(data.blog);
  console.log(data.name);
  console.log(data.location);
  userEl.textContent = `${data.name} - ${data.blog}`;
}
```

The only thing left is to call `displayUser` on pageload. 

Let's go ahead and display the user. To do that we will replace the `endpoint` variable with `baseEndpoint` and make another variable for the `usersEndpoint `  like so

```javascript
const baseEndpoint = "https://api.github.com";
const usersEndpoint = `${baseEndpoint}/users`;
```

Now we can fetch the username that was pass in by replacing our fetch with the following:

```
const response = await fetch(`${usersEndpoint}/${username}`);
```

That allows us to generate the endpoint on the fly based on what was passed in. Let's try calling it from the bottom of our script tag with the user `stolinski`. 

```
<script>
  const baseEndpoint = "https://api.github.com";
  const usersEndpoint = `${baseEndpoint}/users`;
  const userEl = document.querySelector(".user");

  async function displayUser(username) {
    userEl.textContent = "loading...";
    const response = await fetch(`${usersEndpoint}/${username}`);
    const data = await response.json();
    console.log(data);
    console.log(data.blog);
    console.log(data.name);
    console.log(data.location);
    userEl.textContent = `${data.name} - ${data.blog}`;
  }

  function handleError(err) {
    console.log("OH NO!");
    console.log(err);
  }

  displayUser("stolinski")
</script>
```

One thing we are not doing is catching the error so if something went wrong, like we misspelt the github url in our `baseEndpoint`. 

`displayUser("stolinski").catch(handleError);`

![](@attachment/Clipboard_2020-05-21-18-47-30.png) 16:32


TIP: You can filter out just AJAX request from the Network tab by clicking XHR. 
![](@attachment/Clipboard_2020-05-21-18-47-00.png) 16:11

Let's add one more thing to our `handleError` function. 

```
function handleError(err) {
  console.log("OH NO!");
  console.log(err);
  userEl.textContent = `Something went wrong: ${err}`;
}
   
```

![](@attachment/Clipboard_2020-05-21-18-48-54.png) 16:55


Let us do one more example. It is hard to find good APIs that are public and don't require API keys. There is a good list of them in the github repo https://github.com/public-apis/public-apis

![](@attachment/Clipboard_2020-05-21-18-50-37.png) 17:34

You can scroll through and find different APIs for all different things. v

---
## 75 - CORS and Recipes

In this video we are going to build an app that searches for a recipe based on a keyword and then we will display the data.

Instead of Wes using a perfect API and showing you an example with no hurdles, we will use a real API. Working with APIs can be frustrating so Wes wants to go through all those hurdles together so when you try it yourself, you will know how to approach these common pitfalls. 

We will be using www.recipepuppy.com. 

![](@attachment/Clipboard_2020-05-22-07-49-00.png) 00:52 

The way that it works if you look at the docs is you go to the url and you pass `i` which is ingredients, you pass `q` which is your omelet and then you pass `p` which is your page. You can see that on the homepage, they have additional parameters you can pass. 

http://www.recipepuppy.com/api/?i=onions,garlic&q=omelet&p=3 

![](@attachment/Clipboard_2020-05-22-07-54-59.png) 1:08

`i`, `q` and `p` are all parameters. Let's talk about parameters. 

Sometimes when you got to a URL, you see these question marks on the end.
Even when you submit a form they are there.
![](@attachment/Clipboard_2020-05-22-07-59-32.png) 1:22

Those are referred to as **query params**.  Let's break down the ones from the url above. 

```
?i=onions,garlic&q=omelet&p=3 
```

The query parameters portion of a url will always start with a question mark. So the first parameter will always start with a question mark and then the additional parameters are separated by an ampersand `&`. That is how you can multiple parameters. 

```
?
i=onions,garlic
&
q=omelet
&
p=3 
```

We are passing multiple ingredients to the `i` parameter. Using commas to separate the multiple items is not a standard thing, it is just how that API works. `q` is the recipe you are looking for in this example and `p` is page, which is how this API handles pagination. 

The parameters are never standard, every API implements them a little bit differently so you always have to go and read the docs. 

For this lesson we will be working out to the `/excercises/75 - CORS and Recipes/` directory. 

![](@attachment/Clipboard_2020-05-22-08-10-11.png) 2:31

We will have a form where the use can type in a keyword and that will return a list of recipes as well as the recipe ingredients and thumbnails as well. 

 We won't worry about the UI just yet, let's just getting it working.

 In the empty `scripts.js` file, let's add our base url. Then create an async function that takes in a parameter and fetches that from the endpoint, and we will call that function on runtime. 

 ```
 const baseEndpoint = "http://www.recipepuppy.com/api"

 async function fetchRecipes(query){
   const res = await fetch(`${baseEndpoint}?q=${query}`);
   const data = await res.json();
 }
 fetchRecipes('pizza');
 ```

 Now let's fetch some data. If we refresh the page and go to our dev tools to see what we are working with, you will see we get an error.

 ![](@attachment/Clipboard_2020-05-23-08-46-00.png) 4:30

>Access to fetch at 'http://www.recipepuppy.com/api?q=pizza' from origin 'null' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource. >If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.
www.recipepuppy.com/api?q=pizza:1 Failed to load resource: net::ERR_FAILED
scripts.js:6 Uncaught (in promise) TypeError: Failed to fetch

If you look at the network tab, and filter for XHR, you will see the request but there is no response data. 

![](@attachment/Clipboard_2020-05-23-08-49-00.png) 4:57

 What happened there is the browser blocked it because of something called **CORS**. What does CORS mean? It stands for Cross Origin Resource Sharing.

 Let's break down what that means piece by piece. 
 
 The CO stands for cross origin. What are origins? Take the two websites: wesbos.com and github.com. Those are both origins. Domain names are origins. 

 Now if we want to share data between the two, by default you cannot. Onlyt sharing data between the same domain name is allow, so you can share data from wesbos.com to wesbos.com/about for example. 

 As soon as you go cross origin from one domain name to another, then you start getting in trouble because that is a security issue in the browser. Let's say you were logged into your bank at bank.com while you were also running code from wesbos.com.

The javascript you are running on wesbos.com shoul not be able to reach into bank.com. That would be a security issue. So by default, websites cannot talk to each other from one domain to another. 

That is a pretty valid use case however, having a website like wesbos.com from which we want to pull data another websites like from recipepuppy.com. 

How can we get those two websites to talk? What has to happen is the website that the data is being pulled from has to implement something called a CORS policy. A CORS policy is something that happens on the server (it must happen on the server, there is nothing you can do in the browser about this). 

On the server there is a CORS poicy that says wesbos.com is allows to ask for dara and we will return it. Recipepuppy.com has to say these are the domain names that are allowed to transfer data from one to another, and it has to happen on the server of the person that has the data.

In order for us to initially get involved with CORS, we need an origin before we can go ahead and use it. So if we look at the error we got in the console, it says 
>origin 'null' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.

We are getting that error because we are runnign the code right off the file access. The first thing you do when you see that issue is say "okay, I can no longer run this from the file, I need to run it from a server. So the first step we need to do is get the server up and running, so we can at least see if that fixes it (in most cases, it will). 

 Now let's go into the terminal and navigate to our `exercises/75 - CORS and Recipes/` directory. 

 From here we need a server to use. This could be any server, you could use browsersync, upload the code to CodePen, in our case, we are going to use Parcel which is a quick little server. 

 Let's get Parcel running by running `npm init` in the console. 

 ![](@attachment/Clipboard_2020-05-23-09-09-31.png) 9:17

 You need to put a package name which you can call anything, Wes chose `dogrecipes` and then you just keep hitting enter in the console when you are prompted for a few questions like you see above. 

Once that is finished installing, you can type `npm install parcel-bundler` into the terminal. 

Once that is installed, you should see a `packages.json` file in your folder (there will also be a lock file). This packages file is where we can go and change our scripts, just like we did before. Open the file and modify the script start to be the same as you see below: 

```
 "scripts": {
    "start": "parcel index.html"
  },
```

Now when we run `npm start`, it will open up localhost:1234 or another port.  

![](@attachment/Clipboard_2020-05-23-09-14-45.png) 10:04

Let's open that url and look at the console. You will notice we still have another issue. This is issue #2.

![](@attachment/Clipboard_2020-05-23-09-15-26.png) 10:11

We are getting this errror "regeneratorRuntime is not defined". This issue has nothing to do with CORS. You yourself may not see this issue, but instead see another CORS issue. If that is the case, skip ahead to that. 

#### regeneratorRuntime error

If you do run into this issue, Wes will explain it. `regeneratorRuntime` is a thing called Babel. Babel takes your javascript, with things like `async/await` and backticks, which are relatively new to Javascript. Sometimes you need to support browswers that are old and don't know about things like `async/await` etc. 

Babel will take your modern javascript code and transpile it into Javascript that is runnable on older browseres like IE or older Safari. That will give you Javascript that works the same way, it has just been transpiled into the equivalent in older Javascript with callbacks and things like that.

The weird thing about Babel is it wants to compile `async/await`, even though in most cases you don't need to be cause it's available in almost all browsers and has been for a few years. 

So we need to tell Babel not to transpile `async/await` because we don't need that transpiled. The way we can get around that is to go to the `package.json` and somewhere in there we will add a `broswerslist` property to the JSON file.

![](@attachment/Clipboard_2020-05-23-09-45-11.png) 12:40

browserslist is a package that allows you to define which browsers you are currently supporting. There is a huge list of filtering options like less than 1% usage, blackberry 7, etc. You can just write them in plain english and that will convert them. That is what tells babel what to transpile, and what to just leave as is. 

Note: Within `packages.json` you must use double quotes instead of single because it is JSON. 

```
 "browserslist": [
    "last 1 chrome versions"
  ],
```

Wes likes to use the filter above because it tricks babel into thinking you are supporting the latest and greatest and then it won't actually transpile it. 

Now when you look at the page the error should be gone, but you may see other errors which is fine.

![](@attachment/Clipboard_2020-05-23-09-48-29.png) 13:24

If you do have issue, a quick troubleshooting. 

stopped at 13:48







---
## 76 - Dad Jokes

























---
## 77 -  Currency Converter
