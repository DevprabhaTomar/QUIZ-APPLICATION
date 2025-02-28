<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Quiz</title>
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


