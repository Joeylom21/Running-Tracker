Hello, Welcome to your Running Tracker 
Enter your inputs below
<html>
<head>
    <title>Running Tracker</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; padding: 20px; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid black; padding: 10px; text-align: left; }
        th { background-color: #f2f2f2; }
        button { margin: 5px; cursor: pointer; }
    </style>
</head>
<body>
    <h2>Running Tracker</h2>
    <form id="runForm">
        <label>Date: <input type="date" id="date"></label>
        <label>Distance (miles): <input type="number" id="distance" step="0.1"></label>
        <label>Shoe Type: <input list="shoes" id="shoe"></label>
        <datalist id="shoes">
            <option value="Nike Air Zoom Pegasus 40">
            <option value="Nike React Infinity Run 3">
            <option value="Nike Vaporfly 3">
            <option value="Nike Alphafly 2">
            <option value="Nike Zoom Fly 5">
            <option value="Nike Structure 24">
            <option value="Nike Invincible Run 3">
            <option value="Nike Free Run 5.0">
            <option value="Nike Wildhorse 8">
            <option value="Nike Terra Kiger 9">
            <option value="Nike Streakfly">
            <option value="Nike Winflo 10">
            <option value="Nike Downshifter 12">
            <option value="Nike Juniper Trail 2">
        </datalist>
        <label>Location: <input type="text" id="location"></label>
        <label>Time (minutes): <input type="number" id="time"></label>
        <button type="button" onclick="addRun()">Add Run</button>
    </form>
    
    <table id="runTable">
        <tr>
            <th>Date</th>
            <th>Distance</th>
            <th>Shoe Type</th>
            <th>Location</th>
            <th>Time</th>
            <th>Actions</th>
        </tr>
    </table>
    
    <script>
        function addRun() {
            let date = document.getElementById("date").value;
            let distance = document.getElementById("distance").value;
            let shoe = document.getElementById("shoe").value;
            let location = document.getElementById("location").value;
            let time = document.getElementById("time").value;
            
            if (date && distance && shoe && location && time) {
                let table = document.getElementById("runTable");
                let row = table.insertRow(-1);
                row.insertCell(0).innerText = date;
                row.insertCell(1).innerText = distance;
                row.insertCell(2).innerText = shoe;
                row.insertCell(3).innerText = location;
                row.insertCell(4).innerText = time;
                
                let actionsCell = row.insertCell(5);
                let editButton = document.createElement("button");
                editButton.innerText = "Edit";
                editButton.onclick = function() { editRun(row); };
                
                let deleteButton = document.createElement("button");
                deleteButton.innerText = "Delete";
                deleteButton.onclick = function() { deleteRun(row); };
                
                actionsCell.appendChild(editButton);
                actionsCell.appendChild(deleteButton);
            }
        }
        
        function editRun(row) {
            let cells = row.getElementsByTagName("td");
            document.getElementById("date").value = cells[0].innerText;
            document.getElementById("distance").value = cells[1].innerText;
            document.getElementById("shoe").value = cells[2].innerText;
            document.getElementById("location").value = cells[3].innerText;
            document.getElementById("time").value = cells[4].innerText;
            
            row.remove();
        }
        
        function deleteRun(row) {
            row.remove();
        }
    </script>
</body>
</html>
