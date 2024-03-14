# PYTHON:

```py
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
  return render_template('index.html')

if __name__ == '__main__':
  app.run(debug=True)

```

#   HTML:
```html
<!DOCTYPE html>
<html>
<head>
  <title>To-Do List</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='styles.css') }}">
</head>
<body>
  <div class="container">
    <div class="input-container">
      <h1>To-Do List</h1>
      <div class="todo-container">
        <input type="text" id="taskInput" placeholder="Add New Task...">
        <button class="add" onclick="addTask()">Add Task</button>
      </div>
    </div>
    <div class="result-container">
        <h2>Tasks :</h2>
        <ul id="taskList"></ul>
    </div>
  </div> 
  
  <footer>
    <p>Developed by KULASEKARAPANDIAN</p>
  </footer>

  <script src="{{ url_for('static', filename='script.js') }}"></script>
</body>
</html>

```

# CSS:
```css


body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-image: url('nn.jpg'); 
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    overflow-x: hidden;
}

.container {
    background-color: white;
    padding: 109px;
    border-radius: 9px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.08);
    position: fixed;
    opacity: 1;
    backdrop-filter: blur(0px);
    transition: backdrop-filter 0.5s ease-in-out;
    overflow-y: auto;
}

h1 {
    color: black;
    margin-bottom: 20px;
    font-size: 19px;
}

.todo-container {
    margin-bottom: 19px;
}

h1:hover {
    color: #211951;
    transition: color 0.91s ease;
}

.add:hover {
    font-weight: bold;
}

button:hover {
    color: #222831;
    background-color: whitesmoke;
    transition: background-color 0.5s ease-in;
    transition: background-color 0.5s ease-out;
    transition-duration: color 0.9s;
    font-weight: bold;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    background-color: whitesmoke;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    font-size: small;
    font-weight: bold;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 20px;
    display: flex;
    align-items: center;
    position: relative; 

li:hover {
    background-color: white;
}

input[type="text"] {
    color: black;
    padding: 10px 15px;
    border: none;
    border-radius: 25px;
    margin-right: 10px;
    background-color: #eeeeee;
}

input:hover {
    background-color: #c7c8cc;
    transition: background-color 0.9s ease;
}

input:hover::placeholder::target-text {
    color: black;
    font-weight: bold;
}

input[type="text"]::placeholder {
    color: black;
    font-style: italic;
}

input[type="text"]:focus {
    outline: none;
}

.check-button {
    margin-right: 10px;
    cursor: pointer;
}

.delete-button {
    position: absolute;
    top: 0.1;
    right:0;
    background-color: white;
    color: black;
    border: 0.01%;
    padding: 5px 10px;
    border-radius: 19px;
    cursor: pointer;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.08);
    transition: background-color 0.5s ease;
    font-weight: bold;
}

.delete-button:hover {
    color: white;
    background-color: red;
    transition: background-color 0.5s ease;
}

.add {
    padding: 10px 15px;
    border: solid 1px;
    border-radius: 25px;
    margin-right: 10px;
    background-color: #211951;
    color: whitesmoke;
    font-weight: bold;
}

.bg-i {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
}

footer {
    position:fixed;
    bottom:0;
    width:100%;
    text-align: center;
    padding: px;
    background-color: #c7c8cc;
    color: #222831;
}

.result-container {
    max-height: 300px;
    overflow-y: auto;
    margin-top: 20px;
}

.task-wrapper {
    display: flex;
    align-items: center;
}

.task-wrapper span {
    flex-grow: 1;
    padding-right: 10px; 
}

.task-wrapper button {
    margin-left: 10px; 
}

.task-wrapper span.checked {
    text-decoration: line-through;
    font-weight: bold;
}

```


# JAVA SCRIPT:
```js
document.addEventListener("DOMContentLoaded", function() {
    var taskInput = document.getElementById("taskInput");
    taskInput.addEventListener("keyup", function(event) {
        if (event.key === 'Enter') {
            event.preventDefault();
            addTask();
        }
    });
});

function addTask() {
    var taskInput = document.getElementById("taskInput");
    var taskList = document.getElementById("taskList");

    if (taskInput.value === '') {
        alert("Please enter a task!!");
        return;
    }

    var li = document.createElement("li");
    var checkBox = document.createElement("input");
    checkBox.type = "checkbox";
    checkBox.classList.add("check-button");
    checkBox.onclick = function() {
        taskText.classList.toggle("checked");
    };

    var taskWrapper = document.createElement("div"); // New wrapper div
    taskWrapper.classList.add("task-wrapper");

    var taskText = document.createElement("span");
    taskText.textContent = taskInput.value;

    var deleteButton = document.createElement("button");
    deleteButton.textContent = "Delete";
    deleteButton.classList.add("delete-button");
    deleteButton.onclick = function() {
        taskList.removeChild(li);
    };

    li.appendChild(checkBox);
    taskWrapper.appendChild(taskText);
    taskWrapper.appendChild(deleteButton);
    li.appendChild(taskWrapper);
    taskList.appendChild(li);

    taskInput.value = '';
}

```