---
layout: post
title:      "React App with Rails Back End Final Project Weather App"
date:       2018-06-13 19:23:15 +0000
permalink:  react_app_with_rails_back_end_final_project_weather_app
---


## How it Came To Be
My morning routine involves me asking Alexa, "Alexa, do I need a jacket?" or "Alexa, do I need an umbrella?"  before I leave the house. For my React final project, I created a weather application that displays just that--today's forecast along with a recommendation to wear a jacket or carry an umbrella. This recommendation doesn't quite involve a complex algorithm, but is simply based on the low temperature of that day and the chance of precipitation! I do think that in later versions I may try to make something more like the average temperature of the day to come up with jacket recommendation. 

## Client Side
I used `create-react-app` for the initial set up of the project. Just like how having an outline makes it easier to write a paper, it helped tremendously to have a mock-up of the project before I started, even though the final project looks a lot different from it.

![Mock-up](https://imgur.com/kCzdX4d.jpg)

Before I fetched any weather data from an external API (I used Wunderground's API), I stubbed out the forecast just to have my pages rendering similar to what I wanted in the mock-up. For me, everything about this project was to tackle smaller tasks one by one instead of trying to face the whole project at once. I set up what I could in React before implementing the Redux framework. Having smaller victories made this project a little less overwhelming :)

The application without a user logged in fetches weather data based on the user's location on the forecasts page ('/forecast'). The home page ('/') also has a search bar that is able to fetch forecasts based on user's input of zip code, but it doesn't have validations set up yet other than the input having to be 5 digits, so any combination of 5 digits is perceived as a zip code. In the event of an error, the error is displayed just below the header, and the user needs to re-enter the correct zip code.

Up to this point, you might be wondering why this application would even need a database. Here's why. I wanted users to be able to customize recommendations based on whether they get chilly easily (like me), or if they hate carrying things (like my husband)! A user who is sensitive to colder weather gets a recommendation to wear a jacket if the low temperature is below 60F for that day; otherwise, the recommendation is triggered at below 55F. A user who does not like too much in their hands gets a recommendation to carry an umbrella when the chance of precipitation is above 55%; otherwise, the recommendation is triggered at above 50%. The database handled these settings as well as kept a list of user's cities if they saved them to their account.

## Database
I used `rails new [app] --api` for the initial set up of the database. I had 3 models for the database, User, City, and UserCity. The associations among my models were:
* User has many UserCities, and User has many Cities through UserCities
* City has many UserCities, and City has many Users through UserCities
* UserCity is the join table and belongs to both User and City

It was a bit tricky setting up user authentication using JWT, but luckily there are a number of great resources to help guide setting this up!

Using Rails as the API for my application was facilitated by using Postman to help figure out how to set up the fetch requests. It was especially useful for me to see how I need to format JSON data because I had nested associations among my models.

## Final Outcome
![Forecast page for non-logged in users](https://imgur.com/rp18z3k.jpg)

Forecast page that renders weather data based on user's current location if user is not logged in.

![Forecast page for logged-in users](https://i.imgur.com/9sTaoxH.jpg)

Forecast page for logged in users with user cities loaded.

![Settings page](https://i.imgur.com/RXOMPf1.jpg)

Settings page.

[Link to Github Repo](https://github.com/hyoyou/weather-to-wear)

