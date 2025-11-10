<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <!-- 基础适配 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
    <title>粉色生日信</title>

    <style>
        /* 0. 根字号自动适配 */
        html { font-size: calc(100vw / 37.5); }
        @media (min-width: 768px) { html { font-size: 16px; } }

        /* 1. 粉色渐变背景 + 花朵蛋糕点缀 */
        body {
            margin: 0;
            min-height: 100vh;
            background:
                linear-gradient(135deg, #fff0f8 0%, #ffd1dc 50%, #ffc0cb 100%),
                url('data:image/svg+xml;utf8,\
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200" opacity=".15">\
                <g fill="%23ff69b4">\
                <path d="M50 30a20 20 0 0 1 40 0h-40z"/><circle cx="70" cy="20" r="8"/>\
                <circle cx="30" cy="70" r="6"/><circle cx="170" cy="50" r="7"/>\
                <path d="M160 120a15 15 0 0 1 30 0h-30z"/><circle cx="180" cy="110" r="6"/>\
                </g></svg>');
            background-size: 200px 200px;
            font-family: "PingFang SC", "Microsoft YaHei", sans-serif;
            display: flex; justify-content: center; align-items: center;
        }

        /* 2. 通用卡片 */
        .card {
            width: 90%; max-width: 600px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 1.5rem;
            box-shadow: 0 1rem 3rem rgba(0, 0, 0, 0.1);
            padding: 2.5rem 2rem;
            text-align: center;
            backdrop-filter: blur(8px);
        }

        /* 3. 标题 */
        .title {
            font-size: 3rem;
            background: linear-gradient(45deg, #ff69b4, #ffc0cb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 1.5rem;
        }

        /* 4. 幻灯片容器 */
        .slideshow-container { display: none; }
        .slide {
            display: none;
            animation: slideIn 0.5s ease-in-out;
        }
        .slide.active { display: block; }
        @keyframes slideIn {
            from { opacity: 0; transform: translateX(100%); }
            to { opacity: 1; transform: translateX(0); }
        }

        /* 5. 照片统一 600×400 + 文案 */
        .photo-box {
            width: 100%; max-width: 600px; aspect-ratio: 3 / 2;
            margin: 1rem auto; border-radius: 1rem; overflow: hidden;
            box-shadow: 0 0.8rem 2rem rgba(0, 0, 0, 0.15);
        }
        .photo-box img { width: 100%; height: 100%; object-fit: cover; }
        .caption {
            font-size: 1.1rem; color: #555; margin: 0.8rem 0 2rem;
        }

        /* 6. 按钮 */
        .btn {
            display: inline-block; padding: 0.8rem 2.2rem;
            background: linear-gradient(45deg, #ff69b4, #ffc0cb);
            color: #fff; border: none; border-radius: 2rem;
            font-size: 1.2rem; cursor: pointer;
            box-shadow: 0 0.4rem 1.2rem rgba(255, 105, 180, 0.4);
            transition: 0.3s;
        }
        .btn:hover { transform: translateY(-0.2rem); box-shadow: 0 0.6rem 1.6rem rgba(255, 105, 180, 0.5); }

        /* 7. 信页 */
        .letter-page { display: none; text-align: left; }
        .letter-content { font-size: 1.1rem; line-height: 1.8; color: #333; }
        .letter-content h3 { color: #ff69b4; margin-bottom: 1rem; text-align: center; }

        /* 8. 音频控制面板 */
        .audio-controls { position: fixed; bottom: 1rem; right: 1rem; background: rgba(255, 255, 255, 0.85); padding: 0.6rem 1rem; border-radius: 1rem; box-shadow: 0 0.3rem 1rem rgba(0, 0, 0, 0.15); z-index: 1000; }
        .audio-btn { margin: 0.2rem; padding: 0.4rem 0.8rem; background: #ff69b4; color: #fff; border: none; border-radius: 1rem; font-size: 0.9rem; cursor: pointer; }
        .audio-btn:hover { background: #ff1493; }
    </style>
</head>

<body>
    <!-- ========== 0. 音频元素 ========== -->
    <audio id="bgMusic1" loop><source src="song1.mp3" type="audio/mpeg"></audio>
    <audio id="bgMusic2" loop><source src="song2.mp3" type="audio/mpeg"></audio>
    <audio id="bgMusic3" loop><source src="song3.mp3" type="audio/mpeg"></audio>

    <!-- ========== 1. 首页 ========== -->
    <div class="card" id="homePage">
        <h1 class="title">🎂 Happy Birthday 🌸</h1>
        <p style="color:#666;">愿你被鲜花与甜蜜团团围住～</p >
        <button class="btn" onclick="startSlide()">开启回忆</button>
    </div>

    <!-- ========== 2. 幻灯片 ========== -->
    <div class="slideshow-container card" id="slideShow" style="display:none;">
        <!-- 幻灯片1 -->
        <div class="slide active">
            <div class="photo-box">< img src="R1.jpg" alt=""></div>
            <p class="caption">R1- Studying is certainly important, but don't forget to pause and relax once in a while.</p >
        </div>
        <!-- 幻灯片2 -->
        <div class="slide">
            <div class="photo-box">< img src="R2.jpg" alt=""></div>
            <p class="caption">R2- I hope you can always maintain a positive and optimistic attitude.</p >
        </div>
        <!-- 幻灯片3 -->
        <div class="slide">
            <div class="photo-box">< img src="R3.jpg" alt=""></div>
            <p class="caption">R3- As I always say, no matter what happens, I will stand by your side and be your most loyal supporter.</p >
        </div>
        <!-- 幻灯片4 -->
        <div class="slide">
            <div class="photo-box">< img src="R4.jpg" alt=""></div>
            <p class="caption">R4- Thank you for shining on everyone around you like a little sun.</p >
        </div>
        <!-- 幻灯片5 -->
        <div class="slide">
            <div class="photo-box">< img src="R5.jpg" alt=""></div>
            <p class="caption">R5- No matter what happens, we will stand by your side.</p >
        </div>

        <!-- 幻灯片导航 -->
        <div style="margin-top:1.5rem;">
            <button class="btn" onclick="changeSlide(-1)">⬅ 上一张</button>
            <button class="btn" onclick="changeSlide(1)">下一张 ➡</button>
            <button class="btn" onclick="showLetter()">💌 读信</button>
    </div>   <!-- 幻灯片导航结束 -->
    </div>       <!-- 幻灯片容器结束 -->

    <!-- ========== 3. 生日信 ========== -->
    <div class="letter-page card" id="letterPage" style="display:none;">
        <h3>🌸 To My Dearest You 🌸</h3>
        <div class="letter-content">
            <p>Meeting you is truly the luckiest thing I’ve ever felt. Today, I want to take this chance to tell you a few things tucked deep in my heart. To me, you are an extraordinary person—bright, sunny, lovely, and beautiful. Please stop thinking that you're “not enough,” and stop sighing at yourself day after day.</p >

            <p>I hope the days ahead keep you shining in your own unique way: doing what you love, loving those who deserve you. May every furrow of your brow come only from wondering how to embrace the world more warmly; may every tear you shed be born of happiness too big to hold inside. However far the future stretches, I wish you to be met with gentleness—and to learn to cradle yourself just as gently. Remember: you deserve every beauty this life can offer, and you deserve to be chosen—firmly, unshakably.</p >

            <p>Finally, happy birthday. In this new year of your life, we’re still right here beside you.</p >

            <p style="text-align:right;">— Your Loyal Friend 💕</p >
        </div>
        <button class="btn" onclick="backToSlide()" style="margin-top:1.5rem;">返回相册</button>
    </div>

    <!-- ========== 4. 音频控制 ========== -->
    <div class="audio-controls">
        <div>🎵 BGM</div>
        <button class="audio-btn" onclick="playMusic(1)">song1</button>
        <button class="audio-btn" onclick="playMusic(2)">song2</button>
        <button class="audio-btn" onclick="playMusic(3)">song3</button>
        <button class="audio-btn" onclick="stopMusic()">🔇</button>
    </div>

    <!-- ========== 5. 脚本 ========== -->
    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        let currentMusic = null;

        /* 初始播放 */
        window.onload = () => playMusic(1);

        /* 幻灯片流程 */
        function startSlide() {
            document.getElementById('homePage').style.display = 'none';
            document.getElementById('slideShow').style.display = 'block';
        }
        function changeSlide(dir) {
            slides[currentSlide].classList.remove('active');
            currentSlide = (currentSlide + dir + slides.length) % slides.length;
            slides[currentSlide].classList.add('active');
        }
        function showLetter() {
            document.getElementById('slideShow').style.display = 'none';
            document.getElementById('letterPage').style.display = 'block';
        }
        function backToSlide() {
            document.getElementById('letterPage').style.display = 'none';
            document.getElementById('slideShow').style.display = 'block';
        }

        /* 音乐控制 */
        function playMusic(n) {
            if (currentMusic) { currentMusic.pause(); currentMusic.currentTime = 0; }
            currentMusic = document.getElementById('bgMusic' + n);
            if (currentMusic) currentMusic.play().catch(() => {});
        }
        function stopMusic() {
            if (currentMusic) { currentMusic.pause(); currentMusic.currentTime = 0; currentMusic = null; }
        }

        /* 键盘/触摸换页 */
        document.addEventListener('keydown', e => {
            if (document.getElementById('slideShow').style.display === 'block') {
                if (e.key === 'ArrowLeft') changeSlide(-1);
                if (e.key === 'ArrowRight') changeSlide(1);
                if (e.key === 'Enter') showLetter();
            }
        });
        let tx = 0;
        document.addEventListener('touchstart', e => tx = e.changedTouches[0].screenX);
        document.addEventListener('touchend', e => {
            let ty = e.changedTouches[0].screenX;
            if (ty < tx - 50) changeSlide(1);
            if (ty > tx + 50) changeSlide(-1);
        });
    </script>
</body>
</html>
