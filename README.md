<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>ANOMALY DETECTED</title>
<style>
@keyframes shake {
    0% { transform: translate(1px, 1px) rotate(0deg); }
    20% { transform: translate(-3px, 0px) rotate(1deg); }
    40% { transform: translate(1px, -1px) rotate(1deg); }
    60% { transform: translate(-3px, 1px) rotate(0deg); }
    80% { transform: translate(-1px, -1px) rotate(1deg); }
    100% { transform: translate(1px, -2px) rotate(-1deg); }
}

body, html {
    margin: 0; padding: 0; width: 100%; height: 100%;
    background: #000; color: #ff0033; font-family: monospace;
    display: flex; justify-content: center; align-items: center; overflow: hidden;
    animation: shake 0.3s infinite;
}

.container {
    background: #0a0000; border: 2px solid #ff0033; padding: 25px;
    box-shadow: 0 0 25px rgba(255, 0, 51, 0.4); text-align: center; width: 85%; max-width: 320px;
    box-sizing: border-box;
}

h2 { margin-bottom: 15px; font-size: 18px; letter-spacing: 2px; text-shadow: 0 0 8px #ff0033; }
.question { margin-bottom: 20px; font-size: 12px; color: #cc6666; line-height: 1.4; }

input {
    width: 100%; padding: 12px; background: #000; border: 1px solid #ff0033;
    color: #ff0033; font-family: monospace; font-size: 16px;
    text-align: center; box-sizing: border-box; margin-bottom: 15px; outline: none;
    box-shadow: inset 0 0 5px rgba(255, 0, 51, 0.5);
}

button {
    width: 100%; padding: 12px; background: #ff0033; color: #000; border: none;
    font-family: monospace; font-weight: bold; font-size: 16px;
    cursor: pointer;
}

.error { color: #ff9999; font-size: 11px; margin-top: 10px; height: 15px; }
.unlocked { display: none; font-size: 18px; color: #00ff66; text-shadow: 0 0 10px #00ff66; }
</style>
</head>
<body>

<div class="container" id="lockbox">
    <h2>CONTAINMENT BREACH</h2>
    <div class="question">YOU CANNOT ESCAPE THIS SESSION. ENTER THE SEQUENCE TO CEASE THE ANOMALY.</div>
    <input type="password" id="passInput" placeholder="ENTER CODE" pattern="[0-9]*" inputmode="numeric" maxlength="8">
    <button onclick="checkPass()">OVERRIDE</button>
    <div class="error" id="errorMsg"></div>
</div>

<div class="container unlocked" id="contentBox">
    <h2>STABILIZED</h2>
    <p>Session control returned.</p>
</div>

<script>
const CORRECT_PASS = "7935";

function checkPass() {
    const val = document.getElementById('passInput').value;
    const err = document.getElementById('errorMsg');
    
    if (val === CORRECT_PASS) {
        document.body.style.animation = 'none';
        document.getElementById('lockbox').style.display = 'none';
        document.getElementById('contentBox').style.display = 'block';
    } else {
        err.innerText = "WRONG. THE WALLS ARE CLOSING.";
        document.getElementById('passInput').value = '';
        setTimeout(() => { err.innerText = ""; }, 2000);
    }
}

document.getElementById('passInput').addEventListener('keypress', function (e) {
    if (e.key === 'Enter') {
        checkPass();
    }
});
</script>

</body>
</html>
