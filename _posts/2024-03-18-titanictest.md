---
toc: true
comments: false
layout: post
title: Casino ML Test
courses: { compsci: {week: 26} }
type: hacks
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ARE YOU A WINNER?</title>
<style>
    body {
        background-image: url('https://www.guide-du-paysbasque.com/_bibli/annonces/4013/hd/casino-kursaal-23-03.jpg');
        font-family: 'Courier New', monospace;
        background-color: #D4AF37; /* Gold background */
        color: #FFFFFF; /* White text */
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
    }
    .container {
        background-color: #8B0000; /* Dark red container */
        padding: 20px;
        border-radius: 16px; /* Slightly rounded corners */
        box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3); /* Enhanced shadow */
        width: 125%; /* Increase width */
        max-width: 1500px; /* Set a max-width to limit the container size */
        text-align: center; /* Center the content */
        position: relative; /* Make the container positioned */
        left: 50%; /* Move container 50% to the right */
        transform: translateX(-50%); /* Translate container back by 50% of its own width */
    }
    h2 {
        font-family: 'Courier New', monospace;
        color: #FFD700; /* Gold for headings */
    }
    form {
        display: flex;
        flex-direction: column;
    }
    label {
        margin-top: 10px;
        color: #FFD700; /* Gold for labels */
    }
    input,
    select,
    button {
        padding: 12px; /* Slightly larger padding */
        margin-top: 8px; /* Slightly increased spacing */
        border: 2px solid #8B0000; /* Dark red border */
        border-radius: 8px; /* Slightly rounded corners */
        background-color: #B22222; /* Dark red background */
        color: #FFFFFF; /* White text */
    }
    input::placeholder {
        color: #CD853F; /* Lighter red for placeholder text */
        opacity: 1;
    }
    button {
        background-color: #CD853F; /* Lighter red button */
        color: #FFFFFF; /* White text */
        margin-top: 20px;
        transition: background-color 0.3s;
    }
    button:hover {
        background-color: #FF4500; /* Darker red hover */
    }
    #predictionResult {
        margin-top: 20px;
        text-align: center;
        padding: 12px; /* Slightly larger padding */
        background-color: #8B0000; /* Dark red result background */
        color: #FFFFFF; /* White text */
        border-radius: 8px; /* Slightly rounded corners */
        display: none;
    }
    .images {
        display: flex;
        justify-content: space-around;
        margin-top: 20px;
    }
    iframe {
        width: 45%;
        height: auto;
    }
    label {
        font-family: 'Courier New', monospace;
    }
</style>

</head>
<body>
    <div class="container">
        <h2>ARE YOU A WINNER?</h2>
        <form id="predictionForm">
            <!-- Your form inputs here -->
            <label for="pclass">Class:</label>
            <select id="pclass">
                <option value="1">Rich Gambler</option>
                <option value="2" selected>Average Gambler</option>
                <option value="3">Poor Gambler</option>
            </select>
            <label for="sex">Sex:</label>
            <select id="sex">
                <option value="1">Male</option>
                <option value="0">Female</option>
            </select>
            <label for="age">Age:</label>
            <input type="number" id="age" placeholder="18-90" required>
            <label for="sibsp">Siblings/Spouses Gambling With You:</label>
            <input type="number" id="sibsp" placeholder="Answer" required>
            <label for="parch">Parents/Children With You:</label>
            <input type="number" id="parch" placeholder="Answer" required>
            <label for="fare">Budget:</label>
            <input type="number" step="0.01" id="fare" placeholder="Answer" required>
            <label for="alone">Gambling Alone?:</label>
            <input type="checkbox" id="alone">
            <label for="embarked">Traveled From:</label>
            <select id="embarked">
                <option value="C">California</option>
                <option value="N">New York</option>
                <option value="A">Arizona</option>
            </select>
            <button type="submit">Your Probability of Winning Big:</button>
        </form>
        <div id="predictionResult"></div>
    </div>
    <script>
        document.getElementById('predictionForm').onsubmit = async function(e) {
            e.preventDefault();
            const formData = {
                pclass: document.getElementById('pclass').value,
                sex: document.getElementById('sex').value,
                age: document.getElementById('age').value,
                sibsp: document.getElementById('sibsp').value,
                parch: document.getElementById('parch').value,
                fare: document.getElementById('fare').value,
                alone: document.getElementById('alone').checked ? 1 : 0,
                embarked: document.getElementById('embarked').value
            };
            const response = await fetch('http://127.0.0.1:8086/api/titanic/predict', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(formData),
            });
            const result = await response.json();
            const resultDiv = document.getElementById('predictionResult');
            resultDiv.style.display = 'block';
            resultDiv.innerText = `Winning: ${result['LogisticRegression Survival Probability']}%`;
            Print("Always remember, gambling is not sustainable or healthy")
        };
    </script>
</body>
</html>
