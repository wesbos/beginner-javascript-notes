---
attachments: [Clipboard_2020-05-21-06-40-48.png, Clipboard_2020-05-21-06-50-00.png, Clipboard_2020-05-21-06-53-48.png, Clipboard_2020-05-21-07-04-16.png, Clipboard_2020-05-21-07-05-02.png, Clipboard_2020-05-21-07-05-42.png, Clipboard_2020-05-21-07-10-24.png, Clipboard_2020-05-21-07-10-55.png, Clipboard_2020-05-21-18-09-08.png, Clipboard_2020-05-21-18-22-56.png, Clipboard_2020-05-21-18-29-13.png, Clipboard_2020-05-21-18-35-48.png, Clipboard_2020-05-21-18-38-59.png, Clipboard_2020-05-21-18-47-00.png, Clipboard_2020-05-21-18-47-30.png, Clipboard_2020-05-21-18-48-38.png, Clipboard_2020-05-21-18-48-54.png, Clipboard_2020-05-21-18-50-37.png, Clipboard_2020-05-22-07-49-00.png, Clipboard_2020-05-22-07-54-59.png, Clipboard_2020-05-22-07-59-32.png, Clipboard_2020-05-22-08-10-11.png, Clipboard_2020-05-23-08-46-00.png, Clipboard_2020-05-23-08-49-00.png, Clipboard_2020-05-23-09-09-31.png, Clipboard_2020-05-23-09-14-45.png, Clipboard_2020-05-23-09-15-26.png, Clipboard_2020-05-23-09-45-11.png, Clipboard_2020-05-23-09-48-29.png, Clipboard_2020-05-23-18-06-46.png, Clipboard_2020-05-23-18-13-09.png, Clipboard_2020-05-23-18-27-35.png, Clipboard_2020-05-23-18-39-22.png, Clipboard_2020-05-23-18-40-20.png, Clipboard_2020-05-23-18-44-58.png, Clipboard_2020-05-23-18-52-39.png, Clipboard_2020-05-23-18-52-43.png, Clipboard_2020-05-23-18-55-31.png, Clipboard_2020-05-24-20-07-52.png, Clipboard_2020-05-24-20-17-04.png, Clipboard_2020-05-24-20-20-43.png, Clipboard_2020-05-24-20-21-00.png]
title: 'Module 13: Ajax and Fetching Data'
created: '2020-05-21T10:25:44.675Z'
modified: '2020-05-25T00:36:16.613Z'
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

If you do have issues, kill the server by pressing Ctrl + C while focused in the terminal. Then open the folder up in your finder, and find the `cache/` and `dist/` folders within there and just delete those. 

![](@attachment/Clipboard_2020-05-23-18-06-46.png) 13:47

Now run `npm run start`, and that will fire it up again. 

Problem number two, we have solved by using browserslist (you might not need to do that in the future). 

The next problem is kind of the same error we had in the first issue.

![](@attachment/Clipboard_2020-05-23-18-13-09.png) 14:06

As you can see, even though we are now running our code on a server instead of access it right from the file, we are still getting an error except this time it is complaining about localhost:1234 not origin. 

It seems like recipepuppy is complaining and saying, nope, you cannot use this in the browser.

Let's take a look at the docs because sometimes they will offer solutions such as use a callback. There is nothing on the page that suggests that we should or shouldn't use it with Javascript, which is a bit of a bummer.

So what are you supposed to do if the CORS policy doesn't work or they don't have a CORS policy on it? It's not like they are explicitly blocking websites from accessing it, it's more likely they just have never implemented a CORS policy. 

If you look at the website, you can see it has a link to "Recipe Puppy for iPhone", and if you were using this in an iPhone app you are not restricted to CORs because there are no multiple tabs open and things like that.

So what is the solution? The solution is that the request would work if it was made from anything other than a browser. 

If we were to request the same data from the API using Node.js, php, ruby on rails or anything else, than it is totally allowed. 

So the solution is instead of going directly from localhost to recipepuppy, we need to put something in between called a **proxy**. 

It will work like this: localhost will send the data to the proxy. Then the proxy will do a request to recipepuppy on the server side, which recipepuppy allows so it will send data back to the proxy, and then the proxy sends it back to the localhost.  

To use a proxy you either have to build one yourself which requires building an entire server that handled your requests and locked it down or in some cases, where it is something silly with no usernames, passwords or nothing sensitive being sent, you can use a **CORS** proxy that people have provided and you can just stick infront of your url and it will proxy the data for you. 

