---
attachments: [Clipboard_2020-04-13-18-40-09.png, Clipboard_2020-04-13-18-42-05.png, Clipboard_2020-04-13-18-44-15.png, Clipboard_2020-04-13-18-47-12.png, Clipboard_2020-04-13-18-51-19.png, Clipboard_2020-04-13-19-54-31.png, Clipboard_2020-04-13-20-01-24.png, Clipboard_2020-04-13-20-03-31.png, Clipboard_2020-04-13-20-04-13.png, Clipboard_2020-04-13-20-05-28.png, Clipboard_2020-04-13-20-09-22.png, Clipboard_2020-04-13-20-11-27.png, Clipboard_2020-04-13-23-22-05.png, Clipboard_2020-04-13-23-23-16.png, Clipboard_2020-04-13-23-26-57.png, Clipboard_2020-04-13-23-31-21.png, Clipboard_2020-04-13-23-32-58.png, Clipboard_2020-04-13-23-33-14.png, Clipboard_2020-04-13-23-37-28.png, Clipboard_2020-04-13-23-37-32.png, Clipboard_2020-04-13-23-38-35.png, Clipboard_2020-04-14-07-39-08.png, Clipboard_2020-04-14-07-41-24.png, Clipboard_2020-04-14-07-45-20.png, Clipboard_2020-04-14-07-46-49.png, Clipboard_2020-04-14-07-51-17.png, Clipboard_2020-04-14-08-01-39.png, Clipboard_2020-04-14-08-02-45.png, Clipboard_2020-04-14-19-02-38.png, Clipboard_2020-04-14-19-04-36.png, Clipboard_2020-04-14-19-07-49.png, Clipboard_2020-04-14-19-11-00.png, Clipboard_2020-04-14-19-12-41.png, Clipboard_2020-04-14-19-14-18.png, Clipboard_2020-04-14-19-18-55.png, Clipboard_2020-04-14-19-23-24.png, Clipboard_2020-04-14-19-25-05.png, Clipboard_2020-04-14-19-29-46.png]
title: 'Module 9: Gettin'' Loopy'
created: '2020-04-13T22:24:51.247Z'
modified: '2020-04-14T23:31:12.163Z'
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
