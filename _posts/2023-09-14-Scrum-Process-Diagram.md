---
toc: false
comments: false
layout: post
title: Scrum Process Diagram
description: false
type: hacks
courses: { compsci: {week: 4} }
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scrum Process Diagram</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
            font-family: Arial, sans-serif;
        }
        .process-container {
            display: flex;
            align-items: center;
        }
        .box {
            width: 120px;
            height: 80px;
            background-color: #3498db;
            border: 2px solid #2980b9;
            text-align: center;
            line-height: 80px;
            color: #000;
            font-size: 16px;
            font-weight: bold;
            margin: 0 20px;
            border-radius: 8px;
        }
        .arrow {
            display: inline-block;
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 10px 0 10px 10px;
            border-color: transparent transparent transparent #3498db;
            margin: 0 10px;
        }
    </style>
</head>
<body>
    <div class="process-container">
        <div class="box">Give Instructions<br>Scrum Master</div>
        <div class="arrow"></div>
        <div class="box">Sprint<br>Planning</div>
        <div class="arrow"></div>
        <div class="box">Assign Jobs for the Week<br>Scrum Master</div>
        <div class="arrow"></div>
        <div class="box">Sprint</div>
        <div class="arrow"></div>
        <div class="box">Sprint<br>Daily Scrum Meetings</div>
        <div class="arrow"></div>
        <div class="box">Sprint<br>Review Finished Work</div>
        <div class="arrow"></div>
        <div class="box">Sprint<br>Review/Reflection</div>
    </div>
</body>
</html>
