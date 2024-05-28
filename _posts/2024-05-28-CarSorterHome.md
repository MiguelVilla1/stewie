---
toc: true
comments: false
layout: post
title: Car Sorter Home
courses: { compsci: {week: 31} }
type: hacks
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Homepage</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
        }
        h1 {
            margin: 20px 0;
        }
        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            margin: 20px;
        }
        .image-button {
            margin: 10px;
            border: 2px solid #ddd;
            border-radius: 10px;
            overflow: hidden;
            width: 200px;
            height: 150px;
            position: relative;
        }
        .image-button img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .image-button a {
            display: block;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            text-decoration: none;
            color: white;
            font-size: 20px;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s;
        }
        .image-button:hover a {
            opacity: 1;
        }
    </style>
</head>
<body>
    <h1>Welcome to Our Website</h1>
    <div class="container">
        <div class="image-button">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Ford_logo_flat.svg/2560px-Ford_logo_flat.svg.png" alt="Car 1">
            <a href="https://miguelvilla1.github.io/stewie//2024/05/27/CarSortingTables.html">Ford</a>
        </div>
        <div class="image-button">
            <img src="car2.jpg" alt="Car 2">
            <a href="page2.html">BMW</a>
        </div>
        <div class="image-button">
            <img src="car3.jpg" alt="Car 3">
            <a href="page3.html">Honda</a>
        </div>
    </div>
</body>
</html>
