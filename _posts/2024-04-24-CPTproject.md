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
    <p>Guess the number between 1 and 100:</p>
    <input type="text" id="guessInput">
    <button onclick="checkGuess()">Guess</button>
    <p id="feedback"></p>
</div>

<script>
    var secretNumber = Math.floor(Math.random() * 100) + 1;

    function checkGuess() {
        var guess = document.getElementById("guessInput").value;

        if (isNaN(guess) || guess < 1 || guess > 100) {
            document.getElementById("feedback").innerText = "Invalid input. Please enter a number between 1 and 100.";
        } else {
            guess = parseInt(guess);
            var feedback = guessNumber(secretNumber, guess);
            document.getElementById("feedback").innerText = feedback;
        }
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

    function playAgainPrompt() {
        var playAgainInput = prompt("Do you want to play again? (yes/no)").toLowerCase();
        if (playAgainInput === "yes") {
            secretNumber = Math.floor(Math.random() * 100) + 1;
        } else {
            alert("Thank you for playing!");
        }
    }

    function runTests() {
        // Test guessNumber function
        var secretNumberTest = 50;
        console.assert(guessNumber(secretNumberTest, 50) === "Congratulations! You guessed the correct number!");
        console.assert(guessNumber(secretNumberTest, 60) === "Lower");
        console.assert(guessNumber(secretNumberTest, 40) === "Higher");

        // Test playAgainPrompt function
        console.assert(playAgainPrompt("yes") === undefined);
        console.assert(playAgainPrompt("no") === undefined);
    }

    // Run tests
    runTests();
</script>

</body>
</html>
