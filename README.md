<!DOCTYPE html>
<html lang="ar">

<head>
    <meta charset="UTF-8">
    <title>العد التنازلي للأمتحان الوزاري</title>
    <style>
        body {
            text-align: center;
            font-family: 'Traditional Arabic', serif;
            background: #1a1a1a;
            color: white;
            margin-top: 20%;
            overflow: hidden;
        }

        /* مستطيل عدد الزوار */
        #visitors-box {
            position: absolute;
            top: 20px;
            left: 20px;
            border: 3px solid white;
            padding: 15px;
            border-radius: 15px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
            font-size: 1.5rem;
            background-color: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        #countdown-container {
            border: 3px solid white;
            padding: 20px;
            display: inline-block;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.5);
        }

        #countdown {
            font-size: 3rem;
            position: relative;
            z-index: 2;
        }

        /* تنسيق المربعات */
        .box {
            border: 3px solid white;
            padding: 20px;
            margin: 10px;
            display: inline-block;
            border-radius: 15px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
            font-size: 2rem;
            width: 250px;
            background-color: rgba(255, 255, 255, 0.1);
        }

        #days-left, #hours-left {
            font-size: 2rem;
        }

        /* تأثير السقوط البطيء للستيكر 💯 */
        .sticker {
            position: fixed;
            top: -10px;
            left: 0;
            color: white;
            font-size: 2rem;
            user-select: none;
            animation: fall linear infinite;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh);
            }
        }
    </style>
</head>

<body>
    <!-- مستطيل عدد الزوار -->
    <div id="visitors-box">
        <img src="https://drive.google.com/uc?export=view&id=1pvJS3yrTtXNgonkINQ7O1XBA-GdhU7Iw" width="40">
        <span id="visitor-count">0</span>
    </div>

    <h1>عدد الأيام المتبقية للأمتحان الوزاري</h1>

    <!-- المربعات لعرض الأيام والساعات المتبقية -->
    <div id="days-left" class="box">عدد الأيام المتبقية: 0</div>
    <div id="hours-left" class="box">عدد الساعات المتبقية: 0</div>

    <div id="countdown-container">
        <div id="countdown"></div>
    </div>

    <script>
        function countdown() {
            const targetDate = new Date('2025-06-14T00:00:00').getTime();

            setInterval(() => {
                const now = new Date().getTime();
                const timeLeft = targetDate - now;

                if (timeLeft <= 0) {
                    document.getElementById('countdown').innerText = 'انتهى العد التنازلي!';
                    document.getElementById('days-left').innerText = 'عدد الأيام المتبقية: 0';
                    document.getElementById('hours-left').innerText = 'عدد الساعات المتبقية: 0';
                    return;
                }

                const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
                const totalHours = Math.floor(timeLeft / (1000 * 60 * 60));
                const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

                document.getElementById('days-left').innerText = `عدد الأيام المتبقية: ${days}`;
                document.getElementById('hours-left').innerText = `عدد الساعات المتبقية: ${totalHours}`;

                document.getElementById('countdown').innerHTML = `${days} : ${totalHours} : ${minutes} : ${seconds}`;
            }, 1000);
        }

        function createSticker() {
            const sticker = document.createElement('div');
            sticker.className = 'sticker';
            sticker.innerHTML = '💯';
            document.body.appendChild(sticker);

            sticker.style.left = Math.random() * window.innerWidth + 'px';
            sticker.style.animationDuration = (Math.random() * 10 + 10) + 's';

            setTimeout(() => sticker.remove(), 15000);
        }

        function updateVisitorCount() {
            let count = localStorage.getItem('visitorCount') || 0;
            count = parseInt(count) + 1;
            localStorage.setItem('visitorCount', count);
            document.getElementById('visitor-count').innerText = count;
        }

        updateVisitorCount();

        countdown();
        setInterval(createSticker, 5000);
    </script>
</body>

</html>

ing countdown.html…]()
