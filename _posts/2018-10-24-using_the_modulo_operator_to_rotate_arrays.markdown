---
layout: post
title:      "Using the Modulo Operator to Rotate Arrays"
date:       2018-10-24 17:30:46 +0000
permalink:  using_the_modulo_operator_to_rotate_arrays
---

Recently, I have been attending a local meetup that gets together and pair programs on algorithm problems. This week, my programming partner showed me a really neat trick that at first just seemed like magic! We were trying to solve a HackerRank problem to rotate an array to the left.

So if we had an array:

`let array = [1, 2, 3, 4, 5]`

and the number of rotations of `1`, we would shift the array once to the left and the resulting array would be:

`array = [2, 3, 4, 5, 1]`


My initial approach was to loop through the array `n` number of times to pop() and unshift() into the array. My programming buddy told me that there was a way to shift an array to the right using the modulo operator(%)! I was really confused with this approach, as I had only used the modulo operator to calculate even or odd numbers, or for fizzbuzz type problems. 

What he showed me was the modular arithmetic:

A (divident) / B (divisor) = Q (Quotient) remainder R (remainder)

The remainder is never a number greater than the divisor - 1, which sounds a lot like how array lengths and indexes are calculated.  So in our previous example, we shifted the array once to the left, my programming buddy showed me that in order to shift to the right, he would use the formula of `(index + rotation) % array.length)`

Let's see how this will work in our example:

```
let array = [1, 2, 3, 4, 5]

function rotateRight(array, rotation) {
  let newArray = [];

  for (let i = 0; i < array.length; i++) {
    let newIndex = (i + rotation) % array.length
    newArr[newIndex] = arr[i];
  }

  return newArr;
}

rotateRight(array, 2);

// [4, 5, 1, 2, 3]

// first iteration, i = 0
// newIndex = (0 + 2) % 5 = 2
// newArr = [undefined, undefined, 1]

// second iteration, i = 1
// newIndex = (1 + 2) % 5 = 3
// newArr = [undefined, undefined, 1, 2]

// thirditeration, i = 2
// newIndex = (2 + 2) % 5 = 4
// newArr = [undefined, undefined, 1, 2, 3]

// fourth iteration, i = 3
// newIndex = (3 + 2) % 5 = 0
// newArr = [4, undefined, 1, 2, 3]

// fifth iteration, i = 4
// newIndex = (4 + 2) % 5 = 1
// newArr = [4, 5, 1, 2, 3]

```




Awesome! Now how can we implement the same logic to shift to the left? 
We could implement the same logic, but instead of adding the index to the number of rotations, we could subtract it! However, there was one caveat. Subtracting the index from the number of rotations sometimes results in a negative number, and JavaScript is not able to handle the modulo of a negative number in the form of the equation we used in the right rotation. In JavaScript, a negative number modulo a positive one yields a negative remainder. Therefore, we need to use a formula described in this [DEV article](https://dev.to/maurobringolf/a-neat-trick-to-compute-modulo-of-negative-numbers-111e), where we add another divisor, then take the modulo of the sum (which does not change the remainder)!

So again, using our example:

```
let array = [1, 2, 3, 4, 5]

function rotateLeft(array, rotation) {
  let newArray = [];

  for (let i = 0; i < array.length; i++) {
    let newIndex = ((i - rotation) % array.length + array.length) % array.length;
    newArr[newIndex] = arr[i];
  }

  return newArr;
}

rotateLeft(array, 2);

// [3, 4, 5, 1, 2]

// first iteration, i = 0
// newIndex = (0 - 2) % 5 = 3
// newArr = [undefined, undefined, undefined, 1]

// second iteration, i = 1
// newIndex = (1 - 2) % 5 = 4
// newArr = [undefined, undefined, undefined, 1, 2]

// thirditeration, i = 2
// newIndex = (2 - 2) % 5 = 0
// newArr = [3, undefined, undefined, 1, 2]

// fourth iteration, i = 3
// newIndex = (3 - 2) % 5 = 1
// newArr = [3, 4, undefined, 1, 2]

// fifth iteration, i = 4
// newIndex = (4 - 2) % 5 = 2
// newArr = [3, 4, 5, 1, 2]
```

Feel free to play around with the code below:

<iframe height="400px" width="100%" src="https://repl.it/@hyoyou/DeadlyEasygoingUnit?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

