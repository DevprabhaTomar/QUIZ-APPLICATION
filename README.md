<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Application</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        .quiz-container {
            width: 300px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        #quiz {
            margin-bottom: 20px;
        }

        .question {
            margin-bottom: 10px;
        }

        .answers {
            list-style-type: none;
            padding: 0;
        }

        .answers li {
            margin-bottom: 5px;
        }

        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 15px;
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
        const quizContainer = document.getElementById('quiz');
        const resultsContainer = document.getElementById('results');
        const submitButton = document.getElementById('submit');

        const myQuestions = [
            {
                question: "Who is the founder of Microsoft?",
                answers: {
                    a: "Steve Jobs",
                    b: "Bill Gates",
                    c: "Mark Zuckerberg"
                },
                correctAnswer: "b"
            },
            {
                question: "What does HTML stand for?",
                answers: {
                    a: "Hyper Text Markup Language",
                    b: "Highlevel Text Machine Language",
                    c: "Hyperlinks and Text Markup Language"
                },
                correctAnswer: "a"
            },
            {
                question: "Which programming language is known as the backbone of web development?",
                answers: {
                    a: "Python",
                    b: "Java",
                    c: "JavaScript"
                },
                correctAnswer: "c"
            }
        ];

        function buildQuiz() {
            const output = [];

            myQuestions.forEach((currentQuestion, questionNumber) => {
                const answers = [];

                for (letter in currentQuestion.answers) {
                    answers.push(
                        `<label>
                            <input type="radio" name="question${questionNumber}" value="${letter}">
                            ${letter} :
                            ${currentQuestion.answers[letter]}
                        </label>`
                    );
                }

                output.push(
                    `<div class="question"> ${currentQuestion.question} </div>
                    <div class="answers"> ${answers.join('')} </div>`
                );
            });

            quizContainer.innerHTML = output.join('');
        }

        function showResults() {
            const answerContainers = quizContainer.querySelectorAll('.answers');
            let numCorrect = 0;

            myQuestions.forEach((currentQuestion, questionNumber) => {
                const answerContainer = answerContainers[questionNumber];
                const selector = `input[name=question${questionNumber}]:checked`;
                const userAnswer = (answerContainer.querySelector(selector) || {}).value;

                if (userAnswer === currentQuestion.correctAnswer) {
                    numCorrect++;
                } 
            });

            resultsContainer.innerHTML = `${numCorrect} out of ${myQuestions.length}`;
        }

        buildQuiz();
        submitButton.addEventListener('click', showResults);
    </script>
</body>
</html>

