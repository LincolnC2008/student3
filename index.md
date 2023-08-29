---
layout: default
title: Student Blog
---


## Lincoln Crowell's Page 
This is my blog for AP Computer Scinece Principles

![](<images/WIN_20230823_15_11_51_Pro.jpg>)

## About Me


- I have always lived in the US, however I have travelled and lived in many other countries longer than I have lived in the UK, hence the british flag in my picture.
- I have many hobbies but 1 hobby that is very important to me is fishing, I have gone fishing since I was 7 with my dad, and it is still something I like to do every summer.
- I have 2 sisters named Brooklyn and Zuzu, a mom named Cindy, and a dad named Jason. that is who the people in my picture are. We are all Chriastain which is where the cross comes from.
- Another hobby I have is gaming, I put that on there because it is also something I like to do with my sisters.
![](<images/IMG-2487.jpg>)


## I have a picture of me and my dad going fishing,  and on this day we caught a fish over 200lbs!

![](<images/IMG_1500.jpg>)

## This is a video I used to help me with coding

<iframe width="560" height="315" src="https://www.youtube.com/embed/wjbbl0TTMeo?si=hHdkr4Lk7XFZMw1u" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Problems I encountered while coding
I had encountered problems at the very start and a major problem being how I had not installed WSL Ubuuntu properly, WSL kept showing up with "root" so as a result I had to restart everything and reinstall the whole thing again. I am not certain, but I think the problem was when I made my username as I put the wrong one so I tried uninstalling, but I did not uninstall all the way so I looked up videos for help over the weekend until I eventually got it working. I had also encountered problems with inserting videos becasue when I was inserting the links, I did not realise they had to be embeded links so the videos would not work as it would say that the link is not found. As far as inserting pictures, I was struggling when copying the "link" to the picture as I did not realise when you drag and drop the photo into images you have to copy relative.

<body style="width=100px;border:1px solid red;">

