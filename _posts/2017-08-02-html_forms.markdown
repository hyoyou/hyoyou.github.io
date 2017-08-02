---
layout: post
title:  "HTML Forms"
date:   2017-08-02 19:11:28 +0000
---


As I've been going through the labs in the Sinatra ActiveRecord section, many of the hair-pulling moments were due to not naming input attributes to the likes of the Capybara tests of the lab, so I wanted go back to break down each part of forms attributes.

### input type=
Some of the ones we have used in labs so far: 

```<input type="text">``` defines a one-line text input field.

```
<form action="">
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname"><br>
</form>
```

![Text](http://imgur.com/5ffgbPE.jpg)

```<input type="password">``` defines a password field in which characters are masked in circles of asterisks.

```
<form action="">
User name: <input type="text" name="username"><br>
User password: <input type="password" name="password">
</form>
```

![Password](http://imgur.com/x5YQFkS.jpg)

```<input type="submit">``` defines a button for submitting form data to a form-handler, which is defined by the forms action attribute.

```
<form action="">
First name: <input type="text" name="firstname" value="John"><br>
Last name: <input type="text" name="lastname" value="Doe"><br><br>
<input type="submit" value="Submit">
</form> 
```

![Submit](http://imgur.com/EiqedKR.jpg)

```<input type="checkbox">``` defines a checkbox, which allows the user to check zero to multiple number of choices.

```
<form action="">
<input type="checkbox" name="a">Bacon<br>
<input type="checkbox" name="b">Eggs<br>
<input type="checkbox" name="c">Cheese<br><br>
<input type="submit">
</form> 
```

![Checklist](http://imgur.com/3p9ogno.jpg)

```<input type="radio">``` defines a radio button, which allows the user to select one choice.

```
<form action="/action_page.php">
  <input type="radio" name="meat_choice" checked> Chicken<br>
  <input type="radio" name="meat_choice"> Steak<br>
  <input type="radio" name="meat_choice"> No Meat<br><br>
  <input type="submit">
</form> 
```

![Radio](http://imgur.com/eJVwMie.jpg)

### input name=
The name attribute of an ``<input>`` defines how our application will identify each ``<input>`` data. The name attribute is used in the HTTP request sent by your browser to the server as a variable name associated with the data contained in the value attribute.

When it comes to radio buttons, it is important that the name remains consistent throughout each option so that the user cannot select multiple options.

### input id=
The id attribute has nothing to do with the data contained within the element. IDs are for hooking the element with JavaScript and CSS, but they must be **unique** in the whole document.

### Capybara Tests
Using the example in our lab, if we have the below test in our spec file:

```
it 'has a greeting form with a user_name field' do
  visit '/'

  expect(page).to have_selector("form")
  expect(page).to have_field(:user_name)
end
```
 
 First, the test expects our page to have a ``<form>`` element.
 Next, the test expects our page to have a form field with an argument called "user_name", which can be met by either an ID or name attribute that matches the argument like below:
 
```<input type="text" name="user_name" id="user_name">```

It's important that attribute matches exactly what the test is looking for.

### input value=
The value attribute specifies the initial value for an input field so that the form is pre-filled with the specified value.

```
<form action="">
First name: <input type="text" name="firstname" value="John"><br>
Last name: <input type="text" name="lastname" value="Doe">
</form>
```

![Value Attribute](http://imgur.com/tNgeupH.jpg)

