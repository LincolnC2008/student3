---
toc: false
comments: false
layout: post
title: Table on the top 25 hardest Ap classes
description: we're using jQuery to dynamically populate a table with information about the top 25 hardest AP classes. The apClasses array contains objects with the class name and a difficulty rating. The jQuery script loops through this array and appends rows to the table.
type: tangibles
courses: { compsci: {week: 3} }
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Top 25 Hardest AP Classes</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <style>
        table {
            border-collapse: collapse;
            width: 80%;
            margin: 20px auto;
        }
        th, td {
            border: 1px solid #ccc;
            padding: 8px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>
    <table id="apClasses">
        <thead>
            <tr>
                <th>Class Name</th>
                <th>Difficulty Rating</th>
                <th>Percent Scoring 5</th>
            </tr>
        </thead>
        <tbody>
            <!-- Table content will be added via jQuery -->
        </tbody>
    </table>

    <script>
        $(document).ready(function() {
            const apClasses = [
                { className: "AP Calculus BC", difficulty: 5, percent5: 80 },
                { className: "AP Physics C: Mechanics", difficulty: 4, percent5: 70 },
                { className: "AP Chemistry", difficulty: 4, percent5: 75 },
                { className: "AP Biology", difficulty: 3, percent5: 65 },
                { className: "AP Computer Science A", difficulty: 3, percent5: 85 },
                { className: "AP English Literature and Composition", difficulty: 3, percent5: 60 },
                { className: "AP U.S. History", difficulty: 4, percent5: 70 },
                { className: "AP European History", difficulty: 4, percent5: 65 },
                { className: "AP Psychology", difficulty: 2, percent5: 90 },
                { className: "AP Environmental Science", difficulty: 3, percent5: 70 },
                { className: "AP Human Geography", difficulty: 2, percent5: 85 },
                { className: "AP Statistics", difficulty: 3, percent5: 75 },
                { className: "AP French Language and Culture", difficulty: 3, percent5: 70 },
                { className: "AP Spanish Language and Culture", difficulty: 3, percent5: 75 },
                { className: "AP Chinese Language and Culture", difficulty: 3, percent5: 80 },
                { className: "AP Japanese Language and Culture", difficulty: 3, percent5: 75 },
                { className: "AP Art History", difficulty: 3, percent5: 65 },
                { className: "AP Music Theory", difficulty: 3, percent5: 70 },
                { className: "AP Studio Art: 2-D Design", difficulty: 3, percent5: 60 },
                { className: "AP Studio Art: 3-D Design", difficulty: 3, percent5: 55 },
                { className: "AP Studio Art: Drawing", difficulty: 3, percent5: 50 },
                { className: "AP Macroeconomics", difficulty: 3, percent5: 80 },
                { className: "AP Microeconomics", difficulty: 3, percent5: 85 },
                { className: "AP Comparative Government and Politics", difficulty: 3, percent5: 70 },
                { className: "AP U.S. Government and Politics", difficulty: 3, percent5: 75 }
            ];

            const tableBody = $('#apClasses tbody');

            apClasses.forEach(function(apClass) {
                const row = $('<tr>');
                row.append($('<td>').text(apClass.className));
                row.append($('<td>').text(apClass.difficulty));
                row.append($('<td>').text(apClass.percent5 + '%'));
                tableBody.append(row);
            });
        });
    </script>
</body>
</html>