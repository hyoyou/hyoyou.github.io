---
layout: post
title:      "TIL: Week of May 20"
date:       2019-05-24 10:53:33 -0500
permalink:  til_week_of_may_20
---

Mon. May 20

On Friday, I got to pair with Hana, Bjorn, and a bit with Jerome, and we tried to figure out how I could mock axios so that it would return a Promise object that would only reject for testing errors. It turns out, jest has a method, `mockReturnValue` that returns whatever value we set to the method. I didn't understand why this was being used at first, I mean.. if you set your return value to return "hi" and then test that it returns "hi", what was I testing here? It felt like such a forged response, but I forgot to look at the whole problem in a simpler sense. All I wanted to do was test that my function would be able to handle an error. If my `axios.get(url)` returns a Promise object, and I want to test that it rejects with a message, setting the return value to that error message, calling the method, and checking its output would test exactly that. I was thinking more about how to mock the actual behavior -- make a mock `axios.get(url)`, make it handle the request then return an error somehow, then handle the response, and I was not getting very far. I realized that I was too focused on the details, and I needed to step back and reassess the problem. I worked on adding the remaining error tests for the rest of the day, then worked on creating a wrapper for axios to abstract the details away from the components.


Tues. May 21

Today, we got to finally test our client project in the staging environment. We found out that since we didn't touch the front-end React Native side, there was nothing there to hit our endpoint and grab the data we wanted to display. We will have a meeting with the client to see what their expectations are for the front-end, since we haven't discussed it before. We spent some time looking through the existing React Native code, and so far it looks just like React. We figured out some places where we might be able to make new calls to save to the Redux state, so the feature we need to implement doesn't seem so complicated as of now. We will probably start working on this once we have a call with the client to figure out what he expects. I don't know why I thought the feature should start working when the back-emd was implemented, but it made me realize that I focused so much on the web app, API side of the app, that I never followed it through to the front-end, mobile side. Once again, I need to stop focusing on one little detail and learn to step back and assess the larger picture.


Wed. May 22

I worked on .NET koans to learn about C# for my next project. So far, C# seems very Java-like with the types, as well as a bit JavaScript-like, with the const & var declarations. After finishing the koans though, I still don't know how to actually *start* my next project, tic-tac-toe in C#. I think I will follow along an introductory course in Udemy, and code along a small project or two, just to get myself used to working in C# and become familiar with Visual Studio and/or Rider. I hope to be able to set up the project and the unit tests by the end of tomorrow, then actually start working on TTT on Friday and next week!


Thurs. May 23

Today, we had a meeting with our client, and our group decided that I would be the "facilitator" for the meeting. I expected it to be easy and that it would require little to no facilitating, since we assumed the client had something in mind for the front-end and the meeting was just for him to walk us through the expectations. However, this was not the case, and he was rather asking *us* on what we thought could be done and expected us to be the decision-makers. I completely panicked because I had not been prepared for this, but luckily other team members stepped in to ask questions and clarified what we needed to do. It is tough for me to stay calm and think clearly when talking to people I'm not familiar with, but this is something I need to work on consistently. Towards the end of my bootcamp course, I forced myself to go to meetups and other events to talk to people I don't know and become more comfortable being in new environments, but during the past few months, I haven't been keeping up with that and have been too focused on acclimating to my new environment at work. I should push myself to get out to meetups and events a little more, just to get myself used to meeting new people and staying composed and able to answer unexpected questions.