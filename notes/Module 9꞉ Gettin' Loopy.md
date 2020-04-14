---
attachments: [Clipboard_2020-04-13-18-40-09.png, Clipboard_2020-04-13-18-42-05.png, Clipboard_2020-04-13-18-44-15.png, Clipboard_2020-04-13-18-47-12.png, Clipboard_2020-04-13-18-51-19.png, Clipboard_2020-04-13-19-54-31.png, Clipboard_2020-04-13-20-01-24.png, Clipboard_2020-04-13-20-03-31.png, Clipboard_2020-04-13-20-04-13.png, Clipboard_2020-04-13-20-05-28.png, Clipboard_2020-04-13-20-09-22.png, Clipboard_2020-04-13-20-11-27.png, Clipboard_2020-04-13-23-22-05.png, Clipboard_2020-04-13-23-23-16.png, Clipboard_2020-04-13-23-26-57.png, Clipboard_2020-04-13-23-31-21.png, Clipboard_2020-04-13-23-32-58.png, Clipboard_2020-04-13-23-33-14.png, Clipboard_2020-04-13-23-37-28.png, Clipboard_2020-04-13-23-37-32.png, Clipboard_2020-04-13-23-38-35.png]
title: 'Module 9: Gettin'' Loopy'
created: '2020-04-13T22:24:51.247Z'
modified: '2020-04-14T03:44:11.192Z'
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
    return `${word[0].toUppercase()} ${word.slice(1)}`;
}
```


stopped at 7:57
