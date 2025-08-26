<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Jogo de Geografia Infantil</title>
  <style>
    body {
      font-family: 'Comic Sans MS', sans-serif;
      background: #d0f0c0;
      text-align: center;
      padding: 30px;
    }
    h1 {
      color: #2e8b57;
    }
    #quiz-container {
      background: #fff;
      border-radius: 15px;
      padding: 20px;
      max-width: 500px;
      margin: auto;
      box-shadow: 0 0 10px #888;
    }
    .question {
      font-size: 1.2em;
      margin-bottom: 20px;
    }
    .btn {
      background: #87ceeb;
      border: none;
      border-radius: 10px;
      padding: 10px 20px;
      margin: 10px;
      cursor: pointer;
      font-size: 1em;
    }
    .btn:hover {
      background: #00bfff;
    }
    #result {
      font-size: 1.2em;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <h1>🌍 Jogo de Geografia Infantil 🌎</h1>
  <div id="quiz-container">
    <div class="question" id="question">Carregando pergunta...</div>
    <div id="answers"></div>
    <div id="result"></div>
  </div>

  <script>
    const questions = [
      {
        question: "Qual é a capital do Brasil?",
        answers: ["Rio de Janeiro", "São Paulo", "Brasília"],
        correct: 2
      },
      {
        question: "Em que continente está o Egito?",
        answers: ["África", "Europa", "Ásia"],
        correct: 0
      },
      {
        question: "Qual animal vive no Polo Sul?",
        answers: ["Pinguim", "Leão", "Girafa"],
        correct: 0
      },
      {
        question: "Qual é o maior oceano do mundo?",
        answers: ["Atlântico", "Pacífico", "Índico"],
        correct: 1
      },
      {
        question: "Onde vive o canguru?",
        answers: ["Brasil", "Austrália", "Canadá"],
        correct: 1
      }
    ];

    let currentQuestion = 0;

    function showQuestion() {
      const q = questions[currentQuestion];
      document.getElementById("question").textContent = q.question;
      const answersDiv = document.getElementById("answers");
      answersDiv.innerHTML = "";
      q.answers.forEach((answer, index) => {
        const btn = document.createElement("button");
        btn.className = "btn";
        btn.textContent = answer;
        btn.onclick = () => checkAnswer(index);
        answersDiv.appendChild(btn);
      });
      document.getElementById("result").textContent = "";
    }

    function checkAnswer(selected) {
      const q = questions[currentQuestion];
      const result = document.getElementById("result");
      if (selected === q.correct) {
        result.textContent = "✅ Acertou! Muito bem!";
        result.style.color = "green";
      } else {
        result.textContent = `❌ Ops! A resposta certa era: ${q.answers[q.correct]}`;
        result.style.color = "red";
      }

      currentQuestion++;
      if (currentQuestion < questions.length) {
        setTimeout(showQuestion, 2000);
      } else {
        setTimeout(() => {
          document.getElementById("quiz-container").innerHTML = "<h2>🏁 Fim do jogo! Parabéns! 🎉</h2>";
        }, 2000);
      }
    }

    // Iniciar o quiz
    showQuestion();
  </script>

</body>
</html>
