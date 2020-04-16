---
attachments: [Clipboard_2020-04-13-18-40-09.png, Clipboard_2020-04-13-18-42-05.png, Clipboard_2020-04-13-18-44-15.png, Clipboard_2020-04-13-18-47-12.png, Clipboard_2020-04-13-18-51-19.png, Clipboard_2020-04-13-19-54-31.png, Clipboard_2020-04-13-20-01-24.png, Clipboard_2020-04-13-20-03-31.png, Clipboard_2020-04-13-20-04-13.png, Clipboard_2020-04-13-20-05-28.png, Clipboard_2020-04-13-20-09-22.png, Clipboard_2020-04-13-20-11-27.png, Clipboard_2020-04-13-23-22-05.png, Clipboard_2020-04-13-23-23-16.png, Clipboard_2020-04-13-23-26-57.png, Clipboard_2020-04-13-23-31-21.png, Clipboard_2020-04-13-23-32-58.png, Clipboard_2020-04-13-23-33-14.png, Clipboard_2020-04-13-23-37-28.png, Clipboard_2020-04-13-23-37-32.png, Clipboard_2020-04-13-23-38-35.png, Clipboard_2020-04-14-07-39-08.png, Clipboard_2020-04-14-07-41-24.png, Clipboard_2020-04-14-07-45-20.png, Clipboard_2020-04-14-07-46-49.png, Clipboard_2020-04-14-07-51-17.png, Clipboard_2020-04-14-08-01-39.png, Clipboard_2020-04-14-08-02-45.png, Clipboard_2020-04-14-19-02-38.png, Clipboard_2020-04-14-19-04-36.png, Clipboard_2020-04-14-19-07-49.png, Clipboard_2020-04-14-19-11-00.png, Clipboard_2020-04-14-19-12-41.png, Clipboard_2020-04-14-19-14-18.png, Clipboard_2020-04-14-19-18-55.png, Clipboard_2020-04-14-19-23-24.png, Clipboard_2020-04-14-19-25-05.png, Clipboard_2020-04-14-19-29-46.png, Clipboard_2020-04-14-20-34-12.png, Clipboard_2020-04-14-20-54-20.png, Clipboard_2020-04-14-20-54-24.png, Clipboard_2020-04-14-20-59-30.png, Clipboard_2020-04-14-21-10-56.png, Clipboard_2020-04-14-21-11-50.png, Clipboard_2020-04-14-21-13-24.png, Clipboard_2020-04-14-21-22-51.png, Clipboard_2020-04-14-21-28-18.png, Clipboard_2020-04-14-21-31-12.png, Clipboard_2020-04-14-21-32-56.png, Clipboard_2020-04-14-21-33-49.png, Clipboard_2020-04-14-21-35-10.png, Clipboard_2020-04-15-07-39-54.png, Clipboard_2020-04-15-07-40-47.png, Clipboard_2020-04-15-07-43-24.png, Clipboard_2020-04-15-07-50-19.png, Clipboard_2020-04-15-08-25-01.png, Clipboard_2020-04-15-08-29-27.png, Clipboard_2020-04-15-08-35-08.png, Clipboard_2020-04-15-17-03-17.png, Clipboard_2020-04-15-17-04-40.png, Clipboard_2020-04-15-17-10-33.png, Clipboard_2020-04-15-17-54-18.png, Clipboard_2020-04-15-17-57-15.png, Clipboard_2020-04-15-17-59-42.png, Clipboard_2020-04-15-18-07-54.png, Clipboard_2020-04-15-19-16-07.png, Clipboard_2020-04-15-19-31-55.png, Clipboard_2020-04-15-19-34-03.png]
title: 'Module 9: Gettin'' Loopy'
created: '2020-04-13T22:24:51.247Z'
modified: '2020-04-16T00:08:24.284Z'
---

# Module 9: Gettin' Loopy

## 49 Looping and Iterating - Array .forEach

Let's talk about looping and iterating. There are a few different ways to loop in Javascript and we will cover them all.

The most common way you are going to loop over something in javascript is looping over an array. Most of the looping also works the exact same way. 

We use a method that lives on our array, and we pass it a callback, exactly like we did in the previous video. The callback function will run once for every item in the array, giving us access to each individual item.

Open up the `array-looping-methods-START.html` file, which contains all the practice data we will be using for these exercises. Most of it is the same as the last video with the addition of a students array.

```
 const toppings = ['Mushrooms ', 'Tomatoes', 'Eggs', 'Chili', 'Lettuce', 'Avocado', 'Chiles', 'Bacon', 'Pickles', 'Onions', 'Cheese'];
```

If you wanted to loop out over every single one of the toppings in th array and log them to the console, or display them to the user, the very basic loop we have is the `.forEach()`. You should recognize it from previous exercises we did when we were adding event listeners to multiple elements.

What we do is we take toppings and use the `forEach` method on it, passing it a callback function that will run once for each item in the array. We can define our function outside or inline. 

```
function logTopping(topping){
  console.log(topping);
}
toppings.forEach(logTopping)
```

![](@attachment/Clipboard_2020-04-13-18-40-09.png) 10:06

If you refresh the page, you will see that we are logging every single one of the toppings as we loop over them. 

One thing Wes likes to do is throw a debugger into the foreach and take a look at the dev tools. Modify the code like so to add the debugger:

```
function logTopping(topping){
  console.log(topping);
  debugger;
}
```

When you refresh the HTML page, the debugger should open once it hits the first item in the array. 

![](@attachment/Clipboard_2020-04-13-18-42-05.png) 9:52

As you can see, the debugger is in paused state. We have access to the callstack, what function we are in, in our case it tells us we are in `logTopping`. 

Below it tells us what the `topping` variable is equal to which is "Mushrooms". It also tells us the value of the `this` variable which is equal to the Window. 

If you click the symbol shown in this image twice: ![](@attachment/Clipboard_2020-04-13-18-44-15.png) 9:24 
it runs again. Now we have are on thet "Tomatoes" item. You can click all the way through the array. 

