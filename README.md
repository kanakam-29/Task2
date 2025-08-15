<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Intermediate HTML, CSS, JS Project</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #f4f4f4;
    }

    header {
      background-color: #2b6777;
      color: white;
      padding: 20px;
      text-align: center;
    }

    .container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
      padding: 20px;
    }

    .box {
      background-color: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    form input, form textarea, form button {
      display: block;
      width: 100%;
      margin-bottom: 10px;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }

    .todo-list li {
      display: flex;
      justify-content: space-between;
      background: #e0f7fa;
      padding: 8px;
      margin-bottom: 5px;
      border-radius: 4px;
    }

    footer {
      text-align: center;
      padding: 10px;
      background: #2b6777;
      color: white;
    }
  </style>
</head>
<body>

  <header>
    <h1>Intermediate HTML, CSS, and JavaScript</h1>
  </header>

  <div class="container">
    <!-- Contact Form -->
    <div class="box">
      <h2>Contact Form</h2>
      <form id="contactForm">
        <input type="text" id="name" placeholder="Your Name" required />
        <input type="email" id="email" placeholder="Your Email" required />
        <textarea id="message" placeholder="Your Message" required></textarea>
        <button type="submit">Submit</button>
        <p id="formError" style="color: red;"></p>
      </form>
    </div>

    <!-- To-Do List -->
    <div class="box">
      <h2>To-Do List</h2>
      <input type="text" id="taskInput" placeholder="New Task" />
      <button onclick="addTask()">Add Task</button>
      <ul class="todo-list" id="taskList"></ul>
    </div>
  </div>

  <footer>
    &copy; 2025 Intermediate Web Project
  </footer>

  <script>
    // JavaScript Form Validation
    document.getElementById('contactForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const message = document.getElementById('message').value.trim();
      const error = document.getElementById('formError');

      if (!name || !email || !message) {
        error.textContent = "All fields are required.";
        return;
      }

      const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (!email.match(emailPattern)) {
        error.textContent = "Please enter a valid email address.";
        return;
      }

      error.textContent = "";
      alert("Form submitted successfully!");
      this.reset();
    });

    // JavaScript To-Do List
    function addTask() {
      const taskInput = document.getElementById('taskInput');
      const taskList = document.getElementById('taskList');
      const taskText = taskInput.value.trim();

      if (taskText === '') return;

      const li = document.createElement('li');
      li.textContent = taskText;

      const btn = document.createElement('button');
      btn.textContent = "❌";
      btn.style.marginLeft = "10px";
      btn.onclick = () => taskList.removeChild(li);

      li.appendChild(btn);
      taskList.appendChild(li);
      taskInput.value = "";
    }
  </script>

</body>
</html>