Snake Game
credit: https://www.studytonight.com/post/snake-game-in-html-and-javascript#:~:text=Following%20is%20the%20HTML%20code%20where%20we%20have,class%3D%22game-info%22%3E%20%3Ch2%3ESnake%20Game%3C%2Fh2%3E%20%3Cp%20id%3D%22game-status%22%3E%3C%2Fp%3E%20%3Cp%20id%3D%22game-score%22%3E%3C%2Fp%3E%20%3C%2Fdiv%3E
<!DOCTYPE html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Snake Game using HTML and Javascript - Studytonight</title>
    <style>
        .game-box {
            text-align:center;   
        }
        .game-info {
            text-align:center; 
            font-family:arial;
            line-height:24px;
        }
    </style>
  </head>
  <body>
    <div class="game-box"><canvas id="canvas" width="400" height="400"></canvas></div>
    <div class="game-info">
        <h2>Snake Game</h2>
        <p id="game-status"></p>
        <p id="game-score"></p>
    </div>

    <script>
      var canvas, ctx, gameControl, gameActive;
      // render X times per second
      var x = 8;
      
      const CANVAS_BORDER_COLOUR = 'black';
      const CANVAS_BACKGROUND_COLOUR = "white";
      const SNAKE_COLOUR = 'lightgreen';
      const SNAKE_BORDER_COLOUR = 'darkgreen';


      window.onload = function() {
        canvas = document.getElementById("canvas");
        ctx = canvas.getContext("2d");

        document.addEventListener("keydown", keyDownEvent);

        gameControl = startGame(x);
      };
      
      /* function to start the game */
      function startGame(x) {
          // setting gameActive flag to true
          gameActive = true;
          document.getElementById("game-status").innerHTML = "<small>Game Started</small>";
          document.getElementById("game-score").innerHTML = "";
          return setInterval(draw, 1000 / x);
      }
      
      function pauseGame() {
          // setting gameActive flag to false
          clearInterval(gameControl);
          gameActive = false;
          document.getElementById("game-status").innerHTML = "<small>Game Paused</small>";
      }
      
      function endGame(x) {
          // setting gameActive flag to false
          clearInterval(gameControl);
          gameActive = false;
          document.getElementById("game-status").innerHTML = "<small>Game Over</small>";
          document.getElementById("game-score").innerHTML = "<h1>Score: " + x + "</h1>";
      }

      // game world
      var gridSize = (tileSize = 20); // 20 x 20 = 400
      var nextX = (nextY = 0);

      // snake
      var defaultTailSize = 3;
      var tailSize = defaultTailSize;
      var snakeTrail = [];
      var snakeX = (snakeY = 10);

      // apple
      var appleX = (appleY = 15);

      // draw
      function draw() {
        // move snake in next pos
        snakeX += nextX;
        snakeY += nextY;

        // snake over game world?
        if (snakeX < 0) {
          snakeX = gridSize - 1;
        }
        if (snakeX > gridSize - 1) {
          snakeX = 0;
        }

        if (snakeY < 0) {
          snakeY = gridSize - 1;
        }
        if (snakeY > gridSize - 1) {
          snakeY = 0;
        }

        //snake bite apple?
        if (snakeX == appleX && snakeY == appleY) {
          tailSize++;

          appleX = Math.floor(Math.random() * gridSize);
          appleY = Math.floor(Math.random() * gridSize);
        }

        //  Select the colour to fill the canvas
      ctx.fillStyle = CANVAS_BACKGROUND_COLOUR;
      //  Select the colour for the border of the canvas
      ctx.strokestyle = CANVAS_BORDER_COLOUR;

      // Draw a "filled" rectangle to cover the entire canvas
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      // Draw a "border" around the entire canvas
      ctx.strokeRect(0, 0, canvas.width, canvas.height);

        // paint snake
        ctx.fillStyle = SNAKE_COLOUR;
        ctx.strokestyle = SNAKE_BORDER_COLOUR;
        for (var i = 0; i < snakeTrail.length; i++) {
          ctx.fillRect(
            snakeTrail[i].x * tileSize,
            snakeTrail[i].y * tileSize,
            tileSize,
            tileSize
          );
          
          ctx.strokeRect(snakeTrail[i].x * tileSize , snakeTrail[i].y* tileSize, tileSize, tileSize);

          //snake bites it's tail?
          if (snakeTrail[i].x == snakeX && snakeTrail[i].y == snakeY) {
            if(tailSize > 3) {
                endGame(tailSize);
            }
            tailSize = defaultTailSize;  
          }
        }

        // paint apple
        ctx.fillStyle = "red";
        ctx.fillRect(appleX * tileSize, appleY * tileSize, tileSize, tileSize);

        //set snake trail
        snakeTrail.push({ x: snakeX, y: snakeY });
        while (snakeTrail.length > tailSize) {
          snakeTrail.shift();
        }
      }

      // input
      function keyDownEvent(e) {
        switch (e.keyCode) {
          case 37:
            nextX = -1;
            nextY = 0;
            break;
          case 38:
            nextX = 0;
            nextY = -1;
            break;
          case 39:
            nextX = 1;
            nextY = 0;
            break;
          case 40:
            nextX = 0;
            nextY = 1;
            break;
          case 32:
            if(gameActive == true) {
                pauseGame();
            }
            else {
                gameControl = startGame(x);
            }
            break;
        }
      }
    </script>
  </body>
</html>

Calculator
---
title: JS Calculator
comments: true
hide: true
layout: default
description: A common way to become familiar with a language is to build a calculator.  This calculator shows off button with actions.
permalink: /techtalk/home_style
categories: [C7.0]
courses: { csse: {week: 2}, csp: {week: 2, categories: [2.C]}, csa: {week: 2} }
type: ccc
---

<!-- 
Hack 0: Right justify result
Hack 1: Test conditions on small, big, and decimal numbers, report on findings. Fix issues.
Hack 2: Add the common math operation that is missing from calculator
Hack 3: Implement 1 number operation (ie SQRT) 
-->

<!-- 
HTML implementation of the calculator. 
-->

{% include nav_home.html %}

<!-- 
    Style and Action are aligned with HRML class definitions
    style.css contains majority of style definition (number, operation, clear, and equals)
    - The div calculator-container sets 4 elements to a row
    Background is credited to Vanta JS and is implemented at bottom of this page
-->
<style>
  .calculator-output {
    /* calulator output 
      top bar shows the results of the calculator;
      result to take up the entirety of the first row;
      span defines 4 columns and 1 row
    */
    grid-column: span 4;
    grid-row: span 1;
  
    border-radius: 10px;
    padding: 0.25em;
    font-size: 20px;
    border: 5px solid black;
  
    display: flex;
    align-items: center;
  }
</style>

