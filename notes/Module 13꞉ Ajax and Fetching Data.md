---
attachments: [Clipboard_2020-05-21-06-40-48.png, Clipboard_2020-05-21-06-50-00.png, Clipboard_2020-05-21-06-53-48.png, Clipboard_2020-05-21-07-04-16.png, Clipboard_2020-05-21-07-05-02.png, Clipboard_2020-05-21-07-05-42.png, Clipboard_2020-05-21-07-10-24.png, Clipboard_2020-05-21-07-10-55.png]
title: 'Module 13: Ajax and Fetching Data'
created: '2020-05-21T10:25:44.675Z'
modified: '2020-05-21T11:11:58.140Z'
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

stopeped at 9:00











---
## 75 - CORS and Recipes































---
## 76 - Dad Jokes

























---
## 77 -  Currency Converter
