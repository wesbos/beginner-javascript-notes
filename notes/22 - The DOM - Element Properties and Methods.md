---
attachments: [Clipboard_2020-02-13-19-04-56 (2).png, Clipboard_2020-02-13-19-07-45.png, Clipboard_2020-02-13-19-08-37.png, Clipboard_2020-02-13-19-11-38.png, Clipboard_2020-02-13-19-20-42.png]
title: 22 - The DOM - Element Properties and Methods
created: '2020-02-14T00:02:00.647Z'
modified: '2020-02-14T00:20:46.500Z'
---

# 22 - The DOM - Element Properties and Methods 

Now that we have learned how to grab/select an element, let's discuss what you can do with it. 

Let's select an h2 element from the page and console log it. 

![](@attachment/Clipboard_2020-02-13-19-04-56.png)

Although in the console it looks like the `heading` variable is the actual element, in reality it is an object that has a lot of properties and methods inside of it. If we change the `console.log()` to a `console.dir()`, that will show us the object properties instead of the actual element itself. 

![](@attachment/Clipboard_2020-02-13-19-07-45.png)

It's still the same h2 tag, but you can see all the properties on it. One example of that is `parentElement` which shows you what the parent element is. There is `outerText` `textContent` `outerHTML`, and many other properties. 

![](@attachment/Clipboard_2020-02-13-19-08-37.png)

We can use those properties as getters to get the data from the element that we need, or we can use them as setters. We will demontsrate this using `textContent`. 

```
const heading = document.querySelector('h2');
console.dir(heading.textContent);
```

![](@attachment/Clipboard_2020-02-13-19-11-38.png) 

That is an example of a getter. 

A setter is when you update the property. An example of that would be `heading.textContent = 'Wes is cool';`. Now when you reload the page, you will see Wes is cool in the console.

`textContent` and `innerText` are very similar properties, `textContent` is the newer one. The only difference is that innerText returns only the human readable content whereas textContent will get the contents of all of the elements, including script and style elements. 

So if your h2 looked like the following for some reason:

```
<h2>
I am a heading
<style>
  h2 {
    color:red;
  }
</style>
</h2>
```

If you log both the `heading.textContent` and `heading.innerText`, you will see that textContent includes the content within the style tag whereas innerText only returns the text `I am a heading`. 

![](@attachment/Clipboard_2020-02-13-19-20-42.png)

stopped at 3:55