As you know, we can also inline the function like shown below and it will give us the exact same thing.

```
toppings.forEach(topping => {
  console.log(topping);
})
```

One thing you might be having trouble with is where is this `topping` variable shown highlighted below is coming from? You may be wondering if it's a special keyword because it is a singular of toppings which is the name of the variable that holds the `toppings` array. 

![](@attachment/Clipboard_2020-04-13-18-47-12.png) 8:25

If you remember back to when we learned about arguments and placeholders we said that arguments were the actual values and the parameters were the placeholders.

When we define the function, we put a placeholder, a **parameter** in there, and then when the foreach loop is called, javascript will slot the appropriate array item value into our parameter variable, whatever we may have called it.

To capture the argument, we simply define the function with a parameter. How do we know that? We can look at the `forEach()` docs on MDN. 

![](@attachment/Clipboard_2020-04-13-18-51-19.png) 4:30 / 7:22

In our case, we chose to name the currentValue parameter `topping`. 

We also have the ability to get the index and the array, so let's take a look at what that looks like. Modify the code like so:

```
function logToppping(topping, index, array){
  console.log(topping,index, array);
}
toppings.forEach(logTopping);
```

When you refresh the HTML page and open the console, you will see that for each item in the array, the actual item was logged, the index and also the original array. 

![](@attachment/Clipboard_2020-04-13-19-54-31.png) 4:52

Why would you need to pass the original array? Because  if you need to grab something from the original array, you can. 

Let's do a quick example where we have to loop over each topping and:
 - log the topping
 - log the next topping if there is one
 - log the previous topping if there is one
 - if it's the last item in the array, log "goodbye"

The first one is easy, you simply add `console.log(topping)`. 

Let's do the next topping. We have the index already and the original array, which we will rename because `array` is a bad parameter name. We also won't name it `toppings` because we already have a `toppings` array that lives outside of this function. Let's rename it to `originalArray` instead so now it's `function logTopping(topping,index,originalArray)`.  

So let's add  `console.log(originalArray[index])` and refresh the HTML page. 

![](@attachment/Clipboard_2020-04-13-20-01-24.png) 6:26

So now if we try adding 1 to the index like so `console.log(originalArray[index + 1])` we should get the next one. 

Let's also add a console.log to break up and see when it's looping. Modify the code like so:


```
function logTopping(topping, index, originalArray){
  console.log(topping);
  console.log(originalArray[index + 1]);
  console.log('--------🍕-----');
}
```

When you refresh the HTML page, you should see the following:

![](@attachment/Clipboard_2020-04-13-20-03-31.png) 6:49

If you scroll all the way to the bottom, you will see that when we get to the last one, the next index returns undefined. 

![](@attachment/Clipboard_2020-04-13-20-04-13.png) 6:57

What we can do to check whether the next topping exists or not is add the following code:

```
const nextTopping = originalArray[index + 1];
if(nextTopping){
  console.log(nextTopping);
}
```

Now if you refresh the page and look at the console, you will see that for the last item, we are not logging the next one because it doesn't exist. 

![](@attachment/Clipboard_2020-04-13-20-05-28.png) 7:22

We can go a bit further and make it a bit easier to understand using a ternary function. 

```
const nextTopping = originalArray[index + 1];
nextTopping ? console.log(nextTopping) : null;
```

That works just the same. Instead of putting null, you could put an empty string, it doesn't matter as long as you put something there. 

Now let's do the previous topping. Let's move the `prevTopping` and `nextTopping` variables to the top of the function and use the ternary operator to console log the previous topping like so:

```
const nextTopping = originalArray[index + 1];
const prevTopping = originalArray[index - 1];

prevTopping ? console.log(prevTopping) : null;
nextTopping ? console.log(nextTopping) : null;
 console.log('--------🍕-----');
```

![](@attachment/Clipboard_2020-04-13-20-09-22.png) 8:25

Now the first and last topping should only have two items logged while all the other items have three items logged.

Next if it's the last item in the array we need to log "goodbye". How can we do that? 

Let's use `.length` on the array and a ternary statement. 

```
index === array.length - 1 ? console.log('Goodbye') : console.log("getting the next topping");
```

![](@attachment/Clipboard_2020-04-13-20-11-27.png) 9:21

Let's break down what we did exactly in that last example. Sometimes it helps to make it more readable if you put part on it's own line like so:

```
index === originalArray.length - 1
? console.log("Goodbye")
: console.log('Getting the next topping');
```

So the condition we are checking is `index === originalArray.length - 1`. We also have access to the index of the currrent item in the `index` variable, and we can get the index of the last item in the array by doing `originalArray.length - 1`. So all this line does is check whether the current index matches the last index. 

If it does, we log "goodbye" and if it doesn't, we log "getting the next topping". 

You could use an if statement instead of the ternary statement, it would work just as well.

We can also use the && hack we learned about earlier. We can say

```
index === originalArray.length && console.log('Goodbye');
```

Why does that work? Because if the first statement is true, it will keep going for the next one and if it is false, it will shortcircuit and never get to the second one. That is what we referred to as abusing conditionals in our previous videos.

That wraps up the `forEach` method. It is a bit different than the other looping methods because it doesn't return any values. Notice how when we loop over each of our items we don't store our results in a variable like below

```
const result = toppings.forEach(logTopping);
```

When you loop over an array with `forEach` it doesn't actually return anything to you. It goes off and does some work for every item that is in that array. 

Let's see how that is different from what Wes likes to call the 'Big Three' which are: 
- Map
- Filter
- Reduce

---

## 50 - Looping and Iterating - Mapping

In the previous lesson we learned about `forEach`, which is useful when you want to loop over some data and do something with each piece of data. Whether that something is display the data on a page, log the value, or attaching an event listener to each item, those are often referred to as things called **side effects**. 

Side effect is when you are inside of a function and you reach outside of that function to do something else. 

