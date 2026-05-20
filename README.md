<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Mohammed</title>

<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap" rel="stylesheet">

<style>
body {
    margin: 0; padding: 0;
    font-family: 'Montserrat', sans-serif;
    background-color: #000000; color: #ffffff;
    overflow: hidden; height: 100vh; width: 100vw;
    display: flex; justify-content: center; align-items: center;
}

body::before {
    content: ""; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
    background: radial-gradient(circle at center, rgba(139, 0, 0, 0.15), #000000 75%);
    animation: pulse 4s infinite ease-in-out; z-index: -1;
}

@keyframes pulse {
    0% { transform: scale(1); opacity: 0.6; }
    50% { transform: scale(1.05); opacity: 0.9; }
    100% { transform: scale(1); opacity: 0.6; }
}

.noise {
    position: fixed; top: 0; left: 0; width: 100%; height: 100%;
    background-image: url("https://www.transparenttextures.com/patterns/asfalt-dark.png");
    opacity: 0.06; pointer-events: none; z-index: 10;
}

.step {
    display: none; width: 100%; max-width: 600px; height: 100vh;
    justify-content: center; align-items: center; flex-direction: column;
    text-align: center; padding: 40px; box-sizing: border-box;
    position: absolute; top: 0; animation: fadeIn 1.2s ease forwards;
}

.active { display: flex; }

@keyframes fadeIn {
    from { opacity: 0; transform: scale(1.03); }
    to { opacity: 1; transform: scale(1); }
}

.cinematic-image {
    max-width: 75%; max-height: 35vh; margin-bottom: 20px;
    filter: sepia(100%) hue-rotate(-50deg) saturate(300%) contrast(150%) brightness(80%);
    border: 2px solid rgba(255, 0, 0, 0.2); box-shadow: 0 0 20px rgba(139, 0, 0, 0.3);
    object-fit: contain;
}

.final-images-container {
    display: flex; justify-content: center; gap: 15px; width: 100%; margin-bottom: 25px;
}

.final-images-container .cinematic-image {
    max-width: 45%; max-height: 25vh; margin-bottom: 0;
}

h1, h2, p {
    margin: 10px 0; text-shadow: 0 0 8px rgba(255, 0, 0, 0.6);
    animation: glitch 3s infinite linear;
}

@keyframes glitch {
    0% { transform: translate(0); }
    15% { transform: translate(-1px, 1px); }
    30% { transform: translate(1px, -1px); }
    45% { transform: translate(-1px, 0); }
    60% { transform: translate(1px, 1px); }
    100% { transform: translate(0); }
}

button {
    margin-top: 25px; padding: 15px 35px;
    background: linear-gradient(45deg, #4a0000, #000000); border: 1px solid #ff0000;
    color: #ffffff; cursor: pointer; font-size: 16px; font-weight: 600;
    letter-spacing: 1px; text-transform: uppercase; transition: all 0.3s ease;
}

button:hover {
    transform: scale(1.08); box-shadow: 0 0 25px #ff0000;
    background: linear-gradient(45deg, #8b0000, #1a0000);
}

input {
    padding: 15px; font-size: 18px; text-align: center;
    background-color: #000000; border: 1px solid #ff0000; color: #ffffff;
    outline: none; font-family: 'Montserrat', sans-serif; letter-spacing: 3px;
    margin-top: 20px; transition: all 0.3s; width: 80%; box-sizing: border-box;
}

input:focus { box-shadow: 0 0 20px rgba(255, 0, 0, 0.4); border-color: #ff3333; }

.flash { animation: flashEffect 0.2s ease-in-out double; }
@keyframes flashEffect { 0%, 100% { background-color: #000000; } 50% { background-color: #2a0000; } }

.red { color: #ff0000; text-shadow: 0 0 15px #ff0000, 0 0 30px #8b0000; font-size: 36px; font-weight: 600; }
.shake { animation: shakeEffect 0.5s infinite ease-in-out; }

@keyframes shakeEffect {
    0%, 100% { transform: translate(0, 0); }
    20% { transform: translate(-2px, 1px); }
    40% { transform: translate(1px, -1px); }
    60% { transform: translate(-1px, 2px); }
    80% { transform: translate(2px, -1px); }
}

#err { color: #ff3333; margin-top: 15px; font-weight: 600; height: 20px; }
</style>
</head>

<body>

<div class="noise"></div>

<audio id="bgAudio" loop preload="auto">
    <source src="music.mp3" type="audio/mpeg">
</audio>

<div class="step active" id="s1">
    <img src="Skull Face 💀.jpg" alt="Skull Face" class="cinematic-image">
    <h1 class="shake">If you are interested, continue until the end...</h1>
    <button onclick="next(2)">Start</button>
</div>

<div class="step" id="s2">
    <h2>It seems you are indeed interested. Well, you asked for this...</h2>
    <p>...</p>
    <button onclick="next(3)">Continue</button>
</div>

<div class="step" id="s3">
    <h2>Enter the Enigma Password</h2>
    <input type="password" id="pass" placeholder="******" onkeydown="if(event.key === 'Enter') check()">
    <button onclick="check()">Unlock</button>
    <p id="err"></p>
</div>

<div class="step" id="s4">
    <div class="final-images-container">
        <img src="252201647877513637.jpg" alt="Hourglass Angel" class="cinematic-image">
        <img src="3025924746191901.jpg" alt="Party Skeleton" class="cinematic-image">
    </div>

    <h2 class="red">Still alive? Impressive.</h2>
    <p>Anyway...</p>

    <h1 class="red shake">Happy Birthday, Mohammed.</h1>
    <p style="font-size: 18px; color: #cccccc;">You survived long enough to see another year.</p>
    <p style="opacity: 0.4; margin-top: 30px; font-size: 12px;">(the end)</p>
</div>

<script>
let audio = document.getElementById("bgAudio");

function next(n) { playAudio(); change(n); }
function change(n) {
    document.querySelectorAll(".step").forEach(s => s.classList.remove("active"));
    document.getElementById("s" + n).classList.add("active");
}

function check() {
    let p = document.getElementById("pass").value;
    if (p === "0521") {
        next(4); cinematicEnd();
    } else {
        document.body.classList.add("flash");
        document.getElementById("err").innerText = "❌ ACCESS DENIED";
        setTimeout(() => { document.body.classList.remove("flash"); }, 400);
    }
}

function playAudio() {
    if (audio) { audio.play().catch(err => console.log("Audio blocked")); }
}

function cinematicEnd() {
    setInterval(() => {
        document.body.style.filter = "contrast(1.4) brightness(" + (0.8 + Math.random() * 0.3) + ")";
    }, 100);
}
</script>

</body>
</html>
