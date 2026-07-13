<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>✨ A Message for You ✨</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', 'Quicksand', 'Cormorant Garamond', Georgia, serif;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #0a0a1a;
      position: relative;
      overflow-x: hidden;
      overflow-y: auto;
      padding: 1rem;
    }

    /* ---- AESTHETIC NIGHT BACKGROUND ---- */
    .night-background {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(180deg, 
        #0b0b2b 0%, 
        #1a1a3e 25%, 
        #2d1b4e 50%, 
        #1e2a4a 75%, 
        #0f0f2a 100%);
      z-index: 0;
    }

    /* Stars twinkling */
    .stars-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
    }

    .star {
      position: absolute;
      background: white;
      border-radius: 50%;
      animation: twinkle 3s infinite alternate;
      box-shadow: 0 0 6px 2px rgba(255, 255, 200, 0.7);
    }

    @keyframes twinkle {
      0% { opacity: 0.3; transform: scale(0.8); }
      50% { opacity: 1; transform: scale(1.3); }
      100% { opacity: 0.4; transform: scale(0.7); }
    }

    /* Moon */
    .moon {
      position: fixed;
      top: 40px;
      right: 60px;
      width: 100px;
      height: 100px;
      background: radial-gradient(circle at 35% 35%, #fff9c4, #ffe082, #ffcc80);
      border-radius: 50%;
      box-shadow: 0 0 60px 20px rgba(255, 235, 150, 0.5), 0 0 120px 40px rgba(255, 200, 100, 0.3);
      z-index: 1;
      animation: moonGlow 4s infinite alternate;
    }

    @keyframes moonGlow {
      0% { box-shadow: 0 0 60px 20px rgba(255, 235, 150, 0.5), 0 0 120px 40px rgba(255, 200, 100, 0.3); }
      100% { box-shadow: 0 0 80px 30px rgba(255, 235, 150, 0.7), 0 0 150px 55px rgba(255, 200, 100, 0.45); }
    }

    /* Floating night clouds */
    .cloud {
      position: fixed;
      background: rgba(255, 255, 255, 0.06);
      border-radius: 50%;
      filter: blur(35px);
      z-index: 0;
      animation: cloudDrift 30s infinite linear;
    }

    @keyframes cloudDrift {
      0% { transform: translateX(-100px); }
      100% { transform: translateX(calc(100vw + 200px)); }
    }

    /* MAIN CARD */
    .container {
      position: relative;
      z-index: 5;
      background: rgba(20, 15, 35, 0.65);
      backdrop-filter: blur(25px);
      -webkit-backdrop-filter: blur(25px);
      border-radius: 3.5rem;
      padding: 2.5rem 2rem 2.2rem;
      max-width: 500px;
      width: 100%;
      box-shadow: 0 30px 55px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(255, 200, 255, 0.25);
      text-align: center;
      border: 1px solid rgba(255, 220, 255, 0.2);
      transition: all 0.5s ease;
    }

    /* Lock icon */
    .lock-icon {
      font-size: 3.5rem;
      margin-bottom: 0.8rem;
      animation: lockPulse 2s infinite;
    }

    @keyframes lockPulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.08); }
    }

    h1 {
      font-size: 1.8rem;
      font-weight: 500;
      color: #f8e3ff;
      margin: 0.3rem 0 0.5rem;
      letter-spacing: 1.2px;
      text-shadow: 0 0 20px rgba(200, 150, 255, 0.7);
    }

    .subtitle {
      color: #b8a0d0;
      font-size: 0.95rem;
      margin-bottom: 1.8rem;
      letter-spacing: 0.5px;
    }

    /* Password dots */
    .password-dots {
      display: flex;
      justify-content: center;
      gap: 1rem;
      margin: 1.5rem 0;
    }

    .dot {
      width: 18px;
      height: 18px;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.15);
      border: 2px solid rgba(255, 220, 255, 0.5);
      transition: all 0.3s ease;
    }

    .dot.filled {
      background: #ffb3ff;
      border-color: #ffdbff;
      box-shadow: 0 0 18px #d580ff;
    }

    .dot.error {
      background: #ff6b6b;
      border-color: #ff4444;
      box-shadow: 0 0 18px #ff4444;
      animation: shake 0.5s ease;
    }

    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-8px); }
      75% { transform: translateX(8px); }
    }

    /* Number keyboard */
    .keyboard {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 0.8rem;
      margin: 1.5rem 0;
    }

    .key {
      width: 58px;
      height: 58px;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.06);
      backdrop-filter: blur(12px);
      border: 1.5px solid rgba(255, 220, 255, 0.4);
      color: #ffeef9;
      font-size: 1.5rem;
      font-weight: 600;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.2s ease;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      line-height: 1;
    }

    .key:hover {
      background: rgba(200, 160, 255, 0.25);
      border-color: #ffb3ff;
      transform: scale(1.06);
      box-shadow: 0 0 18px #b57edc;
    }

    .key:active {
      transform: scale(0.9);
      background: #b87cff;
    }

    .submit-key {
      background: rgba(180, 130, 255, 0.3);
      border-color: #c9a0ff;
      color: #fff;
      font-size: 0.95rem;
      font-weight: 700;
      letter-spacing: 0.5px;
      width: auto;
      padding: 0 1.6rem;
      border-radius: 2.5rem;
    }

    .clear-key {
      background: rgba(255, 100, 100, 0.2);
      border-color: #ff8a8a;
      font-size: 1.3rem;
    }

    .error-message {
      color: #ff8a8a;
      font-size: 0.9rem;
      margin-top: 0.5rem;
      min-height: 1.5rem;
      transition: 0.3s;
    }

    /* ---- UNLOCKED MESSAGE (hidden until correct) ---- */
    .unlocked-content {
      display: none;
      animation: fadeInUp 0.8s ease;
    }

    @keyframes fadeInUp {
      0% { opacity: 0; transform: translateY(25px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    .unlocked-content h2 {
      font-size: 2rem;
      color: #ffe5b4;
      font-weight: 500;
      text-shadow: 0 0 20px #ffb3ba;
      margin: 0.8rem 0;
    }

    .sweet-message {
      color: #e0c8ff;
      font-size: 1.15rem;
      line-height: 1.7;
      margin: 1rem 0;
      font-style: italic;
    }

    /* ---- FALLING FLOWER PETALS (SVG based, soft animation) ---- */
    .falling-petal {
      position: fixed;
      top: -60px;
      z-index: 25;
      pointer-events: none;
      animation: petalFall linear forwards;
      filter: drop-shadow(0 6px 10px rgba(255, 180, 200, 0.5));
      transform-origin: center;
    }

    @keyframes petalFall {
      0% {
        transform: translateY(0) rotate(0deg) scale(0.4);
        opacity: 0.9;
      }
      15% {
        transform: translateY(12vh) rotate(20deg) scale(0.85);
        opacity: 1;
      }
      40% {
        transform: translateY(38vh) rotate(-15deg) scale(1.05);
        opacity: 0.85;
      }
      70% {
        transform: translateY(68vh) rotate(10deg) scale(0.75);
        opacity: 0.6;
      }
      100% {
        transform: translateY(105vh) rotate(-20deg) scale(0.3);
        opacity: 0;
      }
    }

    /* ---- FALLING HEARTS (high quality SVG) ---- */
    .falling-heart {
      position: fixed;
      top: -60px;
      z-index: 25;
      pointer-events: none;
      animation: fallDown linear forwards;
      filter: drop-shadow(0 8px 12px rgba(200, 60, 80, 0.5));
      transform-origin: center;
    }

    @keyframes fallDown {
      0% {
        transform: translateY(0) rotate(0deg) scale(0.4);
        opacity: 0.95;
      }
      15% {
        transform: translateY(12vh) rotate(15deg) scale(0.9);
        opacity: 1;
      }
      40% {
        transform: translateY(38vh) rotate(-10deg) scale(1.1);
        opacity: 0.9;
      }
      70% {
        transform: translateY(68vh) rotate(8deg) scale(0.8);
        opacity: 0.65;
      }
      100% {
        transform: translateY(105vh) rotate(-15deg) scale(0.3);
        opacity: 0;
      }
    }

    @media (max-width: 480px) {
      .container { padding: 2rem 1rem; }
      .key { width: 48px; height: 48px; font-size: 1.3rem; }
      h1 { font-size: 1.5rem; }
      .submit-key { font-size: 0.85rem; padding: 0 1.2rem; }
    }
  </style>
</head>
<body>
  <!-- Night background -->
  <div class="night-background"></div>
  <div class="stars-container" id="starsContainer"></div>
  <div class="moon"></div>
  <div class="cloud" style="top:15%; left:-150px; width:300px; height:80px;"></div>
  <div class="cloud" style="top:55%; left:-200px; width:400px; height:100px; animation-duration:35s;"></div>

  <div class="container" id="mainContainer">
    <!-- LOCKED STATE (visible initially) -->
    <div id="lockedState">
      <div class="lock-icon">🔒</div>
      <h1>Ishfahan has a message for you</h1>
      <p class="subtitle">enter the code to unlock ✨</p>

      <div class="password-dots" id="passwordDots">
        <div class="dot" id="dot1"></div>
        <div class="dot" id="dot2"></div>
        <div class="dot" id="dot3"></div>
        <div class="dot" id="dot4"></div>
      </div>

      <div class="keyboard" id="keyboard"></div>

      <div class="error-message" id="errorMessage"></div>
    </div>

    <!-- UNLOCKED STATE (hidden initially) -->
    <div class="unlocked-content" id="unlockedContent">
      <h2>Wish You A Happy Monday Night</h2>
      <p class="sweet-message">
        May you sleep early this night,<br>
        wrapped in soft dreams and starlight.<br>
        Let the quiet hours heal your heart,<br>
        and bring you peace for a fresh start.
      </p>
      <button class="key submit-key" id="resetLockBtn" style="margin-top:1.2rem; font-size:0.95rem;">🔁 lock again</button>
    </div>
  </div>

  <script>
    (function() {
      // ----- STARS -----
      function createStars() {
        const container = document.getElementById('starsContainer');
        for (let i = 0; i < 100; i++) {
          const star = document.createElement('div');
          star.className = 'star';
          const size = Math.random() * 3 + 1.5;
          star.style.width = size + 'px';
          star.style.height = size + 'px';
          star.style.left = Math.random() * 98 + '%';
          star.style.top = Math.random() * 95 + '%';
          star.style.animationDelay = Math.random() * 5 + 's';
          star.style.animationDuration = 2.5 + Math.random() * 5 + 's';
          container.appendChild(star);
        }
      }
      createStars();

      // ----- LOCK / UNLOCK LOGIC -----
      const correctCode = '1803';
      let enteredCode = '';
      const dots = [
        document.getElementById('dot1'),
        document.getElementById('dot2'),
        document.getElementById('dot3'),
        document.getElementById('dot4')
      ];
      const errorMessage = document.getElementById('errorMessage');
      const lockedState = document.getElementById('lockedState');
      const unlockedContent = document.getElementById('unlockedContent');
      const keyboardDiv = document.getElementById('keyboard');

      function updateDots() {
        dots.forEach((dot, i) => {
          dot.classList.remove('filled', 'error');
          if (enteredCode[i]) {
            dot.classList.add('filled');
          }
        });
        errorMessage.textContent = '';
      }

      function shakeDots() {
        dots.forEach(dot => dot.classList.add('error'));
        setTimeout(() => {
          dots.forEach(dot => dot.classList.remove('error'));
        }, 600);
      }

      function addDigit(digit) {
        if (enteredCode.length >= 4) return;
        enteredCode += digit;
        updateDots();
      }

      function clearCode() {
        enteredCode = '';
        updateDots();
        errorMessage.textContent = '';
        lockedState.style.display = 'block';
        unlockedContent.style.display = 'none';
      }

      function submitCode() {
        if (enteredCode.length < 4) {
          errorMessage.textContent = '⚠️ Please enter 4 digits';
          return;
        }
        if (enteredCode === correctCode) {
          // SUCCESS
          lockedState.style.display = 'none';
          unlockedContent.style.display = 'block';
          errorMessage.textContent = '';
          // trigger flower petals & hearts
          spawnFallingPetals();
          spawnFallingHearts();
          setTimeout(() => spawnFallingPetals(), 400);
          setTimeout(() => spawnFallingHearts(), 500);
        } else {
          // INCORRECT
          errorMessage.textContent = '❌ Incorrect password. Try again.';
          shakeDots();
          enteredCode = '';
          updateDots();
        }
      }

      // Build keyboard
      function buildKeyboard() {
        keyboardDiv.innerHTML = '';
        for (let i = 1; i <= 9; i++) {
          const btn = document.createElement('button');
          btn.className = 'key';
          btn.textContent = i;
          btn.addEventListener('click', () => addDigit(i.toString()));
          keyboardDiv.appendChild(btn);
        }
        const zeroBtn = document.createElement('button');
        zeroBtn.className = 'key';
        zeroBtn.textContent = '0';
        zeroBtn.addEventListener('click', () => addDigit('0'));
        keyboardDiv.appendChild(zeroBtn);

        const clearBtn = document.createElement('button');
        clearBtn.className = 'key clear-key';
        clearBtn.textContent = '⌫';
        clearBtn.addEventListener('click', clearCode);
        keyboardDiv.appendChild(clearBtn);

        const submitBtn = document.createElement('button');
        submitBtn.className = 'key submit-key';
        submitBtn.textContent = 'Submit';
        submitBtn.addEventListener('click', submitCode);
        keyboardDiv.appendChild(submitBtn);
      }
      buildKeyboard();

      // Reset button
      document.getElementById('resetLockBtn').addEventListener('click', () => {
        clearCode();
        lockedState.style.display = 'block';
        unlockedContent.style.display = 'none';
      });

      updateDots();

      // ----- HIGH QUALITY SVG FALLING HEARTS -----
      function createSVGHeart(color = '#ff6b8a', size = 32) {
        const wrapper = document.createElement('div');
        wrapper.className = 'falling-heart';
        wrapper.style.width = size + 'px';
        wrapper.style.height = size + 'px';
        wrapper.innerHTML = `
          <svg width="100%" height="100%" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M16 28C16 28 4 20.5 4 12C4 8.5 6.5 5.5 10 5.5C12.5 5.5 14.5 7 16 9C17.5 7 19.5 5.5 22 5.5C25.5 5.5 28 8.5 28 12C28 20.5 16 28 16 28Z" 
                  fill="${color}" stroke="#ffccd5" stroke-width="1.2" />
          </svg>
        `;
        return wrapper;
      }

      function spawnFallingHearts() {
        const colors = ['#ff4d6d', '#ff758f', '#ff99aa', '#e63950', '#ffb3c6', '#ff6b8a', '#f06292'];
        const heartCount = 20;
        for (let i = 0; i < heartCount; i++) {
          setTimeout(() => {
            const heart = createSVGHeart(
              colors[Math.floor(Math.random() * colors.length)],
              22 + Math.random() * 42
            );
            heart.style.left = Math.random() * 94 + '%';
            heart.style.animationDuration = (2.5 + Math.random() * 5) + 's';
            heart.style.transform = `rotate(${Math.random() * 40 - 20}deg)`;
            document.body.appendChild(heart);
            heart.addEventListener('animationend', () => heart.remove());
          }, i * 55);
        }
      }

      // ----- FLOWER PETALS (soft SVG petals) -----
      function createSVGPetal(color = '#f8a5c2', size = 24) {
        const wrapper = document.createElement('div');
        wrapper.className = 'falling-petal';
        wrapper.style.width = size + 'px';
        wrapper.style.height = size + 'px';
        wrapper.innerHTML = `
          <svg width="100%" height="100%" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <ellipse cx="12" cy="8" rx="5" ry="9" fill="${color}" opacity="0.9" transform="rotate(15 12 8)"/>
            <ellipse cx="12" cy="8" rx="4.5" ry="8.5" fill="${color}" opacity="0.7" transform="rotate(-20 12 8)"/>
            <circle cx="12" cy="7" r="2.5" fill="#fff5e6" opacity="0.8"/>
          </svg>
        `;
        return wrapper;
      }

      function spawnFallingPetals() {
        const colors = ['#f8a5c2', '#f7c5d0', '#fddde6', '#ffb7c5', '#ffcfd8', '#f4acb7'];
        const petalCount = 22;
        for (let i = 0; i < petalCount; i++) {
          setTimeout(() => {
            const petal = createSVGPetal(
              colors[Math.floor(Math.random() * colors.length)],
              18 + Math.random() * 32
            );
            petal.style.left = Math.random() * 94 + '%';
            petal.style.animationDuration = (3 + Math.random() * 6) + 's';
            document.body.appendChild(petal);
            petal.addEventListener('animationend', () => petal.remove());
          }, i * 65);
        }
      }
    })();
  </script>
</body>
</html>
