---
layout: post
title:      "TIL: Week of May 13"
date:       2019-05-17 10:55:33 -0500
permalink:  til_week_of_may_13
---

Mon. May 13

I started the day off by trying to write more unit tests for error handling. Bjorn asked me to make sure that I test for scenarios such as not being able to fetch the index page due to an API error, or sending the wrong ID for an update and the API throwing back an error. I've been using the jest built-in mocking feature to easily mock my axios calls, but now I am finding it difficult to mock an error response with the built-in mocking function. Bjorn tried to help me figure it out, and though we're not 100% sure, the seam where we can inject an axios wrapper is most likely at the top-level component. I'm not entirely sure how I can do this with a single page app, because there is not a particular spot where I call the application to run and pass in an argument that I know of, maybe it's time to use Vuex for state management? I felt that maybe this could wait for my refactoring stage, so I started on the delete feature and hope to complete it tomorrow!


Tues. May 14

I finished the delete feature relatively quickly, since it was pretty similar to the update feature. I spent more time trying to figure out how to inject an axios wrapper so that I can pass in the actual axios for my app and a mocked axios for my tests. Prior to starting my project, I took some intro courses on Vue.js, and though it went over the basics, it never actually went into multiple components and passing down props, nor did it talk about the router or Vuex state management tool. I also know that my component has gotten huge, and it will require a lot of refactoring and extracting. Hana also mentioned that I shouldn't be making API calls in the actual component, which I should have figured since I've learned to separate these calls when working in React, so I looked into some blogs, and it seems like other developers make a new directory to store these calls. I am surprised that there is no convention (or at least, so far, I haven't discovered it), like there is in React, where there are actions and reducers directories that separate out each functionality. I will have to look through the Vue docs in the near future to make refactoring easier. 


Wed. May 15

I chatted with James today on what he would suggest my next steps to be with mocking axios. He pointed out that I should separate out the API calls away from business logic, as Hana also pointed out. I should also name the methods in the abstraction to be more specific to my needs, instead of naming the methods generally, and as the actual HTTP client calls, `get`, `post`, etc.. I should name it more specifically such as `getIndex`, `createGoal`, etc., since there is no need to reveal and mimic the calls I make using axios. Although in axios, it uses the HTTP verbs, what would happen if I used a different HTTP client that had its own set of methods named differently? I should not be designing my app to depend on a third party service such as axios, but rather focus on the needs of my app and how I can apply an external dependency to fit into my needs. James also talked about setting up a server using Express with endpoints that would return certain responses, like error responses, in my tests. Though this would make my tests more integration-y than unit tests, it's a pretty cool idea, and hopefully I can give that a try.


Thurs. May 16

Today, Connor mentioned looking into the Singleton pattern when I showed him an issue I was facing, having to create a new HttpClient object for each method that needs to use axios. A Singleton is an object which can only be instantiated once, and there is more than one way of doing so. One such way is to assign an immediately invoked expression, an anonymous function, to a variable amd using only that variable, which points to the same instance.

``` 
var Singleton = (function() {
    function add(num1, num2) {
        return num1 + num2
    }

    return {
        add: add
    }
}())
```

with ES6, we can also do something like:

```
const Singleton = {
    add: (num1, num2) => num1 + num2
}
```

In order to use this in my app, I would have to instantiate the HttpClient object in a higher-level component and pass it down to my component as props, which I will try to implement later today.