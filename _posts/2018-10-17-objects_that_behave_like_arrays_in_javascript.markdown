---
layout: post
title:      "Objects that Behave like Arrays in JavaScript"
date:       2018-10-17 22:22:27 +0000
permalink:  objects_that_behave_like_arrays_in_javascript
---

Recently I was working on a problem where I was trying to manipulate an object like an array, but it was in fact, not an array! 

I was able to iterate through this object, but unable to use array methods like push(). So what exactly was this object?

It was a nodeList! DOM collections are returned in a form that *looks* like arrays:

```
document.querySelectorAll("div")

// NodeList(312) [div#notify-container, div#custom-header, div.-container, div.-main, div.ps-relative, div.topbar-dialog.siteSwitcher-dialog.dno, div.header, div.modal-content.current-site-container, div.fl1, div.favicon.favicon-stackoverflow.site-icon.grid--cell, div.related-links, div.L-shaped-icon-container, div.favicon.favicon-stackoverflowmeta.site-icon.grid--cell, ...] 
```

We are able to call methods like .length() and iterate through them in loops, but we will get back an error when we try other array methods like push(), pop(), shift() etc. 

## Making Array-Like Objects Become.. Well, Arrays
If we want to use array functions on these objects, we would need to convert them to arrays.

For this, we can use the following: `Array.prototype.slice.call(object)` or `[].slice.call(object)`
For example, let's say we want to add a child to every DOM element from a nodeList.

```
function addChildren() {
  let allDivs = document.querySelectorAll("div");
  allDivs = Array.prototype.slice.call(allDivs);

  for (let i = 0; i < allDivs.length; i++) {
    let newDiv = document.createElement("div");
    allDivs[i].appendChild(newDiv);
  }
}
```

This would add a child div to each div. So what exactly is Array.prototype.slice.call(object) doing?

First, `Array.prototype` we are using a method of the Array class.

Next, `slice`, this is a function of the Array class, which extracts a section of the array. Since we do not provide a starting and/or ending index, the argument passed, `object` in our case, will simply return a copy of the array.

Finally, `call` is a function that allows us to use a method from one object and then use it in the context of another. So in our case, we are using the slice method of the Array object in the context of the object being passed in as the argument.

So the result of calling this function is a copy of our array-like object, but in an actual array!



