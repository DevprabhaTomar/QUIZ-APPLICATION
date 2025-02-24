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
            height: 100vh;
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
            display: none;
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
            display: none;
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
        <div class="rs">
            Your score: <span id="sc">0</span>
        </div>
        <button class="rst-btn">Restart Quiz</button>
    </div>
    <script>
        window.onload = function () {
            const quiz = [
                { q: "What is the capital of France?", opts: ["Berlin", "Madrid", "Paris", "Lisbon"], ans: "Paris" },
                { q: "Which language is used for web development?", opts: ["Python", "HTML", "Java", "C++"], ans: "HTML" },
                { q: "Who wrote 'Hamlet'?", opts: ["Charles Dickens", "William Shakespeare", "Mark Twain", 
                "Jane Austen"], ans: "William Shakespeare" }
            ];

            let idx = 0, scr = 0, time = 30, timer;
            const timeEl = document.getElementById('t');
            const qEl = document.querySelector('.q');
            const optsEl = document.querySelector('.opts');
            const resEl = document.querySelector('.rs');
            const scrEl = document.getElementById('sc');
            const restartEl = document.querySelector('.rst-btn');

            function loadQ() {
                if (idx >= quiz.length) return endQ();
                const qData = quiz[idx];
                qEl.textContent = qData.q;
                optsEl.innerHTML = '';
                qData.opts.forEach((opt, i) => {
                    const btn = document.createElement('button');
                    btn.classList.add('opt');
                    btn.textContent = `${i + 1}. ${opt}`;
                    btn.onclick = () => checkA(opt);
                    optsEl.appendChild(btn);
                });
            }

            function checkA(opt) {
                if (opt === quiz[idx].ans) scr++;
                idx++;
                loadQ();
            }

            function startT() {
                timer = setInterval(() => {
                    time--;
                    timeEl.textContent = time;
                    if (time <= 0) endQ();
                }, 1000);
            }

            function endQ() {
                clearInterval(timer);
                qEl.style.display = 'none';
                optsEl.style.display = 'none';
                resEl.style.display = 'block';
                scrEl.textContent = scr;
                restartEl.style.display = 'block';
            }

            restartEl.addEventListener('click', () => {
                idx = 0; scr = 0; time = 30;
                timeEl.textContent = time;
                qEl.style.display = 'block';
                optsEl.style.display = 'block';
                resEl.style.display = 'none';
                restartEl.style.display = 'none';
                loadQ();
                startT();
            });
            loadQ();
            startT();
        };
    </script>
</body>
</html>
