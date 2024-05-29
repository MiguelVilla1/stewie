---
toc: true
comments: false
layout: post
title: Car Sorter Home
courses: { compsci: {week: 31} }
type: hacks
permalink: /CarHome
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
            background: url('https://media.istockphoto.com/id/1156933946/photo/international-race-track.jpg?s=612x612&w=0&k=20&c=1PMCZ35aqdXimlTYz9WE1TF3IA_X_FAI7ObGhqveo7M=') no-repeat center center fixed;
            background-size: cover;
        }
        h1 {
            margin: 40px 0; /* Increased margin */
            color: #fff; /* Changed color to white for better readability on dark background */
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7); /* Added text shadow for better readability */
        }
        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            margin: 20px auto; /* Centered container and adjusted margin */
            max-width: 800px; /* Added max-width for better responsiveness */
            background-color: rgba(255, 255, 255, 0.8); /* Added semi-transparent background */
            border-radius: 10px; /* Rounded corners */
            padding: 20px; /* Added padding */
        }
        .image-button {
            margin: 20px;
            border: 2px solid #ddd;
            border-radius: 10px;
            overflow: hidden;
            width: 200px;
            height: 150px;
            position: relative;
            transition: transform 0.3s ease; /* Added smooth transition */
        }
        .image-button:hover {
            transform: scale(1.05); /* Increased size on hover */
        }
        .image-button img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .image-button a {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            text-decoration: none;
            color: white;
            font-size: 18px; /* Adjusted font size */
            background-color: rgba(0, 0, 0, 0.7); /* Improved contrast */
            padding: 10px 20px; /* Added padding */
            border-radius: 5px; /* Added border radius */
            opacity: 0; /* Hidden by default */
            transition: opacity 0.3s;
        }
        .image-button:hover a {
            opacity: 1; /* Visible on hover */
        }
    </style>
</head>
<body>
    <h1>Welcome to Our Dealership! Choose a Car Brand Here:</h1>
    <div class="container">
        <div class="image-button">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Ford_logo_flat.svg/2560px-Ford_logo_flat.svg.png" alt="Car 1">
            <a href="FordModels">Ford</a>
        </div>
        <div class="image-button">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/44/BMW.svg/768px-BMW.svg.png" alt="Car 2">
            <a href="BMWmodels">BMW</a>
        </div>
        <div class="image-button">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Honda.svg/2560px-Honda.svg.png" alt="Car 3">
            <a href="HondaModels">Honda</a>
        </div>
    </div>
</body>
</html>
