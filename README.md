
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Vexora v2</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg: #090a0f;
            --card-bg: rgba(22, 27, 34, 0.85);
            --accent: #8a2be2;
            --accent-glow: #00d2ff;
            --text: #f0f6fc;
            --text-dim: #8b949e;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            overflow-x: hidden;
            padding: 20px;
        }

        .container {
            background: var(--card-bg);
            border: 1px solid rgba(138, 43, 226, 0.4);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border-radius: 24px;
            padding: 40px 30px;
            max-width: 420px;
            width: 100%;
            text-align: center;
            box-shadow: 0 0 40px rgba(138, 43, 226, 0.25);
            animation: fadeIn 0.6s cubic-bezier(0.16, 1, 0.3, 1);
            position: relative;
            z-index: 2;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px) scale(0.96); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }

        .logo-avatar {
            width: 85px;
            height: 85px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent), var(--accent-glow));
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            font-size: 38px;
            box-shadow: 0 0 25px var(--accent-glow);
            animation: pulse 2.5s infinite ease-in-out;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); box-shadow: 0 0 20px var(--accent-glow); }
            50% { transform: scale(1.06); box-shadow: 0 0 35px var(--accent); }
        }

        h1 {
            font-size: 34px;
            font-weight: 800;
            margin-bottom: 8px;
            background: linear-gradient(90deg, #fff, var(--accent-glow));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        p {
            color: var(--text-dim);
            font-size: 14px;
            margin-bottom: 30px;
            line-height: 1.5;
        }

        .btn {
            background: linear-gradient(135deg, var(--accent), #5c00a3);
            color: white;
            border: none;
            padding: 18px 32px;
            border-radius: 14px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            width: 100%;
            transition: all 0.2s ease;
            box-shadow: 0 6px 20px rgba(138, 43, 226, 0.45);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            touch-action: manipulation;
        }

        .btn:active {
            transform: scale(0.95);
            box-shadow: 0 2px 10px rgba(138, 43, 226, 0.3);
        }

        .status {
            margin-top: 25px;
            font-size: 13px;
            color: #00ff88;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            font-weight: 600;
        }

        .status-dot {
            width: 9px;
            height: 9px;
            background-color: #00ff88;
            border-radius: 50%;
            box-shadow: 0 0 10px #00ff88;
        }

        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.75);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.3s ease;
            z-index: 10;
            padding: 20px;
        }

        .modal.active {
            opacity: 1;
            pointer-events: auto;
        }

        .modal-content {
            background: #161b22;
            border: 1px solid var(--accent-glow);
            padding: 25px;
            border-radius: 18px;
            max-width: 320px;
            width: 100%;
            text-align: center;
            box-shadow: 0 0 30px rgba(0, 210, 255, 0.3);
            transform: scale(0.8);
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .modal.active .modal-content {
            transform: scale(1);
        }

        .modal h3 {
            margin-bottom: 10px;
            color: #fff;
        }

        .modal p {
            margin-bottom: 20px;
            font-size: 13px;
        }

        .modal-btn {
            background: var(--accent-glow);
            color: #000;
            font-weight: 700;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            width: 100%;
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="logo-avatar">
            <i class="fa-solid fa-bolt"></i>
        </div>
        <h1>Vexora v2</h1>
        <p>Интерфейс инициализирован и готов к работе.</p>

        <button class="btn" id="launchBtn">
            <i class="fa-solid fa-play"></i> Запустить интерфейс
        </button>

        <div class="status">
            <span class="status-dot"></span> Система активна
        </div>
    </div>

    <div class="modal" id="customModal">
        <div class="modal-content">
            <h3><i class="fa-solid fa-circle-check" style="color: #00ff88;"></i> Успешно!</h3>
            <p>Модуль Vexora v2 успешно запущен.</p>
            <button class="modal-btn" onclick="closeModal()">Закрыть</button>
        </div>
    </div>

    <script>
        let audioCtx = null;

        function playSound() {
            try {
                if (!audioCtx) {
                    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
                }
                if (audioCtx.state === 'suspended') {
                    audioCtx.resume();
                }

                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();

                osc.type = 'sine';
                osc.frequency.setValueAtTime(523.25, audioCtx.currentTime);
                osc.frequency.exponentialRampToValueAtTime(880, audioCtx.currentTime + 0.15);

                gain.gain.setValueAtTime(0.15, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.15);

                osc.connect(gain);
                gain.connect(audioCtx.destination);

                osc.start();
                osc.stop(audioCtx.currentTime + 0.15);
            } catch (e) {
                console.log("Audio API Error: ", e);
            }
        }

        document.getElementById('launchBtn').addEventListener('click', function() {
            playSound();
            document.getElementById('customModal').classList.add('active');
        });

        function closeModal() {
            document.getElementById('customModal').classList.remove('active');
        }
    </script>

</body>
</html>

