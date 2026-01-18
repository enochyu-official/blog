---
author: Enoch Yu
title: "JavaScript Mini-Project 3: Guess the Number"
date: 2026-01-17 
categories: ["Computer Science"]
tags: ["JS Mini-Project"]
---

For my third project, I decided to create a fun guess the number game. [Guess the Number](https://enochyu-js.pages.dev/projects/project3_GuessTheNumber/) and its [source codes](https://github.com/enochyu-official/js-mini-projects/tree/main/projects/project3_GuessTheNumber) are available. Please note that because I did not utilize internet for my script, the solution may not be the optimal version. Let's get started!!

## Introducing Project 3
The product is rather simple. The client is given five chances to guess the random number between 1 and 100 inclusive. If the user guessed the number correctly, they are given the message "YOU WIN". However, if the client was not able to guess the number within five tries, the random number appears with the message "YOU LOSE". The script to activate the game was comparably simple. Below is a more detailed explanation on each components.

## Reviewing the Source Code
### HTML
The entire HTML file is available [here](https://github.com/enochyu-official/js-mini-projects/blob/main/projects/project3_GuessTheNumber/index.html).
```HTML
<div id="status">
  <span>
    Your guess is <span id="guess-status">yet to be made!</span>
  </span>
  <br>
  <span>
    Chances left: <span id="guess-chance">5</span>
  </span>
</div>
<div id="guess">
  <input type="number" id="guess-input" placeholder="1-100">
  <button type="button" id="guess-submit">Guess</button>
</div>
```
In order to actively change the content after each trial, I used `span` tag with id "guess-status" and "guess-chance". Moreover, for ease in CSS, I separated the prompt and user interface.

Just like my [first project](https://enochyu-js.pages.dev/projects/project1_CoffeeShop/) I utilized `pre` tag in order to effectively display ASCII art.
```HTML
<pre id="win">
      _____                   _______                   _____                            _____                    _____                    _____          
     |\    \                 /::\    \                 /\    \                          /\    \                  /\    \                  /\    \         
     |:\____\               /::::\    \               /::\____\                        /::\____\                /::\    \                /::\____\        
     |::|   |              /::::::\    \             /:::/    /                       /:::/    /                \:::\    \              /::::|   |        
     |::|   |             /::::::::\    \           /:::/    /                       /:::/   _/___               \:::\    \            /:::::|   |        
     |::|   |            /:::/~~\:::\    \         /:::/    /                       /:::/   /\    \               \:::\    \          /::::::|   |        
     |::|   |           /:::/    \:::\    \       /:::/    /                       /:::/   /::\____\               \:::\    \        /:::/|::|   |        
     |::|   |          /:::/    / \:::\    \     /:::/    /                       /:::/   /:::/    /               /::::\    \      /:::/ |::|   |        
     |::|___|______   /:::/____/   \:::\____\   /:::/    /      _____            /:::/   /:::/   _/___    ____    /::::::\    \    /:::/  |::|   | _____  
     /::::::::\    \ |:::|    |     |:::|    | /:::/____/      /\    \          /:::/___/:::/   /\    \  /\   \  /:::/\:::\    \  /:::/   |::|   |/\    \ 
    /::::::::::\____\|:::|____|     |:::|    ||:::|    /      /::\____\        |:::|   /:::/   /::\____\/::\   \/:::/  \:::\____\/:: /    |::|   /::\____\
   /:::/~~~~/~~       \:::\    \   /:::/    / |:::|____\     /:::/    /        |:::|__/:::/   /:::/    /\:::\  /:::/    \::/    /\::/    /|::|  /:::/    /
  /:::/    /           \:::\    \ /:::/    /   \:::\    \   /:::/    /          \:::\/:::/   /:::/    /  \:::\/:::/    / \/____/  \/____/ |::| /:::/    / 
 /:::/    /             \:::\    /:::/    /     \:::\    \ /:::/    /            \::::::/   /:::/    /    \::::::/    /                   |::|/:::/    /  
/:::/    /               \:::\__/:::/    /       \:::\    /:::/    /              \::::/___/:::/    /      \::::/____/                    |::::::/    /   
\::/    /                 \::::::::/    /         \:::\__/:::/    /                \:::\__/:::/    /        \:::\    \                    |:::::/    /    
 \/____/                   \::::::/    /           \::::::::/    /                  \::::::::/    /          \:::\    \                   |::::/    /     
                            \::::/    /             \::::::/    /                    \::::::/    /            \:::\    \                  /:::/    /      
                             \::/____/               \::::/    /                      \::::/    /              \:::\____\                /:::/    /       
                              ~~                      \::/____/                        \::/____/                \::/    /                \::/    /        
                                                       ~~                               ~~                       \/____/                  \/____/         
</pre>
<pre id="lose">
```
For anyone wondering, I utilized [Text to ASCII Art Generator (TAAG)](https://patorjk.com/software/taag/#p=display&f=Graffiti&t=Type+Something+&x=none&v=4&h=4&w=80&we=false) to generate the message.

### CSS
My entire style sheet is available [here](https://github.com/enochyu-official/js-mini-projects/blob/main/projects/project3_GuessTheNumber/style.css).

Instead of making my content mobile-first, I decided to use media query for mobile as my page is not extremely big.
```CSS
#introduction {
  display: block;
  font-size: 30px;
  text-align: center;
  padding-left: 3vw;
  padding-right: 3vw;
}

@media only screen and (max-width: 600px) {
  #introduction {
    font-size: 12px;
  }
}

@media (max-width: 768px) {
  #introduction {
    font-size: 16px;
  }
}
```
For my messages, I hid the contents with `display: none`.
```CSS
#win {
  color: #00ff00;
  font-size: 0.7vw;
  display: none;
  padding-top: 10px;
}
```

### JS
I believe there are numerous ways to generate a random number between 1 and 100 inclusive. The intuitive method that I came up with is the following.
```JS
const RanNum = Math.floor( 100 * Math.random() );
```
In JavaScript, `Math.random()` will generate a random number in the interval [0, 1]. Therefore, if I multiply the number by 100 and round the fractional part, I will be able to generate a random integer in the interval [0, 100].

Next, in order to "count" each trial, I utilized increment.
```JS
let trial = 0;

document.getElementById("guess-submit").addEventListener("click", () => {
  trial++;
  
  if (trial === 1) {
    guess1();
  } else if (trial === 2) {
    guess2();
  } else if (trial === 3) {
    guess3();
  } else if (trial === 4) {
    guess4();
  } else if (trial === 5) {
    guess5();
  }
});
```
After each click, the number of trial will increase. Moreover, I was able to map different functions to each trial.

Below is my function named `guess1`.
```JS
function guess1() {
  GueNum = document.getElementById("guess-input").value;

  if (GueNum > RanNum) {
    document.getElementById("guess-status").textContent = "high!";
    document.getElementById("guess-chance").textContent = "4";
  } else if (GueNum < RanNum) {
    document.getElementById("guess-status").textContent = "low!";
    document.getElementById("guess-chance").textContent = "4";
  } else {
    document.getElementById("guess-status").textContent = "correct!";
    document.getElementById("guess-chance").textContent = "0";
    document.getElementById("win").style.display = "block";
    document.getElementById("refresh").style.display = "block";
  }
}
```
The other functions follow the same method. With if-else statements, I was able to "tell" the computer what to do after each comparison.

## Lessons
A new function and logic were utilized in the project. `Math.random()` in JavaScript generates random real number in the interval [0, 1]. Moreover, increments could be utilized in various ways!!


{{< comments-note >}}
