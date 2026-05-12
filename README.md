<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مفاجأة عيد الميلاد</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
            color: #fff;
        }

        /* تنسيق صندوق تسجيل الدخول */
        #login-screen {
            background: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            text-align: center;
            color: #333;
            z-index: 10;
            width: 300px;
        }

        #login-screen h2 { color: #ff4d6d; margin-bottom: 20px; }

        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 8px;
            text-align: center;
            outline: none;
        }

        button {
            background: #ff4d6d;
            color: white;
            border: none;
            padding: 10px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: 0.3s;
        }

        button:hover { background: #ff758c; }

        /* تنسيق محتوى المفاجأة (مخفي في البداية) */
        #surprise-content {
            display: none; /* مخفي */
            text-align: center;
            background: rgba(255, 255, 255, 0.2);
            padding: 40px;
            border-radius: 20px;
            backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            z-index: 1;
            max-width: 90%;
            animation: fadeIn 1s ease-in;
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .photo-box {
            width: 180px; height: 180px;
            border: 5px solid white;
            border-radius: 15px;
            display: inline-block;
            margin: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .photo-box img { width: 100%; height: 100%; object-fit: cover; }

        .heart {
            position: fixed; top: -10vh; font-size: 20px;
            z-index: 0; animation: fall linear forwards;
        }

        @keyframes fall { to { transform: translateY(110vh) translateX(20px); } }
    </style>
</head>
<body>

    <!-- شاشة تسجيل الدخول -->
    <div id="login-screen">
        <h2>سجلي دخولك لرؤية المفاجأة ✨</h2>
        <input type="text" id="username" placeholder="اسم المستخدم">
        <input type="password" id="password" placeholder="كلمة المرور">
        <br>
        <button onclick="checkLogin()">دخول</button>
        <p id="error-msg" style="color: red; font-size: 0.8rem; margin-top: 10px; display: none;">البيانات غير صحيحة، حاولي مرة أخرى!</p>
    </div>

    <!-- محتوى الصفحة الرئيسي (القلوب والصور) -->
    <div id="surprise-content">
        <h1>عيد ميلاد سعيد يا أغلى أخت! 🎂</h1>
        <h2 style="font-size: 4rem; color: #ff4d6d; margin: 0;">21</h2>
        <p>كل سنة وأنتِ منورة حياتنا وعقبال سنين كتير في نجاح وسعادة  ويارب دايما  يوفقك  واشوفك ناجحة دايما ويخليكي  لينا يارب  ❤️❤️❤️.</p>
        
        <div class="photos-container">
            <div class="photo-box"><img src="photo1.jpg" alt="صورة 1"></div>
            <div class="photo-box"><img src="photo2.jpg" alt="صورة 2"></div>
        </div>
        <p>كبرتِ وبقيتِ أحلى عروسة! ❤️✨</p>
    </div>

    <script>
        function checkLogin() {
            const user = document.getElementById('username').value;
            const pass = document.getElementById('password').value;
            const errorMsg = document.getElementById('error-msg');

            // التحقق من البيانات (الاسم: Mustafa، الباسورد: 21)
            if (user === "EL_Zoz" && pass === "21") {
                document.getElementById('login-screen').style.display = 'none';
                document.getElementById('surprise-content').style.display = 'block';
                startHearts();
            } else {
                errorMsg.style.display = 'block';
            }
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 2 + 's';
            heart.style.opacity = Math.random();
            document.body.appendChild(heart);
            setTimeout(() => { heart.remove(); }, 5000);
        }

        function startHearts() {
            setInterval(createHeart, 300);
        }
    </script>
</body>
</html>
