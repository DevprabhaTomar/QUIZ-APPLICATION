<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Quiz</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .quiz-container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .question {
            margin-bottom: 15px;
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
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h2>Simple Quiz</h2>

        <div class="question">
            <p>1. What is the capital of France?</p>
            <ul class="options">
                <li><input type="radio" name="q1" value="Paris"> Paris</li>
                <li><input type="radio" name="q1" value="London"> London</li>
                <li><input type="radio" name="q1" value="Berlin"> Berlin</li>
            </ul>
        </div>

        <div class="question">
            <p>2. What is 2 + 2?</p>
            <ul class="options">
                <li><input type="radio" name="q2" value="3"> 3</li>
                <li><input type="radio" name="q2" value="4"> 4</li>
                <li><input type="radio" name="q2" value="5"> 5</li>
            </ul>
        </div>

        <button class="btn">Submit</button>
    </div>
</body>
</html>



