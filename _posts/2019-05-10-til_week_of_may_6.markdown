---
layout: post
title:      "TIL: Week of May 6"
date:       2019-05-10 10:55:33 -0500
permalink:  til_week_of_may_6
---

Mon. May 6

I worked with Olga and Chris the whole day on the client project, and it was the first time we paired remotely. It was not as hectic as I had imagined, and for the first half of our session, I was sharing my screen and being the driver, while Chris and Olga were navigating. I think the navigators were more specific about where they wanted me to insert or edit code (ie. indicating by line numbers instead of function names on just pointing "there" as we did previously). The hardest part of this day was coming up with good names during the refactoring. Some of the feedback we received, indicated that our naming could use some improvement. For example, one function that we extracted, which basically processed a transaction if a coupon was available, was named `updatable()`. Damon said that a name ending in -able usually sounds more like a role than an action to him. We changed this later to `validate()`, and then `process_coupon()`, which we again changed to `successful_coupon()`… until we just removed the extraction and inlined the function since it was significantly reduced in our refactoring.


Tues. May 7

I was trying to get my update feature fixed on my crud app, but realized that because I only did Elixir koans prior to starting my project, there were parts of Phoenix that I still needed to learn. I decided to use some time in the morning to make progress on an Elixir/Phoenix Udemy course I enrolled in. There were some parts of Phoenix that I assumed were working in a certain way (comparing it to what I knew from Ruby on Rails), but it was really helpful to do a code-along with an instructor explaining things along the way. He pointed out a couple things, like how Phoenix apps work with changesets, which I had a very shallow understanding of. While navigating Elixir, Phoenix, and Ecto docs, I always thought they were very well done, and after learning about function docs and how easy it is made to be shown in html, I thought it was a really neat feature of Elixir.


Wed. May 8

Today, I am a bit annoyed at myself for being a sloppy with my commits. I seem too eager to make a commit once something is working, that I forget to look over everything, make sure there are no comments and other parts in the code that can be removed before making a commit. Usually these fixes are so minor that it is not enough to make a new commit for them, and I usually discover them while working on the next item on the list. For example, I removed the default styling from buttons so that my “achieved” button is showing just the glyphycon, but in doing so, it also removed the styling of the “submit” button, which was not something I had wanted to do. I will try to be more careful and make sure to:
1. Check my code for comments, print statements, extra whitespace
2. Run all tests to make sure even minor changes don’t break them


Thurs. May 9

Today I ran into a problem trying to write a test for a redirect using the Vue router. I am still trying to resolve it, but it seems like the issue is because I am finding solutions for a typical javascript page. My frontend, written in Vue.js, is a single page app, so it is not actually redirecting but imitating a redirect( maybe? ). I am unable to use `window.location.______` to find the pathname, as it keeps returning ‘/‘, which makes me wonder if it is always on the index route page since it is a SPA. There is a function in Vue router that facilitates the redirect with `this.$router.push([pathname])`, but it is difficult to find a way to write a test for this function. For now, I think I will test that the data in the "redirected" component exists, and then figure out a way to test for the redirect.