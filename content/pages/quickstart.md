<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Hello Kitty</title>
    <!-- خط آيفون الشهير من جوجل -->
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Cairo", sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: #ffe6f2;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            width: 100vw;
            position: relative;
        }

        /* تأثير القلوب المتحركة في الخلفية */
        .hearts-bg {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            top: 0;
            left: 0;
            z-index: 1;
            pointer-events: none;
        }

        .heart {
            position: absolute;
            display: block;
            width: 20px;
            height: 20px;
            background: #ff66b2;
            transform: rotate(-45deg);
            opacity: 0.6;
            animation: floatUp 6s linear infinite;
            bottom: -50px;
        }

        .heart:before, .heart:after {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            background: #ff66b2;
            border-radius: 50%;
        }

        .heart:before { top: -10px; left: 0; }
        .heart:after { top: 0; left: 10px; }

        @keyframes floatUp {
            0% { transform: translateY(0) rotate(-45deg); opacity: 0; }
            10% { opacity: 0.6; }
            90% { opacity: 0.6; }
            100% { transform: translateY(-105vh) rotate(-45deg); opacity: 0; }
        }

        /* واجهة شاشة الآيفون */
        .iphone-container {
            width: 100%;
            max-width: 414px;
            height: 100vh;
            background: rgba(255, 230, 242, 0.4);
            backdrop-filter: blur(5px);
            z-index: 2;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 40px 20px 30px 20px;
            position: relative;
        }

        /* منطقة المحادثة والشخصية */
        .chat-area {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            margin-bottom: 20px;
        }

        .kitty-avatar {
            width: 140px;
            height: 140px;
            background-image: url('https://i.pinimg.com/originals/a0/0b/a0/a00ba02538cb123e4726e6f47738bc86.png'); /* رابط مباشر لصورة هيلو كيتي */
            background-size: contain;
            background-repeat: no-repeat;
            background-position: center;
            margin-bottom: 25px;
            transition: transform 0.3s ease;
        }

        .kitty-avatar.angry {
            animation: shake 0.5s ease-in-out;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-10px); }
            40%, 80% { transform: translateX(10px); }
        }

        .bubble {
            background: white;
            padding: 18px 24px;
            border-radius: 25px;
            border-bottom-right-radius: 5px;
            box-shadow: 0 4px 15px rgba(255, 102, 178, 0.15);
            color: #333;
            font-size: 1.15rem;
            font-weight: 600;
            max-width: 85%;
            line-height: 1.6;
            position: relative;
            animation: popIn 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes popIn {
            0% { transform: scale(0.7); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        /* نظام أزرار الآيفون */
        .options-area {
            display: flex;
            flex-direction: column;
            gap: 12px;
            width: 100%;
            padding-bottom: 10px;
        }

        .ios-btn {
            background: #ff66b2;
            color: white;
            border: none;
            padding: 16px;
            border-radius: 16px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(255, 102, 178, 0.3);
            transition: all 0.2s ease;
            text-align: center;
            width: 100%;
            animation: slideUp 0.5s ease;
        }

        .ios-btn:active {
            transform: scale(0.97);
            background: #e64d99;
        }

        @keyframes slideUp {
            0% { transform: translateY(20px); opacity: 0; }
            100% { transform: translateY(0); opacity: 1; }
        }

        /* زر القلب النابض */
        .big-heart-btn {
            background: none;
            border: none;
            font-size: 80px;
            cursor: pointer;
            animation: pulse 1.2s infinite;
            display: block;
            margin: 0 auto;
            outline: none;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        /* مشغل الموسيقى الفخم */
        .music-player {
            background: rgba(255, 255, 255, 0.9);
            border: 2px solid #ff99cc;
            border-radius: 20px;
            padding: 20px;
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
            box-shadow: 0 8px 20px rgba(255, 102, 178, 0.2);
            animation: popIn 0.5s ease;
        }

        .player-info {
            font-weight: 700;
            color: #ff3399;
            font-size: 1rem;
        }

        .play-bar {
            width: 100%;
            height: 6px;
            background: #ffe6f2;
            border-radius: 3px;
            position: relative;
            overflow: hidden;
        }

        .play-progress {
            width: 40%;
            height: 100%;
            background: #ff66b2;
            border-radius: 3px;
            animation: progressSim 20s linear infinite;
        }

        @keyframes progressSim {
            0% { width: 0%; }
            100% { width: 100%; }
        }
    </style>
</head>
<body>

    <!-- الخلفية المترعة بالقلوب الطايرة -->
    <div class="hearts-bg" id="heartsBg"></div>

    <div class="iphone-container">
        
        <div class="chat-area">
            <!-- صورة هيلو كيتي -->
            <div class="kitty-avatar" id="kittyAvatar"></div>
            <!-- صندوق حوار هيلو كيتي -->
            <div class="bubble" id="chatBubble">هلو اسراء تعالي احجي وياج موضوع</div>
        </div>

        <!-- الأزرار التفاعلية لإسراء -->
        <div class="options-area" id="optionsArea">
            <button class="ios-btn" onclick="nextStep(1)">شنو</button>
        </div>

    </div>

    <!-- تضمين صوت الأغنية (ميادة الحناوي - كان يا ما كان) -->
    <audio id="bgMusic" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
        <!-- ملاحظة: يمكنك استبدال الرابط الفوق برابط مباشر لأغنية ميادة mp3 لتعمل فوراً -->
    </audio>

    <script>
        // توليد القلوب العشوائية بالخلفية
        const heartsBg = document.getElementById('heartsBg');
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 4 + 's';
            heart.style.width = heart.style.height = Math.random() * 15 + 15 + 'px';
            heartsBg.appendChild(heart);
            setTimeout(() => { heart.remove(); }, 6000);
        }
        setInterval(createHeart, 400);

        // إدارة خطوات السيناريو التفاعلي
        const bubble = document.getElementById('chatBubble');
        const optionsArea = document.getElementById('optionsArea');
        const avatar = document.getElementById('kittyAvatar');
        const audio = document.getElementById('bgMusic');

        function nextStep(step) {
            optionsArea.innerHTML = ''; // تفريغ الأزرار القديمة

            if (step === 1) {
                bubble.innerText = "اكو شخص يحبچ ويموت عليچ تعرفينه";
                optionsArea.innerHTML = `
                    <button class="ios-btn" onclick="nextStep(2)">لا ماكو</button>
                    <button class="ios-btn" onclick="nextStep(2)">منو</button>
                `;
            } 
            else if (step === 2) {
                avatar.classList.add('angry'); // تأثير العصبية لهيلو كيتي
                bubble.innerText = "هيييي تعرفينه كلش زين علي تحبينه لو لا";
                setTimeout(() => { avatar.classList.remove('angry'); }, 500);
                
                optionsArea.innerHTML = `
                    <button class="ios-btn" onclick="nextStep(3)">مدري</button>
                `;
            } 
            else if (step === 3) {
                bubble.innerText = "اذا تحبين علي اضغطي";
                optionsArea.innerHTML = `
                    <button class="big-heart-btn" onclick="nextStep(4)">❤️</button>
                `;
            } 
            else if (step === 4) {
                bubble.innerText = "رسالة من علي :\nاسراء احبچ واموت عليچ شوكت نتزوج ونجيب طفله حلوه تشبهچ الله يحفظچ الي للابد";
                optionsArea.innerHTML = `
                    <button class="ios-btn" style="background:#ff3399;" onclick="playMusic()">اسمعي هاي الاغنيه من علي</button>
                `;
            }
        }

        // تشغيل الموسيقى وعرض مشغل كيتي الفخم بآخر خطوة
        function playMusic() {
            audio.play().catch(e => console.log("تحتاج تفاعل لتشغيل الصوت"));
            
            optionsArea.innerHTML = `
                <div class="music-player">
                    <div class="player-info">🎵 ميادة الحناوي - كان يا ما كان (هدية من علي) 🎵</div>
                    <div class="play-bar">
                        <div class="play-progress"></div>
                    </div>
                    <div style="font-size: 30px; animation: pulse 1s infinite;">🐱💝✨</div>
                </div>
            `;
        }
    </script>
</body>
</html>
