<!DOCTYPE html>
<html lang="bg">
<head>
  <meta charset="UTF-8">
  <title>AI Природен изследовател</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<h1>🌱 AI Природен изследовател</h1>

<div class="menu">
  <button onclick="showSection('ask')">🗣️ Попитай природата</button>
  <button onclick="showSection('quiz')">🧠 Провери знанията</button>
</div>

<div id="ask" class="section">
  <h2>Попитай природата</h2>
  <input id="question" placeholder="Напиши въпрос...">
  <button onclick="askAI()">Попитай</button>
  <p id="answer"></p>
</div>

<div id="quiz" class="section" style="display:none;">
  <h2>Въпрос</h2>
  <p id="quizQuestion"></p>
  <button onclick="checkAnswer('yes')">🌿 Живо</button>
  <button onclick="checkAnswer('no')">🪨 Не е живо</button>
  <p id="quizResult"></p>
</div>

<script src="script.js"></script>
</body>
</html>
