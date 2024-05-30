---
toc: true
comments: false
layout: post
title: BMW Sorter
courses: { compsci: {week: 35} }
type: hacks
permalink: /BMWmodels
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMW Car Models</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background: url('https://cdn.dicklovett.co.uk/uploads/header_image/2_90_l.jpg?v=1643385270') no-repeat center center fixed;
            background-size: cover;
        }
        h1 {
            text-align: center;
            color: white;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background-color: white;
        }
        th, td {
            padding: 10px;
            border: 1px solid #ddd;
            text-align: left;
            color: white;
            color: #333;
        }
        th {
            cursor: pointer;
            background-color: #f2f2f2;
        }
        th:hover {
            background-color: #ddd;
        }
        th.sort-asc:after {
            content: " ▲";
        }
        th.sort-desc:after {
            content: " ▼";
        }
        button {
            display: block;
            margin: 20px auto;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
<button id="HomeButton" onclick="location.href='CarHome';">Back To Home</button>

<body>
    <h1>BMW Car Models</h1>
    <button id="fetchDataBtn">Retrieve Data</button>
    <table id="carTable">
        <thead>
            <tr>
                <th onclick="sortTable('model_name')">Model</th>
                <th onclick="sortTable('year')">Year</th>
                <th onclick="sortTable('price')">Price</th>
                <th onclick="sortTable('horsepower')">Horsepower</th>
            </tr>
        </thead>
        <tbody>
            <!-- Data will be inserted here -->
        </tbody>
    </table>
    <script>
        document.getElementById('fetchDataBtn').addEventListener('click', fetchCarData);
        let currentSortColumn = '';
        let currentSortOrder = 'asc';
        function fetchCarData() {
            fetch('http://127.0.0.1:5000/cars/bmw')
                .then(response => response.json())
                .then(data => {
                    populateTable(data);
                })
                .catch(error => {
                    console.error('Error fetching data:', error);
                });
        }
        function sortTable(column) {
            if (currentSortColumn === column) {
                currentSortOrder = currentSortOrder === 'asc' ? 'desc' : 'asc';
            } else {
                currentSortColumn = column;
                currentSortOrder = 'asc';
            }
            fetch(`http://127.0.0.1:5000/sort_cars/bmw?sort_by=${column}&order=${currentSortOrder}`)
                .then(response => response.json())
                .then(data => {
                    populateTable(data);
                    updateSortIndicators(column);
                })
                .catch(error => {
                    console.error('Error sorting data:', error);
                });
        }
        function populateTable(data) {
            const tableBody = document.getElementById('carTable').getElementsByTagName('tbody')[0];
            tableBody.innerHTML = ''; // Clear previous data
            data.forEach(car => {
                const row = tableBody.insertRow();
                row.insertCell(0).innerText = car.model_name;
                row.insertCell(1).innerText = car.year;
                row.insertCell(2).innerText = `$${car.price.toFixed(2)}`;
                row.insertCell(3).innerText = car.horsepower;
            });
        }
        function updateSortIndicators(column) {
            const ths = document.querySelectorAll("#carTable th");
            ths.forEach(th => {
                th.classList.remove("sort-asc", "sort-desc");
            });
            const sortedTh = Array.from(ths).find(th => th.innerText.toLowerCase() === column);
            if (sortedTh) {
                sortedTh.classList.add(currentSortOrder === 'asc' ? 'sort-asc' : 'sort-desc');
            }
        }
    </script>
</body>

