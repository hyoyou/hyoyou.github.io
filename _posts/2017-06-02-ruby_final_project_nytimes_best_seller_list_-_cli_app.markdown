---
layout: post
title:  "Ruby Final Project CLI App"
date:   2017-06-02 17:15:02 -0400
---

![My CLI Project](http://imgur.com/RAvnaUS.jpg)

**Overview** 

This application allows the user to select a category in which they want to view the NYTimes best seller list for. After showing the list, the user is prompted to choose a book from the list that he or she would like more information on. The user is then given an option to view the book on the Barnes & Noble website, or to go back and choose another book or category.



**Getting There**

There were quite a few bumps on the road getting to a working model of this project. There were no tests to pass, which was invigorating *yet* intimidating at the same time. Initially, I wanted to scrape from the New York Times website since it was the most obvious place to look for the New York Times Best Seller list. Working outside-in, I drew out the interface and had a draft of the CLI controller, then moved on to work on the scraper class. I grabbed all the css selectors for the information I needed using the web developer tool, but when I actually used Nokogiri to scrape the webpage using those css selectors, the webpage wouldn't allow access to any of its content. It turns out the New York Times has an API available to anyone who wants the content and requests for an API key, but I wasn't too sure on how to use the API and began looking around for alternatives, which led me to the Barnes & Noble website.

As soon as I got the scraper working, I got carried away on making the program work, that I forgot to think about object oriented programming. Everything was in my scraper class as I was extracting the title, author, summary, and url by scraping each individual information and storing them in individual arrays--what Avi referred to as the "zipper method" in his videos. It was tough breaking apart a working program and reassembling it in an object oriented way. My program was broken until the refactoring was done, but now my code makes a lot more sense--it instantiates category objects, which instantiates book objects.

Building this application from scratch taught me a lot. It was not just about the code, but on how I should design a controller, the flow, the objects. I am going to build a simpler CLI application on the side, just to reinforce what I learned. Even though my application still needs some work, it amazes me that I can build such a program, something I couldn't even imagine months ago. I'm really excited and eager to learn what's next!

