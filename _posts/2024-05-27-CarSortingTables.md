---
toc: true
comments: false
layout: post
title: Car Sorter
courses: { compsci: {week: 31} }
type: hacks
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ford Car Models</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        h1 {
            text-align: center;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        th, td {
            padding: 10px;
            border: 1px solid #ddd;
            text-align: left;
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
    </style>
</head>
<body>
    <h1>Ford Car Models</h1>
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
            <!-- Sample data -->
            <tr>
                <td>Mustang</td>
                <td>2023</td>
                <td>V8</td>
                <td>GT</td>
                <td>55000.00</td>
                <td>450</td>
            </tr>
            <tr>
                <td>F-150</td>
                <td>2022</td>
                <td>V6</td>
                <td>XLT</td>
                <td>45000.00</td>
                <td>400</td>
            </tr>
            <tr>
                <td>Escape</td>
                <td>2021</td>
                <td>I4</td>
                <td>Titanium</td>
                <td>35000.00</td>
                <td>250</td>
            </tr>
            <tr>
                <td>Explorer</td>
                <td>2023</td>
                <td>V6</td>
                <td>Limited</td>
                <td>50000.00</td>
                <td>365</td>
            </tr>
            <tr>
                <td>Bronco</td>
                <td>2023</td>
                <td>I4</td>
                <td>Base</td>
                <td>35000.00</td>
                <td>300</td>
            </tr>
            <tr>
                <td>Escape</td>
                <td>2024</td>
                <td>I4</td>
                <td>Base</td>
                <td>29345.00</td>
                <td>180</td>
            </tr>
        </tbody>
    </table>
    <script>
        function sortTable(n) {
            const table = document.getElementById("carTable");
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
                        if (n === 4 || n === 5) { // For numeric columns (Price, Horsepower)
                            if (parseFloat(x.innerHTML) > parseFloat(y.innerHTML)) {
                                shouldSwitch = true;
                                break;
                            }
                        } else {
                            if (x.innerHTML.toLowerCase() > y.innerHTML.toLowerCase()) {
                                shouldSwitch = true;
                                break;
                            }
                        }
                    } else if (dir === "desc") {
                        if (n === 4 || n === 5) {
                            if (parseFloat(x.innerHTML) < parseFloat(y.innerHTML)) {
                                shouldSwitch = true;
                                break;
                            }
                        } else {
                            if (x.innerHTML.toLowerCase() < y.innerHTML.toLowerCase()) {
                                shouldSwitch = true;
                                break;
                            }
                        }
                    }
                }
                if (shouldSwitch) {
                    rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
                    switching = true;
                    switchcount++;
                } else {
                    if (switchcount === 0 && dir === "asc") {
                        dir = "desc";
                        switching = true;
                    }
                }
            }
            // Reset all sort indicators
            const ths = table.getElementsByTagName("TH");
            for (let j = 0; j < ths.length; j++) {
                ths[j].classList.remove("sort-asc", "sort-desc");
            }
            // Set the correct sort indicator
            ths[n].classList.add(dir === "asc" ? "sort-asc" : "sort-desc");
        }
    </script>
</body>
</html>