While side effects are totally fine, because at some point you do need to do things that reach outside the function, there are a whole slew of other types of loops that are simply taking in data, doing something with that data and then returning the data that has been modified, massaged or transformed in some way. 

That is where we get into `map`, `filter`, and `reduce`. 

We have already looked at one example of `filter` and that is `find`, where you take in an array and return one thing. That is a transformation of that data and are often referred to as **pure functions**. 

Pure functions take in data, they return data, they always work exactly the same way given the data that's inputed, it returns the exact same thing. They don't reach outside themselves to do that. 

Let's talk about `map`. Map is like a machine in a factory. It takes in data, performs an operation and then spits it out on the other side.

`map` will always produce the same length of the array as it starts with. 

Lets go into a little example right now. 

First add `console.clear()` to the script tag to clear all the toppings work we did. 

Wes loves the analogy of a machine, taking in data, performing an operation and then spitting it out on the other side. You can think of like a toy machine in a factory which adds one arm then the other arm then a leg. 

Let's do a really simple example. 

We have this array `const faces = ['😃', '🤠', '🤡', '🤑', '😵', '🌞', '🐶', '😺'];`. 

Let's create some functions that will map over each one. 

So if we make a function called `addArms`, it takes in a face, and from that let's return an emoji:

```js
function addArms(face){
  return `👋${face} 👋`;
}
```

That is just a regular function like we have written a hundred times by now. You can play with it in the console. It's silly, but it works.

![](@attachment/Clipboard_2020-04-13-23-22-05.png) 3:01

Now what we can do is we can take our array of faces and add arms to all of them, and this how that works. 

```
const toys = faces.map(addArms);
console.log(toys);
```

![](@attachment/Clipboard_2020-04-13-23-23-16.png) 3:36

As you can see, what was returned to us is an array of exactly the same length as we put it in, so if the array had 8 things, it will have 8 things when it's returned, there is no way to return more or less items with `map`. You simply take in something and return something else. 

One other simple example is lets say you have 

```
const fullNames = ['wes','kait','poppy'].map(name => `${name} bos`);
console.log(fullNames);
```

![](@attachment/Clipboard_2020-04-13-23-26-57.png) 4:33

We could do multiple transforms. 

Let's make the code above into a function. 

```
function bosify(name){
  return `${name} Bos`;
}

const fullNames = [ 'wes', 'kait', 'poppy'].map(bosify);
```

![](@attachment/Clipboard_2020-04-13-23-31-21.png) 5:17

Now the first names don't have capitals so let's make another function called `capitalize` which takes in a word. 

You can access each character of a word using an index. 

For example `'wes'[0]`, `'wes'[1]`, `'wes'[2]` will return the following..

![](@attachment/Clipboard_2020-04-13-23-33-14.png) 5:55
 
So we can capitalize the first letter of word like so: 

```
function capitalize(word){
    return word[0].toUppercase();
}
```

Let's try that so far. So now we are going to chain our maps like so:

```
const fullNames = [ 'wes', 'kait', 'poppy'].map(capitalize).map(bosify);
```

You can chain as many maps as you want because each returns a new array until it reaches the last one. 


A nice way to format that to make it easier to read is to put each map on its on line. You still only put one semi colon `;` at the end of the chain, not on each line. 

```
const fullNames = ['wes','kait','poppy']
  .map(capitalize)
  .map(bosify);
console.log(fullNames);
```

![](@attachment/Clipboard_2020-04-13-23-37-32.png) 6:56

As you can see, that does not return the whole word. Let's fix that.

We will use slice to return the words from index 1 to the end of the word like so:

```
function capitalize(word){
    return word[0].toUppercase() + word.slice(1);
}
```

![](@attachment/Clipboard_2020-04-13-23-38-35.png) 7:12

As you can see, that works. 

Let's change that so instead of using the `+` operator, we use backticks because it's better to reserve adding for numbers. 

Modify it like below. 

```js
function capitalize(word){
    return `${word[0].toUppercase()}${word.slice(1)}`;
}
```

![](@attachment/Clipboard_2020-04-14-07-39-08.png) 7:%6

Map will always take in an item, do some work with it and then return a new value. 

The same thing works with numbers. 

```
const orderTotals = [342, 1002, 523, 34, 634, 854, 1644, 2222];
```

Lets say we want to add tax to all items in the `orderTotals` array. 

Watch what happens if for every single item in our map, we just return one. 

```
const orderTotalsWithTax = orderTotals.map(total => 1);
```

![](@attachment/Clipboard_2020-04-14-07-41-24.png) 8:32

As you can see, all the items in the array have now been turned into 1. Why? Because whatever you return from your map function will replace whatever was initially in your map function.

It is not mutable. What that means is our `orderTotals` are still there. The new array has the updated value. So back to our example, to add the tax to every item in the order total we will do

```
const orderTotalsWithTax = orderTotals.map(total => total * 1.13);
```

![](@attachment/Clipboard_2020-04-14-07-45-20.png) 9:09

As you can see, we now have our values with tax added to them. 

Wes finds map to be extremely helpful.

There is one really silly example that Wes wants to show us. There is this thing on twitter where you can make cowboy bodies out of emojis.

 ![](@attachment/Clipboard_2020-04-14-07-46-49.png) 9:41

```
function attachBody(face, body) {
  return `
      ${face}
　　　　　${body.repeat(3)}
　　　　 ${Array(3).fill(body).join(' ')}
　　　👇🏽　 ${body.repeat(2)}　👇🏽
    ${Array(2).fill(body).join('   ')}
    ${Array(2).fill(body).join('   ')}
　　　　　👢　　👢
  `
}

faces.map(face => attachBody(face, '🍟')).forEach(body => console.log(body))
```

What Wes has done here is he has taken our faces array that we used earlier, looped over each one and passed the face as an argument along with whatever he wants to body to be made up of. That will return us a new array and then for each of those we just console log them. 

