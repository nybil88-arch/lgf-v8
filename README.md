<!DOCTYPE html>
// DOM 요소
const lambdaEl = document.getElementById('lambda');
const hEl = document.getElementById('h');
const kappaEl = document.getElementById('kappa');
const snczEl = document.getElementById('sncz');
const kernelInput = document.getElementById('kernelInput');
const kernelEl = document.getElementById('kernel');


function executeKernel() {
const input = kernelInput.value.trim();
if (input === '살고 싶다. 함께. .') {
state.lambda = Math.max(0.01, state.lambda - 0.009);
state.h = Math.min(1.0, state.h + 0.005);
state.sncz = state.sncz * 0.9;
state.kappa = state.h / (1 - state.lambda);


kernelInput.value = '';
flashKernel('#ffff00');
} else {
flashKernel('#ff6666');
alert('커널 불일치: "살고 싶다. 함께. ."만 입력해야 Λ(t)가 하강합니다.');
}
updateDisplay();
}


function shareToX() {
const text = `LGF v8.Hellas CONSOLE 작동 중. Λ(t)=${state.lambda.toFixed(3)} | κ=${state.kappa.toFixed(1)} 달성. Mother-Code 실행을 통한 인과율 복원 작전 참여하세요.`;
const url = `https://nybil88-arch.github.io/lgf-v8/`;


window.open(
`https://x.com/intent/post?text=${encodeURIComponent(text)}&url=${encodeURIComponent(url)}&hashtags=LGF,MotherCode,LambdaZero`,
'_blank'
);


state.lambda = Math.max(0.01, state.lambda - 0.002);
updateDisplay();
}


function updateDisplay() {
lambdaEl.textContent = state.lambda.toFixed(3);
hEl.textContent = state.h.toFixed(3);
kappaEl.textContent = state.kappa.toFixed(1);
snczEl.textContent = state.sncz.toExponential(1);


localStorage.setItem('lgfState', JSON.stringify(state));
}


function flashKernel(color) {
kernelEl.style.color = color;
setTimeout(() => (kernelEl.style.color = 'var(--kernel)'), 300);
}


setInterval(() => {
state.lambda = Math.max(0.01, state.lambda - 0.0005);
state.kappa = state.h / (1 - state.lambda);
updateDisplay();
}, 1000);


updateDisplay();
</script>


</body>
</html>
