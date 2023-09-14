---
toc: false
comments: false
layout: post
title: 2 Player Pong
description: This code provides a basic implementation of a Tetris game using HTML, CSS, and JavaScript. It includes a simple game loop, drawing functions, and basic controls for moving and rotating the pieces. You can see the falling piece and it merges with the board when it reaches the bottom or encounters a placed block.
type: hacks
courses: { compsci: {week: 4} }
---

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2-Player Pong</title>
    <style>
        body {
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #000;
        }
        canvas {
            border: 2px solid white;
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas" width="800" height="400"></canvas>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const canvas = document.getElementById('gameCanvas');
            const ctx = canvas.getContext('2d');
            const paddleWidth = 10;
            const paddleHeight = 80;
            const ballSize = 10;
            let player1Y = (canvas.height - paddleHeight) / 2;
            let player2Y = (canvas.height - paddleHeight) / 2;
            let ballX = canvas.width / 2;
            let ballY = canvas.height / 2;
            let ballDX = 2;
            let ballDY = 2;

            function draw() {
                // Clear the canvas
                ctx.clearRect(0, 0, canvas.width, canvas.height);

                // Draw paddles
                ctx.fillStyle = 'white';
                ctx.fillRect(0, player1Y, paddleWidth, paddleHeight);
                ctx.fillRect(canvas.width - paddleWidth, player2Y, paddleWidth, paddleHeight);

                // Draw ball
                ctx.fillRect(ballX - ballSize / 2, ballY - ballSize / 2, ballSize, ballSize);

                // Move ball
                ballX += ballDX;
                ballY += ballDY;

                // Ball collision with top and bottom walls
                if (ballY - ballSize / 2 <= 0 || ballY + ballSize / 2 >= canvas.height) {
                    ballDY = -ballDY;
                }

                // Ball collision with paddles
                if (ballX - ballSize / 2 <= paddleWidth) {
                    if (ballY > player1Y && ballY < player1Y + paddleHeight) {
                        ballDX = -ballDX;
                    } else {
                        // Player 2 scores a point
                        resetBall();
                    }
                } else if (ballX + ballSize / 2 >= canvas.width - paddleWidth) {
                    if (ballY > player2Y && ballY < player2Y + paddleHeight) {
                        ballDX = -ballDX;
                    } else {
                        // Player 1 scores a point
                        resetBall();
                    }
                }

                requestAnimationFrame(draw);
            }

            function resetBall() {
                ballX = canvas.width / 2;
                ballY = canvas.height / 2;
            }

            // Player 1 controls
            document.addEventListener('keydown', (e) => {
                if (e.key === 'w' && player1Y > 0) {
                    player1Y -= 10;
                } else if (e.key === 's' && player1Y < canvas.height - paddleHeight) {
                    player1Y += 10;
                }
            });

            // Player 2 controls
            document.addEventListener('keydown', (e) => {
                if (e.key === 'ArrowUp' && player2Y > 0) {
                    player2Y -= 10;
                } else if (e.key === 'ArrowDown' && player2Y < canvas.height - paddleHeight) {
                    player2Y += 10;
                }
            });

            draw();
        });
    </script>
</body>
</html>
