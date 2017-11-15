---
layout: post
title:      "Rails Final Project Recipe App"
date:       2017-11-15 16:30:16 +0000
permalink:  rails_final_project_recipe_app
---

![Emotional Roller Coaster](https://imgur.com/8lKJifl.jpg)

(image via [Brainless Tales](http://www.brainlesstales.com/2016-05-04/emotional-roller-coaster))

#### Emotional Roller Coaster

I'm not sure whether our curriculum purposely includes the Amusement Park lab prior to the final project or not, but this project was my very own roller coaster ride. I started out nervous, unsure of what was ahead, but sure of a nerve-wrecking, slow, upward climb. My initial idea didn't quite work out because it was hard to meet the join table requirement (Note to self: read over the requirements carefully and plan out all models and associations **prior** to getting knee deep into a project). So after my big disappointment, it was a struggle for me to come up with a unique new idea, and I decided to take the project's suggestion to create a recipe app. I spent a couple days planning out the models, associations, and a rough sketch of how I wanted my app to look. I really took my time here because I didn't want to have to restart the process. My understanding of a join table was not clear, and it was helpful to go over the lessons again and supplement other readings to reinforce the concept. The first hurdle to go over was creating the nested forms and getting them to work, the next few hurdles were less challenging, and before I knew it, I was finally enjoying the ride.

#### Join Table

I had a RecipeIngredients join table that belongs to a Recipe and belongs to an Ingredient. My join table also stored the quantity attribute of each ingredient for each recipe. This was the most challenging part of the project getting the new recipe form to create a recipe, ingredient, and recipe_ingredient all at once. I was able to get this working by using the accepts_nested_attributes macro, but the recipe_ingredients didn't save with my custom attribute writer. While I tried to resolve that, I had a hideous method to work for the time being:

```
  def save_recipe_ingredients(recipe_params)
    if recipe_params[:ingredients_attributes]
      recipe_params[:ingredients_attributes].each do |ingredient_attribute|
        if !recipe_params[:ingredients_attributes][ingredient_attribute][:name].blank? && !recipe_params[:ingredients_attributes][ingredient_attribute][:recipe_ingredients_attributes]["0"][:quantity].blank?
          ingredient_name = recipe_params[:ingredients_attributes][ingredient_attribute][:name].capitalize
          ingredient = Ingredient.find_or_create_by(name: ingredient_name)
          recipe_ingredient = RecipeIngredient.find_or_create_by(recipe_id: @recipe.id, ingredient_id: ingredient.id)
          recipe_ingredient.quantity = recipe_params[:ingredients_attributes][ingredient_attribute][:recipe_ingredients_attributes]["0"][:quantity]
          recipe_ingredient.key_ingredient = recipe_params[:ingredients_attributes][ingredient_attribute][:recipe_ingredients_attributes]["0"][:key_ingredient]
          recipe_ingredient.save
        end
      end
    end
  end
```

Yup, it's quite a pain to look at!! But it got me to move forward with the project while I sought help to refactor this.

I also had a key_ingredient attribute in recipe_ingredients, which I used to allow the user to filter other recipes using the same key ingredient.

#### Improvements

I learned so much throughout this project -- nesting and nested attributes, devise, validations, just to name a few -- and I can't wait to improve on some of the features as my learning continues! Right now, filtering by key ingredient from the recipe show page includes the original recipe, which kind of defeats the purpose of finding **other** recipes that use the same ingredient. I also would like to add photos to each recipe to make recipes visually appealing. There were a couple gems that I wanted to use, such as the cocoon gem, which require jQuery, so I hope to be able to have more options when we get to the project with jQuery.
