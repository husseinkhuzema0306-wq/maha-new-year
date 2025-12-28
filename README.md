# maha-new-year
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Happy New Year Maha 💖</title>

<style>
:root {
  --pink: #ff8fb1;
  --bg: #fff6fa;
  --dark: #4a2c3a;
}

* { box-sizing: border-box; font-family: "Poppins", sans-serif; }

body {
  margin: 0;
  background: radial-gradient(circle at top, #ffe4ef, var(--bg));
  color: var(--dark);
  overflow-x: hidden;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 0;
}

.container {
  position: relative;
  z-index: 2;
  max-width: 900px;
  margin: 60px auto;
  background: white;
  border-radius: 24px;
  padding: 40px;
  box-shadow: 0 20px 50px rgba(0,0,0,0.15);
  text-align: center;
}

h1 { color: var(--pink); font-size: 2.6rem; }
h2 { color: var(--pink); margin-top: 40px; }

button {
  background: var(--pink);
  border: none;
  color: white;
  padding: 14px 22px;
  border-radius: 30px;
  font-size: 1rem;
  cursor: pointer;
  transition: transform .2s, box-shadow .2s;
  box-shadow: 0 8px 20px rgba(255,143,177,0.4);
}

button:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 26px rgba(255,143,177,0.6);
}

.countdown {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin: 30px 0;
  flex-wrap: wrap;
}

.box {
  background: var(--pink);
  color: white;
  border-radius: 18px;
  padding: 18px;
  min-width: 95px;
}

.box span { font-size: 2rem; font-weight: bold; display: block; }

.heart {
  font-size: 3rem;
  animation: pulse 1.5s infinite;
  margin: 20px 0;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.25); }
  100% { transform: scale(1); }
}

.letter {
  background: #fff0f6;
  border-radius: 20px;
  padding: 30px;
  text-align: left;
  line-height: 1.8;
  margin-top: 30px;
}

.superman {
  font-size: 2rem;
  cursor: pointer;
  transition: transform .3s;
}

.superman:hover { transform: scale(1.3); }

.hidden {
  display: none;
  margin-top: 20px;
  background: #ffe0ec;
  padding: 20px;
  border-radius: 16px;
  animation: fadeIn .6s ease;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

footer {
  margin-top: 40px;
  opacity: .8;
  font-size: .9rem;
}
</style>
</head>

<body>

<canvas id="fireworks"></canvas>

<audio id="bgMusic" loop>
  <!-- 🔊 Replace with your preferred romantic song -->
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_5d9e6b6f1b.mp3" type="audio/mpeg">
</audio>

<div class="container">
  <h1>Happy New Year, Maha ✨</h1>
  <p>Distance means nothing when my heart chooses you 💕</p>

  <button onclick="playMusic()">🎵 Play Our Song</button>

  <div class="countdown">
    <div class="box"><span id="d">0</span>Days</div>
    <div class="box"><span id="h">0</span>Hours</div>
    <div class="box"><span id="m">0</span>Minutes</div>
    <div class="box"><span id="s">0</span>Seconds</div>
  </div>

  <div class="heart">💗</div>

  <h2>A Letter For You</h2>
  <div class="letter">
    <p>Dear Maha,</p>

    <p>
      You are truly amazing — creative, hardworking, and endlessly inspiring.
      Every day I’m reminded how lucky I am to know someone like you.
    </p>

    <p>
      Even across the distance, you make my world brighter. Your strength,
      kindness, and passion push me to be better.
    </p>

    <p>
      I hope this new year gives you everything you deserve and more. I’ll
      always believe in you — no matter how far apart we are.
    </p>

    <p>Happy New Year, my love 💖</p>
  </div>

  <h2>Tap the Superman 🦸‍♂️</h2>
  <div class="superman" onclick="reveal()">🦸‍♂️</div>

  <div id="secret" class="hidden">
    <p>
      Your Superman is always here — cheering for you, protecting your dreams,
      and loving you endlessly 💕
    </p>
  </div>

  <footer>
    Made with love for Maha ✨
  </footer>
</div>

<script>
// 🎵 MUSIC
function playMusic() {
  document.getElementById("bgMusic").play();
}

// ⏰ COUNTDOWN
const newYear = new Date("January 1, 2026 00:00:00").getTime();
setInterval(() => {
  const now = new Date().getTime();
  const diff = newYear - now;
  if (diff <= 0) return;

  d.innerText = Math.floor(diff / (1000*60*60*24));
  h.innerText = Math.floor(diff / (1000*60*60) % 24);
  m.innerText = Math.floor(diff / (1000*60) % 60);
  s.innerText = Math.floor(diff / 1000 % 60);
}, 1000);

// 🦸‍♂️ CLICK SURPRISE
function reveal() {
  document.getElementById("secret").style.display = "block";
}

// 🎆 FIREWORKS
const canvas = document.getElementById("fireworks");
const ctx = canvas.getContext("2d");
canvas.width = innerWidth;
canvas.height = innerHeight;

let fireworks = [];

function Firework() {
  this.x = Math.random() * canvas.width;
  this.y = Math.random() * canvas.height / 2;
  this.r = 0;
  this.alpha = 1;
  this.color = `hsl(${Math.random()*360},100%,70%)`;
}

function animateFireworks() {
  ctx.clearRect(0,0,canvas.width,canvas.height);
  if (Math.random() < 0.05) fireworks.push(new Firework());

  fireworks.forEach((f,i) => {
    f.r += 2;
    f.alpha -= 0.02;
    ctx.beginPath();
    ctx.arc(f.x,f.y,f.r,0,Math.PI*2);
    ctx.strokeStyle = f.color;
    ctx.globalAlpha = f.alpha;
    ctx.stroke();
    if (f.alpha <= 0) fireworks.splice(i,1);
  });
  requestAnimationFrame(animateFireworks);
}
animateFireworks();
</script>

</body>
</html>
