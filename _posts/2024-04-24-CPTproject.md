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
            background-color: #FF0000; /* Red background */
            color: #FFFFFF; /* White text */
            font-family: Arial, sans-serif; /* Font family */
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            text-align: center;
            padding-top: 50px;
        }
        .container {
            width: 80%;
            margin: 0 auto;
            padding: 20px;
        }
        input[type="text"],
        button {
            padding: 10px;
            margin-bottom: 10px;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            width: 200px;
        }
        button {
            background-color: #FFFFFF; /* White button background */
            color: #FF0000; /* Red button text color */
            cursor: pointer;
        }
        button:hover {
            background-color: #FF4500; /* Darker red on hover */
        }
        p {
            font-size: 18px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Number Guessing Game</h1>
    <p>Guess a number between 1 and 100:</p>
    <input type="text" id="guessInput">
    <button onclick="checkGuess()">Guess</button>
    <p id="feedback"></p>
    <p>Previous guesses:</p>
    <ul id="guessList"></ul>
</div>

<script>
    var secretNumber = Math.floor(Math.random() * 100) + 1;
    var previousGuesses = [];

    function checkGuess() {
        var guess = document.getElementById("guessInput").value;

        if (!isValidGuess(guess)) {
            document.getElementById("feedback").innerText = "Invalid input. Guess a number that's between 1 and 100.";
            return;
        }

        guess = parseInt(guess);
        previousGuesses.push(guess);

        var feedback = guessNumber(secretNumber, guess);
        document.getElementById("feedback").innerText = feedback;

        displayGuesses();
    }

    function isValidGuess(guess) {
        return !isNaN(guess) && guess >= 1 && guess <= 100;
    }

    function guessNumber(secretNumber, guess) {
        if (guess === secretNumber) {
            return "Congratulations! You guessed the correct number!";
        } else if (guess < secretNumber) {
            return "Higher";
        } else {
            return "Lower";
        }
    }

    function displayGuesses() {
        var guessList = document.getElementById("guessList");
        guessList.innerHTML = "";
        for (var i = 0; i < previousGuesses.length; i++) {
            var guessItem = document.createElement("li");
            guessItem.innerText = previousGuesses[i];
            guessList.appendChild(guessItem);
        }
    }

    function resetGame() {
        secretNumber = Math.floor(Math.random() * 100) + 1;
        previousGuesses = [];
        document.getElementById("feedback").innerText = "";
        displayGuesses();
    }

    function runTests() {
        // Test isValidGuess function
        console.assert(isValidGuess(50) === true);
        console.assert(isValidGuess(0) === false);
        console.assert(isValidGuess(101) === false);
        console.assert(isValidGuess("abc") === false);
    }

    // Run tests
    runTests();
    
    document.getElementById('resetButton').addEventListener('click', resetGame);


</script>

</body>
</html>
