---
layout: post
title:      "TIL: Week of May 27"
date:       2019-05-24 10:53:33 -0500
permalink:  til_week_of_may_27
---

Tues. May 28

Olga and I got together today to continue working on our client project. We are both new to React Native, but since I had done a few personal projects in React, the transition from React to React Native was not bad at all. We are going to continue with spiking the feature, and right now it works the way we expect when the user goes through the check out process as a signed in user. However, the problem is when the user is not signed in and tries to go to the check out process, the app blows up when the user navigates back to that page since it looks for a `props.user.profile` which does not exist unless the user is signed in. We have bandaged the issue by adding a bunch of null checking.. and by a bunch, we have it at every attribute.   `props.user !== null` -> `props.user.profile !== null` -> and so on.. We are thinking about ways to refactor this, and want to see if React has any feature that lets us check if the props is empty prior to checking, or if we can set each attribute to null by default.


Wed. May 29

We have done so much spiking here and there on my laptop, that we wanted to walk through our steps one more time on Olga's computer. She pulled the latest master, which had about 7 new commits merged in. One of them was a fix for a CocoaPods error, and though it was fixed, it started throwing a bunch of errors on Olga's computer. There were no errors when we installed the Pod dependencies, but XCode blew up when we tried to build the program to run the simulator. We tried to debug it, removing and installing the dependencies all over, and could not resolve it. Later in the afternoon, I tried to pull the latest master and create a new branch to see if it was a problem with the new changes, but mine was able to run after getting over a couple snags. We are still not sure what the problem is, but hope that we are able to resolve it so that we can continue on with testing and wrapping legacy code in tests.


Thurs. May 30

This morning, the CocoaPod error was still not gone, so Olga tried one last time by creating a new branch off of master, this time, installing Pods instead of removing repo & doing a new install, and it worked! What happened?! We are very confused, but happy that it is now working. We were ready to tackle on writing tests for legacy code, and then quickly faced with our next challenge. Setting up Jest, with Jest-Expo, kept throwing syntax errors in the `node_modules` folder. We researched and tried to fix it the entire afternoon, and came to a conclusion that it has to do with a recent update of Jest-Expo, and we needed to configure it to ignore certain files. This worked, and we finally got to write some tests towards the tail end of our day, and then found out that our test will throw errors since we are trying to test a component that is connected to a redux store. We are going to get some help from someone who has done React with Redux testing, so hopefully we will figure this out soon!