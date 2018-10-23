---
layout: post
title:      "Intro to Test Driven Development"
date:       2018-10-05 20:15:04 +0000
permalink:  intro_to_test_driven_development
---


I recently attended a code and connect event that further familiarized me to test driven development (TDD), plus I got to pair program with an awesome fellow Flatiron grad!

Even though our curriculum has taught us the advantages of TDD, it seemed like a daunting task to try writing tests myself (what if my test is written poorly that the correct code doesn't pass?!!). 

So what is TDD?
TDD is a development process in which we are not allowed to write any production code before writing a failing test. We've seen this before, there are 3 steps: Red, Green, Refactor

**Step 1: Red** Write a test, run it, see it fail

**Step 2: Green** Write the minimum amount of code needed to make the test pass

**Step 3: Refactor** Clean up code to satisfy all test cases

Then repeat these steps with each new test :)

The advantages of using TDD are that it creates an overall accountability for the expectation of the application, allowing for improved collaboration and better software.

What we are going to go over today are **unit tests**. Unit tests, like the name suggests, should test one small piece of code. In object-oriented programming, we have different objects that interact with each other, and unit tests try to test each object individually, so that the objects return the information we expect so that we can make sure the object's internal structure is working as designed.

The software engineer who presented this learning event (also another awesome Flatiron grad!) gave us very easy to use examples. We needed to build a string calculator method, #add, that when numbers are passed into the method in the form a string, the output would be the sum of those numbers.

First test: an ('') empty string will return 0:

in our tests, we can do something like:

```
it 'can take an empty string and return 0' do
  expect(add("")).to eq 0
end
```

Once we run the tests, we get to our first step, red. We get back a failing test: NoMethodError: undefined method `add`

We will first need to define our method:

```
def add str
end
```

In order to get to our next step, green, we need to write the minimal amount of code to pass. What would it be? Remember, *minimal* amount of code:

```
def add str
  return 0
end
```

and voila! A passing green light... but of course that's not the solution we want. 

What if we tried something like:
```
def add str
  str.to_i
end
```

Yup, back to passing green lights!

Next test: a string of ('1,2') will return 3:

First, let's write the test:

```
it 'can take a string of two numbers and return a sum of those numbers' do
  expect(add("1,2")).to eq 3
end
```

Run the test, and we get our red lights!

Why don't we build a method to convert the string into an array of numbers, which we can than iterate through to add up to the sum?

```
def add str
  sum = 0
  str.split(',').map do |n|
    sum += n.to_i
  end
  sum
end
```

Back to the passing green lights! 

Now for another test: a string separated by newlines and commas, ie ('1\n2,3') will return 6:
Writing the tests should now be pretty simple:
```
it 'can take a string of three numbers, separated by newlines and commas, and return a sum of those numbers' do
  expect(add("1\n2,3")).to eq 6
end
```

First run the tests for our red light.

Now we want to write code to have a passing test. There are several ways to do this, such as the presenter's solution where she gsub'ed the whitespace with a comma!

```
def add str
  str.gsub!(' ', ',')
  str.split(',').inject(0){ |sum,x| sum + x.to_i }
end
```

What my pair programming partner and I came up with is to use regex to check for both commas and newlines:
```
def add str
  sum = 0
  str.split(/[,]|[\n]/).map do |n|
    sum += n.to_i
  end
  sum
end
```

There we go, now we have all passing tests again! Even though what we wrote here are very simple tests, this exercise helped me become more familiar with writing tests and made it less intimidating. I would love to start writing some tests for future projects. 

Feel free to play around with the code below!

<iframe height="400px" width="100%" src="https://repl.it/@hyoyou/LumberingMasculineAggregator?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

