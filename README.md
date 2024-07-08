INDEX.HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="style.css">
</head>
<body >
    <div class="container">
        <h1>To-Do List</h1>
        <div class="add-task">
            <input type="text" id="taskInput" placeholder="Add a new task">
            <button onclick="addTask()"><i class="bi bi-plus-circle-fill"></i><br>Add</i></button>
        </div>
        
        <ul class="tasks" id="taskList"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>

```
style.css
```body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    margin: 0;
    padding: 20px;
}
.container {
    max-width: 1200px;
    margin: auto;
    padding: 20px;
    background-color: #ce0a0a;
    
    border-radius: 5px;
}
h1 {
    text-align: center;
}
.add-task {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
}
.add-task input {
    flex: 1;
    padding: 10px;
    margin-right: 10px;
    border: 1px solid #ccc;
}
.add-task button {
    padding: 10px;
    background-color: #007BFF;
    color: #fff;
    border: none;
    cursor: pointer;
    transition-duration: 0.4s;
    transition-duration: 0.4s;
    border-radius: 5px;
}

.tasks {
    list-style: none;
    padding: 0;
}
.tasks li {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    background-color: #f9f9f9;
    margin-bottom: 10px;
    border: 1px solid #ccc;
}
.tasks li.completed {
    text-decoration: line-through;
    color: #888;
}
.tasks li button {
    height: 35px;
    background-color: red;
    color: #fff;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    transition-duration: 0.4s; 
    transition-duration: 0.4s;
}

```
script.js
```

class Task {
    constructor(name) {
        this.name = name;
        this.completed = false;
    }
}


class ToDoList {
    constructor() {
        this.tasks = [];
        this.render();
    }

    addTask(taskName) {
        if (taskName.trim()) {
            const task = new Task(taskName);
            this.tasks.push(task);
            this.render();
        }
    }

    toggleTask(index) {
        if (this.tasks[index]) {
            this.tasks[index].completed = !this.tasks[index].completed;
            this.render();
        }
    }

    deleteTask(index) {
        if (this.tasks[index]) {
            this.tasks.splice(index, 1);
            this.render();
        }
    }

    render() {
        const taskList = document.getElementById('taskList');
        taskList.innerHTML = '';

        this.tasks.forEach((task, index) => {
            const taskItem = document.createElement('li');
            taskItem.className = task.completed ? 'completed' : '';

            taskItem.innerHTML = `
                <span onclick="toDoList.toggleTask(${index})">${task.name}</span>
                <button onclick="toDoList.deleteTask(${index})"><i class="bi bi-trash3-fill"></i><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash3-fill" viewBox="0 0 16 16">
  <path d="M11 1.5v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5m-5 0v1h4v-1a.5.5 0 0 0-.5-.5h-3a.5.5 0 0 0-.5.5M4.5 5.029l.5 8.5a.5.5 0 1 0 .998-.06l-.5-8.5a.5.5 0 1 0-.998.06m6.53-.528a.5.5 0 0 0-.528.47l-.5 8.5a.5.5 0 0 0 .998.058l.5-8.5a.5.5 0 0 0-.47-.528M8 4.5a.5.5 0 0 0-.5.5v8.5a.5.5 0 0 0 1 0V5a.5.5 0 0 0-.5-.5"/>
</svg></button>
            `;

            taskList.appendChild(taskItem);
        });
    }
}

// Create a new To-Do list instance
const toDoList = new ToDoList();

// Function to add a new task
function addTask() {
    const taskInput = document.getElementById('taskInput');
    const taskName = taskInput.value;
    toDoList.addTask(taskName);
    taskInput.value = '';
}
```
![Screenshot 2024-07-08 232953](https://github.com/JAIGANESHVETRISELVAN/to-do-list/assets/133752156/86753755-f1a1-4fab-b7a6-83dc5fe31d66)