The `attachBody` function simply takes in a face, and then whatever the body is made up of and we use backticks so we can use multiple lines and then it fills in the variables. So it fills in the face variable, then the body variable repeats three times.  

One thing Wes hasn't shown us yet is `repeat`. You can take a string and call repeat on it and javascript will repeat that however many times you like, like so:

```
'x'.repeat(199);
```

![](@attachment/Clipboard_2020-04-14-07-51-17.png) 10:46

Another thing Wes hasn't shown us yet is `Array.fill()`.  

With `Array(3)`, it will create three empty spots in an array, much like `Array.from()`. 

![](@attachment/Clipboard_2020-04-14-08-01-39.png) 10:53

However if you want to fill them with the exact same thing, you can use `Array(3).fill('x')`. That is a bit quicker than `Arrau.from` and map function that we looked at. 

![](@attachment/Clipboard_2020-04-14-08-02-45.png) 11:09

In our `attachBody` function, we are just filling it with an emoji and then calling `.join(' ')` with a space separator in it. That gives us the actual body of the person.

`.map` can be used with any type of data. So far we have looked at examples with strings and numbers but more often than not, you will actually have an array of objects that comes back from the API. 


Let's take a look at an example with the `peoples` array.

```
const people = [
  {
    birthday: "April 22, 1993",
    names: {
      first: "Keith",
      last: "Buckley",
    },
  },
  {
    birthday: "January 3, 1975",
    names: {
      first: "Larry",
      last: "Heep",
    },
  },
  {
    birthday: "February 12, 1944",
    names: {
      first: "Linda",
      last: "Bermeer",
    },
  },
];
```

Each person is signified by an object, and each person has a birthday, and a names object which has a nested first and last property inside of that.

That data is okay but it's not in the format that we need. That happens all the time when you are working with APIs. 

So what we have to do is take in that data, "massage" it a little bit and then return the new formatted data that we want. Let's go ahead and do that. 

```
const cleanPeople = people.map(function(person){
  console.log(person);
})
```

 We are using an inline function which takes in an parameter of `person` (which will be each item in the array as it loops through). We are logging the person. 

 It is fine to log within a `map` function, just don't ever do things like updating the dom inside of a map function. That is what a `forEach` is for.

 The first thing we need this function to do is get the person's birthday, and then figure out how old they are. Then we want to return their full name and birthday in an object.

So first we have to get their birthday, which is stored in a string like "February 12, 1944". That is not very helpful to us because when you want to work with dates in Javascript, it has to be changed over to what is called a Javascript date.

Wes will show us how we can do that within our inline map function like so:


```
const cleanPeople = people.map(function(person){
  console.log(person);
  const birthday = new Date();
})
```

If you don't pass a date when you create a date in Javascript like so `new Date()`  it will give you the current date time like so:

![](@attachment/Clipboard_2020-04-14-19-02-38.png) 14:17

The date you see in the console is the date that Wes is recording the video. 

If you do however pass `new Date()` a string of a date like we have access to with `person.birthday`, it will return that date. 

```
const cleanPeople = people.map(function(person){
  console.log(person);
  const birthday = new Date(person.birthday);
  console.log(birthday);
})
```

![](@attachment/Clipboard_2020-04-14-19-04-36.png)14:37

As you can see, for each person we log the person and then it actual logs a true javascript date.

HOT TIP: Use `console.dir(birthday)` to see all the methods that exist on a Date object.

If the date that you pass to the `new Date()` function doesn't have a time value, it will default to midnight. 

Now that we have the birthday, we want to figure out how old the person is. In order to do that, we need to know what is right now. 

Modify our inline function like so to capture the current date in the variable `now` like so: 

```
const cleanPeople = people.map(function(person){
  const birthday = new Date(person.birthday);
  const now = new Date();
  console.log(birthday,now);
})
```

![](@attachment/Clipboard_2020-04-14-19-07-49.png) 15:20

As you can see we have three different dates showing up. 

There are a number of methods on a Date in javascript that allow you to work with it. 

What Wes likes to do when comparing dates or trying to figure out how much time is in between two dates, is to change them into **timestamps**. 

Let's open up the console and run the code below, you will see that we get a number returned to us.

```
const now = new Date();
now.getTime();
```

![](@attachment/Clipboard_2020-04-14-19-11-00.png) 15:48

That number might look random but it is actually not random at all. That is the number of milliseconds since January 1, 1970. That is the time when they said okay, this is when date starts. Any dates that are negative, go back from that time and any dates that are positive go forward for that time. 

There is actually a shortcut to get the timestamp and that is using `Date.now()`. If you try running that a few times in the console, the number should change each time.

![](@attachment/Clipboard_2020-04-14-19-12-41.png) 16:17

If you ever have one of these timestamps, you can go to the website https://epoch.now.sh. 

![](@attachment/Clipboard_2020-04-14-19-14-18.png) 16:36

This website allows you to convert any date in the future or in the past to a timestamp. Javascript deals with miliseconds so you want to always work with that. 

It also allows you to do the opposite. It will take in a timestamp and convert it back to a regular date for you. 

So back to our inline map function, we don't want to just grab the persons birthday and convert it to a date, we want to convert it to a full blown timestamp. 

We can do that by chaining the `getTime` method to our `new Date(person.birthday).getTime();`. 

For the `now` variable, we will use `Date.now()` to get the timestamp instead of `new Date()`.  `.now()` is a static method because it lives on the `Date` object.

```
const cleanPeople = people.map(function(person){
  const birthday = new Date(person.birthday).getTime();
  const now = Date.now();
  console.log(birthday,now);
})
```

Now we want to find out what the difference is between the two like so: 

```
const age = now - birthday;
console.log(age);
```

![](@attachment/Clipboard_2020-04-14-19-18-55.png) 18:12

That is how old each person is in miliseconds. We need to convert it into years. We need to do some math for that. Let's ask ourselves how many miliseconds in a year. We know there are 1000 miliseconds in a second, there is 60 seconds in a minute, there is 60 minutes in an hour, there are 24 hours in a day and 365 days in a year.

