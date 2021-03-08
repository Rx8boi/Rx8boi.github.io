---
layout: post
title:      "Adding a lottie file to your React App"
date:       2021-03-07 22:42:31 -0500
permalink:  adding_a_lottie_file_to_your_react_app
---


If you're looking to spice up your portfolio project with another component or two in React why not try integrating a lottie file or two into your application? What's that? Never heard of lottie files? Well neither did I until I started looking into splash pages for my application. When it comes to React Native applications I don't know many other animations as efficient as LottieFiles. Lottie files are lightweight, scalable interative animations all in a `.json` file. Crazy right? You can create them yourselves or head to  [LottieFiles](https://lottiefiles.com/) and go through a few free ones and add them to your project like I did. 

Now to the fun part... 

Most of the docs tend to focus on utilizing React Native and mobile applications, but with abit of React no-how you can easily add a few to your application like i did. 

![](https://www.dropbox.com/s/iqlo45bp9fi65db/Step%201.png?dl=0)
## 1st Things 1st
So lets start by adding a file to the Intro page.
Download the lottie.json file you want to use and add it to your assets folder (however you have your React-app organized). 

![](https://www.dropbox.com/s/hominiua53btihe/Step%202.png?dl=0)

- Next we're going to install lottie-web so we can use the .json animations.
Head to your terminal and in the application folder run `npm install lottie-web`

![](https://www.dropbox.com/s/3ezd7xsvukjjyex/Screen%20Shot%202021-03-07%20at%209.20.42%20PM.png?dl=0)

- Once thats done lets move to your text editor for your application & create a new `Thinker.js` file (or whatever the animation is in your application) to start adding the component.

![](https://www.dropbox.com/s/c9p1jvenolxz9os/Step%203.png?dl=0)

We're going to start by importing lottie (that we just installed) as well as the Effect hook

```
import React, { useEffect, useRef } from "react";
import lottie from "lottie-web";
```

The Effect Hook lets you perform side effects in function components:

and since this is a functional component and we're using ES6 we're going to set 'Thinker' & 'Container' variables to export and later call in our div.

```
import React, { useEffect, useRef } from "react";
import lottie from "lottie-web";

const Thinker = () => {
  const container = useRef(null);

```

Next we'll have useEffect the first argument being a function & the second an empty array.

```
useEffect(() => {
    lottie.loadAnimation({
      container: container.current,   //where the element will exist in the DOM
      renderer: "svg",
      loop: true, //set to true if you want it to continuously play
      autoplay: true,
      animationData: require("../../assets/37478-intelligence-ai.json"), //set to where your animation is located
    });
  }, []);
```

Now for the rest of the thinker Component will have the return statement with the div className set to the container class which will have a reference to the variable container.

```
  return (
    <div>
      <div className="container" ref={container}></div>
    </div>
  );
};

export default Thinker;
```

![](https://www.dropbox.com/s/nowz9625m6girh3/step%206.png?dl=0)

Once that's set all thats left is to import the component into the Intro page and we'll be good to go!


## Wrapping it up
Go back to `Intro.js` and we'll import the component like usual & place the self closing `<Thinker />` tags where you want the Lottie file to be:

```
import React from "react";
import Thinker from "../components/lottie/Thinker";
import Container from "react-bootstrap/Container";
import Row from "react-bootstrap/Row";
import Col from "react-bootstrap/Col";

const Intro = () => {
  return (
    <div>
      <br></br>
      <Container> 
        <Row>
          <Col>
            <Thinker /> // I placed mine in a column beside the paragraphs
          </Col>
          <Col>
            <h1>Welcome To TimeLine App</h1>
```

Once that's done save your files & run `npm start` and see make sure everythings working!
If yes then you're good to go like me!

![](https://www.dropbox.com/s/e6rz5v0aor83adz/Step%204.png?dl=0)

Thanks for reading!

## Hope this was helpful!
