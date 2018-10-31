---
layout: post
title:      "SOLID Principles of Object Oriented Programming"
date:       2018-10-31 20:15:47 +0000
permalink:  solid_principles_of_object_oriented_programming
---

SOLID is the acronym of the first five principles of object-oriented-design (OOD), which is promoted by Robert Martin (popularly known as Uncle Bob). It's a group of guidelines and principles to help write clean code, which is easier to maintain and extend. Here's what the acronym stands for:

**S**ingle Responsibility Principle

**O**pen/Closed Principle

**L**iskov Substitution Principle

**I**nterface Segregation Principle

**D**ependency Inversion Principle

### Single Responsibility Principle

> ...each software module should have one and only one reason to change...
> Gather together the things that change for the same reasons. Separate those things that change for different reasons.

from [The Clean Code Blog](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html)

This principle says that each responsibility (reason to change) should have a separate class, so that when changes are made, we can avoid unnecessary side-effects.

Uncle Bob says to keep in mind that the reasons for these changes are *people*. People request changes and you don't want to have unseparated code create confusion for them, or yourself.

### Open-Closed Principle

Bertrand Meyer is credited for proposing the open-closed principle, in which a class should be open for extension, but closed for modification. 

As requirements change, a class should be able to behave in new and different ways to meet the new requirements, but the source code shouldn't change. As Uncle Bob expressed it:

> You should be able to extend the behavior of a system without having to modify that system.

### Liskov Substitution Principle

> If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T.

from *Data Abstraction and Hierarchy* by Barbara Liskov

What is means here is that an instance of a derived class should work without breaking if called in a method of a base class. 

### Interface Segregation Principle

This principle states that the dependency of one class to another should depend on the smallest possible interface, and that no client should be forced to implement an interface or depend on methods that it doesn't use.

This principle was founded as a solution to a design problem faced by Uncle Bob himself. While consulting for Xerox, he worked on a software for a new printer system that could handle multiple jobs such as faxing and stapling. A single Job class was used for all these tasks, so a print job would know all the methods of a stable job and vice versa. This made for a very difficult implementation of extensions. Favor composition instead of inheritance, by separating responsibilities. 

### Dependency Inversion Principle

Last but not least, the dependency inversion principle states that:

A. High level modules should not depend upon low level modules. Both should depend upon abstractions

B. Abstractions should not depend upon details. Details should depend upon abstractions.

The intend behind the dependency inversion principle is to decouple objects so that no client code needs to be changed when an object that depends on it needs to be changed. You are looking to achieve loosely coupled components that have little to no knowledge of the definitions of other separate components.






