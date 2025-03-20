<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عداد الزوار و العداد التنازلي</title>
    <style>
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
        <div>عدد الزوار: <span id="visitor-count">0</span></div>
    </div>

    <!-- العداد التنازلي -->
    <div id="countdown-container">
        <div id="countdown">
            <span id="days-left">0</span> أيام
            <span id="hours-left">0</span> ساعات
        </div>
    </div>

    <!-- ستيكر السقوط 💯 -->
    <div class="sticker">
        💯
    </div>

    <script>
        // مثال لتحديث عدد الزوار
        let visitorCount = 0;
        function updateVisitorCount() {
            visitorCount++;
            document.getElementById('visitor-count').innerText = visitorCount;
        }
        setInterval(updateVisitorCount, 5000); // تحديث عدد الزوار كل 5 ثواني

        // مثال لعداد تنازلي
        const countdownDate = new Date("March 31, 2025 00:00:00").getTime();
        let countdownTimer = setInterval(function() {
            let now = new Date().getTime();
            let distance = countdownDate - now;

            let days = Math.floor(distance / (1000 * 60 * 60 * 24));
            let hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));

            document.getElementById('days-left').innerText = days;
            document.getElementById('hours-left').innerText = hours;

            if (distance < 0) {
                clearInterval(countdownTimer);
                document.getElementById('countdown').innerText = "انتهى الوقت!";
            }
        }, 1000);
    </script>
</body>
</html>
