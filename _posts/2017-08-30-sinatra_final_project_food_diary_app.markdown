---
layout: post
title:  "Sinatra Final Project Food Diary App"
date:   2017-08-30 18:05:31 +0000
---

My initial idea for the Sinatra Final Project was to make an application that was related to my work in property management. 

We are using very outdated systems at our company that I've been unhappy with for a while, and I was getting overzealous, wanting to add too many features to the application. I found myself in over my head and overwhelmed by the complexity of the associations and nested params. I'll go back to working on this when I have a better understanding and more practice.

I decided to go with a much simpler application about keeping a food diary, intrigued by its benefits from a recent article I read. A food diary is a log in which a user keeps track of the meals they ate for the day and how many calories were consumed. It raises awareness to what the user eats, and the habit deters the user from unhealthy snacking habits. Being attentive to what the user eats can draw out unhealthy eating patterns and figure out which nutrients may be missing.

I had three models for my application: the User, the Log, and the Meal

A User has many Logs and Meals
A Log has many Meals and belongs to a User
A Meal belongs to a User and a Log

The user creates individual log entries for a specified date like so:

![Log Show Page](http://imgur.com/QqjUx9b.jpg)

and the application will display the total meals for that day as well as the total calories consumed thus far.

The user can also select individual meals to gain more information about it:

![Meal Show Page](http://imgur.com/tKql7iU.jpg)

Of course there are so many other features I would love to put on the application such as nutritional breakdown and a water consumption tracker, and I hope to get to working on them as I gain more practice and become more comfortable with working with more models. So far I am just happy to have a working application even though it may be far, far from perfect! :)