1000 x 60 x60 x 24 x 365 = 31536000000

There are other ways to do dates that will account for leap years and all that. There are whole libraries out there like the date functions library date-fns. Those libraries provide you with a whole bunch of robust tools for working with dates. 

So we will take our age calculation timestamp and divide it by that number like so:

```
const cleanPeople = people.map(function(person){
  const birthday = new Date(person.birthday).getTime();
  const now = Date.now();
  const age = now - birthday / 31536000000;
  console.log(age);
})

```

![](@attachment/Clipboard_2020-04-14-19-23-24.png) 19:22

We have those decimals and what we will do is just take the lower bound of their number because if they haven't hit their next birthday yet, you would say you are 26 years old. 

How do we take the lower bound of any number? It's not round because you don't round up to say how old you are. You take the lower bound with `Math.floor`. 

Modify the code like so:

```
const age = Math.floor(now - birthday / 31536000000);
```

![](@attachment/Clipboard_2020-04-14-19-25-05.png) 19:52

Now that we have their birthday and figured out how old they are, we now want to return their full name and birthday in an object.

To do this we will simply return an object from our inline function that has a property of `age `which is equal to our `age` variable, and then the `name` property will be the person's last and first name variables combined using interpolation as shown below. 


```
const cleanPeople = people.map(function(person){
  const birthday = new Date(person.birthday).getTime();
  const now = Date.now();
  const age = Math.floor(now - birthday / 31536000000);
  console.log(age);
  return {
    age: age,
    name: `${person.names.first} ${person.names.last}`,
  }
})
```

Note: as mentioned before, if the property is the same name as the variable, we could have returned the object like so:
```
 return {
    age,
    name: `${person.name.first} ${person.name.last}`,
  }
```

They both work the exact same way.

Now let's console.table our `cleanPeople` like so:

```
console.table(cleanPeople);
```

![](@attachment/Clipboard_2020-04-14-19-29-46.png) 21:16

As you can see we have everyones name and age. 

So once again, that is what Map does. It takes in some data that doesn't look exactly how you like it. You do a bunch of data massaging and then spit it out the other end. 

---

## 51 - Looping and Iterating = Filter, Find and Higher Order Functions

You can skip this lesson if you feel confident with your knowledge of `filter` and `find` because we have already covered that a few times. Wes just wants to have a video specifically dedicated to it so we can come back and refer it at a later time conveniently. 

Let's continue from the example in our previous lesson. We created an array `cleanPeople`.  Let's work with that. 

![](@attachment/Clipboard_2020-04-14-20-34-12.png) 00:25

Very often you will find yourself in a situation where you either need to find one person in that or you want to filter the list down to be a subset of it. 

Let's say we want to find people who are over 40 years old. We can use `.filter()` for that. The way filter works is you loop over every single item in an array, and you either say yes, true or no, false. If you return true that item will be in the array subset, if you return false it will out that item from the array that is returned.

```js
const over40 = cleanPeople.filter(function(person){
  if(person.age > 40 ){
    return true;
  }
  else {
    return false;
  }
})
console.table(over40);
```

That is the verbose way to write it, which Wes is using just to show us how it works.

![](@attachment/Clipboard_2020-04-14-20-54-24.png) 1:39

As you can see, we now have only a subset of the original array. 

Now let's refactor the function above to make it more concise.

How Wes would approach it is he would look at the condition within the filter function. If the condition is met, we will return true. That means there is no need for an else because anything that comes after the condition will only run if the condition is true. So that else is unnecessary.

```
  if(person.age > 40 ){
    return true;
  }
  return false;
}
```

Since the condition evaluates to true or false, we can just return the condition like so 

```
const over40 = cleanPeople.filter(function(person){ return person.age > 40});
```

We can make it an arrow function like so:

```js
const over40 = cleanPeople.filter((person) => { return person.age > 40});
```

We can go one step further and make it an implicit return and take off the parameter parenthesis like so:

```js
const over40 = cleanPeople.filter(person => person.age > 40);
```

If there ever is a situation where we call this filter method on an array with no people over 40 in it, it will just return to us an empty array. ![](@attachment/Clipboard_2020-04-14-20-59-30.png) 3:29

 If you wanted to check if there were any people over 40 in this case you could use the following code:

 ```
 if(over40.length){
   console.log('There are some people over 40');
 }
 ```

That is how filter works. 

`.find()` works the exact same way except that find only finds one item in the array and returns it whereas filter will always return to you all of the items that match. 

`.filter()` will always return an array

`.find()` will always return the item that you want. 

Let's use the `students` array for our find example. 

Here is what that array looks like:

```
const students = [
  {
    id: "11ce",
    first_name: "Dall",
    last_name: "Puckring",
  },
  {
    id: "2958",
    first_name: "Margarete",
    last_name: "Brandi",
  },
  {
    id: "565a",
    first_name: "Bendicty",
    last_name: "Woodage",
  },
  {
    id: "3a16",
    first_name: "Micki",
    last_name: "Mattes",
  },
  {
    id: "f396",
    first_name: "Flory",
    last_name: "Gladeche",
  },
  {
    id: "de5f",
    first_name: "Jamill",
    last_name: "Emilien",
  },
  {
    id: "54cb",
    first_name: "Brett",
    last_name: "Aizikowitz",
  },
  {
    id: "9135",
    first_name: "Lorry",
    last_name: "Smallman",
  },
  {
    id: "978f",
    first_name: "Gilly",
    last_name: "Flott",
  },
];
```

Now let's say we want to find a student with the `id` of `565a`.


```
const student = students.find(student => );
```

The code above is incomplete, but one weird thing worth pointing out is that we are naming the variable that we are storing the item in as `student` but we are also naming the individual loop a student. Is that okay? 

