---
layout: post
title:      "Writing Asynchronous JavaScript"
date:       2018-09-28 02:51:10 +0000
permalink:  writing_asynchronous_javascript
---


JavaScript is a synchronous, blocking, single-threaded language, but there are a number of ways to make it behave asynchronously.

This is especially important if we are trying to process and load data from an API. Some of us with high speed internet have been lucky to have not run into an issue where slower internet connection prevents a page from loading properly; however, many other parts of the world have slower internet speeds, and if our async calls are not set up properly, these users will not be able to access the website properly because the scripts that render the page depend on the data received back from an API.

### Callback
One of the most straightforward ways we can make a JavaScript code run asynchronously is through the use of callbacks. Using callbacks allow us to save a reference of a function into a variable, then invoke this function to send off a request later in the arguments of another function.

```
// Our callback function that takes in a number and adds it to 10
function addNumToTen(num) {
    console.log(num + 10);
}

// The asynchronous function that takes in 2 parameters, the parameter to pass into our callback function, and the callback function itself
function asyncFunc(num, callback) {
    callback(num);
}

// Call our asynchronous function with the callback function
asyncFunc(5, addNumToTen);
// Console:
// 15
```

Another example would be the setTimeout() function, which queues the code to run after waiting a specified amount of time.
```
setTimeout(function() {
    console.log("Async!");
}, 1000);

// after 1 second..
// Console:
// Async!
```

These are rather simple examples, but callbacks can allow you to send off a function that sends off a database request and wait for the response while the rest of the code continues to load. However, because it is hard to predict exactly when something will resolve, many functions are nested under the callback functions, which can get really messy, really fast. 

### Promises
A `Promise`, implemented natively in ES6, is an object that allows us to produce either a resolved or unresolved value at a later time. The promise object is returned synchronously from an asynchronous function.

A promise can be in the following states:

**Pending** where it has not yet been fulfilled/resolved or rejected

**Fulfilled/Resolved** where the action relating to it has succeeded

**Rejected** where the action relating to it has failed

**Settled** where it has either beein fulfilled/resolved or rejected. Once a promise has settled, it cannot change its state.

A promise also has a `.then()` method, which can be chained to the promise object and returns a new promise. A `.then()` must be followed by a return statement if you don't want it to continue running to the next condition. If this promise is rejected, we can use `.catch()` method to handle rejections.

```
new Promise(function(resolve, reject) {
    var value = doSomething();
		if (itWorked) {
		    resolve(value);
		} else if (didntWork) {
		    reject();
		}
})
.then(handleSuccess)
.catch(handleError)
```

A lot of where we saw this pattern is when we made fetch requests. The Fetch API uses Promises to simplify network requets. An example from [Google Web Fundamentals](https://developers.google.com/web/updates/2015/03/introduction-to-fetch):

An XMLHttpRequest
```
function reqListener() {
    var data = JSON.parse(this.responseText);
    console.log(data);
}

function reqError(err) {
    console.log('Fetch Error :-S', err);
}

var oReq = new XMLHttpRequest();
oReq.onload = reqListener;
oReq.onerror = reqError;
oReq.open('get', './api/some.json', true);
oReq.send();
```

vs. A Fetch Request
```
fetch('./api/some.json')
    .then(
        function(response) {
            if (response.status !== 200) {
                console.log('Looks like there was a problem. Status Code: ' +
                    response.status);
                return;
            }

            response.json().then(function(data) {
                console.log(data);
		        return data;
            });
        }
     )
    .catch(function(err) {
        console.log('Fetch Error :-S', err);
    });
```

### Async/Await
Async/Await is built on top of Promises and introduced in ES7. Writing an async function is actually pretty simple. Putting the keyword `async` before a function ensures that the function returns a promise. Inside our async function, we can use the keyword `await` to tell JavaScript to wait for this function to resolve before moving onto the next step. The advantage of using async/await is that it writes asynchronous code in a way that looks very synchronous.

Assuming we had a function getData that returns a promise, this is how we would implement it using a promise:

```
const request = () => {
    getData()
		.then(data => {
		    console.log(data); 
		    return data;
		})
}
```

Using async/await, we could do:
```
const request = async () => {
    console.log(await getData());
}
```

As you can see, using async/await makes it much easier to read the code and is concise.

Syntax: Add `async` before the function, and `await` before the action that needs to resolve before running the next step.
```
async function asyncFunc() {
    await fetch('/some/url');
    runAnotherFunc();
}
```

Syntax with arrow functions:
```
asyncFunc = async () => {
    await fetch('/some/url');
    runAnotherFunc();
}
```

### Generators
Generators, introduced in ES6, are another approach to having asynchronous code that look synchronous. They are noted with a * in `function` and instead of a `return` statement, they have a `yield` statement. It stops excecuting a function until `.next()` is called:

```
function* generateNums(num) {
    for (let i = 0; i < num; i++) {
		yield console.log(i);
    }
}

const callFunc = generateNums(3);

callFunc.next();
// 0
callFunc.next();
// 1
callFunc.next();
// 2
callFunc.next();
// 3
```

More information on generators can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)
