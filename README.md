<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>System Scanner 💀</title>

  <style>
    body {
      margin: 0;
      background: #050505;
      color: #00ff66;
      font-family: monospace;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      text-align: center;
    }

    .box {
      width: 90%;
      max-width: 500px;
      padding: 25px;
      border: 1px solid #00ff66;
      border-radius: 15px;
      box-shadow: 0 0 25px #00ff6644;
    }

    h1 {
      font-size: 28px;
    }

    #status {
      margin: 25px 0;
      font-size: 18px;
      min-height: 50px;
    }

    .bar {
      width: 100%;
      height: 20px;
      background: #222;
      border-radius: 20px;
      overflow: hidden;
    }

    #progress {
      width: 0%;
      height: 100%;
      background: #00ff66;
      transition: width .2s;
    }

    button {
      margin-top: 25px;
      padding: 12px 25px;
      border: none;
      border-radius: 10px;
      background: #00ff66;
      color: #000;
      font-weight: bold;
      cursor: pointer;
    }

    #prank {
      display: none;
    }

    .emoji {
      font-size: 70px;
    }
  </style>
</head>

<body>

  <div class="box" id="main">
    <h1>⚠️ SYSTEM SCANNER</h1>

    <div id="status">Preparing scan...</div>

    <div class="bar">
      <div id="progress"></div>
    </div>

    <button onclick="startPrank()">START SCAN</button>
  </div>

  <div class="box" id="prank">
    <div class="emoji">💀</div>
    <h1>BRO GOT PRANKED 😭</h1>
    <p>Relax bro, nothing happened 💀</p>
    <p>It was just a fake prank website 😂</p>
  </div>

  <script>
    function startPrank() {
      let progress = 0;
      const bar = document.getElementById("progress");
      const status = document.getElementById("status");

      const messages = [
        "Scanning system...",
        "Checking files...",
        "Analyzing Wi-Fi...",
        "Scanning memes...",
        "Detecting skill level...",
        "Almost done 💀"
      ];

      const interval = setInterval(() => {
        progress += Math.floor(Math.random() * 12) + 5;

        if (progress >= 100) {
          progress = 100;
          clearInterval(interval);

          setTimeout(() => {
            document.getElementById("main").style.display = "none";
            document.getElementById("prank").style.display = "block";
          }, 800);
        }

        bar.style.width = progress + "%";

        status.textContent =
          messages[Math.min(
            Math.floor(progress / 18),
            messages.length - 1
          )];
      }, 500);
    }
  </script>

</body>
</html>

