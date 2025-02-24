<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 300vh;
        }
        .qz {
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 90%;
            max-width: 600px;
            padding: 20px;
            text-align: center;
        }
        .q {
            font-size: 1.4em;
            margin-bottom: 20px;
            color: #333;
            font-weight: bold;
        }
        .opts {
            display: flex;
            flex-direction: column;
            gap: 15px;
            align-items: center;
            width: 100%;
        }
        .opt {
            padding: 12px 20px;
            border: 2px solid #ccc;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.1em;
            width: 80%;
            transition: background-color 0.3s, color 0.3s;
        }
        .opt:hover {
            background-color: #007bff;
            color: #fff;
        }
        .tm {
            font-size: 1.2em;
            margin-bottom: 20px;
            color: #ff5722;
        }
        .rs {
            font-size: 1.5em;
            color: #4caf50;
        }
        .rst-btn {
            background-color: #007bff;
            color: #fff;
            border: none;
            padding: 12px 24px;
            font-size: 1.2em;
            border-radius: 8px;
            cursor: pointer;
            margin-top: 20px;
            transition: background-color 0.3s;
        }
        .rst-btn:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="qz">
        <div class="tm">Time Left: <span id="t">30</span>s</div>
        <div class="q">Question will appear here</div>
        <div class="opts">
        </div>
        <div class="rs" style="display: none;">
            Your score: <span id="sc">0</span>
        </div>
        <button class="rst-btn" style="display: none;">Restart Quiz</button>
    </div>
    <script defer src="intro.js"></script>
</body>
</html>

