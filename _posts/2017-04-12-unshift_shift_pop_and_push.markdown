---
layout: post
title:  "unshift, shift, pop, and push"
date:   2017-04-12 15:32:33 +0000
---


The four array methods: unshift, shift, pop, and push, were a bit confusing when I took the intro to javascript course prior to enrollment at Flatiron School. Then after beginning my Full Stack Web Development journey, I saw these methods again in Ruby, and have since learned it is used in other languages as well. The best way for me to understand and memorize these methods was using a diagram like the one I recreated below.

![](http://imgur.com/B6ekvJZ.jpg)

I was confusing myself thinking push and pop would be opposites, in that push would add a new array element to the beginning and pop would take one element off the end. Looking at the diagram, it's best to think of the beginning of the array methods and end of the array methods as separately. 

### Some examples in Ruby

```
Adding a new element to the beginning of an array
#unshift

array = [1, 2, 3, 4]

array.unshift(0)
#=> [0, 1, 2, 3, 4]

```




```
Removing an element from the beginning of an array
#shift

array = [1, 2, 3, 4]

array.shift
#=> [1]

array
#=> [2, 3, 4]

```




```
Adding a new element to the end of an array
#push

array = [1, 2, 3, 4]

array.push(5)
#=> [1, 2, 3, 4, 5]

we can also use <<
array << 5
#=> [1, 2, 3, 4, 5]
```




```
Removing an element from the end of an array
#pop

array = [1, 2, 3, 4]

array.pop
#=> 4

array
#=> [1, 2, 3]
```


