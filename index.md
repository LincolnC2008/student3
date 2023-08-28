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