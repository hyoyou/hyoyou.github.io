---
layout: post
title:      "Controlling Access in Java and How to (Not) Test Private Methods"
date:       2019-02-14 10:22:33 -0500
permalink:  controlling_access_in_java_and_how_to_not_test_private_methods
---


When programming in Ruby, though we are able to control access to methods by making them public, protected, or private, I didn't fully comprehend when it was appropriate to use any other access control, and I left most methods at its default public scope other than some methods for params and before_action methods, which were private.

However, I am currently building an HTTP server in Java, and each method and class generally explicitly define an access level modifier - `public`, `private`, `protected`, or `package-private`. Not including a modifier gives it the default `package-private` visibility, which makes it visible only within its package. Below is a handy chart that summarizes the access level of the 4 different modifiers:

![Modifiers Chart](https://www.programcreek.com/wp-content/uploads/2011/11/access-level.png)

Image Credit: https://www.programcreek.com

Using access level modifiers protects your program from misuse, especially if other programmers have access to your classes. A good rule of thumb that I have seen/heard from many different sources is to start by using `private` unless there is a reason to change it. This is the rule that I was following, until I found that you can't unit test private methods. 

Since I am learning TDD, I ended up writing a failing test, writing the method (with `private` access level modifier) to try and pass the failing test, only to be alerted that the method cannot be accessed due to the private access modifier. In order to "fix" this problem, I looked at the options IntelliJ provided for a solution, and changed it to a `public` method. 

![IntelliJ Options](https://imgur.com/CSU8tnL.jpg)

I admired IntelliJ for its brilliance and wanted to believe my errors were resolved, though deep down I knew I was just sweeping my problems under the rug. I put up a pull request for one of the features that I finished working on, and to no surprise, my reviewer pointed out that some of my methods should be `private` since it is only needs access within its own class.

So, I reverted all the methods back to `private` that I made `public` for the purpose of unit testing. Asking around for ways to test these `private` methods, the response I got were:

> Kent Beck in _Test Driven Development_ suggests that while you always write tests to test-drive a method, it's fine to delete them after you've made the method private. With judicious use of git commits, you can always put the tests back if the method is made public again.

> Usually, you do not want to unit test private methods. Private methods contain a lot of implementation details that do not directly affect the API of the public methods in your class...when you do the red-green-refactor cycle, you pull details into private methods during the refactor step [and] private methods should not be “designed” up front
 
> ...from what I understand, we shouldn’t be testing private methods. We should test the methods that implement any of our private methods to ensure that they are working properly.

> someone told me a long time ago ... that when you start wanting to test private methods, that could be a signal that there might be an Extract Class refactoring asking to be made

> Bob Martin put this to me once succinctly - “If you can’t get to it through the public methods, why does it exist?” It’s definitely a different way of designing classes - I’d argue a superior one. If you build up implementation from private methods, you’ve already “decided” how it’s gonna work. Why even bother testing? But if you work from the interface and extract them you find a clean interface to your classes.

So basically, the way you test `private` methods is, well, **you don't**.

You should be unit testing the public methods that implement your private methods. For example:

![Public Method](https://imgur.com/Cx51yMW.jpg)

I have the `public processRequest` method (which could probably use some refactoring after this!) that makes calls to several `private` methods. Unit testing `processRequest()` should verify that my `public` and the `private` methods it implements collectively return the result I expect. 

Even after understanding the public method that implements the private methods, if you still feel the need to test private methods, it most likely indicates that there is a flaw in your application's design, or the method you are trying to test really shouldn't be private.

If a public method is not calling the private method, do you even need this private method or is it dead code? If the private method in question is only called by other private methods, consider refactoring it to a separate class. While encapsulation is usually a good thing, hiding too much implementation behind private methods is not ideal and may be a signal that it can be a class of its own. As mentioned in one of the suggestions I got above, [Extract Class](https://refactoring.guru/extract-class) refactoring advises creation of new classes when a single class has too many responsibilities. This helps us stick to the *Single Responsibility Principle* as well. 

![Extract Class from Martin Fowler](https://imgur.com/5MPqQxr.jpg)

Image Credit: https://refactoring.com/catalog/extractClass.html

Though the consensus seems to be that you should not test private methods, there are ways to get around it if you are working with some legacy code where you're not allowed to change the visibility of your methods. You can give your methods package access, use a nested test class, or use reflection.

In conclusion, when practicing TDD, it is better to **not** follow the suggestion to begin every method in private scope, then change it when necessary. Instead:
1. Write a failing unit test
2. Create a **public** method to make your test green
3. Refactor from within the public method and extract **private** methods, without changing your unit test



### Further Reading:
[Java Tutorial](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html)

[Testing Private Methods with JUnit and SuiteRunner by Bill Venners](https://www.artima.com/suiterunner/private.html)

[Extract Class - Martin Fowler](https://refactoring.com/catalog/extractClass.html)
