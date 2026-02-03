---
author: Enoch Yu
title: "JavaScript Mini-Project 2: Stopwatch"
date: 2026-01-07
categories: ["Computer Science"]
tags: ["JS Mini-Project"]
---

As for my second project, I decided to make a stopwatch. After
reading and watching numerous tutorials, I was able to understand
the general logic of JavaScript stopwatch. The
[stopwatch](https://js.enochyu.com/projects/project2_TimerStopwatch/) and
[source code](https://github.com/enochyu-official/js-mini-projects/tree/main/projects/project2_TimerStopwatch)
are available. Please enjoy, and provide any feedback!!

## Introducing Project 2
The stopwatch that I created behaves like any other stopwatch.
It can start, pause, resume, and reset the counter accurately.
Surprisingly, the general logical structure was much more easier to
come up with than my
[first project](https://js.enochyu.com/projects/project1_CoffeeShop/).
The method to calculate the elapsed time is finding the difference
between current time and the time when the stopwatch started.
The function `Date.now()` will call the current time from the local
machine up to milliseconds! Below is a more detailed explanation
with source code.

## Reviewing the Source Code
### HTML
Below is the body of the HTML markup for the stopwatch.
```html
<body>
  <div class="container">
    <h2>STOPWATCH</h2>
    <div id="stopwatch">
      <span class="count" id="hour">00</span>
      <span class="unit">HR</span>
      <span class="count" id="minute">00</span>
      <span class="unit">MIN</span>
      <span class="count" id="second">00</span>
      <span class="unit">SEC</span>
      <span class="count" id="millisecond">000</span>
      <span class="unit">MS</span>
    </div>
    <div id="buttons">
      <button type="button" class="button" id="startBtn">Start</button>
      <button type="button" class="button" id="pauseBtn">Pause</button>
      <button type="button" class="button" id="resetBtn">Reset</button>
    </div>
  </div>
  <script src="script.js"></script>
</body>
```
The structure is intuitive. There is a header, a division for
exhibiting numbers, and a division for buttons. Different
classes were used in the first division for ease in CSS.

### CSS
Below are few key styles from my CSS file.
```css
body, html {
  background-color: #141414;
  color: #f9f9f9;
  font-family: serif;
  margin: 0;
  border: 0;
  padding: 0;
  height: 100%;
}

```
Because I wanted my stopwatch to look opulent, I tried implementing
dark background and font serif. I am not sure if that did the job
though..
```css
h2 {
  font-family: Bodoni;
  margin-block-start: 0;
  margin-block-end: 0;
  font-size: 6dvw;
  font-weight: 400;
}

.count {
  font-size: 10dvw;
}

.unit {
  font-size: 2dvw
}
```
After learning my lessons from the first project, I decided to use
more responsive units like `dvw` to not rely on external files.

There are more style in the sheet. However, I will leave the rest
for all of you since the project is mainly about JavaScript.

### JS
As always, I started with declaring and assigning the variables.
```javascript
const startBtn = document.getElementById('startBtn');
const pauseBtn = document.getElementById('pauseBtn');
const resetBtn = document.getElementById('resetBtn');

const hr = document.getElementById('hour');
const min = document.getElementById('minute');
const sec = document.getElementById('second');
const ms = document.getElementById('millisecond');

let timeStarted;
let timePassed = 0;
let counter;
let runningStatus = false;
```
For comfort, buttons and time were assigned. Moreover, variables
that would be used to count were also declared.

Next, I started defining the functions.
```javascript
function start() {
  if (!runningStatus) {
    timeStarted = Date.now() - timePassed;
    counter = setInterval(display, 1);
    runningStatus = true;
  }
}
```
The first function "start" will properly execute if the
`runningStatus` boolean is false. The "timeStarted" will be
defined as the difference between current time `Date.now()` and
`timePassed`, which is initially assigned as zero. Here, the
reason for not assigning value for `timePassed` in the function
is to properly execute "resume" after the pause.

The next function `setInterval(display, 1)` will theoretically
run the function "display" every millisecond. The step is
*theoretical* due to browser throttling and other factors.
Subsequently, it will set the boolean of `runningStatus` as true.

Similarly, the "pause" and "reset" function were intuitively
defined. However, the "display" function required a different
approach.
```javascript
function display() {
  timePassed = Date.now() - timeStarted;
  let finalHr = String(Math.floor(timePassed / (60 * 60 * 1000))).padStart(2, '0');
  let finalMin = String(Math.floor(timePassed / (60 * 1000)) % 60).padStart(2, '0');
  let finalSec = String(Math.floor(timePassed / 1000) % 60).padStart(2, '0');
  let finalMs = String(timePassed % 1000).padStart(3, '0');

  hr.textContent = `${finalHr}`;
  min.textContent = `${finalMin}`;
  sec.textContent = `${finalSec}`;
  ms.textContent = `${finalMs}`;
}
```
First, we must notice that `Date.now()` will return current
timestamp in milliseconds since the Unix epoch. For instance, as
of the time I am writing this post right now, in January 7,
approximately 1767778367064 milliseconds passed since the Unix epoch
(January 1, 1970, 00:00:00 UTC). Therefore, `Math.floor()` and
modular arithmetic with `%` will return the desired value.
Moreover, `String().padStart(2, '0')` was used for leading zeros.

The rest of the script follows similar pattern and commands!!

## Lessons
Through this project, I grew accustom to new functions and math in
JavaScript. Especially, `Date.now`, `if (!someBoolean)`, and
`Math.floor()` caught my attention as it helped me learn about Unix
time, convenient method of writing conditional statements, and using
math in JavaScript. As a math enthusiast, it was intriguing to link
both my interests, math and computer science, together. As for my
next project, I am planning to make a JavaScript calculator. Please
look forward to my future posts!!


{{< comments-note >}}


