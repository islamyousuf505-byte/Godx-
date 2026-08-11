<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>👀 Don't Click</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  height: 100vh;
  background: #000;
  color: white;
  font-family: monospace;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

#start {
  text-align: center;
}

button {
  padding: 18px 35px;
  border: 2px solid red;
  background: black;
  color: red;
  font-size: 20px;
  font-family: monospace;
  border-radius: 10px;
  cursor: pointer;
  box-shadow: 0 0 20px red;
}

button:hover {
  background: red;
  color: black;
}

#loading {
  display: none;
  text-align: center;
}

.bar {
  width: 300px;
  height: 20px;
  border: 1px solid red;
  margin-top: 20px;
}

.progress {
  width: 0%;
  height: 100%;
  background: red;
}

#scare {
  display: none;
  position: fixed;
  inset: 0;
  background: #000;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  z-index: 999;
}

.face {
  font-size: 150px;
  animation: shake 0.08s infinite;
  filter: drop-shadow(0 0 25px red);
}

.scary {
  color: red;
  font-size: 35px;
  font-weight: bold;
  text-shadow: 0 0 15px red;
  animation: flash 0.15s infinite;
}

.dad {
  position: absolute;
  bottom: 15px;
  color: #777;
  font-size: 13px;
}

@keyframes shake {
  0% { transform: translate(5px, 5px) rotate(2deg); }
  50% { transform: translate(-5px, -5px) rotate(-2deg); }
  100% { transform: translate(5px, -5px) rotate(2deg); }
}

@keyframes flash {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.2; }
}
</style>
</head>

<body>

<div id="start">
  <h1>👀 DON'T CLICK</h1>
  <p>Seriously... don't.</p>
  <button onclick="startPrank()">CLICK IF YOU DARE 💀</button>
</div>

<div id="loading">
  <h2>Scanning your device...</h2>
  <p id="status">Initializing...</p>

  <div class="bar">
    <div class="progress" id="progress"></div>
  </div>
</div>

<div id="scare">
  <div class="face">👹</div>
  <div class="scary">GET JUMPSCARED 💀</div>
  <div class="dad">Made by Rahat's dad 😭</div>
</div>

<script>

function startPrank() {

  document.getElementById("start").style.display = "none";
  document.getElementById("loading").style.display = "block";

  let percent = 0;

  const messages = [
    "Initializing...",
    "Checking system...",
    "Scanning screen...",
    "Detecting suspicious activity...",
    "Almost done...",
    "WARNING ⚠️"
  ];

  let i = 0;

  const scan = setInterval(() => {

    percent += 10;

    document.getElementById("progress").style.width =
      percent + "%";

    if (i < messages.length) {
      document.getElementById("status").innerText =
        messages[i];
      i++;
    }

    if (percent >= 100) {

      clearInterval(scan);

      setTimeout(() => {
        jumpscare();
      }, 800);
    }

  }, 500);
}


function jumpscare() {

  document.getElementById("loading").style.display = "none";

  const scare = document.getElementById("scare");

  scare.style.display = "flex";

  // Fake jumpscare sound using Web Audio
  try {

    const audio = new AudioContext();
    const oscillator = audio.createOscillator();
    const gain = audio.createGain();

    oscillator.type = "sawtooth";
    oscillator.frequency.setValueAtTime(
      900,
      audio.currentTime
    );

    gain.gain.setValueAtTime(
      0.15,
      audio.currentTime
    );

    oscillator.connect(gain);
    gain.connect(audio.destination);

    oscillator.start();

    setTimeout(() => {
      oscillator.stop();
      audio.close();
    }, 700);

  } catch (e) {
    // Sound unavailable — jumpscare still works
  }
}

</script>

</body>
</html>
