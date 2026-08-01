# -tyagi-friendship
🌸 Friendship Day surprise for Tyagi
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>🌸 Friendship Day · Tyagi 🌸</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      font-family: 'Segoe UI', 'Poppins', sans-serif;
      background: #0a0e1a;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      touch-action: none;
    }

    #flowerCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    #loading {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #0a0e1a;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 99999;
      transition: opacity 0.5s ease;
    }

    #loading.hide {
      opacity: 0;
      pointer-events: none;
    }

    .loader {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      border: 3px solid transparent;
      border-top: 3px solid #fd79a8;
      border-right: 3px solid #6c5ce7;
      animation: spin 0.8s linear infinite;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .load-text {
      margin-top: 12px;
      color: rgba(255, 255, 255, 0.3);
      font-size: 0.9rem;
    }

    #slideshow {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 2;
      display: flex;
      justify-content: center;
      align-items: center;
      background: rgba(0, 0, 0, 0.7);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
    }

    .slide-content {
      max-width: 800px;
      width: 95%;
      max-height: 95vh;
      text-align: center;
      animation: fadeSlide 0.6s ease;
      padding: 10px 0;
    }

    @keyframes fadeSlide {
      0% { opacity: 0; transform: scale(0.9); }
      100% { opacity: 1; transform: scale(1); }
    }

    .slide-content .media {
      width: 100%;
      max-height: 60vh;
      object-fit: contain;
      border-radius: 25px;
      background: rgba(0, 0, 0, 0.3);
      border: 2px solid rgba(255, 255, 255, 0.05);
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
    }

    .slide-content .title {
      font-size: 1.5rem;
      font-weight: 700;
      background: linear-gradient(135deg, #fd79a8, #6c5ce7);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      margin-top: 0.6rem;
      padding: 0 10px;
    }

    .slide-content .msg {
      font-size: 0.9rem;
      color: rgba(255, 255, 255, 0.4);
      margin-top: 0.2rem;
      padding: 0 10px;
    }

    .slide-content .counter {
      font-size: 0.7rem;
      color: rgba(255, 255, 255, 0.12);
      margin-top: 0.4rem;
    }

    #progressBar {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 3px;
      background: rgba(255, 255, 255, 0.05);
      z-index: 999;
    }

    #progressBar .fill {
      height: 100%;
      background: linear-gradient(90deg, #fd79a8, #6c5ce7, #00cec9);
      width: 0%;
      transition: width 0.3s linear;
    }

    .music-btn {
      position: fixed;
      top: 15px;
      right: 15px;
      z-index: 9999;
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.05);
      border-radius: 50%;
      width: 40px;
      height: 40px;
      font-size: 1rem;
      color: rgba(255, 255, 255, 0.3);
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .music-btn:active {
      transform: scale(0.9);
    }

    #specialMessage {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.9);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      z-index: 999999;
      justify-content: center;
      align-items: center;
      animation: popIn 0.6s ease;
      padding: 20px;
    }

    #specialMessage.show {
      display: flex;
    }

    @keyframes popIn {
      0% { opacity: 0; transform: scale(0.7); }
      100% { opacity: 1; transform: scale(1); }
    }

    .msg-box {
      max-width: 500px;
      width: 100%;
      background: linear-gradient(145deg, #1a1a3e, #2d1b4e);
      border-radius: 40px;
      padding: 2rem 1.5rem;
      text-align: center;
      border: 1px solid rgba(255, 255, 255, 0.05);
      box-shadow: 0 20px 60px rgba(108, 92, 231, 0.15);
      position: relative;
      overflow: hidden;
      max-height: 90vh;
      overflow-y: auto;
    }

    .msg-box::-webkit-scrollbar {
      width: 3px;
    }
    .msg-box::-webkit-scrollbar-thumb {
      background: rgba(108, 92, 231, 0.3);
      border-radius: 10px;
    }

    .msg-box::before {
      content: '';
      position: absolute;
      inset: 0;
      background: conic-gradient(from 0deg, transparent, rgba(108, 92, 231, 0.05), transparent, rgba(253, 121, 168, 0.05), transparent);
      animation: spinBg 10s linear infinite;
    }

    @keyframes spinBg {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .msg-box .big-heart {
      font-size: 3.5rem;
      animation: heartBeat 1.5s ease-in-out infinite;
      position: relative;
      z-index: 1;
    }

    @keyframes heartBeat {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.15); }
    }

    .msg-box h2 {
      color: white;
      font-size: 1.5rem;
      margin: 0.3rem 0;
      background: linear-gradient(135deg, #fd79a8, #6c5ce7);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      position: relative;
      z-index: 1;
    }

    .msg-box p {
      color: rgba(255, 255, 255, 0.8);
      font-size: 0.95rem;
      line-height: 2;
      margin: 0.5rem 0 1.2rem;
      position: relative;
      z-index: 1;
    }

    .msg-box .highlight-name {
      color: #fd79a8;
      font-weight: 700;
      font-size: 1.1rem;
    }

    .msg-box .highlight-rajat {
      color: #6c5ce7;
      font-weight: 700;
      font-size: 1rem;
    }

    .msg-box .highlight-important {
      color: #00cec9;
      font-weight: 600;
      font-size: 1rem;
    }

    .msg-box .heart-line {
      color: #fd79a8;
      font-size: 1.3rem;
      letter-spacing: 4px;
      position: relative;
      z-index: 1;
    }

    .msg-box .close-btn {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid rgba(255, 255, 255, 0.05);
      padding: 0.5rem 2rem;
      border-radius: 50px;
      color: rgba(255, 255, 255, 0.5);
      cursor: pointer;
      transition: all 0.3s ease;
      font-size: 0.85rem;
      position: relative;
      z-index: 1;
      touch-action: manipulation;
    }

    .msg-box .close-btn:active {
      transform: scale(0.95);
    }

    @media (max-width: 550px) {
      .slide-content .title {
        font-size: 1.2rem;
        margin-top: 0.4rem;
      }
      .slide-content .msg {
        font-size: 0.8rem;
      }
      .slide-content .media {
        max-height: 50vh;
        border-radius: 20px;
      }
      .music-btn {
        width: 36px;
        height: 36px;
        font-size: 0.9rem;
        top: 12px;
        right: 12px;
      }
      .msg-box {
        padding: 1.5rem 1.2rem;
        border-radius: 30px;
      }
      .msg-box h2 {
        font-size: 1.3rem;
      }
      .msg-box p {
        font-size: 0.85rem;
        line-height: 1.8;
      }
      .msg-box .big-heart {
        font-size: 3rem;
      }
      #progressBar {
        height: 2px;
      }
    }

    @media (max-width: 400px) {
      .slide-content .title {
        font-size: 1rem;
      }
      .slide-content .msg {
        font-size: 0.7rem;
      }
      .slide-content .media {
        max-height: 40vh;
      }
    }
  </style>
