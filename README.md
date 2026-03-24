Супер — ще го направим **като истински продукт (уеб сайт)** и ще ти покажа **точно как да го направиш ТУК, стъпка по стъпка**, без да се луташ 👇

Ще използваме **най-лесния и сигурен вариант**:
👉 сайт + AI + безплатен хостинг

---

# 🚀 🧭 ОБЩ ПЛАН

Ще направиш:

1. 💻 Уеб страница (тук ще ти дам кода)
2. 🤖 AI (OpenAI API)
3. 🌐 Публикуване онлайн (безплатно)

---

# 🧱 СТЪПКА 1: Създай проекта

## 📁 1. Направи папка:

Име:

```
ai-priroda
```

Вътре създай 3 файла:

```
index.html
style.css
script.js
```

---

# 🎨 СТЪПКА 2: Сложи дизайна

## 📄 index.html

```html
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
  <button onclick="checkAnswer('yes')">Живо</button>
  <button onclick="checkAnswer('no')">Не е живо</button>
  <p id="quizResult"></p>
</div>

<script src="script.js"></script>

</body>
</html>
```

---

## 🎨 style.css

```css
body {
  font-family: Arial;
  text-align: center;
  background: #e8f5e9;
}

h1 {
  color: green;
}

button {
  padding: 10px;
  margin: 5px;
  border-radius: 10px;
  border: none;
  background: #4caf50;
  color: white;
  cursor: pointer;
}

input {
  padding: 10px;
  width: 200px;
}
```

---

# ⚙️ СТЪПКА 3: Логика (script.js)

```javascript
function showSection(section) {
  document.getElementById("ask").style.display = "none";
  document.getElementById("quiz").style.display = "none";

  document.getElementById(section).style.display = "block";
}

// AI функция
async function askAI() {
  let question = document.getElementById("question").value;

  let response = await fetch("https://api.openai.com/v1/chat/completions", {
    method: "POST",
    headers: {
      "Authorization": "Bearer ТУК_СЛАГАШ_API_KEY",
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      model: "gpt-4o-mini",
      messages: [
        {
          role: "system",
          content: "Обяснявай като на дете от 1 до 4 клас. Кратко и ясно."
        },
        {
          role: "user",
          content: question
        }
      ]
    })
  });

  let data = await response.json();
  document.getElementById("answer").innerText =
    data.choices[0].message.content;
}

// тест
let correct = "yes";

document.getElementById("quizQuestion").innerText =
  "Кое е живо: дърво?";

function checkAnswer(ans) {
  if (ans === correct) {
    document.getElementById("quizResult").innerText = "Браво! ⭐";
  } else {
    document.getElementById("quizResult").innerText = "Опитай пак!";
  }
}
```

---

# 🔑 СТЪПКА 4: Вземи AI ключ

1. Отиди на: [https://platform.openai.com](https://platform.openai.com)
2. Регистрирай се
3. Вземи API key
4. Замени:

```
ТУК_СЛАГАШ_API_KEY
```

---

# 🌐 СТЪПКА 5: Публикувай сайта (МНОГО ВАЖНО)

## Най-лесният начин: GitHub Pages

### 1. Отиди на:

👉 github.com

### 2. Направи акаунт

### 3. Създай нов репозитори:

* име: `ai-priroda`

### 4. Качи файловете

### 5. Включи:

👉 Settings → Pages → Enable

---

## 🎉 Получаваш линк:

```
https://твоето-име.github.io/ai-priroda
```

👉 Това е твоят **готов продукт за конкурса**

---

# 🏆 Как да изглежда „завършен проект“

Добави:

* ✔️ име
* ✔️ описание
* ✔️ работещ линк
* ✔️ 1–2 функции

👉 това е напълно достатъчно да участваш

---

# ⚡ Ако искаш да стане още по-яко



