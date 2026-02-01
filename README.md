<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Be My Valentine ❤️</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
    }
    .hearts span {
      position: absolute;
      bottom: -20px;
      font-size: 20px;
      animation: float 8s linear infinite;
      opacity: 0.8;
    }
    @keyframes float {
      from { transform: translateY(0); opacity: 1; }
      to { transform: translateY(-110vh); opacity: 0; }
    }
    .card {
      background: white;
      padding: 30px 40px;
      border-radius: 20px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.15);
      text-align: center;
      max-width: 400px;
      animation: pop 0.5s ease;
      z-index: 2;
    }
    @keyframes pop {
      from { transform: scale(0.8); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }
    h1 {
      color: #ff4d6d;
      font-size: 1.6rem;
      margin-bottom: 20px;
    }
    .options {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      justify-content: center;
    }
    button {
      border: none;
      padding: 12px 20px;
      border-radius: 25px;
      font-size: 1rem;
      cursor: pointer;
      background: #ff4d6d;
      color: white;
      transition: transform 0.2s, background 0.2s;
    }
    button:hover {
      transform: scale(1.05);
      background: #e63b5d;
    }
    .no {
      background: #999;
      position: relative;
    }
    .spin-out {
      animation: spinOut 3s forwards;
    }
    @keyframes spinOut {
      to {
        transform: translateX(1000px) rotate(720deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <!-- Floating hearts -->
  <div class="hearts"></div>
  <div class="card" id="card">
    <h1 id="question">Hey Ann, do you wanna know something? 💕</h1>
    <div class="options" id="options">
      <button onclick="next()">Yes</button>
      <button onclick="next()">Yes</button>
    </div>
  </div>  <script>
    let step = 0;

    // floating hearts generator
    const heartsContainer = document.querySelector('.hearts');
    setInterval(() => {
      const heart = document.createElement('span');
      heart.innerHTML = '❤️';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (6 + Math.random() * 4) + 's';
      heartsContainer.appendChild(heart);
      setTimeout(() => heart.remove(), 9000);
    }, 500);

    function next() {
      step++;
      const q = document.getElementById('question');
      const o = document.getElementById('options');

      if (step === 1) {
        q.innerHTML = 'I love you so much, Ann 😘❤️';
        o.innerHTML = '<button onclick="next()">Really</button>';
      }
      else if (step === 2) {
        q.innerHTML = 'Yep. Do you know how happy you make me? 🥰';
        o.innerHTML = '<button onclick="next()">Maybe</button>' +
                      '<button onclick="next()">I know 😏</button>';
      }
      else if (step === 3) {
        q.innerHTML = "Do you know you're my favourite person, Ann? 💖";
        o.innerHTML = '<button onclick="next()">Awww</button>' +
                      '<button onclick="next()">Really</button>';
      }
      else if (step === 4) {
        q.innerHTML = "So would you babe make me the happiest person this Valentine's Day? 💋💝";
        o.innerHTML = '<button onclick="yes()">Of course</button>' +
                      '<button onclick="yes()">Yes</button>' +
                      '<button class="no" id="noBtn">No</button>';

        const noBtn = document.getElementById('noBtn');
        setTimeout(() => {
          noBtn.classList.add('spin-out');
        }, 300);
      }
    }

    function yes() {
      const q = document.getElementById('question');
      const o = document.getElementById('options');
      q.innerHTML = 'YAY Ann!!! You just made me the luckiest person ever 😍❤️💋';
      o.innerHTML = '<button onclick="screenshot()">Screenshot this moment 📸</button>';
      launchConfetti();
    }

    function launchConfetti() {
      for (let i = 0; i < 80; i++) {
        const c = document.createElement('div');
        c.className = 'confetti';
        c.innerHTML = Math.random() > 0.5 ? '💖' : '💘';
        c.style.left = Math.random() * 100 + 'vw';
        c.style.animationDuration = (2 + Math.random() * 3) + 's';
        document.body.appendChild(c);
        setTimeout(() => c.remove(), 4000);
      }
    }

    function screenshot() {
      alert('Take a screenshot, Ann 💕 This moment is forever 😘');
    }

</script></body>
</html>
