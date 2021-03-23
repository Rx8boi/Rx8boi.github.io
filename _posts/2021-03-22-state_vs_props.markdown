---
layout: post
title:      "State vs Props? "
date:       2021-03-23 02:29:23 +0000
permalink:  state_vs_props
---

# Defining & Utilizing both in ReactJs
### State – An overview in pure React apps
	
  React has a lot of concepts that take a while to grasp but once you do they easily expand the scope of your engineering process. One of these concepts though basic is essential to understand ReactJs is called ‘state’ and the other simply ‘props’. Understanding the basics of state/props in a pure React app is crucial to integrating a state container like Redux in your project. So this blog post will hopefully open your eyes to what state is, what props are, &  how to use hopefully providing a few examples to help us both along the way.
	
### First off what is state?
Generally speaking there are multiple definitions one can think of state. I used to believe it was what you literally see from your app on the screen, the data, variables, visual appeal, etc.  A more accurate description would be the things on the app that can be changed. Anything you can change lives in an object i.e. state. We can call these variables “still” & are initialized and managed by the component. 

### Props what are they?
Props on the other hand are variables (properties) passed from a parent component to a child component. These are passed by using a specific syntax ->


```
            <p>
              <CardCount count={count} />
            </p>
```

In my example I am passed the variable “count” to the “cardCount” so that It can access this prop. This also allows for that child component to access methods associated with the prop furthermore preventing the need to have a child component need it’s own state. Which coincides with the general rule that props in shouldn’t be changed in the component that is accessing them. 

## Lets apply this logic:

![](https://www.dropbox.com/s/826ze4nf6v3p9fw/Screen%20Shot%202021-03-22%20at%207.58.13%20PM.png?dl=0)
In my application we’ve created a counter to track the amount of likes on each timeline card. In the code snippet seen above we’ve imported CardCount between a <p> tag to pass the variable “count” to the child component => CardCount

In the CardCount class we have a functional component that is taking in the variable to add to it’s current like count. 

```
import React, { useState } from 'react'



// props is going to be passed 
const CardCount = props => {
  //set to cards intial count value
  const [cardCounts, setCount] = useState(0)
// Each card renders its own count
    return <>
        {/* Call current card likes -> add parent props -> Show props to button */}
        THIS CARDS LIKES: {cardCounts}
        <br></br><button onClick={() => { setCount(cardCounts + props.count) }}>Add {props.count} More Likes!</button>
    </>;
}

export default CardCount
```

We’re also using that ‘prop’ for the button’s description. We do this by first adding props as the argument.

```
const CardCount = props => {
```

Then attaching the variable we’ve passed to props. `...Add {props.count} More Likes!</button>`
![](https://www.dropbox.com/s/7rlromsdyqatvx0/Screen%20Shot%202021-03-22%20at%209.09.54%20PM.png?dl=0)

### Expanded view

And viola! Our props have been passed from parent to child on each card.

![](https://www.dropbox.com/s/irruhz7tqe0gw02/Screen%20Shot%202021-03-22%20at%209.01.54%20PM.png?dl=0)