It is allowed because the student which is a parameter of the `.find()` loop is scoped to within that function. It is confusing however so it's often better to change it to something else. We will name the parameter `stud` instead like so:

```
const student = students.find(stud => stud.id === '565a');
console.log(student);
```

![](@attachment/Clipboard_2020-04-14-21-10-56.png) 5:19 

As you can see, the correct student record is returned. If that didn't match anything, what would we find? We would get undefined. You always want to check if something got found. 

![](@attachment/Clipboard_2020-04-14-21-11-50.png) 5:25

As you may have noticed, the `find` method did not return an array of students to us, it returns to us an object which is the student itself. 

We could just swap the `.find()` to a `.filter()` like so:

```
const student = students.filter(stud => stud.id === '565a');
console.log(student);
```

![](@attachment/Clipboard_2020-04-14-21-13-24.png) 5:41

As you can see, that returns to us an array of one item. That is the different between `.filter()` and `.find()`, everything else is exactly the same.

One neat thing that we could do is make an external function and then pass that in, like so:

```
function isStudent(student){
  return student.id === '565a';
}
const student = students.find(isStudent);
console.log(student);
```

Now that is a little bit weird. Why would we write a function that is hardccoded to a specific id? It's more likely that we will be looking for a student with a specific id. 

What we can do is wrap that in another function called `findById`, which takes in one parameter: `id` which returns another function like so:

```
function findById(id){
  return function isStudent(student){
    return student.id === id;
  }
};
```

This is called a **high order function** or a **higher order function**. It is a function that will return another function. 

Now we can simply replace the method we pass to `.find()` like so:

```
const student = students.find(findById('56a'));
```

`findById('56a')` will generate a new function that is coded to find the id that we are looking for. 

![](@attachment/Clipboard_2020-04-14-21-22-51.png) 7:22

It still finds the right person. So that is a little more flexible.

Even further we can make another function that is even more flexible because let's say you run into a scenario where the object has a lot of properties. Are you going to create a separate function called `findByFirstName` and then `findByLastName` and then all the other properties? 

We can actually modify the function to make it even more flexible. We will start with a new function instead. That function takes in two things: the property and then the property we are looking for. It will return a function which is the looping function. 

We are not going to return if the id is equal to the id, we are going to return if the student property is equal to the property value we are looking for. 

```
function findByProp(prop, propWeAreLookingFor){
  return function isStudent(student){
    return student[prop] === propWeAreLookingFor;
  }
}
```

Now that might be a little confusing to you. Let's go over how it works.

```
const student = students.find(findByProp('id', '565a'));
```

What that does is it makes the function really flexible. The code we added above still works, but we can make other student where the first name property is equal to  'Micki'. 


```
const student = students.find(findByProp('id', '565a'));
const student = students.find(findByProp('first_name', 'Micki'));
console.log(student);
console.log(student2);
```

![](@attachment/Clipboard_2020-04-14-21-31-12.png) 9:17

Let's go over the function one more time. The `findByProp` function takes in a prop as the first parameter and `propWeAreLookingFor` as the second parameter. What we mean by that is the first parameter takes in the key, and the second parameter takes in the value we are matching the property against.

![](@attachment/Clipboard_2020-04-14-21-32-56.png) 9:39

In the image above, the text that is selected is the property `last_name` . It is the property key. 

![](@attachment/Clipboard_2020-04-14-21-33-49.png) 9:40

The property value for the `last_name` property for the student shown above is `Aizikowitz`. 

So our function takes in a property and a value, and then it will look in each object for whatever property you specified is equal to whatever value you specified.

![](@attachment/Clipboard_2020-04-14-21-35-10.png) 9:55

The reaosn we have to use square brackets and not the dot notation in the code highlighted in the image above is because the property that we are looking for is being passed in as an argument to the function. 

This is a bit advance so don't feel too let down if you feel a bit confused. It took Wes years to understand the benefit of a function like we just made with `findByProp`. 

---

## 52 - Looping and Iterating - Reduce 

Let's add a `console.clear()` to the bottom of the script section in the HTML page we have been using for the last few examples. 

So far we have covered `.map()`, where you take in items and return transformed items, and `.filter()` where you take in items and return a subset of those items. 
`.reduce()` is probably one of the trickier array methods to understand because it does so muc and there are a couple of different use cases for it. 

So what does it do? It takes in an array of data (just like `map` and `filter`) and it will return to you a result of or a single value. 

Now what does that 👆exactly mean? Let's do an example to demonstrate. 

```
const orderTotals = [342, 1002, 523, 34, 634, 854, 1644, 2222];
```

We want to take the ordersTotal array and add up all the numbers in the array. 

Maybe one way you could approach it is to set a let variable to zero and then use a `forEach()` to loop over each item and add to the total. 

```js
let total = 0;
orderTotals.forEach(singleTotal => {
  total = total + singleTotal;
})
console.log(total);
```

![](@attachment/Clipboard_2020-04-15-07-39-54.png) 1:40

As you can see, that does work. 
However, is that the best way to add up a bunch of things? No, it is not. 

![](@attachment/Clipboard_2020-04-15-07-40-47.png) 1:52

We have the callback method within our `forEach`, which relies on an external variable being made. So we have sort of reached outside of it. That is what is referred to as a **side effect** which is where you update a variable that exists outside of the function. 

`.reduce()` will allow us to loop over every single item in that array, and in this case it would allow us to do a running total with those numbers. 

Here are some visualizations that Wes has pulled from online by google image searching "map filter reduce".

![](@attachment/Clipboard_2020-04-15-07-43-24.png) 2:36

In the image above, the language is not javascript but it doesn't matter because each language has some for of those three. 

So in the image above, in the map, it takes in raw materials of cow, potato, chicken and corn and that returns the cooked materials via the cook function. 

The filter will return to you a subset of the original array of what is vegetarian. 

`.reduce()` will take in an array of food and return to you something that is compiled into a smaller version of it.

