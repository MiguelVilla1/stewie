---
toc: true
comments: false
layout: post
title: Car Sorter
courses: { compsci: {week: 35} }
type: hacks
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ford Car Models</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            padding: 8px 12px;
            border: 1px solid #ddd;
            text-align: left;
        }
        th {
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Ford Car Models</h1>
    <button id="fetchDataBtn">Fetch Car Models</button>
    <table id="carTable">
        <thead>
            <tr>
                <th onclick="sortTable(0)">Model</th>
                <th onclick="sortTable(1)">Year</th>
                <th onclick="sortTable(2)">Engine</th>
                <th onclick="sortTable(3)">Trim</th>
                <th onclick="sortTable(4)">Price</th>
                <th onclick="sortTable(5)">Horsepower</th>
            </tr>
        </thead>
        <tbody>
            <!-- Data will be inserted here -->
        </tbody>
    </table>
    <script>
        document.getElementById('fetchDataBtn').addEventListener('click', fetchCarData);
        function fetchCarData() {
            fetch('http://127.0.0.1:5000/cars')
                .then(response => response.json())
                .then(data => {
                    const tableBody = document.getElementById('carTable').getElementsByTagName('tbody')[0];
                    tableBody.innerHTML = '';
                    data.forEach(car => {
                        const row = tableBody.insertRow();
                        row.insertCell(0).innerText = car.model_name;
                        row.insertCell(1).innerText = car.year;
                        row.insertCell(2).innerText = car.engine;
                        row.insertCell(3).innerText = car.trim;
                        row.insertCell(4).innerText = `$${car.price.toFixed(2)}`;
                        row.insertCell(5).innerText = car.horsepower;
                    });
                });
        }
        function sortTable(n) {
            const table = document.getElementById('carTable');
            let rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
            switching = true;
            dir = "asc"; 
            while (switching) {
                switching = false;
                rows = table.rows;
                for (i = 1; i < (rows.length - 1); i++) {
                    shouldSwitch = false;
                    x = rows[i].getElementsByTagName("TD")[n];
                    y = rows[i + 1].getElementsByTagName("TD")[n];
                    if (dir === "asc") {
                        if (x.innerHTML.toLowerCase() > y.innerHTML.toLowerCase()) {
                            shouldSwitch = true;
                            break;
                        }
                    } else if (dir === "desc") {
                        if (x.innerHTML.toLowerCase() < y.innerHTML.toLowerCase()) {
                            shouldSwitch = true;
                            break;
                        }
                    }
                }
                if (shouldSwitch) {
                    rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
                    switching = true;
                    switchcount ++;
                } else {
                    if (switchcount === 0 && dir === "asc") {
                        dir = "desc";
                        switching = true;
                    }
                }
            }
        }
    </script>
</body>
</html>
