---
attachments: [Clipboard_2020-05-21-06-40-48.png, Clipboard_2020-05-21-06-50-00.png, Clipboard_2020-05-21-06-53-48.png, Clipboard_2020-05-21-07-04-16.png, Clipboard_2020-05-21-07-05-02.png, Clipboard_2020-05-21-07-05-42.png, Clipboard_2020-05-21-07-10-24.png, Clipboard_2020-05-21-07-10-55.png, Clipboard_2020-05-21-18-09-08.png, Clipboard_2020-05-21-18-22-56.png, Clipboard_2020-05-21-18-29-13.png, Clipboard_2020-05-21-18-35-48.png, Clipboard_2020-05-21-18-38-59.png, Clipboard_2020-05-21-18-47-00.png, Clipboard_2020-05-21-18-47-30.png, Clipboard_2020-05-21-18-48-38.png, Clipboard_2020-05-21-18-48-54.png, Clipboard_2020-05-21-18-50-37.png, Clipboard_2020-05-22-07-49-00.png, Clipboard_2020-05-22-07-54-59.png, Clipboard_2020-05-22-07-59-32.png, Clipboard_2020-05-22-08-10-11.png]
title: 'Module 13: Ajax and Fetching Data'
created: '2020-05-21T10:25:44.675Z'
modified: '2020-05-22T12:18:26.572Z'
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

 Now let's fetch some data. If we refresh the page and go to our dev tools to see what we are working with, you will see we get an error

 4:36














---
## 76 - Dad Jokes

























---
## 77 -  Currency Converter