If you think about making a reduction when you're cooking or making a soup, what you do is you add a whole bunch of stuff to it and then you let it simmer and sort of become one. It is typically reduced down to something that is smaller than the original value that it came from. 

Now we will go through a bunch of use cases for `.reduce()`. We will make a new variable called `allOrders`. We will call `.reduce()` on our `orderTotals` array.

```
const allOrders = orderTotals.reduce();
```

We need a callback function that will be run on each item in the array. Let's call it `tallyNumbers`. It will take in two arguments because that is what the callback function of a reduce method takes. Let's look that up in the MDN docs.

![](@attachment/Clipboard_2020-04-15-07-50-19.png) 4:26

So the two parameters it takes is the **accumulator** and the current balue.
The accumulator is the thing that has been handed to you from the last instance of the loop. The `currentValue` parameter is the current item in the array.

We will name our parameters `tally` and `currentTotal`. Inside of the function we will add a log specifying what the current tally is and what the current total is like so:

```
function tallyNumbers(tally, currentTotal){
  console.log(`The current tally is ${tally}`);
  console.log(`The current total is ${currentTotal}`);
  console.log('--------');
}
const allOrders = ordersTotal.reduce(tallyNumbers);
console.log(allOrders);
```

![](@attachment/Clipboard_2020-04-15-08-25-01.png) 5:31

Now there might be some stuff in the console does not make sense, so let's go through it together. 

The first time the loop runs, the current tally is 342 and the current total is 1002. 
The second time the loop unrs, we get the current tally is undefined and the current value. In fact every time other than the first instance of the loop, `tally` is undefined. 

That is because `reduce()` takes in another argument which is what do you want to start the accumulator at. In our case  we want to start counting at 0 so we pass in 0 like so:

```
const allOrders = orderTotals.reduce(tallyNumbers, 0);
```

![](@attachment/Clipboard_2020-04-15-08-29-27.png) 6:39

So as you can see, in the first loop the tally is 0 and then in the rest it is undefined. 

Now that we got the loop working, we have this problem where everything after the first loop is returning undefined for the tally. That is because of the accumulator parameter, in our case `tally`, that is passed from the previous iteration of the loop. 

So if we were to just return `'WES IS COOL';` from each of the iteration in our loop, the accumulator is going to be equal to that on the next iteration. Modify the `tallyNumbers` function by adding `return 'WES IS COOL'` as shown below. 

```js
function tallyNumbers(tally, currentTotal) {
  console.log(`The current tally is ${tally}`);
  console.log(`The current total is ${currentTotal}`);
  console.log("----------");
  return "WES IS COOL";
}
const allOrders = orderTotals.reduce(tallyNumbers, 0);
```

![](@attachment/Clipboard_2020-04-15-08-35-08.png) 7:18

As you can see, the first time the loop runs, the tally is 0 because we started with an accumulator of 0 and then for all the next instances, our accumulator `tally` is equal to "WES IS COOL" because whatever you return from this function is what the accumulator is equal to. 

So what we really want to do is return the current tally PLUS the current order's total. 


```
function tallyNumbers(tally, currentTotal) {
  console.log(`The current tally is ${tally}`);
  console.log(`The current total is ${currentTotal}`);
  console.log("----------");
  return tally + currentTotal;
}
const allOrders = orderTotals.reduce(tallyNumbers, 0);

```

![](@attachment/Clipboard_2020-04-15-17-03-17.png) 7:49

In the console above, as you can see we start with 0 because our accumulator starts at 0 as shown in the highlighted code in the image below. 

![](@attachment/Clipboard_2020-04-15-17-04-40.png) 7:56

If we were to not pass an accumulator, the first loop iteration will take the first two numbers. In our case, that would still work but Wes always like to pass a default value so we know what we are starting with and so we can see what type we are starting with. 

So we start with 0, then the currentTotal is 342. Then in the next iteration, because we have returned 342 from the previous iteration, we are going to start with that as tally variable in the next iteration. We add the current value and return the tally variable to the next iteration and so on.

So, a reduce will loop over items in an array and every single time that you loop over an item in an array, you have an option to return a value which you can use to accumulate values or distill them down into one value.

Now, if we want to total the numbers, we already have them in the `allOrders` variable so we can simply add `console.log(allOrders);` which should return to us 7255.

For the next example, let's look at the `inventory` variable. 

```js
const inventory = [
  { type: "shirt", price: 4000 },
  { type: "pants", price: 4532 },
  { type: "socks", price: 234 },
  { type: "shirt", price: 2343 },
  { type: "pants", price: 2343 },
  { type: "socks", price: 542 },
  { type: "pants", price: 123 },
];
```

It is an array of objects and each object has a `type` and a `price` property on it. 

In this exercise, we need to figure out how many instances there are with type of pants, how many are pants, and how many are socks. We also want to figure out what is the total value of all of the inventory that we have.

You could probably figure out how to calculate the total value form the last exercise, but the other part where we need to count how many instances of something there are, happens all the time in Javascript.

Let's add some code. Let's make a function called `inventoryReducer` which we will pass to `.reduce()` when we call it.  

```
function inventoryReducer(){

}
const inventoryCounts = inventory.reduce(inventoryReducer,);
```


We also need to decide what value we should start with for the accumulator. 
In our case, we want to return an object that looks something like this 👇

```
{
  shirts: 3,
  pants: 2,
  socks: 523
}
```

In order for us to get that, we need to pass an object. We could pass an object like this:

```
const inventoryCounts = inventory.reduce(inventoryReducer, {
  shirts:0,
  pants: 0,
  socks: 0
});
```

That would start everything off at zero. 

However, more often then not, you are not aware of all of the different types that will be coming in so there is no way for you to go in and make a huge list of everything ahead of time. Or -- you might be aware of it and there are 50 different things so it doesn't make sense to do that.

What we will do instead is we will start of with an empty object and then add the keys and set them to one as they appear, otherwise if they already exist, we will increment them by one. 

