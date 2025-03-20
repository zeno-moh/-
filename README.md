[Upload<!DOCTYPE html>
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

        .snowflake {
            position: fixed;
            top: -10px;
            color: white;
            font-size: 1rem;
            user-select: none;
            animation: fall linear infinite;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh);
            }
        }

        .time-unit {
            display: inline-block;
            margin: 0 10px;
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
    </style>
</head>

<body>
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
                const totalHours = Math.floor(timeLeft / (1000 * 60 * 60)); // عدد الساعات المتبقية من الآن حتى التاريخ المحدد
                const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

                // عرض عدد الأيام المتبقية في المربع العلوي
                document.getElementById('days-left').innerText = `عدد الأيام المتبقية: ${days}`;

                // عرض عدد الساعات المتبقية في المربع الثاني
                document.getElementById('hours-left').innerText = `عدد الساعات المتبقية: ${totalHours}`;

                // تنسيق العد التنازلي باستخدام ":" بين الأرقام
                document.getElementById('countdown').innerHTML = 
                    `${days} : ${totalHours} : ${minutes} : ${seconds}`;
            }, 1000);
        }

        function createSnow() {
            const snowflake = document.createElement('div');
            snowflake.className = 'snowflake';
            snowflake.innerHTML = '❄';
            document.body.appendChild(snowflake);

            snowflake.style.left = Math.random() * window.innerWidth + 'px';
            snowflake.style.animationDuration = (Math.random() * 5 + 5) + 's';
            snowflake.style.fontSize = (Math.random() * 1.5 + 0.5) + 'rem';

            setTimeout(() => snowflake.remove(), 10000);
        }

        setInterval(createSnow, 200);

        countdown();
    </script>
</body>

</html>
ing countdown.html…]()
