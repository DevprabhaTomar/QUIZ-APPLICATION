<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Application</title>
    <link rel="stylesheet" href="styles.css">/* styles.css */
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

</head>
<body>
    <div class="quiz-container">
        <div id="quiz"></div>
        <button id="submit">Submit Quiz</button>
        <div id="results"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>
// script.js
const quizContainer = document.getElementById('quiz');
const resultsContainer = document.getElementById('results');
const submitButton = document.getElementById('submit');

const quizQuestions = [
    {
        question: "Which is the largest planet in our solar system?",
        answers: {
            a: "Earth",
            b: "Jupiter",
            c: "Mars"
        },
        correctAnswer: "b"
    },
    {
        question: "What is the capital of France?",
        answers: {
            a: "Berlin",
            b: "London",
            c: "Paris"
        },
        correctAnswer: "c"
    },
    // Add more questions here
];

function buildQuiz() {
    const output = [];
    quizQuestions.forEach((currentQuestion, questionNumber) => {
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
            `<div class="question">${currentQuestion.question}</div>
            <div class="answers">${answers.join('')}</div>`
        );
    });
    quizContainer.innerHTML = output.join('');
}

function showResults() {
    const answerContainers = quizContainer.querySelectorAll('.answers');
    let numCorrect = 0;
    quizQuestions.forEach((currentQuestion, questionNumber) => {
        const answerContainer = answerContainers[questionNumber];
        const selector = `input[name=question${questionNumber}]:checked`;
        const userAnswer = (answerContainer.querySelector(selector) || {}).value;
        if (userAnswer === currentQuestion.correctAnswer) {
            numCorrect++;
            answerContainers[questionNumber].style.color = 'green';
        } else {
            answerContainers[questionNumber].style.color = 'red';
        }
    });
    resultsContainer.innerHTML = `You got ${numCorrect} out of ${quizQuestions.length} correct.`;
}

buildQuiz();
submitButton.addEventListener('click', showResults);