</head>
<body>

  <canvas id="flowerCanvas"></canvas>

  <div id="loading">
    <div class="loader"></div>
    <div class="load-text">🌸 Loading...</div>
  </div>

  <div id="progressBar">
    <div class="fill" id="progressFill"></div>
  </div>

  <div id="slideshow">
    <div class="slide-content" id="slideContent">
      <img class="media" id="slideMedia" src="" alt="slide">
      <div class="title" id="slideTitle"></div>
      <div class="msg" id="slideMsg"></div>
      <div class="counter" id="slideCounter"></div>
    </div>
  </div>

  <button class="music-btn" id="musicToggle">
    <i class="fas fa-music"></i>
  </button>

  <div id="specialMessage">
    <div class="msg-box">
      <div class="big-heart">❤️</div>
      <h2>💌 A Special Message For You</h2>
      <p>
        <span class="highlight-name">✨ My Dearest Tyagi,</span>
        <br><br>
        We met online, and even though we've never met in person —<br>
        and maybe we never will —<br>
        I just want you to know...
        <br><br>
        <span class="highlight-important">💫 You are the best female friend I have ever had.</span>
        <br><br>
        Through every conversation, every laugh, and every moment —<br>
        you have been there for me.
        <br><br>
        <span style="color:#fd79a8; font-weight:600;">Tumhara toh pata nahi...</span><br>
        <span style="color:#a29bfe;">ki main tumhare liye kitna matter karta hu,</span><br>
        <span style="color:#fd79a8; font-weight:600;">but mere liye tum karti ho —</span><br>
        <span style="color:#00cec9; font-size:1.1rem; font-weight:700;">✨ You mean the world to me. ✨</span>
        <br><br>
        <span style="color:#fd79a8; font-weight:600;">Thank you for existing.</span><br>
        <span style="color:#a29bfe;">Thank you for being you.</span>
        <br><br>
        <span class="heart-line">💖💕💗💖💕</span>
        <br><br>
        <span style="color:rgba(255,255,255,0.4); font-size:0.8rem;">
          with all my heart,<br>
          <span class="highlight-rajat">Yours Obediently,<br>Rajat ❤️</span>
        </span>
      </p>
      <button class="close-btn" onclick="closeMessage()">
        <i class="fas fa-heart"></i> Close with love
      </button>
    </div>
  </div>

  <audio id="bgMusic" loop preload="auto">
    <source src="background-music.mp3" type="audio/mpeg">
  </audio>

  <script>
    (function() {
      // ===== SLIDES DATA =====
      const slides = [{
        type: 'image',
        file: 'tyagi1.jpg',
        title: '🌸 First Glow',
        msg: 'You light up every room!'
      }, {
        type: 'video',
        file: 'tyagi2.mp4',
        title: '🎬 Special Moments',
        msg: 'Beautiful energy!'
      }, {
        type: 'image',
        file: 'tyagi3.jpg',
        title: '💎 Pure Gem',
        msg: 'Rare & precious!'
      }, {
        type: 'video',
        file: 'tyagi4.mp4',
        title: '🎬 Joyful Vibes',
        msg: 'Pure happiness!'
      }, {
        type: 'video',
        file: 'tyagi5.mp4',
        title: '🌊 Free Spirit',
        msg: 'Your energy is contagious!'
      }, {
        type: 'image',
        file: 'tyagi.jpg',
        title: '🌟 You Are Special',
        msg: 'Extraordinary! Grateful for you!'
      }];

      // ===== DOM REFS =====
      const slideContent = document.getElementById('slideContent');
      const slideTitle = document.getElementById('slideTitle');
      const slideMsg = document.getElementById('slideMsg');
      const slideCounter = document.getElementById('slideCounter');
      const progressFill = document.getElementById('progressFill');

      let currentIndex = 0;
      let slideTimeout = null;
      let progressInterval = null;
      let videoElement = null;

      // ===== FLOWERS =====
      const canvas = document.getElementById('flowerCanvas');
      const ctx = canvas.getContext('2d');
      let flowers = [];
      let flowerRunning = false;
      let flowerFrame;

      function resizeCanvas() {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
      }
      window.addEventListener('resize', resizeCanvas);
      resizeCanvas();

      const flowerEmojis = ['🌸', '🌺', '🌷', '🌹', '🌻', '🌼', '💐', '🌸', '🌺', '🌷'];

      class Flower {
        constructor() {
          this.x = Math.random() * canvas.width;
          this.y = Math.random() * canvas.height - canvas.height;
          this.size = Math.random() * 24 + 18;
          this.speed = Math.random() * 1.8 + 1.2;
          this.rotation = Math.random() * 360;
          this.rotSpeed = (Math.random() - 0.5) * 0.03;
          this.emoji = flowerEmojis[Math.floor(Math.random() * flowerEmojis.length)];
          this.wobble = Math.random() * 10;
          this.wobbleSpeed = Math.random() * 0.03 + 0.01;
          this.opacity = Math.random() * 0.4 + 0.5;
          this.scale = Math.random() * 0.4 + 0.6;
        }

        update() {
          this.y += this.speed;
          this.x += Math.sin(this.wobble) * 0.6;
          this.wobble += this.wobbleSpeed;
          this.rotation += this.rotSpeed;
          if (this.y > canvas.height + 50) {
            this.y = -30;
            this.x = Math.random() * canvas.width;
            this.emoji = flowerEmojis[Math.floor(Math.random() * flowerEmojis.length)];
          }
        }

        draw() {
          ctx.save();
          ctx.translate(this.x, this.y);
          ctx.rotate(this.rotation);
          ctx.globalAlpha = this.opacity;
          ctx.font = `${this.size * this.scale}px sans-serif`;
          ctx.textAlign = 'center';
          ctx.textBaseline = 'middle';
          ctx.shadowColor = 'rgba(253, 121, 168, 0.15)';
          ctx.shadowBlur = 12;
          ctx.fillText(this.emoji, 0, 0);
          ctx.restore();
        }
      }

      function startFlowers(count = 50) {
        if (flowerRunning) return;
        flowerRunning = true;
        flowers = [];
        for (let i = 0; i < count; i++) {
          const f = new Flower();
          f.y = Math.random() * canvas.height;
          flowers.push(f);
        }
        animateFlowers();
      }

      function animateFlowers() {
        if (!flowerRunning) return;
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        flowers.forEach(f => { f.update();
          f.draw(); });
        flowerFrame = requestAnimationFrame(animateFlowers);
      }

      // ===== SLIDESHOW FUNCTIONS =====
      function showSlide(index) {
        if (videoElement) {
          videoElement.pause();
          videoElement.removeEventListener('ended', onVideoEnd);
          videoElement.removeEventListener('timeupdate', onVideoTimeUpdate);
          videoElement = null;
        }

        const oldMedia = slideContent.querySelector('.media');
        if (oldMedia) oldMedia.remove();

        const slide = slides[index];
        if (!slide) {
          showSpecialMessage();
          return;
        }

        slideTitle.textContent = slide.title;
        slideMsg.textContent = slide.msg;
        slideCounter.textContent = `${index + 1} / ${slides.length}`;

        if (slide.type === 'image') {
          const img = document.createElement('img');
          img.className = 'media';
          img.src = slide.file;
          img.alt = 'slide';
          img.loading = 'lazy';
          slideContent.insertBefore(img, slideContent.firstChild);

          startProgress(4000);

          clearTimeout(slideTimeout);
          slideTimeout = setTimeout(() => {
            nextSlide();
          }, 4000);
        } else {
          const vid = document.createElement('video');
          vid.className = 'media';
          vid.src = slide.file;
          vid.muted = true;
          vid.autoplay = true;
          vid.playsInline = true;
          vid.controls = false;
          vid.preload = 'auto';
          vid.style.width = '100%';
          vid.style.maxHeight = '60vh';
          vid.style.objectFit = 'contain';
          vid.style.borderRadius = '25px';
          vid.style.background = 'rgba(0,0,0,0.3)';
          vid.style.border = '2px solid rgba(255,255,255,0.05)';

          slideContent.insertBefore(vid, slideContent.firstChild);
          videoElement = vid;

          vid.play().catch(() => {});

          // Auto unmute after 1 second
          setTimeout(() => {
            if (videoElement) {
              videoElement.muted = false;
              videoElement.play().catch(() => {});
            }
          }, 1000);

          vid.addEventListener('ended', onVideoEnd);
          vid.addEventListener('timeupdate', onVideoTimeUpdate);

          let fallbackTimer = setTimeout(() => {
            if (videoElement && !videoElement.ended) {
              if (videoElement.currentTime === 0 || videoElement.paused) {
                nextSlide();
              }
            }
          }, 15000);

          vid.addEventListener('play', function() { clearTimeout(fallbackTimer); });
          vid.addEventListener('canplay', function() { clearTimeout(fallbackTimer); });
          vid.addEventListener('ended', function() { clearTimeout(fallbackTimer); });
        }

        for (let i = 0; i < 5; i++) {
          const f = new Flower();
          f.y = -20 - Math.random() * 100;
          flowers.push(f);
        }
      }

      function onVideoTimeUpdate() {
        if (videoElement) {
          const duration = videoElement.duration;
          const currentTime = videoElement.currentTime;
          if (duration && isFinite(duration) && duration > 0) {
            const percent = (currentTime / duration) * 100;
            progressFill.style.width = Math.min(percent, 100) + '%';
          }
        }
      }

      function onVideoEnd() {
        setTimeout(() => { nextSlide(); }, 500);
      }

      function startProgress(duration) {
        clearInterval(progressInterval);
        let startTime = Date.now();
        progressFill.style.width = '0%';

        if (duration > 0) {
          progressInterval = setInterval(() => {
            const elapsed = Date.now() - startTime;
            const percent = Math.min((elapsed / duration) * 100, 100);
            progressFill.style.width = percent + '%';
            if (percent >= 100) {
              clearInterval(progressInterval);
            }
          }, 50);
        }
      }

      function nextSlide() {
        currentIndex++;
        if (currentIndex >= slides.length) {
          showSpecialMessage();
          return;
        }
        showSlide(currentIndex);
      }

      // ===== SPECIAL MESSAGE =====
      let messageShown = false;

      function showSpecialMessage() {
        if (messageShown) return;
        messageShown = true;

        clearTimeout(slideTimeout);
        clearInterval(progressInterval);

        document.getElementById('slideshow').style.display = 'none';
        document.getElementById('progressBar').style.display = 'none';
        document.getElementById('specialMessage').classList.add('show');

        for (let i = 0; i < 40; i++) {
          const f = new Flower();
          f.x = canvas.width / 2 + (Math.random() - 0.5) * 350;
          f.y = -20 - Math.random() * 250;
          f.size = Math.random() * 35 + 22;
          flowers.push(f);
        }
      }

      window.closeMessage = function() {
        document.getElementById('specialMessage').classList.remove('show');
        document.getElementById('slideshow').style.display = 'flex';
        document.getElementById('progressBar').style.display = 'block';
        currentIndex = 0;
        messageShown = false;
        showSlide(0);
      };

      // ===== LOADING =====
      setTimeout(() => {
        document.getElementById('loading').classList.add('hide');
        startFlowers(50);
        showSlide(0);
      }, 2000);

      // ===== MUSIC =====
      const audio = document.getElementById('bgMusic');
      const toggle = document.getElementById('musicToggle');
      let playing = false;

      toggle.addEventListener('click', function() {
        if (playing) {
          audio.pause();
          this.innerHTML = '<i class="fas fa-music" style="opacity:0.2;"></i>';
          playing = false;
        } else {
          audio.play().catch(() => {});
          this.innerHTML = '<i class="fas fa-music" style="color:#a29bfe;"></i>';
          playing = true;
        }
      });

      document.addEventListener('click', function initMusic() {
        if (!playing) {
          audio.play().catch(() => {});
          playing = true;
          toggle.innerHTML = '<i class="fas fa-music" style="color:#a29bfe;"></i>';
        }
        document.removeEventListener('click', initMusic);
      }, { once: true });

      // ===== CONTINUOUS FLOWERS =====
      setInterval(() => {
        if (flowerRunning && flowers.length < 100) {
          for (let i = 0; i < 2; i++) {
            flowers.push(new Flower());
          }
        }
      }, 2500);

    })();
  </script>
</body>
</html>
