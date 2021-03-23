---
layout: post
title:      "useState A helpful hook to reel you Into React"
date:       2021-03-23 03:41:05 +0000
permalink:  usestate_a_helpful_hook_to_reel_you_into_react
---


As it is still being developed ReactJs has tons of features that you can use on your components one of which being hooks. These are functions that allow you to utilize lifecycle features of state from the confines of functional components. Basically with a hook you don’t have to use class components and can utilize a hook to “hook onto” a core React feature.  Just how with ruby & activerecord we found pre set methods in the framework React has built in hooks, namely one I used in my app called ‘useState’.

## UseState as a hook
UseState as we said before is a built-in hook that allows you to add State to a functional component. With useState you don’t need to declare a setState call or the initial state property. The UseState hook returns the current state & a function that allows you to also update the state respective to it. Even more interesting you can call useState multiple times to update multiple values. For instance in my app we call useState to update the Boolean value of show -> to hide / show my modal. And to count the likes from my previous blog post. Finally Updating useState replaces the previous state so you can piggyback off the new state to create concurrent counters 

(like my card likes below)

![](https://www.dropbox.com/s/tma2ixjji7123na/Screen%20Shot%202021-03-22%20at%2010.07.48%20PM.png?dl=0)


```
const EventsList = ({ events, removeEvent }) => {
  const [show, setShow] = useState(false);

  const [count, setCount] = useState(1);
  // Initial state should be 0....
  console.log(count);

```

## How do we use it?
###	Lets pull an example from my code:

Using hooks at first seems intimidating. But they’re fun & we’re created to quickly implement logic into your functional components. First we’re going to import it into our functional component, in my case:
```
import { useState } from "react";
```

![](https://www.dropbox.com/s/cugwmsjoxjwztfz/Screen%20Shot%202021-03-22%20at%2010.08.37%20PM.png?dl=0)
then we’re going to define the [parameter, and function] to show / hide my modal. Parameter is the current state & the function is there to update the state.
here I set the initial state to false so the modal will be closed on page render.

```
const [show, setShow] = useState(false);
```

And just like that we’re halfway through from here I created a span element for the user to click on and ‘onClick’ we update the state calling the previously defined setShow method with an argument of ‘true’.

`<span variant="link" className="add" data-tip="Click to add" data-place="bottom" onClick={() => setShow(true)}>`

## And Viola! 
### It works


![](https://www.dropbox.com/s/y8qzsht88htuuim/Screen%20Shot%202021-03-22%20at%2010.08.03%20PM.png?dl=0)
![](https://www.dropbox.com/s/iuoqw80etm4xrr5/Screen%20Shot%202021-03-22%20at%2010.10.02%20PM.png?dl=0)

Now the only thing left is to set the state back to false when the modal is closed. Simple enough grabbing our hooks method setShow and adding the argument false. 

```
<Modal
          show={show}
          onHide={() => setShow(false)}
          dialogClassName="modal-90w"
          aria-labelledby="example-custom-modal-styling-title"
        >
```


### I hope you enjoyed my blog on useState!


