<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Titanic Survival Prediction</title>
    <style>
        input[type="text"] {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <h1>Titanic Survival Prediction</h1>
    <p>Please provide your information:</p>
    <label for="name">Name:</label><br>
    <input type="text" id="name"><br>
    <label for="age">Age:</label><br>
    <input type="text" id="age"><br>
    <label for="gender">Gender:</label><br>
    <select id="gender">
        <option value="male">Male</option>
        <option value="female">Female</option>
    </select><br>
    <label for="pclass">Ticket Class:</label><br>
    <select id="pclass">
        <option value="1">1st Class</option>
        <option value="2">2nd Class</option>
        <option value="3">3rd Class</option>
    </select><br>
    <label for="fare">Fare:</label><br>
    <input type="text" id="fare"><br>
    <label for="sibsp">Number of Siblings/Spouses Aboard:</label><br>
    <input type="text" id="sibsp"><br>
    <label for="parch">Number of Parents/Children Aboard:</label><br>
    <input type="text" id="parch"><br>
    <label for="embarked">Embarked From:</label><br>
    <select id="embarked">
        <option value="C">Cherbourg</option>
        <option value="Q">Queenstown</option>
        <option value="S">Southampton</option>
    </select><br>
    <label for="alone">Travelling Alone?</label><br>
    <input type="checkbox" id="alone"><br>
    <button onclick="submitData()">Submit</button>
    <script>
        function submitData() {
            var name = document.getElementById("name").value;
            var age = parseFloat(document.getElementById("age").value);
            var gender = document.getElementById("gender").value;
            var pclass = parseInt(document.getElementById("pclass").value);
            var fare = parseFloat(document.getElementById("fare").value);
            var sibsp = parseInt(document.getElementById("sibsp").value);
            var parch = parseInt(document.getElementById("parch").value);
            var embarked = document.getElementById("embarked").value;
            var alone = document.getElementById("alone").checked;
            // Prepare data to send to backend
            var passengerData = {
                "name": name,
                "age": age,
                "sex": gender,
                "pclass": pclass,
                "fare": fare,
                "sibsp": sibsp,
                "parch": parch,
                "embarked": embarked,
                "alone": alone
            };
            // Send data to backend (replace 'backend_url' with actual backend URL)
            fetch('backend_url', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(passengerData),
            })
            .then(response => response.json())
            .then(data => {
                var result = data.survival ? "You would survive!" : "You would not survive.";
                alert(result);
            })
            .catch((error) => {
                console.error('Error:', error);
            });
        }
    </script>
</body>
</html>
