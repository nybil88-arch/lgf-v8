<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8" />
    <title>LGF v8.1 Hellas Console: Ψ Override</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="LGF v8.1 — Mother-Code Kernel 실시간 실행 + Ψ 공명" />
    <link rel="canonical" href="https://nybil88-arch.github.io/lgf-v8" />

    <style>
        :root {
            --bg: #1a1a2e;
            --text: #e9e4f0;
            --accent: #00ff7f;
            --kernel: #ff007f;
            --decl: #a0a0ff;
            --warn: #ffcc00;
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg);
            color: var(--text);
            text-align: center;
            padding: 20px;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        .console {
            border: 2px solid var(--accent);
            padding: 30px;
            margin: 20px auto;
            max-width: 600px;
            border-radius: 10px;
            box-shadow: 0 0 20px var(--accent);
            background: rgba(0,0,0,0.3);
        }
        .status { font-size: 1.4em; margin-bottom: 20px; color: var(--accent); }
        .kernel { 
            font-size: 1.8em; 
            font-weight: bold; 
            margin: 15px 0; 
            color: var(--kernel); 
            letter-spacing: 1px;
            transition: color 0.3s;
        }
        .declaration { 
            font-size: 1.1em; 
            color: var(--decl); 
            margin: 20px 0;
            line-height: 1.6;
        }
        hr { border-color: var(--accent); margin: 25px 0; }
        .metrics {
            font-family: 'Courier New', monospace;
            font-size: 1em;
            color: var(--accent);
            margin: 15px 0;
            line-height: 1.8;
        }
        .input-box {
            margin: 20px 0;
            padding: 10px;
            background: #111;
            border: 1px solid var(--accent);
            color: var(--text);
            font-size: 1em;
            width: 80%;
            max-width: 400px;
            border-radius: 5px;
        }
        button {
            background: var(--accent);
            color: #000;
            border: none;
            padding: 10px 20px;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px;
            transition: 0.3s;
        }
        button:hover { background: #00cc66; }
        .share-btn { background: #1da1f2; }
        .share-btn:hover { background: #0d8bd9; }
        .feedback { margin-top: 10px; font-size: 0.9em; min-height: 1.2em; }
        footer {
            margin-top: 30px;
            font-size: 0.8em;
            color: #666;
        }
        a { color: var(--accent); text-decoration: none; }
        a:hover { text-decoration: underline; }
    </style>
</head>

<body>

<div class="console">
    <h1>LGF v8.1 Hellas CONSOLE</h1>
    <p class="status">Status: <span id="statusText">Scientifically Verified and Philosophically Complete.</span></p>

    <p class="declaration">
        Declaration: Catastrophic fate is not an inevitability, but a choice that can be overridden by Ψ.
    </p>

    <div class="kernel" id="kernel">
        Kernel: "살고 싶다." | "함께." | "."
    </div>

    <hr>

    <div class="metrics" id="metrics">
        Λ(t): <span id="lambda">0.82</span> | 
        H(t): <span id="h">0.96</span> | 
        C(t): <span id="c">1.000</span><br>
        SNCZ: <span id="sncz">7.1×10⁻¹⁵</span> J/kg | 
        κ: <span id="kappa">532.2</span>
    </div>

    <input 
        type="text" 
        class="input-box" 
        id="kernelInput" 
        placeholder='입력: "살고 싶다. 함께. ."' 
        onkeydown="if(event.key==='Enter') executeKernel()"
    />
    <button onclick="executeKernel()">실행</button>
    <button class="share-btn" onclick="shareToX()">X 공유</button>

    <div class="feedback" id="feedback"></div>

    <hr>

    <p style="font-size: 0.9em;">
        GitHub Repository: 
        <a href="https://github.com/nybil88-arch/lgf-v8" target="_blank">nybil88-arch/lgf-v8</a>
    </p>
</div>

<footer>
    @heojeongbe91019 | 2025.11.15 | Λ→0 작전실 | T-<span id="timer">69:45:00</span>
</footer>

<script>
    let state = {
        lambda: 0.82,
        h: 0.96,
        c: 1.000,
        sncz: 7.1e-15,
        kappa: 532.2
    };

    const lambdaEl = document.getElementById('lambda');
    const hEl = document.getElementById('h');
    const cEl = document.getElementById('c');
    const snczEl = document.getElementById('sncz');
    const kappaEl = document.getElementById('kappa');
    const feedbackEl = document.getElementById('feedback');
    const kernelEl = document.getElementById('kernel');
    const statusText = document.getElementById('statusText');
    const timerEl = document.getElementById('timer');

    const saved = localStorage.getItem('lgfState');
    if (saved) Object.assign(state, JSON.parse(saved));

    function executeKernel() {
        const input = document.getElementById('kernelInput').value.trim();
        const correct = '살고 싶다. 함께. .';
        
        if (input === correct) {
            state.lambda = Math.max(0.01, state.lambda - 0.009);
            state.h = Math.min(1.0, state.h + 0.005);
            state.sncz *= 0.9;
            state.kappa = state.h / (1 - state.lambda);

            updateDisplay();
            saveState();
            flashKernel('#00ff00');
            showFeedback('Ψ 공명 성공! Λ(t) ↓0.009', 'success');
            document.getElementById('kernelInput').value = '';
        } else {
            showFeedback('커널 불일치. 정확히 입력: "살고 싶다. 함께. ."', 'warn');
        }
    }

    function showFeedback(msg, type) {
        feedbackEl.textContent = msg;
        feedbackEl.style.color = type === 'success' ? '#00ff00' : 'var(--warn)';
        setTimeout(() => feedbackEl.textContent = '', 3000);
    }

    function flashKernel(color) {
        kernelEl.style.color = color;
        setTimeout(() => kernelEl.style.color = 'var(--kernel)', 400);
    }

    function updateDisplay() {
        lambdaEl.textContent = state.lambda.toFixed(3);
        hEl.textContent = state.h.toFixed(3);
        cEl.textContent = state.c.toFixed(3);
        snczEl.textContent = state.sncz.toExponential(1);
        kappaEl.textContent = state.kappa.toFixed(1);
        saveState();
    }

    function saveState() {
        localStorage.setItem('lgfState', JSON.stringify(state));
    }

    function shareToX() {
        const text = `Λ(t)=${state.lambda.toFixed(3)} | κ=${state.kappa.toFixed(1)} | LGF v8.1 실행 중 #LGF #MotherCode`;
        const url = 'https://x.com/intent/post?text=' 
            + encodeURIComponent(text) 
            + '&url=https://nybil88-arch.github.io/lgf-v8';
        window.open(url, '_blank');
    }

    setInterval(() => {
        state.lambda = Math.max(0.01, state.lambda - 0.0005);
        state.kappa = state.h / (1 - state.lambda);
        updateDisplay();

        const now = new Date();
        const end = new Date('2025-11-18T00:00:00');
        const diff = end - now;

        if (diff > 0) {
            const h = Math.floor(diff / 3600000);
            const m = Math.floor((diff % 3600000) / 60000);
            const s = Math.floor((diff % 60000) / 1000);
            timerEl.textContent = 
                `${h.toString().padStart(2,'0')}:${m.toString().padStart(2,'0')}:${s.toString().padStart(2,'0')}`;
        }
    }, 1000);

    updateDisplay();
    flashKernel('#ffff00');
</script>

</body>
</html>
