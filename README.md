let questions = [];
let currentIndex = 0;
let correctCount = 0;
let wrongCount = 0;

async function loadQuestions() {
  try {
    const response = await fetch('questions.json');
    questions = await response.json();
    showQuestion();
  } catch (error) {
    console.error('Грешка при зареждане на въпросите:', error);
    document.getElementById('question').textContent = "Неуспешно зареждане на въпросите.";
  }
}

function showQuestion() {
  if (currentIndex < 0) currentIndex = 0;
  if (currentIndex >= questions.length) currentIndex = questions.length - 1;

  document.getElementById('question').textContent = questions[currentIndex].text;
  document.getElementById('result').textContent = '';
  updateScore();
}

function checkAnswer(answer) {
  const correct = questions[currentIndex].correct;
  if (answer === correct) {
    document.getElementById('result').textContent = "Верен отговор!";
    correctCount++;
  } else {
    document.getElementById('result').textContent = "Грешен отговор!";
    wrongCount++;
  }
  updateScore();
}

function updateScore() {
  document.getElementById('score').textContent = `Верен: ${correctCount} | Грешен: ${wrongCount}`;
}

document.getElementById('yesBtn').addEventListener('click', () => checkAnswer('yes'));
document.getElementById('noBtn').addEventListener('click', () => checkAnswer('no'));
document.getElementById('nextBtn').addEventListener('click', () => {
  currentIndex++;
  if (currentIndex >= questions.length) currentIndex = questions.length - 1;
  showQuestion();
});
document.getElementById('prevBtn').addEventListener('click', () => {
  currentIndex--;
  if (currentIndex < 0) currentIndex = 0;
  showQuestion();
});

loadQuestions();
