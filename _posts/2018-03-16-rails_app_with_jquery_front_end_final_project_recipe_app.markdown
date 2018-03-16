---
layout: post
title:      "Rails App with jQuery Front End Final Project Recipe App"
date:       2018-03-16 20:41:58 +0000
permalink:  rails_app_with_jquery_front_end_final_project_recipe_app
---


For my final project for the JavaScript section, I didn't really add much more functionality to the original Rails app other than the ability for users to add comments to recipes. Instead of rendering an index and show page of another model such as users or catgories, I decided to make a "Quick View" of recipes, sort of like viewing recipe cards! I also added a bit of styling, although it still needs a lot of work, it looks better than what I originally had :) My recipe app's idea involves around my experience of buying all these different ingredients to make one dish, then having to toss the unused, leftover ingredients because I'm not much of a cook and didn't have ideas on how to use them!

![Home Page](https://imgur.com/6KjLEGQ.jpg)

### Index Page

![Index rendered with Rails](https://imgur.com/wIZPK1l.jpg)


The index page generated through Rails is separated into 3 columns, with information underneath each Recipe object such as the key ingredient and category.


![Index rendered with Ajax](https://imgur.com/8jkJLJ3.jpg)


The index page generated through Ajax only lists links to the names of each Recipe object.

### Show Page

![Show rendered with Rails](https://imgur.com/eevtflo.jpg)


The show page generated through Rails contains much more information, such as Ratings, Comments, and the ability of the Recipe's user to edit or delete information.


![Show rendered with Ajax](https://imgur.com/xeuMak3.jpg)


The show page generated through Ajax only contains the description and ingredients!







