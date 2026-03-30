<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Strap SMP</title>

  <!-- Minecraft font -->
  <link href="https://fonts.cdnfonts.com/css/minecraft-4" rel="stylesheet">

  <style>
    body {
      margin: 0;
      font-family: 'Minecraft', Arial, sans-serif;
      background: linear-gradient(to bottom, #2b0000, #8b0000, #000000);
      color: white;
      text-align: center;
    }

    header {
      padding: 40px;
    }

    h1 {
      font-size: 50px;
      text-shadow: 0 0 10px red;
    }

    .tagline {
      color: #ffcccc;
    }

    .box {
      background: rgba(0,0,0,0.7);
      margin: 20px auto;
      padding: 20px;
      border-radius: 10px;
      width: 90%;
      max-width: 500px;
      box-shadow: 0 0 15px rgba(255,0,0,0.5);
    }

    .ip {
      font-size: 22px;
      color: #ff4d4d;
    }

    button {
      margin-top: 10px;
      padding: 10px 20px;
      border: none;
      background: #ff0000;
      color: white;
      border-radius: 5px;
      cursor: pointer;
      font-family: 'Minecraft', Arial, sans-serif;
    }

    button:hover {
      background: #cc0000;
    }

    .discord-btn {
      background: #5865F2;
    }

    footer {
      margin-top: 30px;
      color: #aaa;
    }
  </style>
</head>

<body>

<header>
  <h1>⚔️ Strap SMP</h1>
  <p class="tagline">Lifesteal Minecraft Server (Aternos Hosted)</p>
</header>

<div class="box">
  <h2>🎮 Server IP</h2>
  <p class="ip" id="serverIP">YOUR-ATERNOS-IP.aternos.me</p>
  <button onclick="copyIP()">Copy IP</button>
</div>

<div class="box">
  <h2>📡 Server Status</h2>
  <p id="status">Checking...</p>
</div>

<div class="box">
  <h2>💬 Join our Discord</h2>
  <a href="https://discord.gg/YOURCODE" target="_blank">
    <button onclick="playClick()" class="discord-btn">Join Discord</button>
  </a>
</div>

<div class="box">
  <h2>🔥 About</h2>
  <p>
    Strap SMP is a Lifesteal server where killing players gives hearts ❤️  
    and dying removes them. Survive and dominate!
  </p>
</div>

<footer>
  © 2026 Strap SMP
</footer>

<!-- Sound effect -->
<audio id="clickSound" src="https://www.myinstants.com/media/sounds/minecraft_click.mp3"></audio>

<script>
  function playClick() {
    document.getElementById("clickSound").play();
  }

  function copyIP() {
    playClick();
    const ip = document.getElementById("serverIP").innerText;
    navigator.clipboard.writeText(ip);
    alert("Copied: " + ip);
  }

  fetch("https://api.mcsrvstat.us/2/YOUR-ATERNOS-IP.aternos.me")
    .then(res => res.json())
    .then(data => {
      const status = document.getElementById("status");
      if (data.online) {
        status.innerHTML = "🟢 Online (" + data.players.online + "/" + data.players.max + ")";
      } else {
        status.innerHTML = "🔴 Offline";
      }
    });
</script>

</body>
</html>
