# -Import-Data-using-Transform-Maps-Spreadsheet-
This project focuses on importing spreadsheet data into a target table using Transform Maps. It ensures accurate field mapping, data validation, and efficient data management.

<!DOCTYPE html>
<html>
<head>
    <title>Import Data Using Transform Maps</title>
    <style>
        body {
            font-family: Arial;
            text-align: center;
            background-color: #f0f4f8;
            padding: 30px;
        }

        h1 {
            color: #234e70;
        }

        input, button {
            padding: 10px;
            margin: 10px;
        }

        table {
            margin: 20px auto;
            border-collapse: collapse;
            background: white;
        }

        th, td {
            border: 1px solid black;
            padding: 10px;
        }

        th {
            background-color: #234e70;
            color: white;
        }
    </style>
</head>
<body>

    <h1>Import Data Using Transform Maps</h1>
    <p>Upload a CSV Spreadsheet File</p>

    <input type="file" id="fileInput" accept=".csv">
    <button onclick="importData()">Import Data</button>

    <table id="dataTable"></table>

    <script>
        function importData() {
            const file = document.getElementById("fileInput").files[0];

            if (!file) {
                alert("Please select a CSV file!");
                return;
            }

            const reader = new FileReader();

            reader.onload = function(event) {
                const rows = event.target.result.trim().split(/\r?\n/);
                const table = document.getElementById("dataTable");

                table.innerHTML = "";

                rows.forEach((row, index) => {
                    const tr = document.createElement("tr");

                    row.split(",").forEach(value => {
                        const cell = document.createElement(
                            index === 0 ? "th" : "td"
                        );

                        cell.textContent = value.trim();
                        tr.appendChild(cell);
                    });

                    table.appendChild(tr);
                });

                alert("Spreadsheet data imported successfully!");
            };

            reader.readAsText(file);
        }
    </script>

</body>
</html>
