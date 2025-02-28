<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Quiz</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .quiz-container {
            background-color: white;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 600px;
        }
        .quiz-container h2 {
            text-align: center;
        }
        .question {
            margin-bottom: 20px;
        }
        .options {
            list-style-type: none;
            padding: 0;
        }
        .options li {
            margin-bottom: 10px;
        }
        .btn {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }
        .btn:hover {
            background-color: #45a049;
        }
        .result {
            text-align: center;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h2>Interactive Quiz</h2>

        <div class="question">
            <p>1. What is the capital of France?</p>
            <ul class="options">
                <li><input type="radio" name="q1" value="0"> London</li>
                <li><input type="radio" name="q1" value="1"> Paris</li>
                <li><input type="radio" name="q1" value="0"> Berlin</li>
            </ul>
        </div>

        <div class="question">
            <p>2. What is 2 + 2?</p>
            <ul class="options">
                <li><input type="radio" name="q2" value="0"> 3</li>
                <li><input type="radio" name="q2" value="1"> 4</li>
                <li><input type="radio" name="q2" value="0"> 5</li>
            </ul>
        </div>

        <button class="btn" onclick="calculateScore()">Submit</button>
        <div class="result" id="result"></div>
    </div>

    <script>
        function calculateScore() {
            var score = 0;
            var totalQuestions = 2;

            // Get selected answers
            var q1 = document.querySelector('input[name="q1"]:checked');
            var q2 = document.querySelector('input[name="q2"]:checked');

            // Calculate score
            if (q1 && q1.value == "1") score++;
            if (q2 && q2.value == "1") score++;

            // Display result
            var result = document.getElementById('result');
            result.innerHTML = "You scored " + score + " out of " + totalQuestions + ".";
        }
    </script>
</body>
</html>