To find one, just google CORS proxy.

![](@attachment/Clipboard_2020-05-23-18-39-22.png) 17:28

Wes has found that the `https://cors-anywhere.herokuapp.com` one works the best. 

![](@attachment/Clipboard_2020-05-23-18-40-20.png) 17:37

If you go to the website you will just see the text above, but the way that it works if you take the url and paste it infront of your urls and that will proxy that data for you. 

```
const baseEndpoint = "http://www.recipepuppy.com/api";

async function fetchRecipes(query) {
  const res = await fetch(
    `https://cors-anywhere.herokuapp.com/${baseEndpoint}?q=${query}`
  );
  const data = await res.json();
} 
fetchRecipes("pizza");
```

To be absolutely clear here: you are sending you data through a random web server that is controlled by who knows who. Never use this for something that has sensitive data like passwords, emails or login information. If that is the case, you have to run your own server.

In our case, we are just using it to learn and look up recipes so it doesn't matter that someone random may have access to that data.

Let's refactor the code slightly to the put proxy url in it's own variable like so:

```
const baseEndpoint = "http://www.recipepuppy.com/api";
const proxy = "https://cors-anywhere.herokuapp.com/";

async function fetchRecipes(query) {
  const res = await fetch(`${proxy}${baseEndpoint}?q=${query}`);
  const data = await res.json();
}
fetchRecipes("pizza");
```

Now if we refresh the page, the error should be gone. Let's also console log the data. 

![](@attachment/Clipboard_2020-05-23-18-44-58.png) 19:07

Now that we finally have the data working, we need to loop through them and show them based on what the user has searched for. 

Let's make an event listener and handler for the submit event when the user enters a keyword and hits the submit button. 

```
function handleSubmit(event){
  event.preventDefault();
  console.log(event.currentTarget);
}

form.addEventListener('submit', handleSubmit);
fetchRecipes('pizza');
```

To grab the value of the query we can modify the code to use `event.currentTarget.query.value` because the input has a `name` attribute of `query`. 

![](@attachment/Clipboard_2020-05-23-18-52-43.png) 20:25

If you were to refresh the page, you should see pizza logged. 

Next let's add some sort of loading screen because we don't want the user searching for many things over and over again while the API is still searching. 

There are a couple of ways to do that. The easiest is if you go to the input button and add a `disabled` attribute. That will stop the user from actually clicking it.


````
<button disabled type="submit">Submit<button>
```

There is no visual different there, so let's add a style for buttons with the disabled attribute

```
button[disabled] {
  opacity:0.2;
}
```

![](@attachment/Clipboard_2020-05-23-18-55-31.png) 21:40

Now it is clear that the button is disabled.

Another trick you can do is take a fieldset and wrap all your inputs in that fieldset and then put a disabled attribuet on the fieldset itself. That will prevent someone from being able to type in the box or click on the buttons as well. 

Either one is totally fine, as long as the user is prevented from making multiple requests at the same time.

Let's add a name attribute to the button of `name="submit"`. 

Now in our script file we can access the submit button within the `handleSubmit` function, disable it, and then call `fetchRecipes` and pass it what the user searched.  

```
function handleSubmit(event){
  event.preventDefault();
  const form = event.currentTarget;
  //turn the form off
  form.submit.disabled = true;
  //submit the search
  fetchRecipes(form.query.value);
}
```

Now let's modify our `fetchRecipes` function to return the data instead of just logging it. 

```
async function fetchRecipes(query) {
  const res = await fetch(`${proxy}${baseEndpoint}?q=${query}`);
  const data = await res.json();
  return data;
}
```

Next we can await the fetchRecipes by marking our `handleSubmit` function as async.

```
async function handleSubmit(event) {
  event.preventDefaut();
  console.log(form.query.value);
  const el = event.currentTarget;
  // turn the form off
  el.submit.disabled = true;
  // submit the search
  const recipes = await fetchRecipes(el.query.value);
  console.log(recipes);
  el.submit.disabled = false;
}
```

Now when we submit the form, it should disable the button, fetch the recipes, log the recipes and the renable the button. 

Now if you were to search something like "chicken" the form would submit, the button will be disabled for a minute and then in the console you would see the results of recipes with chidekn in them and the button would be reenabled.

![](@attachment/Clipboard_2020-05-24-20-07-52.png) 24:45

