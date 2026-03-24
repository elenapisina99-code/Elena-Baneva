<!DOCTYPE html>
<html lang="bg">
<head>
  <meta charset="UTF-8">
  <title>AI Природен изследовател</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<h1>🌱 AI Природен изследовател
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
[
  { "text": "Кое е живо: дърво?", "correct": "yes" },
  { "text": "Кое е живо: камък?", "correct": "no" },
  { "text": "Кое е живо: куче?", "correct": "yes" },
  { "text": "Кое е живо: слънце?", "correct": "no" },
  { "text": "Кое е живо: цвете?", "correct": "yes" },
  { "text": "Кое е живо: вода?", "correct": "no" }
]// Превключване на секции
function showSection(section) {
  document.getElementById("ask").style.display = "none";
  document.getElementById("quiz").style.display = "none";
  document.getElementById(section).style.display = "block";
}

// AI функция
async function askAI() {
  let question = document.getElementById("question").value;
  if (!question) return;

  document.getElementById("answer").innerText = "Мисля... 🤔";

  let response = await fetch("/ask", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ question })
  });

  let data = await response.json();
  let answer = data.answer || "Няма отговор, опитай пак.";
  document.getElementById("answer").innerText = answer;
  speak(answer);
}

// Text-to-Speech функция
function speak(text) {
  if (!window.speechSynthesis) return;
  let utterance = new SpeechSynthesisUtterance(text);
  utterance.lang = 'bg-BG';
  utterance.rate = 0.9;
  window.speechSynthesis.speak(utterance);
}

// Quiz
let questions = [];
let current = 0;

async function loadQuiz() {
  let res = await fetch("/questions.json");
  questions = await res.json();
  current = 0;
  showQuestion();
}

function showQuestion() {
  if (questions.length === 0) return;
  document.getElementById("quizQuestion").innerText = questions[current].text;
  document.getElementById("quizResult").innerText = "";
}

function checkAnswer(ans) {
  if (questions.length === 0) return;

  let resultEl = document.getElementById("quizResult");

  if (ans === questions[current].correct) {
    resultEl.innerText = "Браво! ⭐";
    resultEl.classList.add("correct");
  } else {
    resultEl.innerText = "Опитай пак!";
    resultEl.classList.add("wrong");
  }

  current = (current + 1) % questions.length;
  setTimeout(() => {
    resultEl.classList.remove("correct", "wrong");
    showQuestion();
  }, 1000);
}

// Стартиране на quiz
loadQuiz();
