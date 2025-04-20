# Javascript-final-web
We have developed a fully functional website using JavaScript...
<!DOCTYPE html>
<html>
<head>
  <title>Smart Mini Site</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: Arial;
      text-align: center;
      padding: 30px;
      transition: background 0.5s, color 0.5s;
    }
    input, button {
      padding: 10px;
      margin: 10px;
      font-size: 1rem;
      width: 80%;
      max-width: 300px;
    }
    .dark {
      background: #121212;
      color: #fff;
    }
  </style>
</head>
<body>
  <h1 id="title">Welcome!</h1>

  <input id="nameInput" placeholder="Enter your name" />
  <button onclick="greetUser()">Greet</button>

  <br><br>
  <button onclick="toggleMode()">Toggle Dark Mode</button>

  <script src="script.js"></script>
</body>
</html>
//Javascript code begins here//
// Load stored name and mode on page load
window.onload = () => {
  const savedName = localStorage.getItem('name');
  const isDark = localStorage.getItem('darkMode') === 'true';

  if (savedName) {
    document.getElementById('title').innerText = `Welcome back, ${savedName}!`;
    document.getElementById('nameInput').value = savedName;
  }

  if (isDark) document.body.classList.add('dark');
};

function greetUser() {
  const name = document.getElementById('nameInput').value;
  if (name) {
    document.getElementById('title').innerText = `Hello, ${name}!`;
    localStorage.setItem('name', name);
  }
}

function toggleMode() {
  document.body.classList.toggle('dark');
  const isDark = document.body.classList.contains('dark');
  localStorage.setItem('darkMode', isDark);
}
