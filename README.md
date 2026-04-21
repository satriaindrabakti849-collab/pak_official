<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PNK - Perlindungan Nusantara Komunitas</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <style>
        :root {
            --primary: #004e92;
            --secondary: #000428;
            --accent: #00d2ff;
            --text: #ffffff;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, var(--secondary), var(--primary));
            color: var(--text);
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow-x: hidden;
        }

        #app-container {
            width: 100%;
            max-width: 450px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            text-align: center;
        }

        /* Animasi Tombol */
        .btn {
            background: var(--accent);
            color: var(--secondary);
            border: none;
            padding: 12px 25px;
            border-radius: 50px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            margin-top: 15px;
            text-decoration: none;
            display: inline-block;
        }

        .btn:active { transform: scale(0.95); }

        /* Chat AI Box */
        #chat-box {
            height: 300px;
            overflow-y: auto;
            background: rgba(0,0,0,0.3);
            border-radius: 10px;
            padding: 10px;
            margin: 20px 0;
            text-align: left;
            font-size: 14px;
        }

        .input-group { margin-bottom: 15px; text-align: left; }
        input, select {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border-radius: 5px;
            border: none;
            box-sizing: border-box;
        }

        /* Kartu Intro */
        #id-card {
            background: linear-gradient(45deg, #1e3c72, #2a5298);
            padding: 20px;
            border-radius: 15px;
            border: 2px solid var(--accent);
            margin-top: 20px;
            display: none;
        }

        .hidden { display: none; }
    </style>
</head>
<body>

<div id="app-container">
    <div id="page1">
        <h2>PNK AI ASSISTANT</h2>
        <p>Sistem Keamanan Ketat & AI Cerdas</p>
        <div id="chat-box">
            <p><strong>AI:</strong> Halo! Selamat datang di PNK. Saya adalah AI sistem perlindungan nusantara yang baru. Silakan klik tombol di bawah untuk mulai registrasi.</p>
        </div>
        <button class="btn" onclick="startIntro()">🔊 Perkenalkan Diri</button>
        <br>
        <small style="display:block; margin-top:10px;">Owner: SatriaOfficial170</small>
    </div>

    <div id="page2" class="hidden">
        <h3>Form Registrasi Anggota</h3>
        <div class="input-group">
            <label>Nama Lengkap:</label>
            <input type="text" id="nama" placeholder="Masukkan nama...">
        </div>
        <div class="input-group">
            <label>Umur & Tgl Lahir:</label>
            <input type="text" id="ttl" placeholder="Contoh: 20, 17 Mei 2004">
        </div>
        <div class="input-group">
            <label>Username TikTok:</label>
            <input type="text" id="tiktok" placeholder="@username">
        </div>
        <div class="input-group">
            <label>Gender:</label>
            <select id="gender">
                <option value="Laki-laki">Laki-laki</option>
                <option value="Perempuan">Perempuan</option>
            </select>
        </div>
        <div class="input-group">
            <label>Asal Daerah:</label>
            <input type="text" id="asal" placeholder="Kota/Provinsi">
        </div>
        <div class="input-group">
            <label>Alasan Bergabung:</label>
            <input type="text" id="alasan" placeholder="Kenapa ingin gabung?">
        </div>
        <button class="btn" onclick="generateCard()">Proses Kartu & Join Grup</button>
    </div>

    <div id="page3" class="hidden">
        <h3>Kartu Anggota PNK</h3>
        <div id="id-card">
            <h4 style="margin:0">PNK MEMBER</h4>
            <hr>
            <p id="res-nama" style="margin:5px 0"></p>
            <p id="res-asal" style="font-size: 12px;"></p>
            <p id="res-status" style="color: #00d2ff;">STATUS: TERVERIFIKASI</p>
        </div>
        <p style="font-size: 12px; color: #ccc;">Kartu sedang diunduh otomatis...</p>
        <button class="btn" onclick="goToWhatsApp()">Masuk Grup WhatsApp</button>
    </div>
</div>

<script>
    // Audio Effect (Simulasi suara klik)
    const clickSound = new Audio('https://www.soundjay.com/buttons/sounds/button-16.mp3');

    function playClick() {
        clickSound.play();
    }

    function startIntro() {
        playClick();
        // Animasi transisi ke TikTok Owner sebentar sebelum form
        const chatBox = document.getElementById('chat-box');
        chatBox.innerHTML += "<p><strong>AI:</strong> Mengalihkan ke profil Owner untuk verifikasi...</p>";
        
        setTimeout(() => {
            window.open("https://www.tiktok.com/@satriaofficial170?_r=1&_t=ZS-95XtmwCfUSG", "_blank");
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
        }, 2000);
    }

    function generateCard() {
        playClick();
        // Ambil Data
        const nama = document.getElementById('nama').value;
        const asal = document.getElementById('asal').value;

        if(!nama || !asal) return alert("Mohon lengkapi data!");

        document.getElementById('res-nama').innerText = nama.toUpperCase();
        document.getElementById('res-asal').innerText = "ASAL: " + asal.toUpperCase();

        document.getElementById('page2').classList.add('hidden');
        document.getElementById('page3').classList.remove('hidden');
        document.getElementById('id-card').style.display = 'block';

        // Fitur Download Otomatis Menggunakan html2canvas
        setTimeout(() => {
            html2canvas(document.querySelector("#id-card")).then(canvas => {
                let link = document.createElement('a');
                link.download = 'PNK-ID-CARD-' + nama + '.png';
                link.href = canvas.toDataURL();
                link.click();
            });
        }, 1000);
    }

    function goToWhatsApp() {
        window.location.href = "https://chat.whatsapp.com/KJQGOzP9OazAF3MbyUFx65?mode=gi_t";
    }
</script>

</body>
</html>
