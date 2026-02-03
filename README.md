# Baby-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bebboo ❤️ NNI 😘🧿</title>
<style>
  :root {
    --primary: #ff4d94;
    --secondary: #ff99cc;
    --glass: rgba(255, 255, 255, 0.2);
    --neon: 0 0 15px #ff4d94, 0 0 30px #ff99cc;
  }

  body {
    margin: 0; padding: 0; font-family: 'Poppins', sans-serif;
    background: radial-gradient(circle at top, #33001b 0%, #000000 100%);
    color: white; text-align: center; overflow-x: hidden;
    min-height: 100vh; display: flex; flex-direction: column; align-items: center;
  }

  .box {
    background: var(--glass); border-radius: 35px; padding: 30px; margin: 20px;
    width: 88%; max-width: 450px; backdrop-filter: blur(20px);
    box-shadow: 0 10px 50px rgba(255, 77, 148, 0.2);
    border: 1px solid rgba(255,255,255,0.2); z-index: 10;
    animation: slideIn 0.8s ease-out;
  }

  @keyframes slideIn { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }

  button {
    background: white; color: var(--primary); border: none; padding: 16px 32px;
    border-radius: 50px; font-size: 17px; font-weight: bold; cursor: pointer;
    margin: 10px; transition: 0.3s; box-shadow: 0 5px 15px rgba(0,0,0,0.3);
  }

  button:hover { transform: translateY(-3px); box-shadow: 0 8px 20px #ff4d94; }
  .hidden { display: none; }
  .option-btn { width: 100%; margin: 12px 0; display: block; text-align: center; }

  /* BIG GLOWING ORBS */
  .orb-container { display: flex; justify-content: center; gap: 30px; margin: 30px 0; }
  .orb {
    width: 125px; height: 125px; border-radius: 50%;
    background: radial-gradient(circle at 30% 30%, #fff, #ffb3d9, #ff4d94);
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    font-size: 15px; font-weight: bold; color: var(--primary);
    animation: float3d 6s infinite ease-in-out; box-shadow: var(--neon);
    border: 3px solid white; transition: 0.5s;
  }
  .orb span { font-size: 32px; }

  @keyframes float3d {
    0%, 100% { transform: translateY(0) rotateY(0deg); }
    50% { transform: translateY(-25px) rotateY(180deg); }
  }

  .progress-fill { height: 12px; width: 0%; background: linear-gradient(90deg, #ff99cc, #ff4d94); border-radius: 10px; transition: 0.5s; }

  /* SCRATCH CARD */
  .scratch-wrap { position: relative; width: 280px; height: 140px; margin: 20px auto; background: #fff; border-radius: 20px; overflow: hidden; border: 3px solid #ff99cc; }
  .scratch-content { position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; color: #ff4d94; font-weight: bold; padding: 15px; }
  #scratchCanvas { position: absolute; top: 0; left: 0; z-index: 2; touch-action: none; cursor: crosshair; }

  .heart-pop { position: fixed; pointer-events: none; z-index: 100; animation: popUp 1.5s ease-out forwards; }
  @keyframes popUp { 0% { transform: scale(0); opacity: 1; } 100% { transform: scale(2) translateY(-150px); opacity: 0; } }

  .no-btn { position: relative; transition: 0.1s; }
</style>
</head>
<body>

<h1>Bebboo ❤️ NNI 😘🧿</h1>

<div id="startBox" class="box">
  <p style="font-size: 1.2rem;">Welcome to our Love Journey ❤️🧿<br><span style="font-size: 0.9rem;">Are you ready, NNI?</span></p>
  <div class="orb-container">
    <div class="orb"><span>🧔🏻‍♂️</span>Bebboo</div>
    <div class="orb"><span>👩🏻‍❤️‍💋‍👨🏻</span>NNI 😘</div>
  </div>
  <button onclick="startApp()">Start Our Story ❤️</button>
</div>

<div id="questionBox" class="hidden box">
  <div style="font-size: 0.8rem; margin-bottom: 5px;">Love Meter: <span id="percent">0%</span></div>
  <div style="width:100%; background:rgba(255,255,255,0.1); border-radius:10px;"><div class="progress-fill" id="progressFill"></div></div>
  <h2 id="questionText" style="min-height: 80px; font-size: 1.2rem; margin-top:20px;"></h2>
  <div id="options"></div>
</div>

<div id="final" class="hidden box">
  <div class="orb" style="width: 150px; height: 150px; margin: 0 auto 20px;"><span>💍🧿</span>MINE</div>
  <h2>100% Love Achieved! ❤️</h2>
  <p>Scratch to reveal your gift: 👇</p>
  <div class="scratch-wrap">
    <div class="scratch-content">🎁 LIFETIME OF HAPPINESS & 1 MILLION KISSES! 💋🧿💍</div>
    <canvas id="scratchCanvas" width="280" height="140"></canvas>
  </div>
  <p><b>Always yours, Bebboo ❤️</b></p>
  <button onclick="location.reload()">Replay 😘🧿</button>
</div>

<script>
const questions = [
  // YOUR ORIGINAL QUESTIONS
  { text: "Do you know you are Bebboo's safest place, NNI 😘🧿?", type: "yesno" },
  { text: "What is my absolute favorite thing in the world?", type: "mcq", options: ["Pasta 🍝", "Cold Coffee ☕", "Traveling ✈️", "Sleeping 😴"], real: "None of these… it’s YOU NNI 😘🧿" },
  { text: "What did Bebboo give you when we first met?", type: "mcq", options: ["Rose 🌹", "Chocolates 🍫", "A Gift 🎁", "A Smile 😊"], real: "Actually… I gave you my HEART ❤️🥹🧿" },
  
  // THE NEW INTERACTIVE QUESTIONS
  { text: "If we were in a room full of people, who would my eyes look for? 👀", type: "mcq", options: ["Friends 🕺", "Food 🍕", "The Exit 🚪", "Only You 👩‍❤️‍👨"], real: "My eyes will always only look for YOU NNI! 🥺❤️" },
  { text: "Do you know that you are the 'Password' to my heart? 🔑❤️", type: "yesno" },
  { text: "If I ever get lost, will you promise to find me? 🥺🗺️", type: "yesno" },
  { text: "Which habit of NNI does Bebboo love the most? 🤔", type: "mcq", options: ["The way you talk 🗣️", "Your cute anger 😡🤏", "Everything! 😍"], real: "I choose 'Everything'! Even your anger is cute to me! 🧿😘" },
  { text: "Are you ready to grow old and eat pasta with me forever? 🍝👵🏻👴🏻", type: "yesno" },
  { text: "Will you promise to never let go of Bebboo's hand? 🤝🥺", type: "yesno" },
  { text: "Do you know that no one is as lucky as me? Because I have you! 🍀💖", type: "yesno" },
  { text: "Will you be the mother of my future kids? 👶🏻❤️🍼", type: "yesno" },
  { text: "Do you believe that we are protected from every evil eye? 🧿🙏", type: "yesno" },
  { text: "Final: Will you stay with Bebboo forever & ever? 💍🧿😘", type: "yesno" }
];

let index = 0;
let noScale = 1;

function startApp() {
  document.getElementById("startBox").classList.add("hidden");
  document.getElementById("questionBox").classList.remove("hidden");
  showQuestion();
}

function showQuestion() {
  const q = questions[index];
  document.getElementById("questionText").innerText = q.text;
  const opt = document.getElementById("options");
  opt.innerHTML = "";
  
  const perc = Math.floor((index / questions.length) * 100);
  document.getElementById("progressFill").style.width = perc + "%";
  document.getElementById("percent").innerText = perc + "%";

  if (q.type === "yesno") {
    opt.innerHTML = `<button onclick="next()">YES! 😭❤️</button>
                     <button id="noBtn" class="no-btn" onmouseover="moveNo()" onclick="moveNo()" ontouchstart="moveNo()">NO 🙄</button>`;
  } else {
    q.options.forEach(o => {
      const b = document.createElement("button");
      b.className = "option-btn";
      b.innerText = o;
      b.onclick = () => reveal(q.real);
      opt.appendChild(b);
    });
  }
}

function moveNo() {
  const btn = document.getElementById("noBtn");
  const x = Math.random() * 240 - 120;
  const y = Math.random() * 160 - 80;
  noScale = Math.max(0.3, noScale - 0.1); 
  btn.style.transform = `translate(${x}px, ${y}px) scale(${noScale})`;
}

function reveal(txt) {
  document.getElementById("options").innerHTML = `<p style="margin:20px 0; font-weight:bold;">${txt}</p><button onclick="next()">Next ❤️</button>`;
}

function next() {
  index++;
  burstHearts();
  if (index < questions.length) { showQuestion(); } 
  else { 
    document.getElementById("questionBox").classList.add("hidden");
    document.getElementById("final").classList.remove("hidden");
    initScratch();
  }
}

function initScratch() {
  const canvas = document.getElementById("scratchCanvas");
  const ctx = canvas.getContext("2d");
  ctx.fillStyle = "#C0C0C0"; 
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.fillStyle = "#ff4d94"; ctx.font = "bold 18px Arial";
  ctx.fillText("SCRATCH WITH LOVE 😘", 40, 80);

  let isDrawing = false;
  const scratch = (e) => {
    if (!isDrawing) return;
    const rect = canvas.getBoundingClientRect();
    const x = (e.clientX || e.touches[0].clientX) - rect.left;
    const y = (e.clientY || e.touches[0].clientY) - rect.top;
    ctx.globalCompositeOperation = 'destination-out';
    ctx.beginPath(); ctx.arc(x, y, 25, 0, Math.PI * 2); ctx.fill();
  };
  canvas.addEventListener("mousedown", () => isDrawing = true);
  canvas.addEventListener("mouseup", () => isDrawing = false);
  canvas.addEventListener("mousemove", scratch);
  canvas.addEventListener("touchstart", () => isDrawing = true);
  canvas.addEventListener("touchend", () => isDrawing = false);
  canvas.addEventListener("touchmove", scratch);
}

function burstHearts() {
  for(let i=0; i<6; i++) {
    const h = document.createElement("div");
    h.className = "heart-pop";
    h.innerHTML = ["❤️","🧿","😘","💍"][Math.floor(Math.random()*4)];
    h.style.left = Math.random() * 100 + "vw";
    h.style.top = "80vh";
    document.body.appendChild(h);
    setTimeout(() => h.remove(), 1500);
  }
}
</script>
</body>
</html>
