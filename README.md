<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Application</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
            margin: 0;
        }
        .quiz-container {
            width: 50%;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <div id="quiz"></div>
        <button id="submit">Submit Quiz</button>
        <div id="results"></div>
    </div>
    <script>
        const quizData = [
            {
                question: "What is the capital of France?",
                options: ["Berlin", "Madrid", "Paris", "Lisbon"],
                correct: "Paris"
            },
            {
                question: "What is 2 + 2?",
                options: ["3", "4", "5", "6"],
                correct: "4"
            },
            // Add more questions here
        ];

        const quizContainer = document.getElementById('quiz');
        const resultsContainer = document.getElementById('results');
        const submitButton = document.getElementById('submit');

        function buildQuiz() {
            const output = [];

            quizData.forEach((currentQuestion, questionIndex) => {
                const options = [];

                for (letter in currentQuestion.options) {
                    options.push(
                        `<label>
                            <input type="radio" name="question${questionIndex}" value="${currentQuestion.options[letter]}">
                            ${letter} :
                            ${currentQuestion.options[letter]}
                        </label>`
                    );
                }

                output.push(
                    `<div class="question"> ${currentQuestion.question} </div>
                    <div class="options"> ${options.join('')} </div>`
                );
            });

            quizContainer.innerHTML = output.join('');
        }

        function showResults() {
            const answerContainers = quizContainer.querySelectorAll('.options');

            let numCorrect = 0;

            quizData.forEach((currentQuestion, questionIndex) => {
                const answerContainer = answerContainers[questionIndex];
                const selector = `input[name=question${questionIndex}]:checked`;
                const userAnswer = (answerContainer.querySelector(selector) || {}).value;

                if (userAnswer === currentQuestion.correct) {
                    numCorrect++;
                }
            });

            resultsContainer.innerHTML = `You got ${numCorrect} out of ${quizData.length} correct!`;
        }

        buildQuiz();
        submitButton.addEventListener('click', showResults);
    </script>
</body>
</html>


