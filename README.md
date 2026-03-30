
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Strap SMP</title>
<style>
  body {
    margin: 0;
    font-family: 'Minecraft', Arial, sans-serif;
    background: linear-gradient(to bottom, #2b0000, #8b0000, #000000);
    color: white;
    text-align: center;
    padding: 40px;
  }
  header h1 {
    font-size: 50px;
    text-shadow: 0 0 10px red;
    margin-bottom: 10px;
  }
  .tagline {
    color: #ffcccc;
    font-style: italic;
  }
  .box {
    background: rgba(0, 0, 0, 0.7);
    margin: 20px auto;
    padding: 20px;
    border-radius: 10px;
    max-width: 500px;
    box-shadow: 0 0 15px rgba(255, 0, 0, 0.5);
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
    font-weight: bold;
    transition: background-color 0.3s ease;
  }
  button:hover {
    background: #cc0000;
  }
  .discord-btn {
    background: #5865F2;
    margin-top: 20px;
    display: inline-block;
    padding: 10px 25px;
    border-radius: 8px;
    text-decoration: none;
    color: white;
    font-weight: bold;
  }
  footer {
    margin-top: 30px;
    color: #aaa;
  }
  #status {
    font-weight: bold;
    margin-top: 10px;
  }
</style>
</head>
<body>

<header>
  <h1>⛏️ Strap SMP</h1>
  <p class="tagline">Lifesteal Minecraft Server (Aternos Hosted)</p>
</header>

<div class="box">
  <h2>🎮 Server IP</h2>
  <p id="serverIP">YOUR-ATERNOS-IP.aternos.me</p>
  <button id="copyBtn">Copy IP</button>
</div>

<div class="box">
  <h2>📡 Server Status</h2>
  <p id="status">Checking...</p>
</div>

<div class="box">
  <h2>💬 Join our Discord</h2>
  <a href="https://your-discord-link-here" target="_blank" class="discord-btn">Join Discord</a>
</div>

<footer>
  © 2026 Strap SMP
</footer>

<script>
  const serverIP = document.getElementById('serverIP').textContent.trim();
  const statusEl = document.getElementById('status');
  const copyBtn = document.getElementById('copyBtn');

  // Copy IP to clipboard
  copyBtn.addEventListener('click', () => {
    navigator.clipboard.writeText(serverIP).then(() => {
      alert('Copied: ' + serverIP);
    }).catch(() => {
      alert('Failed to copy');
    });
  });

  // Fetch server status from mcstatus API
  async function fetchStatus() {
    try {
      const res = await fetch(`https://api.mcsrvstat.us/2/${serverIP}`);
      const data = await res.json();

      if (data.online) {
        statusEl.textContent = `🟢 Online — ${data.players.online} / ${data.players.max} players`;
      } else {
        statusEl.textContent = '🔴 Offline';
      }
    } catch (error) {
      statusEl.textContent = 'Error fetching status';
      console.error(error);
    }
  }

  fetchStatus();

  // Optionally, refresh status every 60 seconds
  setInterval(fetchStatus, 60000);
</script>

</body>
</html>
