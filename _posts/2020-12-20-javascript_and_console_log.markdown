---
layout: post
title:      "Javascript & ` console.log`"
date:       2020-12-20 19:16:09 +0000
permalink:  javascript_and_console_log
---


The art of Talking to yourself & shaking your own hand



With my Javascript project as you’re well aware I found that manipulating the DOM is no easy task. Sure we at Flatiron have cohort leads & fellow cohorts, but none compare to your best friend “console.log”. Through the middle of the night & early mornings when you have a question if this happens on a `‘click’`, a mouseover or a submit; `console.log `is always there.

In a snippet of my code you can see how often I’ve used it implementing delete & update functions on my NBA Fantasy League app. 

![](https://www.dropbox.com/s/xt1hofhn7p612t0/Screenshot%202020-12-14%20103133.png?dl=0http://)


We’ll begin from here:
![](https://www.dropbox.com/s/kgy2rhdewj0cd61/Picture1.png?dl=0)

As you can see there are update & delete links on each players card. Unfortunately they don’t work but since we’ve already utilized a fetch request to fill this list we can have our old friend ‘console.log’ help us with the rest.

```
const athlete_list = document.querySelector('.athlete_list');
```
-	defined athlete_list we’re going to use for an eventListener method:
-	after we will have console.log return you’re clicking the card.

```
athlete_list.addEventListener('click', (e) => {
    console.log("You're clicking the card")

```

![](https://www.dropbox.com/s/ds9m5uiya2c4erg/Picture2.png?dl=0)
Success!
Next we grab the ID’s from the links(or buttons) that we’re clicking so the method knows what we’re looking for.
Change up the console log to select event target id like so:

```
athlete_list.addEventListener('click', (e) => {
    //console.log("You're clicking the card")
    console.log(e.target.id);

```

and everytime you click NOW you’ll see either ‘delete-athlete’ or ‘update-athlete’
![](https://www.dropbox.com/s/j18xhvabcphm90n/Picture3.png?dl=0)

Now that we’ve got our focus down we can set some variables ->
```
athlete_list.addEventListener('click', (e) => {
    //console.log("You're clicking the card")
    //console.log(e.target.id);
    e.preventDefault();
    let delButtonIsPressed = e.target.id == 'delete-athlete';
    let updateButtonIsPressed = e.target.id == 'update-athlete'; //copy & paste is your friend!!!
    let id = e.target.parentElement.dataset.id;

```

Now were going to back to Rails/Routes and methods.
We’re going to use the DELETE method so throw an if statement for our fetch request:

```
if (delButtonIsPressed) {
        console.log('remove athlete')

```
and on button click?
![](https://www.dropbox.com/s/zguo03qq1a6uzo5/Picture4.png?dl=0)
Beautiful!
Now? Its almost fetch request time. But first we’re going to grab the parent element and once again utilize console.log to help us.
Doing so allows us to define another variable 


```
    let id = e.target.parentElement.dataset.id;
    //how do i grab specific Athlete ID???
    //console.log(e.target.parentElement.dataset.id);

```

Which we can use in our fetch request:

```
if (delButtonIsPressed) {
        //console.log('remove athlete')
        fetch(`${url}/${id}`, {
            method: 'DELETE',
        })

        .then(res => res.json())
    }

```

Finally with the promise it allows us to delete a record in our rails server which we should double check in the rails console:
![](https://www.dropbox.com/s/y0bb93u88sfiuq9/Picture5.png?dl=0)


All that’s left to do is refresh the page, which we can tie to our delete ‘a href’ tag like so:
 `<a href="#" class="card-link" id="delete-athlete" onClick="window.location.reload()">Delete</a> `

I hope you enjoyed this quick dive into the benefits of using console.log on your javascript project. It’s nice to have a companion that works almost like tests in ruby; guiding you through your actions and event listeners. 