<!-- Add a container for the animation -->
<div id="animation">
  <div class="calculator-container">
      <!--result-->
      <div class="calculator-output" id="output">0</div>
      <!--row 1-->
      <div class="calculator-number">1</div>
      <div class="calculator-number">2</div>
      <div class="calculator-number">3</div>
      <div class="calculator-operation">+</div>
      <!--row 2-->
      <div class="calculator-number">4</div>
      <div class="calculator-number">5</div>
      <div class="calculator-number">6</div>
      <div class="calculator-operation">-</div>
      <!--row 3-->
      <div class="calculator-number">7</div>
      <div class="calculator-number">8</div>
      <div class="calculator-number">9</div>
      <div class="calculator-operation">*</div>
      <!--row 4-->
      <div class="calculator-clear">A/C</div>
      <div class="calculator-number">0</div>
      <div class="calculator-number">.</div>
      <div class="calculator-equals">=</div>
  </div>
</div>

<!-- JavaScript (JS) implementation of the calculator. -->
<script>
// initialize important variables to manage calculations
var firstNumber = null;
var operator = null;
var nextReady = true;
// build objects containing key elements
const output = document.getElementById("output");
const numbers = document.querySelectorAll(".calculator-number");
const operations = document.querySelectorAll(".calculator-operation");
const clear = document.querySelectorAll(".calculator-clear");
const equals = document.querySelectorAll(".calculator-equals");

// Number buttons listener
numbers.forEach(button => {
  button.addEventListener("click", function() {
    number(button.textContent);
  });
});

// Number action
function number (value) { // function to input numbers into the calculator
    if (value != ".") {
        if (nextReady == true) { // nextReady is used to tell the computer when the user is going to input a completely new number
            output.innerHTML = value;
            if (value != "0") { // if statement to ensure that there are no multiple leading zeroes
                nextReady = false;
            }
        } else {
            output.innerHTML = output.innerHTML + value; // concatenation is used to add the numbers to the end of the input
        }
    } else { // special case for adding a decimal; can't have two decimals
        if (output.innerHTML.indexOf(".") == -1) {
            output.innerHTML = output.innerHTML + value;
            nextReady = false;
        }
    }
}

// Operation buttons listener
operations.forEach(button => {
  button.addEventListener("click", function() {
    operation(button.textContent);
  });
});

// Operator action
function operation (choice) { // function to input operations into the calculator
    if (firstNumber == null) { // once the operation is chosen, the displayed number is stored into the variable firstNumber
        firstNumber = parseInt(output.innerHTML);
        nextReady = true;
        operator = choice;
        return; // exits function
    }
    // occurs if there is already a number stored in the calculator
    firstNumber = calculate(firstNumber, parseFloat(output.innerHTML)); 
    operator = choice;
    output.innerHTML = firstNumber.toString();
    nextReady = true;
}

// Calculator
function calculate (first, second) { // function to calculate the result of the equation
    let result = 0;
    switch (operator) {
        case "+":
            result = first + second;
            break;
        case "-":
            result = first - second;
            break;
        case "*":
            result = first * second;
            break;
        case "/":
            result = first / second;
            break;
        default: 
            break;
    }
    return result;
}

// Equals button listener
equals.forEach(button => {
  button.addEventListener("click", function() {
    equal();
  });
});

// Equal action
function equal () { // function used when the equals button is clicked; calculates equation and displays it
    firstNumber = calculate(firstNumber, parseFloat(output.innerHTML));
    output.innerHTML = firstNumber.toString();
    nextReady = true;
}

// Clear button listener
clear.forEach(button => {
  button.addEventListener("click", function() {
    clearCalc();
  });
});

// A/C action
function clearCalc () { // clears calculator
    firstNumber = null;
    output.innerHTML = "0";
    nextReady = true;
}
</script>

<!-- 
Vanta animations just for fun, load JS onto the page
-->
<script src="/teacher/assets/js/three.r119.min.js"></script>
<script src="/teacher/assets/js/vanta.halo.min.js"></script>
<script src="/teacher/assets/js/vanta.birds.min.js"></script>
<script src="/teacher/assets/js/vanta.net.min.js"></script>
<script src="/teacher/assets/js/vanta.rings.min.js"></script>

<script>
// setup vanta scripts as functions
var vantaInstances = {
  halo: VANTA.HALO,
  birds: VANTA.BIRDS,
  net: VANTA.NET,
  rings: VANTA.RINGS
};

// obtain a random vanta function
var vantaInstance = vantaInstances[Object.keys(vantaInstances)[Math.floor(Math.random() * Object.keys(vantaInstances).length)]];

// run the animation
vantaInstance({
  el: "#animation",
  mouseControls: true,
  touchControls: true,
  gyroControls: false
});
</script>

