<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <!-- 手机/电脑自适应 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
    <title>HAPPY BIRTHDAY RILEY</title>

    <style>
        /* 0. 根字号自适应：375px=10px，电脑锁16px */
        html { font-size: calc(100vw / 37.5); }
        @media (min-width: 768px) { html { font-size: 16px; } }

        /* 1. 粉色渐变背景 + 花朵蛋糕 SVG 点缀 */
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

        /* 2. 卡片容器 */
        .card {
            width: 90%; max-width: 40rem;
            background: rgba(255, 255, 255, .85);
            border-radius: 2rem;
            box-shadow: 0 1rem 3rem rgba(0, 0, 0, .1);
            padding: 3rem 2rem;
            text-align: center;
            backdrop-filter: blur(10px);
        }

        /* 3. 标题 */
        .title {
            font-size: 3.6rem;
            background: linear-gradient(45deg, #ff69b4, #ffc0cb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 2rem;
            letter-spacing: .2rem;
        }

        /* 4. 照片区 600×400 固定框 + 文案 */
        .photo-box {
            width: 600px; height: 400px;
            margin: 2rem auto;
            border-radius: 1.5rem;
            overflow: hidden;
            box-shadow: 0 .8rem 2rem rgba(0, 0, 0, .15);
        }
        .photo-box img { width: 100%; height: 100%; object-fit: cover; }

        .caption {
            font-size: 1.2rem; color: #666;
            margin: 1rem 0 2rem;
            line-height: 1.6;
        }

        /* 5. 按钮 */
        .btn {
            display: inline-block;
            padding: 1rem 3rem;
            background: linear-gradient(45deg, #ff69b4, #ffc0cb);
            color: #fff; border: none;
            border-radius: 3rem; font-size: 1.4rem;
            cursor: pointer;
            box-shadow: 0 .4rem 1.2rem rgba(255, 105, 180, .4);
            transition: .3s;
        }
        .btn:hover { transform: translateY(-.2rem); box-shadow: 0 .6rem 1.6rem rgba(255, 105, 180, .5); }

        /* 6. 响应式：手机缩小 */
        @media (max-width: 620px) {
            .photo-box { width: 100%; height: auto; aspect-ratio: 3 / 2; }
            .title { font-size: 2.8rem; }
        }

        /* 7. 祝福信页 */
        .letter-page {
            display: none;
            text-align: left; font-size: 1.1rem; line-height: 1.8;
            color: #333; margin-top: 2rem;
        }
        .letter-page h3 { color: #ff69b4; margin-bottom: 1rem; }

        /* 8. 音乐控制条 */
        .audio-bar {
            position: fixed; bottom: 1rem; right: 1rem;
            background: rgba(255, 255, 255, .9);
            border-radius: 1rem; padding: .8rem 1.2rem;
            box-shadow: 0 .4rem 1.2rem rgba(0, 0, 0, .15);
            display: flex; gap: .6rem;
        }
        .audio-bar button {
            border: none; border-radius: .6rem;
            padding: .4rem .8rem; background: #ff69b4; color: #fff;
            cursor: pointer; font-size: 1rem;
        }
    </style>
</head>

<body>
    <div class="card">
        <h1 class="title">🌸 Happy Birthday 🎂</h1>

        <!-- ====== 5 张照片 + 文案 ====== -->
        <div class="photo-box">< img src="R1.jpg" alt=""></div>
        <p class="caption">R1 - Studying is certainly important, but don't forget to pause and relax once in a while.</p >

        <div class="photo-box">< img src="R2.jpg" alt=""></div>
        <p class="caption">R2 - I hope you can always maintain a positive and optimistic attitude.</p >

        <div class="photo-box">< img src="R3.jpg" alt=""></div>
        <p class="caption">R3 - As I always say, no matter what happens, I will stand by your side and be your most loyal supporter.</p >

        <div class="photo-box">< img src="R4.jpg" alt=""></div>
        <p class="caption">R4 - Thank you for shining on everyone around you like a little sun.</p >

        <div class="photo-box">< img src="R5.jpg" alt=""></div>
        <p class="caption">R5 - No matter what happens, we will stand by your side.</p >

        <!-- 按钮：展开祝福信 -->
        <button class="btn" onclick="toggleLetter()">💌 Read My Letter</button>

        <!-- 祝福信 -->
        <div class="letter-page" id="letterPage">
            <h3>To My Dearest You</h3>
            <p>Meeting you is truly the luckiest thing I’ve ever felt. Today, I want to take this chance to tell you a few things tucked deep in my heart. To me, you are an extraordinary person—bright, sunny, lovely, and beautiful. Please stop thinking that you're "not enough," and stop sighing at yourself day after day.</p >
            <p>I hope the days ahead keep you shining in your own unique way: doing what you love, loving those who deserve you. May every furrow of your brow come only from wondering how to embrace the world more warmly; may every tear you shed be born of happiness too big to hold inside. However far the future stretches, I wish you to be met with gentleness—and to learn to cradle yourself just as gently. Remember: you deserve every beauty this life can offer, and you deserve to be chosen—firmly, unshakably.</p >
            <p>Finally, happy birthday. In this new year of your life, we’re still right here beside you.</p >
            <p style="text-align:right;">— Your Friend</p >
        </div>
    </div>

    <!-- ====== 音乐控制 ====== -->
    <div class="audio-bar">
        <button onclick="playMusic(1)">🎵 1</button>
        <button onclick="playMusic(2)">🎵 2</button>
        <button onclick="playMusic(3)">🎵 3</button>
        <button onclick="stopMusic()">🔇</button>
    </div>

    <!-- 音频文件 -->
    <audio id="bgMusic1" loop><source src="song1.mp3" type="audio/mpeg"></audio>
    <audio id="bgMusic2" loop><source src="song2.mp3" type="audio/mpeg"></audio>
    <audio id="bgMusic3" loop><source src="song3.mp3" type="audio/mpeg"></audio>

    <script>
        let currentMusic = null;
        function playMusic(n) {
            if (currentMusic) { currentMusic.pause(); currentMusic.currentTime = 0; }
            currentMusic = document.getElementById('bgMusic' + n);
            if (currentMusic) currentMusic.play().catch(() => {});
        }
        function stopMusic() {
            if (currentMusic) { currentMusic.pause(); currentMusic.currentTime = 0; currentMusic = null; }
        }
        function toggleLetter() {
            const box = document.getElementById('letterPage');
            box.style.display = box.style.display === 'block' ? 'none' : 'block';
        }
        // 默认播放第一首
        window.onload = () => playMusic(1);
    </script>
</body>
</html>
