```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Focus Task</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f4f7fb;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            width: 90%;
            max-width: 600px;
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 5px 25px rgba(0,0,0,0.1);
        }

        h1 {
            text-align: center;
            margin-bottom: 25px;
        }

        .input-box {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        input {
            flex: 1;
            padding: 13px;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 16px;
        }

        button {
            border: none;
            padding: 13px 18px;
            border-radius: 8px;
            cursor: pointer;
            background: #2563eb;
            color: white;
            font-size: 15px;
        }

        button:hover {
            background: #1d4ed8;
        }

        ul {
            list-style: none;
        }

        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            margin-bottom: 10px;
            background: #f8fafc;
            border-radius: 8px;
            border-left: 4px solid #2563eb;
        }

        li.completed {
            text-decoration: line-through;
            opacity: 0.6;
        }

        .delete {
            background: #ef4444;
            padding: 8px 12px;
        }

        .delete:hover {
            background: #dc2626;
        }

        .task-text {
            cursor: pointer;
            flex: 1;
        }

        .counter {
            text-align: center;
            margin-top: 20px;
            color: #555;
        }
    </style>
</head>

<body>

<div class="container">

    <h1>🎯 Focus Task</h1>

    <div class="input-box">
        <input 
            type="text" 
            id="taskInput" 
            placeholder="Enter your task..."
        >

        <button onclick="addTask()">Add</button>
    </div>

    <ul id="taskList"></ul>

    <div class="counter">
        Total Tasks: <span id="taskCount">0</span>
    </div>

</div>

<script>

    function addTask() {

        const input = document.getElementById("taskInput");
        const taskText = input.value.trim();

        if (taskText === "") {
            alert("Please enter a task!");
            return;
        }

        const li = document.createElement("li");

        const span = document.createElement("span");
        span.className = "task-text";
        span.textContent = taskText;

        // Mark task as completed
        span.onclick = function () {
            li.classList.toggle("completed");
        };

        // Delete button
        const deleteBtn = document.createElement("button");
        deleteBtn.className = "delete";
        deleteBtn.textContent = "Delete";

        deleteBtn.onclick = function () {
            li.remove();
            updateCount();
        };

        li.appendChild(span);
        li.appendChild(deleteBtn);

        document.getElementById("taskList").appendChild(li);

        input.value = "";

        updateCount();
    }

    function updateCount() {
        const tasks = document.querySelectorAll("#taskList li");
        document.getElementById("taskCount").textContent = tasks.length;
    }

    // Press Enter to add task
    document.getElementById("taskInput").addEventListener("keypress", function(event) {
        if (event.key === "Enter") {
            addTask();
        }
    });

</script>

</body>
</html>
```
