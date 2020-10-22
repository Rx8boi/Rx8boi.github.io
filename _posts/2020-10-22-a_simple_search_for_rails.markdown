---
layout: post
title:      "A simple_Search for Rails"
date:       2020-10-22 04:04:07 +0000
permalink:  a_simple_search_for_rails
---


With my Rails project completed I was tasked with adding a feature to my application. The future was in mind and the suggestion brought up that I add a search bar to the games index page for my User. 

![](https://i.imgur.com/FcubUJrl.png)

With this as my starting point, I knew I would first have to have an idea of how it would show on my /games index page & decided that the best route would be utilizing one of the helper methods form_for or form_tag. Form_tag would narrow down my focus and from my experience would best best be used creating & updating an object. What I would need is form_tag because i'm just using a get request on attributes i'll be putting into the params. This /get request will also show in the url in a way that would be beneficial to the user (for copy & paste reasons). This implementation of a feature is utilizing foresight for when my app contains users with multiple games & ratings (that don't always show on one page). 

# Game Index view
Starting with the ruby guide on form_helpers:

https://guides.rubyonrails.org/v5.2/form_helpers.html#a-generic-search-form]RubyGuide 

I started with a simple form_tag on my game's index page. Currently iterating over ALL the current_user's games this would create a search bar for the user to add text to query.

```

<h1 align="center"> Games Index </h1>
<div align="center"> 
Select one or <%= form_tag(games_path, method: :get) do %>
<%= text_field_tag(:search, params[:search], placeholder: "Search by Title") %>
<%= submit_tag "Submit"%>
<%end%></div>
```

Also added a "placeholder" that would be the default view of the control without any input. Saving this created a non-working search bar looking like: 

![](https://i.imgur.com/DOskHszl.png)

# Controller
Of course i clicked it and popped an error so next I entered the controller and went to work on the` games_controller.rb` file and implemented new lines to my #index method.

Because of this line in the index show page:

```
<%= text_field_tag(:search, params[:search], placeholder: "Search by Title") %>

```
I added an `if` statement surrounding the `params` with a `:search` argument.

```
	if params[:search]
		@games = @games.search(params[:search].downcase)
	end

```


# Q's for the Model
From here I created a nice new class method for my games to implement `search`. Utilizing the rails console and SQL query methods to find the best way to "search" for a specific game. 

At first I was only able to pull game's by the EXACT name & spacing... until i found this page on "SQL Like operators" 

https://www.w3schools.com/sql/sql_like.asp

This table was a HUGE help![](https://i.imgur.com/3WFluNDl.png)

leading me to a finalized class method:

```
  def self.search(params)
  	where("LOWER(title) LIKE ?", "%#{params}%")
  end
	
	
```
That allows me to query the games table for ANYTHING like the params i entered from a 'space' to the full title, to even the letter 'a'.

![](https://i.imgur.com/IwPn5NWl.png)

# Success!

Hope you enjoyed my blog post :)



