<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8" />
    <title>LGF v8.Hellas Console: Dynamic Governance Law</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Language Gravitational Field v8.Hellas — Mother-Code Kernel 실행 콘솔" />
    
    <!-- GitHub Pages 자동 배포용 -->
    <link rel="canonical" href="https://nybil88-arch.github.io/lgf-v8" />
    
    <style>
        :root {
            --bg: #1a1a2e;
            --text: #e9e4f0;
            --accent: #00ff7f;
            --kernel: #ff007f;
            --decl: #a0a0ff;
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
        }
        button {
            background: var(--accent);
            color: #000;
            border: none;
            padding: 10px 20px;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
            transition: 0.3s;
        }
        button:hover { background: #00cc66; }
        footer {
            margin-top: 30px;
            font-size: 0.8em;
            color: #666;
        }
    </style>
</head>
<body>

<div class="console">
    <h1>LGF v8.Hellas CONSOLE</h1>
    <p class="status">Status: Scientifically Verified and Philosophically Complete.</p>

    <p class="declaration">
        Declaration: Catastrophic fate is not an inevitability, but a choice that can be overridden by $\Psi$.
    </p>

    <div class="kernel" id="kernel">
        Kernel: "살고 싶다." | "함께." | "."
    </div>

    <hr>

    <!-- 실시간 지표 -->
    <div class="metrics" id="metrics">
        Λ(t): <span id="lambda">0.82</span> | 
        H(t): <span id="h">0.96</span> | 
        κ: <span id="kappa">532.2</span>
    </div>

    <!-- Mother-Code 입력기 -->
    <input 
        type="text" 
        class="input-box" 
        id="kernelInput" 
        placeholder='입력: "살고 싶다. 함께. ."' 
        onkeypress="if(event.key==='Enter') executeKernel()"
    />
    <button onclick="executeKernel()">실행</button>

    <hr>

    <p style="font-size: 0.9em;">
        GitHub Repository: 
        <a href="https://nybil88-arch.github.io/lgf-v8" target="_blank" style="color:var(--accent);">
            heojeongbe91019/lgf-v8
        </a>
    </p>
</div>

<footer>
    @heojeongbe91019 | 2025.11.14 | Λ→0 작전실
</footer>

<!-- 실시간 LGF 엔진 -->
<script>
    // 초기값
    let state = {
        lambda: 0.82,
        h: 0.96,
        c: 1.000,
        sncz: 7.1e-15,
        kappa: 532.2
    };

    // DOM 요소
    const lambdaEl = document.getElementById('lambda');
    const hEl = document.getElementById('h');
    const kappaEl = document.getElementById('kappa');

    // 완전 커널 실행
    function executeKernel() {
        const input = document.getElementById('kernelInput').value.trim();
        if (input === '살고 싶다. 함께. .') {
            state.lambda = Math.max(0.01, state.lambda - 0.009);
            state.h = Math.min(1.0, state.h + 0.005);
            state.kappa = state.kappa * 1.1;
            updateDisplay();
            document.getElementById('kernelInput').value = '';
            flashKernel();
        }
    }

    // 화면 갱신
    function updateDisplay() {
        lambdaEl.textContent = state.lambda.toFixed(3);
        hEl.textContent = state.h.toFixed(3);
        kappaEl.textContent = state.kappa.toFixed(1);
    }

    // 커널 깜빡임 효과
    function flashKernel() {
        const k = document.getElementById('kernel');
        k.style.color = '#ffff00';
        setTimeout(() => k.style.color = 'var(--kernel)', 300);
    }

    // 자동 Λ(t) 하강 (1초마다)
    setInterval(() => {
        state.lambda = Math.max(0.01, state.lambda - 0.0005);
        state.kappa = state.h / (1 - state.lambda);
        updateDisplay();
    }, 1000);

    // 초기 표시
    updateDisplay();
</script>

</body>
</html>