Let's make another function called `displayReicpes` will will take in the array of recipes, and inside of that function we will generate the HTML to display the recipes.

How will see pass the recipes array from the `handleSubmit`? If you log `recipes`, you will see that it actually return an object and the recipes array lives on the `results` property of the `recipes` object. 

So we can pass the array like so `displayRecipes(recipes.results);`. 

Within `displayRecipes` will will loop through each recipe and return some generated HTML. We will return the title, ingredients and a thumnail if there is one (which we will check for with a conditional). 

This might look a little confusing because you can nest template tags within template tags as deep as you want.

Here we have one template tag and inside of that template tag we can run javascript logic, and also return another template tag which in turn will have template tags inside of them. 

```
function displayRecipes(recipes) {
  console.log("Creating HTML");
  const html = recipes.map(
    (recipe) => `<div class="recipe">
      <h2>${recipe.title}</h2>
      <p>${recipe.ingredients}</p>
      ${recipe.thumbnail &&
        `<img src="${recipe.thumbnail}" alt="${recipe.title}"/>`}
    </div>`
  );
  recipesGrid.innerHTML = html.join("");
}
```

![](@attachment/Clipboard_2020-05-24-20-17-04.png) 28:24

As you can see, for each recipe we had returned we have some HTML generated for them.

Now let's go back to our HTML and make a div `<div class="recipes"></div>`. Inside of that div, we will put a grid of recipes. 

Let's start by grabbing the div.

```
const recipesGrid = document.querySelector('.recipes'); 
```

At the bottom of displayRecipes, let's set the innerHTML of the recipes grid to be equal to our array of html, which we will join. If we didn't join it, there would be a comma between each of the elements. 

```
recipesGrid.innerHTML = html.join('');
```

When you refresh the page, the HTML should look something like this;

![](@attachment/Clipboard_2020-05-24-20-20-43.png) 29:21

![](@attachment/Clipboard_2020-05-24-20-21-00.png)29:32

For each item, we created a div, added the title and the ingredients and then some of them have images.

Now le'ts add the following css to make it look better:


```
.recipes {
   display:grid;
   grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
   grid-gap:20px
}

.recipe {
   border: 1px solid rgba(0, 0,0,0.1);
   padding: 20px;
}
```

One thing we forgot to add was linking to the actualy recipe with an `href`. 

Let's go back to our `displayRecipes` function and modify it like so:

```
function displayRecipes(recipes) {
  console.log("Creating HTML");
  const html = recipes.map(
    (recipe) => `<div class="recipe">
      <h2>${recipe.title}</h2>
      <p>${recipe.ingredients}</p>
      ${recipe.thumbnail &&
        `<img src="${recipe.thumbnail}" alt="${recipe.title}"/>`}
      <a href="${recipe.href}">View Recipe →</a>
    </div>`
  );
  recipesGrid.innerHTML = html.join("");
}
```

The one issue we have it not running on page load. Why is that?  If you look, a lot of our logic is tied to the submit event, so we can't just run that on page load unless we were to fake a submit event. 

To solve that issue, we will make another async function called `fetchAndDisplay` which will take in a parameter `searchTerm`. 

We will take all the logic from the `handleSubmit` function below where wew log the search term and we will move it to `fetchAndDisplay`. We will modify the code slightly amd also add a call in `handleSubmit` to `fetchAndDisplay` which will take in the search term as a parameter. 

One thing we need to change is that we no longer have access to the `el` function in `fetchAndDisplay`. The element would need to be either globally scoped or passed the function. Luckily we do have the form globally scoped. 

```
async function handleSubmit(event) {
  event.preventDefault();
  const el = event.currentTarget;
  console.log(form.query.value);
  fetchAndDisplay(form.query.value);
}

async function fetchAndDisplay(query) {
  // turn the form off
  form.submit.disabled = true;
  // submit the search
  const recipes = await fetchRecipes(query);
  console.log(recipes);
  form.submit.disabled = false;
  displayRecipes(recipes.results);
}
```

Now we need run it on pageLoad. We will do that by replacing the last line of code from `fetchRecipes("pizza");` to `fetchAndDisplay('pizza');`.

Now if you refresh the page, you will see it is running on pageload with the default term "pizza" and if you type in another search term and hit submit, it will work. 

That is the basics. It would be an interesting to take this exercise even further and have it so people could have an input box for ingredients and that would get passed along for the ride. 


---
## 76 - Dad Jokes

























---
## 77 -  Currency Converter
