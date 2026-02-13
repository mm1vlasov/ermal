<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💕 Будь моей валентинкой 💕</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Caveat:wght@700&family=Pacifico&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Pacifico', cursive;
            background: linear-gradient(135deg, #FFE5EC 0%, #FFC4D6 50%, #FFB3C9 100%);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }
        
        /* Плавающие эмодзи */
        .floating-emoji {
            position: absolute;
            font-size: 40px;
            animation: float 6s ease-in-out infinite;
            opacity: 0.8;
            z-index: 1;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            25% { transform: translateY(-20px) rotate(5deg); }
            50% { transform: translateY(-10px) rotate(-5deg); }
            75% { transform: translateY(-30px) rotate(3deg); }
        }
        
        .floating-emoji:nth-child(1) { top: 10%; left: 10%; animation-delay: 0s; }
        .floating-emoji:nth-child(2) { top: 20%; right: 15%; animation-delay: 1s; font-size: 50px; }
        .floating-emoji:nth-child(3) { top: 60%; left: 5%; animation-delay: 2s; }
        .floating-emoji:nth-child(4) { top: 70%; right: 10%; animation-delay: 3s; font-size: 45px; }
        .floating-emoji:nth-child(5) { top: 40%; left: 20%; animation-delay: 1.5s; }
        .floating-emoji:nth-child(6) { top: 30%; right: 25%; animation-delay: 2.5s; font-size: 38px; }
        .floating-emoji:nth-child(7) { top: 80%; left: 15%; animation-delay: 0.5s; }
        .floating-emoji:nth-child(8) { top: 15%; left: 50%; animation-delay: 4s; font-size: 42px; }
        
        /* Пульсирующие сердечки */
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }
        
        .floating-emoji.pulse {
            animation: pulse 2s ease-in-out infinite;
        }
        
        /* Основной контейнер */
        .container {
            position: relative;
            z-index: 10;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        /* Заголовок */
        .title {
            font-size: 48px;
            color: #FF1493;
            text-align: center;
            margin-bottom: 60px;
            text-shadow: 3px 3px 6px rgba(255, 105, 180, 0.3);
            animation: titleFloat 3s ease-in-out infinite;
            line-height: 1.4;
        }
        
        @keyframes titleFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        /* Кнопки */
        .buttons {
            display: flex;
            gap: 30px;
            margin-top: 20px;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
        }
        
        button {
            font-family: 'Pacifico', cursive;
            font-size: 28px;
            padding: 20px 50px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
            position: relative;
            flex-shrink: 0;
        }
        
        .btn-yes {
            background: linear-gradient(135deg, #FF1493, #FF69B4);
            color: white;
            transition: all 0.3s ease;
        }
        
        .btn-yes:hover {
            transform: scale(1.1);
            box-shadow: 0 12px 30px rgba(255, 20, 147, 0.4);
        }
        
        .btn-yes:active {
            transform: scale(0.95);
        }
        
        .btn-no {
            background: linear-gradient(135deg, #FFB6C1, #FFC0CB);
            color: #FF1493;
            transition: all 0.2s ease;
        }
        
        .btn-no:hover {
            background: linear-gradient(135deg, #FF69B4, #FFB6C1);
        }
        
        /* Экран успеха */
        .success-screen {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #FF1493, #FF69B4, #FFB6C1);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }
        
        .success-text {
            font-size: 42px;
            color: white;
            text-align: center;
            padding: 30px;
            text-shadow: 3px 3px 10px rgba(0, 0, 0, 0.3);
            animation: successPulse 2s ease-in-out infinite;
            line-height: 1.6;
            max-width: 90%;
        }
        
        @keyframes successPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        /* Фейерверк из сердечек */
        .heart {
            position: fixed;
            font-size: 30px;
            pointer-events: none;
            z-index: 3000;
            animation: firework 2s ease-out forwards;
        }
        
        @keyframes firework {
            0% {
                opacity: 1;
                transform: translate(0, 0) scale(0);
            }
            50% {
                opacity: 1;
                transform: translate(var(--tx), var(--ty)) scale(1);
            }
            100% {
                opacity: 0;
                transform: translate(var(--tx), calc(var(--ty) + 100px)) scale(0.5);
            }
        }
        
        /* Адаптация для мобильных */
        @media (max-width: 768px) {
            .title {
                font-size: 32px;
                margin-bottom: 40px;
            }
            
            button {
                font-size: 22px;
                padding: 15px 35px;
            }
            
            .floating-emoji {
                font-size: 30px;
            }
            
            .floating-emoji:nth-child(2),
            .floating-emoji:nth-child(4) {
                font-size: 35px;
            }
            
            .success-text {
                font-size: 28px;
                padding: 20px;
            }
            
            .buttons {
                gap: 20px;
            }
        }
        
        @media (max-width: 480px) {
            .title {
                font-size: 26px;
            }
            
            button {
                font-size: 20px;
                padding: 12px 30px;
            }
            
            .success-text {
                font-size: 22px;
            }
        }
    </style>
</head>
<body>
    <!-- Плавающие эмодзи -->
    <div class="floating-emoji pulse">💕</div>
    <div class="floating-emoji">💖</div>
    <div class="floating-emoji pulse">💗</div>
    <div class="floating-emoji">💘</div>
    <div class="floating-emoji pulse">💝</div>
    <div class="floating-emoji">🌹</div>
    <div class="floating-emoji pulse">💓</div>
    <div class="floating-emoji">✨</div>
    
    <!-- Основной контент -->
    <div class="container">
        <div class="title">
            Даша, ты будешь<br>моей валентинкой? 💕
        </div>
        
        <div class="buttons">
            <button class="btn-yes" onclick="sayYes()">Да! 💖</button>
            <button class="btn-no" id="btnNo" onclick="clickNo()">Нет</button>
        </div>
    </div>
    
    <!-- Экран успеха -->
    <div class="success-screen" id="successScreen">
        <div class="success-text">
            🎉 УРА! 🎉<br>
            Ты теперь моя валентинка!<br>
            💕<br>
            Ты моя слабость<br>
            и сила одновременно 💖
        </div>
    </div>
    
    <script>
        let yesButtonScale = 1;
        
        // Увеличение кнопки "Да" при клике на "Нет"
        function clickNo() {
            const btnYes = document.querySelector('.btn-yes');
            yesButtonScale += 0.3;
            
            // Ограничение максимального размера
            if (yesButtonScale > 4) {
                yesButtonScale = 4;
            }
            
            btnYes.style.transform = `scale(${yesButtonScale})`;
            btnYes.style.transition = 'transform 0.3s ease';
        }
        
        // Фейерверк из сердечек
        function createHeartFirework(x, y) {
            const hearts = ['💕', '💖', '💗', '💘', '💝', '💓', '💞', '💟'];
            const count = 30;
            
            for (let i = 0; i < count; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
                
                const angle = (Math.PI * 2 * i) / count;
                const distance = 150 + Math.random() * 100;
                const tx = Math.cos(angle) * distance;
                const ty = Math.sin(angle) * distance;
                
                heart.style.setProperty('--tx', tx + 'px');
                heart.style.setProperty('--ty', ty + 'px');
                heart.style.left = x + 'px';
                heart.style.top = y + 'px';
                
                document.body.appendChild(heart);
                
                setTimeout(() => heart.remove(), 2000);
            }
        }
        
        // Множественные фейерверки
        function launchFireworks() {
            const positions = [
                { x: window.innerWidth * 0.25, y: window.innerHeight * 0.3 },
                { x: window.innerWidth * 0.75, y: window.innerHeight * 0.3 },
                { x: window.innerWidth * 0.5, y: window.innerHeight * 0.5 },
                { x: window.innerWidth * 0.2, y: window.innerHeight * 0.7 },
                { x: window.innerWidth * 0.8, y: window.innerHeight * 0.7 }
            ];
            
            positions.forEach((pos, index) => {
                setTimeout(() => createHeartFirework(pos.x, pos.y), index * 300);
            });
        }
        
        // Нажатие на "Да"
        function sayYes() {
            document.getElementById('successScreen').style.display = 'flex';
            
            // Запуск фейерверков
            launchFireworks();
            
            // Повторные фейерверки
            setTimeout(launchFireworks, 1500);
            setTimeout(launchFireworks, 3000);
        }
    </script>
</body>
</html>
