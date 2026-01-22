---
author: Enoch Yu
title: "JavaScript Mini-Project 1: Coffee Shop"
date: 2026-01-05
categories: ["Computer Science"]
tags: ["JS Mini-Project"]
---

Before getting started with competitive programming, I decided to motivate myself with small JavaScript projects, mainly for growing accustomed to coding and learning logics. As for my first JavaScript mini-project, I decided to create a Coffee Shop simply because I love coffee and coffee shops. For your reference, here is the [Coffee Shop](https://enochyu-js.pages.dev/projects/project1_CoffeeShop/) and the [source code](https://github.com/enochyu-official/js-mini-projects/tree/main/projects/project1_CoffeeShop) of the project. Please feel free to leave any feedback in the comment section below for improvements!!

## Introducing Project 1
In this project, I wanted each phase to be separated with new sections and slides. With each input, the robot receiving the order will retain the information and utilize it in next phase. To practice using `<div>` tag in html, I decided to change the background color and robot's expression in new slides. Notice that when the customer entered a value that is not in the menu, the robot's expression will change. Moreover, in the last phase, the brew time is equal to two times the number of coffee ordered.

## Reviewing the Source Code
### HTML
The full HTML markup is available in [GitHub](https://github.com/enochyu-official/js-mini-projects/blob/main/projects/project1_CoffeeShop/index.html). Because most of my sections follow same style as the first section, here is a brief description of the first section.
```html
<section class="slide" id="greeting">
  <div class="ascii-background">
    <pre>
                    o                              o
                     \                            /
                      \                          /
                       \                        /
                        \______________________/
                        |                      |
                        |   /\     oo     /\   |
                        |______________________|
    ___________________/                        \___________________ 
   /                                                                \
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
@  |                                                                |  *
 \ |                                                                | /
  \|                                                                |/
   #                                                                #
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   |                                                                |
   \________________________________________________________________/
    </pre>
  </div>

  <div class="robot-input" id="greeting-div">
    <label id="question-name">Hi!! What is your name?</label>
    <br> 
    <input class="inputBox" id="name">
    <button class="button" id="name-button">Submit</button>
  </div>
</section>
```
I wrapped my ASCII art and buttons in a section with class "slides" and id "greeting" because I would be the first phase of the order that contains the art and input box. Moreover, the robot in the division with class "ascii-background" was drawn inside `<pre>` tag since it preserves the white spaces.

In the next division, the actual input and buttons were defined. Id and class were used to define function and the style of the elements.

### CSS
Here is the link to my [CSS Style Sheet](https://github.com/enochyu-official/js-mini-projects/blob/main/projects/project1_CoffeeShop/style.css). Because styling the elements does not significantly affect the motive of the project, please review the file and provide any feedback!

### JS
Here is the link to full [JS script](https://github.com/enochyu-official/js-mini-projects/blob/main/projects/project1_CoffeeShop/script.js). Because this is my first script writing entirely on my own with online tutorials, the script may not be in its ideal version. Anyhow, here is a brief description to each parts.

Unlike Python, modern JavaScript requires declaring of the variable before assigning it.
```javascript
let order;
let price;
let nextSlide;
const menuItem = [ "Espresso", "espresso", "Ristretto", "ristretto", "Americano", "americano", "Cappuccino", "cappuccino" ];
```
I first declared the variables that will be used before defining any functions.

```javascript
function NextSlide(slideButton){
  nextSlide = document.getElementById(slideButton);

  document.getElementById(slideButton).style.display = "block";

  nextSlide.scrollIntoView({ behavior: "smooth" });
};
```
This is the part that defines the function named "NextSlide". It will first define a variable "nextSlide" as an element with id "slideButton" in the document. Then, the element with id "slideButton" will be displayed as a block. Lastly, the "nextSlide" will be visible with a smooth scroll. Its application is shown below.

```javascript
document.getElementById("project-button").onclick = () => NextSlide("greeting");
```
After clicking an element with id "project-button", the function "NextSlide" will be initiated on "greeting".

Similarly, below defines the behavior when the element with id "name-button" is clicked. Here, `().textContent` will help display the content in dedicated locations. Moreover, `${name}` will reuse the saved information from the input.
```javascript
document.getElementById("name-button").onclick = function(){
  let name = document.getElementById("name").value;

  document.getElementById("opening-statement").textContent =
    `Nice to meet you ${name}!\n` +
    `Below is the available menu:`;

  document.getElementById("menu").textContent =
    "  Espresso: $3\n" +
    "  Ristretto: $2.5\n" +
    "  Americano: $4\n" +
    "  Cappuccino: $5";

  document.getElementById("order-statement").textContent =
    `What would you like to order today?`;

  document.getElementById("ordering").style.display = "block";

  NextSlide("ordering");
};
```
Here, I utilized the function NextSlide again to scroll to the next slide.

Below is the last section that introduces new concept of if-else statement.
```javascript
function OrderOutput(order) {
  document.getElementById("order-reorder").textContent = "";
  document.getElementById("order-remenu").textContent = "";

  /* 
  while (true) {
    if (order == "Espresso") {
      price = 3;
      break;
  } else if (order == "Ristretto") {
      price = 2.5;
      break;
  } else if (order == "Americano") {
      price = 4;
      break;
  } else if (order == "Cappuccino") {
      price = 5;
      break;
  } else {
      document.getElementById("order-reorder").textContent =
        `I am sorry. ${order} is currently not available. Please select from the menu below.`;
      document.getElementById("order-remenu").textContent =
        "  Espresso: $3\n" +
        "  Ristretto: $2.5\n" +
        "  Americano: $4\n" +
        "  Cappuccino: $5";

      document.getElementById("reorder-input").style.display = "block";
      document.getElementById("reorder-button").style.display = "block";
    }
  };
  */
 
  switch (order) {
    case "Espresso":
      price = 3;
      break;

    case "espresso":
      price = 3;
      break;

    case "Ristretto":
      price = 2.5;
      break;

    case "ristretto":
      price = 2.5;
      break;

    case "Americano":
      price = 4;
      break;

    case "americano":
      price = 4;
      break;

    case "Cappuccino":
      price = 5;
      break;

    case "cappuccino":
      price = 5;
      break;

    default:
      document.getElementById("first-ascii").style.display = "none";
      document.getElementById("second-ascii").style.display = "block";
      document.getElementById("order-reorder").textContent =
        `I am sorry. ${order} is currently not available.\n` +
        `Please select from the menu below.`;

      document.getElementById("order-remenu").textContent =
        "  Espresso: $3\n" +
        "  Ristretto: $2.5\n" +
        "  Americano: $4\n" +
        "  Cappuccino: $5";

      document.getElementById("first-order").style.display = "none";
      document.getElementById("reorder-input").style.display = "block";
      document.getElementById("reorder-button").style.display = "block";

      return;
  };

  document.getElementById("number-statement").textContent =
    `How many cups of ${order} would you like?`;

  NextSlide("ordering-number");
  document.getElementById("ordering-number").style.display = "block";
  document.getElementById("number-ascii").style.display = "block";
}
```
The commented if-else statements is the original script that I used, and it works fine. However, because I am not a huge fan of using if-else statements numerous times, I decided to use switch statement, which is a great replacement. From there, the same logic and properties were used to complete the project.


## Lessons
From this project, I was able be more familiarized with different properties such as `document.getElementById`, `().textContent`, switch statement, and logical structures. Moreover, I realized that making a website responsive requires love and care. Mobile-first approach and using responsive components such as `rem` was also a new concept that I learned. As for my next project, I am planning to make a stopwatch with JavaScript!!! Thank you~


{{< comments-note >}}

