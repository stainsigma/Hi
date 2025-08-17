<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>⚠️ RANSOMWARE LOCK ⚠️</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      height: 100vh;
      background: black;
      color: lime;
      font-family: monospace;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
    }
    .warning {
      font-size: 30px;
      color: red;
      font-weight: bold;
      animation: blink 0.7s infinite;
    }
    @keyframes blink {
      0%, 100% { color: red; }
      50% { color: yellow; }
    }
    #output {
      font-size: 16px;
      white-space: pre-line;
      margin: 15px;
      max-width: 600px;
      text-align: left;
    }
    .input-area {
      margin-top: 20px;
    }
    input {
      padding: 10px;
      font-size: 18px;
      border: 2px solid red;
      border-radius: 8px;
      background: black;
      color: lime;
      text-align: center;
      outline: none;
      width: 200px;
    }
    button {
      margin-top: 15px;
      padding: 10px 20px;
      font-size: 18px;
      border: none;
      border-radius: 8px;
      background: red;
      color: white;
      cursor: pointer;
      box-shadow: 0 0 10px red;
    }
    button:hover { background: darkred; }
  </style>
</head>
<body>
  <div class="warning">⚠️ PERANGKAT ANDA TERKUNCI ⚠️</div>
  <div id="output"></div>

  <div class="input-area">
    <input type="password" id="pass" placeholder="Masukkan Kode Unlock">
    <br>
    <button onclick="cekPassword()">Unlock</button>
  </div>

  <audio id="beep">
    <source src="https://actions.google.com/sounds/v1/alarms/beep_short.ogg" type="audio/ogg">
  </audio>

  <script>
    const output = document.getElementById("output");
    const beep = document.getElementById("beep");

    function ketik(teks, delay = 50) {
      return new Promise(resolve => {
        let i = 0;
        let interval = setInterval(() => {
          output.innerHTML += teks[i];
          i++;
          if (i >= teks.length) {
            clearInterval(interval);
            output.innerHTML += "\n";
            resolve();
          }
        }, delay);
      });
    }

    async function mulai() {
      await ketik("🔍 Memindai file sistem...");
      await ketik("⚡ File berhasil terenkripsi!\n");

      for (let i = 0; i < 5; i++) {
        let file = "/system/file_" + Math.floor(Math.random()*9999) + ".dat";
        await ketik("Mengunci " + file, 15);
        beep.play();
        if (navigator.vibrate) navigator.vibrate(200);
      }

      await ketik("\n💀 Masukkan Kode Unlock untuk membuka perangkat.");
    }

    function cekPassword() {
      let pass = document.getElementById("pass").value;
      if (pass === "1234") {
        alert("😂 PRANK!!! Semua aman, nggak ada yang terkunci.");
      } else {
        alert("❌ Kode salah! File tetap terkunci!");
        if (navigator.vibrate) navigator.vibrate([300,150,300]);
      }
    }

    // Cegah user keluar dari halaman
    setInterval(() => {
      if (document.hidden) {
        window.location.href = window.location.href;
      }
    }, 800);

    mulai();
  </script>
</body>
</html>
