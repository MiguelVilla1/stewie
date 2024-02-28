---
toc: true
comments: true
layout: post
title: Casino lights demo
description: 
courses: { compsci: {week: 20} }
type: hacks
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Casino Lights Animation</title>
    <style>
        .container {
            text-align: center;
            margin-top: 50px;
        }
        #animation {
            display: block;
            margin: 0 auto;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Welcome to the Casino</h1>
        <p>Enjoy the lights!</p>
        <img id="animation" src="{{ url_for('static', filename='animation.png') }}" alt="Casino Lights Animation">
    </div>
</body>
</html>
