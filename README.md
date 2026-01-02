# index.html
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sistem Uyarısı | 0x88219</title>
    <style>
        body { background: #000; color: #0f0; font-family: 'Courier New', Courier, monospace; margin: 0; overflow: hidden; height: 100vh; font-size: 13px; }
        #overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 1000; padding: 20px; box-sizing: border-box; }
        .red { color: #ff0000; font-weight: bold; }
        .blink { animation: blinker 0.2s linear infinite; }
        @keyframes blinker { 50% { opacity: 0; } }
        .scanline { position: absolute; top: 0; width: 100%; height: 2px; background: rgba(0, 255, 0, 0.1); animation: scan 4s linear infinite; }
        @keyframes scan { from { top: 0; } to { top: 100%; } }
        .hidden { display: none; }
        #final-screen { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #000; display: none; flex-direction: column; justify-content: center; align-items: center; z-index: 9999; }
    </style>
</head>
<body onclick="enableAudio()">

<div class="scanline"></div>
<div id="overlay">
    <div id="console"></div>
</div>

<div id="final-screen">
    <h1 class="red blink" style="font-size: 40px;">HACKED</h1>
    <p style="color: white; text-align: center; padding: 20px;">
        TELEFONUNUZA TAM ERİŞİM SAĞLANDI.<br><br>
        TÜM KİŞİSEL VERİLERİNİZ (REHBER, FOTOĞRAFLAR, ŞİFRELER) UZAK SUNUCUYA AKTARILMIŞTIR.<br><br>
        <span class="red">CİHAZI KAPATMAK VERİ KAYBINI DURDURMAZ.</span>
    </p>
    <div style="border: 2px solid #0f0; padding: 10px; color: #0f0;">
        IP: <span id="user-ip">Yükleniyor...</span><br>
        CİHAZ: <span id="user-device">Tespit ediliyor...</span>
    </div>
</div>

<script>
    const consoleDiv = document.getElementById('console');
    const finalScreen = document.getElementById('final-screen');
    
    // Cihaz Bilgilerini Al
    const ua = navigator.userAgent;
    let deviceName = "Unknown Device";
    if (ua.indexOf("Android") > -1) deviceName = "Android Mobile";
    if (ua.indexOf("iPhone") > -1) deviceName = "Apple iPhone";

    const messages = [
        "> Initializing exploit...",
        "> Searching for vulnerabilities in " + deviceName + "...",
        "> [SUCCESS] Buffer overflow achieved.",
        "> Injecting payload into Kernel...",
        "> <span class='red'>WARNING: Firewall bypassed.</span>",
        "> Accessing Internal Storage (/sdcard/0)...",
        "> Uploading DCIM/Camera/ to 'dark_web_srv_4'...",
        "> Accessing WhatsApp Database (msgstore.db.crypt14)...",
        "> Downloading contact list...",
        "> <span class='red'>SENSITIVE DATA BREACH: 100%</span>",
        "> Synchronizing with cloud server...",
        "> Activating front camera... [OK]",
        "> Capture initiated...",
        "> Deleting system logs to hide tracks...",
        "> SHUTDOWN SEQUENCE INITIATED."
    ];

    let i = 0;
    function typeWriter() {
        if (i < messages.length) {
            let p = document.createElement('p');
            p.innerHTML = messages[i];
            consoleDiv.appendChild(p);
            consoleDiv.scrollTop = consoleDiv.scrollHeight;
            i++;
            setTimeout(typeWriter, Math.random() * 1000 + 500);
        } else {
            setTimeout(() => {
                document.getElementById('overlay').style.display = 'none';
                finalScreen.style.display = 'flex';
                document.getElementById('user-device').innerText = deviceName;
                document.getElementById('user-ip').innerText = "185." + Math.floor(Math.random()*255) + ".12.42";
            }, 1000);
        }
    }

    function enableAudio() {
        // Buraya istersen bir bip sesi ekleyebilirsin
        console.log("Audio enabled");
    }

    window.onload = () => {
        setTimeout(typeWriter, 1000);
    };
</script>

</body>
</html>

