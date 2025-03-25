# Quizz-bts-2.0
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz de Révision</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; }
        #quiz-container, #score-container { display: none; }
        button { margin-top: 10px; padding: 10px; cursor: pointer; }
    </style>
</head>
<body>
    <div id="access-container">
        <h2>Entrez le code d'accès</h2>
        <input type="text" id="access-code" placeholder="Code d'accès">
        <button onclick="checkAccess()">Accéder</button>
    </div>

    <div id="quiz-container">
        <h2>Quiz de Révision</h2>
        <p id="question"></p>
        <button onclick="answer(true)">Vrai</button>
        <button onclick="answer(false)">Faux</button>
        <p id="explanation"></p>
    </div>

    <div id="score-container">
        <h2>Score Final</h2>
        <p id="score"></p>
    </div>

    <script>
        const correctCode = "1234";  // Code d'accès unique
        const questions = [
            { q: "Un signal analogique a une fréquence fixe.", a: false, e: "Un signal analogique varie continuellement en amplitude et en fréquence." },
            { q: "Un microphone à condensateur nécessite une alimentation fantôme.", a: true, e: "Les microphones à condensateur nécessitent généralement une alimentation de +48V." }
        ];
        let score = 0, index = 0;

        function checkAccess() {
            const inputCode = document.getElementById("access-code").value;
            if (inputCode === correctCode) {
                document.getElementById("access-container").style.display = "none";
                document.getElementById("quiz-container").style.display = "block";
                loadQuestion();
            } else {
                alert("Code incorrect !");
            }
        }

        function loadQuestion() {
            if (index < questions.length) {
                document.getElementById("question").textContent = questions[index].q;
                document.getElementById("explanation").textContent = "";
            } else {
                document.getElementById("quiz-container").style.display = "none";
                document.getElementById("score-container").style.display = "block";
                document.getElementById("score").textContent = `Votre score : ${score}/${questions.length}`;
            }
        }

        function answer(userAnswer) {
            if (userAnswer === questions[index].a) {
                score++;
            }
            document.getElementById("explanation").textContent = questions[index].e;
            index++;
            setTimeout(loadQuestion, 2000);
        }
    </script>
</body>
</html>

