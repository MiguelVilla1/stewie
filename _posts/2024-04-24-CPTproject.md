---
layout: default
title: Higher or Lower Number Guesser
permalink: /CPTgame
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number Guessing Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
    </style>
</head>
<body>
    <h1>Number Guessing Game</h1>
    <p>Guess a number between 1 and 100:</p>
    <input type="number" id="guessInput">
    <button onclick="checkGuess()">Submit</button>
    <p id="hint"></p>
    <script>
        let randomNumber = Math.floor(Math.random() * 100) + 1;
        function checkGuess() {
            const guess = parseInt(document.getElementById('guessInput').value);
            const hintElement = document.getElementById('hint'); 
            if (guess === randomNumber) {
                hintElement.textContent = 'Congratulations! You guessed the number.';
                randomNumber = Math.floor(Math.random() * 100) + 1;
            } else if (guess < randomNumber) {
                hintElement.textContent = 'Higher';
            } else {
                hintElement.textContent = 'Lower';
            }
        }
    </script>
</body>
</html>