Here is how you pass an empty object as the accumulator `const inventoryCounts = inventory.reduce(inventoryReducer, {});`

Our reducer takes two things: 
1. our accumulator which we will call `totals`
2. our item which we will call `item`


Let's add a log to our reducer function which logs the item's type like so

```js
function inventoryReducer(totals, item){
  console.log(`Looping over ${item.type}`);
}
```

![](@attachment/Clipboard_2020-04-15-17-54-18.png) 11:54

Inside of the reducer we need to increment the type by 1 and then return the accumulator or return the totals so the next loop can use it. 

To increment the type, let's try the following:

```
function inventoryReducer(totals, item){
  console.log(`Looping over ${item.type}`);
  totals.shirt = totals.shirt + 1; 
  return totals;
}
const inventoryCounts = inventory.reduce(inventoryReducer, {});
console.log(inventoryCounts);
```

![](@attachment/Clipboard_2020-04-15-17-57-15.png) 12:42 

Hm.. shirt is equal to NaN. Why would that be? That is because if you are trying to add one to something that doesn't exist, it will give you NaN (not a number). 

What we can do is check if the shirt already exists on our totals and if it does we increment it by one but if it doesn't, we will set it to zero. 

So what we can try to do is say totals.shirt equals to itself plus 1 or 1 like so

```
totals.shirt = totals.shirt + 1 || 1;
```
Lets try it. 

![](@attachment/Clipboard_2020-04-15-17-59-42.png) 13:17

Why did that work? This is an example of taking advantage of conditionals or abusing conditionals. 

If we were to write that as an if statement, it would look like this:

```
if(totals.shirt){
  totals.shirt = totals.shirt + 1;
}
else {
  totals.shirt = 1;
}
```

Note you can also increment totals.shirt like this `totals.shirt++;` Both work!

So what is happening there is if the property doesn't exist, we first need to add it, and set it to one, and then we can start incrementing it.

In this statement `totals.shirt = totals.shirt + 1 || 1;`, if `totals.shirt + 1` turns out to be NaN, then that is falsy and it will fall back to 1. It's a bit harder to read which in a lot of cases isn't ideal, but it is nice to do it in a one liner. 

Another way we could do it is write 

```
totals.shirt ? totals.shirt + 1 : totals.shirt = 1;
```

So we are checking if `totals.shirt` exists, if it does, we increment it by 1, if it doesn't we create the property and set it to 1. 

Now one thing you may have noticed is we have been hardcoding shirt, which we shouldn't be doing because there are a few differnt types. 

We can change it to a variable lookup item using square brackets like so: 

```
totals[item.type] = totals[item.type] + 1 || 1;
```

![](@attachment/Clipboard_2020-04-15-18-07-54.png) 15:33

As you can see, now our accumulator has the 2 shirts, 2 socks and 3 pants.

Pretty often a reduce can be done in an arrow function, a really quick one. 

In our case, we just want to add up the inventory `price` on each of them. We will start with 0 as our accumulator because we want to add up the total prices. 

```
const totalInventoryPrice = inventory.reduce((acc, item) => acc + item.price, 0);
console.log(totalInventoryPrice);
```

We loop over every single item and then we return the accumulator plus the current item price.

--

## 53 - Looping and Iterating - Reduce Exercise

This lesson is an exercise where you have to use `map`, `filter`, and `reduce` all in one exercise. 

The task is to go to any webpage, like the Mozilla Developer Docs for reduce, copy every single piece of text like Wes is doing in the screenshot below by pressing= Cmd + A and Cmd + C and then counting how many times every letter and number occurs on the page.

![](@attachment/Clipboard_2020-04-15-19-16-07.png) 00:27

Here are a couple of tips:
- first grab all the text
- then convert the text to an array of letters 
- then we need to filter the text to grab only letters and numbers and ignore other text content like parenthesis, question marks, white space etc.
- we want to make sure that whether the letter is uppercase or lowercase, we still only count it once. For example `a` and `A` would could as two "a"s, not one uppercase A and one lowercase a.

This is going to use `filter`, and `reduce` all in one go. 

Open up the file `reduce-challenge.html`. 

The first thing we will do is get the text in there. We will create a variable called `text` and use backticks for the value because we are going to paste the text we copied between the backticks and backticks allow our text to be multi line. 

Note: the text within the `text` variable has been shortened for demonstration purposes in the following code examples. 

```js
const text = `
[0, 1, 2, 3, 4].reduce( (accumulator, currentValue, currentIndex, array) => accumulator + currentValue );
If you were to provide an initialValue as the second argument to reduce(), the result would look like this:
The value returned by reduce() in this case would be 20.

Examples
Sum all the values of an array`;


console.log(text);
```

![](@attachment/Clipboard_2020-04-15-19-31-55.png) 1:48

As you can see, we have over 31.1 KB worth of text. 

How can we convert all of the text into an array of every single letter? You can call `split()` or spread it into an array.

For example we can call split on our `text` variable and pass it an emptry string so that we split it on nothing like so:

```
const everything = text.split('');
console.log(everything);
```

![](@attachment/Clipboard_2020-04-15-19-34-03.png) 2:18

As you see, now we get an array with 15,911 letters that are in it. 

Next we need to deal with ignoring the case when counting letters. There are two ways we can do that, we can either lowercase everything immediately or we could filter the things out for what we want.

If we do lowercase first, we will be unnecessarily lowercasing things that do not have lowercase and uppercase, such as symbols like the question mark ? and numbers etc. 

 However, if we filter first, then our matcher will have to match both uppercase and lowercase.

 Let's get rid of the junk first using `.filter()`. 

 ```js
 const result = everything.filter(char => )
 ```

We pass our filter a `char`, which is an instance of the item from our array, and then we want to filter out any items that are not letters or numbers from a-zA-Z and numbers 0-9. 

So how do we check if a character is from a-z, A-Z or 0-9? We can use a `.match()` function. 

Let's look 

stopped at 3:37
```

```
