<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Patient Surgery History</title>

<style>
    body {
        font-family: Arial, sans-serif;
        background: #f4f6f9;
        padding: 20px;
    }

    .container {
        max-width: 900px;
        margin: auto;
    }

    h1 {
        text-align: center;
        color: #2c7be5;
    }

    .patient-card, .surgery-card {
        background: #fff;
        padding: 20px;
        margin-top: 20px;
        border-radius: 10px;
        box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    .row {
        margin: 8px 0;
    }

    .label {
        font-weight: bold;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 10px;
    }

    th, td {
        padding: 10px;
        border-bottom: 1px solid #ddd;
        text-align: left;
    }

    th {
        background: #eef4ff;
    }

    button {
        padding: 6px 12px;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }

    .edit-btn {
        background: #ffc107;
    }

    .save-btn {
        background: #28a745;
        color: white;
        display: none;
    }

    .add-btn {
        background: #2c7be5;
        color: white;
        margin-top: 15px;
    }

    input {
        width: 100%;
        padding: 5px;
    }
</style>
</head>

<body>

<div class="container">
    <h1>Patient Surgery History</h1>

    <!-- Patient Details -->
    <div class="patient-card">
        <div class="row"><span class="label">Patient ID:</span> P-10245</div>
        <div class="row"><span class="label">Patient Name:</span> John Doe</div>
        <div class="row"><span class="label">Age:</span> 28</div>
        <div class="row"><span class="label">Hospital:</span> Dr. Ashwin Health and Care, Chennai</div>
    </div>

    <!-- Surgery History -->
    <div class="surgery-card">
        <h3>Past & Current Surgeries</h3>

        <table id="surgeryTable">
            <tr>
                <th>Type</th>
                <th>Reason</th>
                <th>Doctor</th>
                <th>Start</th>
                <th>End</th>
                <th>Status</th>
                <th>Action</th>
            </tr>

            <!-- Surgery 1 -->
            <tr>
                <td>Cardiac Surgery</td>
                <td>Minor Heart Attack</td>
                <td>Dr. Ashwin</td>
                <td>09:30</td>
                <td>11:57</td>
                <td>Recovered</td>
                <td>
                    <button class="edit-btn" onclick="editRow(this)">Edit</button>
                    <button class="save-btn" onclick="saveRow(this)">Save</button>
                </td>
            </tr>

            <!-- Surgery 2 -->
            <tr>
                <td>Angioplasty</td>
                <td>Blocked Artery</td>
                <td>Dr. Kumar</td>
                <td>10:00</td>
                <td>11:15</td>
                <td>Recovered</td>
                <td>
                    <button class="edit-btn" onclick="editRow(this)">Edit</button>
                    <button class="save-btn" onclick="saveRow(this)">Save</button>
                </td>
            </tr>

            <!-- Surgery 3 -->
            <tr>
                <td>Appendix</td>
                <td>Appendicitis</td>
                <td>Dr. Ravi</td>
                <td>08:45</td>
                <td>09:30</td>
                <td>Recovered</td>
                <td>
                    <button class="edit-btn" onclick="editRow(this)">Edit</button>
                    <button class="save-btn" onclick="saveRow(this)">Save</button>
                </td>
            </tr>

            <!-- Surgery 4 -->
            <tr>
                <td>Knee Surgery</td>
                <td>Accident Injury</td>
                <td>Dr. Suresh</td>
                <td>07:30</td>
                <td>09:00</td>
                <td>Under Observation</td>
                <td>
                    <button class="edit-btn" onclick="editRow(this)">Edit</button>
                    <button class="save-btn" onclick="saveRow(this)">Save</button>
                </td>
            </tr>
        </table>

        <button class="add-btn" onclick="addSurgery()">+ Add New Surgery</button>
    </div>
</div>

<script>
function editRow(btn) {
    let row = btn.parentElement.parentElement;
    let cells = row.querySelectorAll("td");

    for (let i = 0; i < cells.length - 1; i++) {
        let value = cells[i].innerText;
        cells[i].innerHTML = `<input value="${value}">`;
    }

    btn.style.display = "none";
    btn.nextElementSibling.style.display = "inline-block";
}

function saveRow(btn) {
    let row = btn.parentElement.parentElement;
    let inputs = row.querySelectorAll("input");

    inputs.forEach(input => {
        let td = input.parentElement;
        td.innerText = input.value;
    });

    btn.style.display = "none";
    btn.previousElementSibling.style.display = "inline-block";
}

function addSurgery() {
    let table = document.getElementById("surgeryTable");
    let row = table.insertRow(-1);

    let fields = ["", "", "", "", "", ""];
    fields.forEach(value => {
        let cell = row.insertCell();
        cell.innerHTML = `<input>`;
    });

    let actionCell = row.insertCell();
    actionCell.innerHTML = `
        <button class="save-btn" style="display:inline-block" onclick="saveRow(this)">Save</button>
    `;
}
</script>

</body>
</html>
