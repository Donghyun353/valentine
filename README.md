<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Valentine</title>
  <style>
    body{
      font-family: Arial, sans-serif;
      background:#ffe6ea;
      display:flex;
      align-items:center;
      justify-content:center;
      min-height:100vh;
      margin:0;
      overflow:hidden;
    }
    .card{
      background:#fff;
      width:min(540px, 92vw);
      padding:28px 22px;
      border-radius:18px;
      text-align:center;
      box-shadow:0 10px 30px rgba(0,0,0,.15);
      position:relative;
      z-index:2;
    }
    h1{ margin:0 0 10px; font-size:26px; line-height:1.25; }
    p{ margin:0 0 18px; color:#444; }
    .btns{
      display:flex;
      gap:12px;
      justify-content:center;
      align-items:center;
      flex-wrap:wrap;
      position:relative;
    }
    button{
      padding:12px 20px;
      font-size:16px;
      border:none;
      border-radius:12px;
      cursor:pointer;
      user-select:none;
      transition: transform .12s ease;
    }
    #yesBtn{ background:#ff4d6d; color:#fff; }
    #noBtn { background:#e9ecef; color:#111; }
    #message{
      margin-top:16px;
      font-size:18px;
      font-weight:700;
      min-height:24px;
    }
    .heart{
      position:fixed;
      font-size:22px;
      pointer-events:none;
      z-index:1;
      animation: floatUp 1.4s ease-out forwards;
      left:50%;
      top:55%;
      transform: translate(-50%, -50%);
    }
    @keyframes floatUp{
      0%   { opacity:0; transform: translate(-50%, -45%) scale(.7); }
      10%  { opacity:1; }
      100% { opacity:0; transform: translate(calc(-50% + var(--x)), calc(-50% - 260px)) scale(1.5); }
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>Will you be my Valentine,</h1>
    <h1>Hwiyoon my lovely baby princess? 💘</h1>
    <p>Choose wisely 😄</p>

    <div class="btns">
      <button id="yesBtn">Yes 💖</button>
      <button id="noBtn">No 🙈</button>
    </div>

    <div id="message"></div>
  </div>

  <script>
    const yesBtn = document.getElementById("yesBtn");
    const noBtn  = document.getElementById("noBtn");
    const msg    = document.getElementById("message");

    function popHearts(count = 22){
      for(let i=0; i<count; i++){
        const h = document.createElement("div");
        h.className = "heart";
        h.textContent = "💖";
        h.style.setProperty("--x", (Math.random()*360 - 180).toFixed(0) + "px");
        h.style.left = (50 + (Math.random()*18 - 9)) + "%";
        h.style.top  = (58 + (Math.random()*10 - 5)) + "%";
        document.body.appendChild(h);
        setTimeout(()=> h.remove(), 1500);
      }
    }

    yesBtn.addEventListener("click", () => {
      msg.textContent = "Yay!! I love you so much 💕";
      popHearts();
      yesBtn.style.transform = "scale(1.06)";
      setTimeout(()=> yesBtn.style.transform = "scale(1)", 150);
    });

    function moveNoButton(){
      const padding = 16;
      const rect = noBtn.getBoundingClientRect();
      const maxX = window.innerWidth  - rect.width  - padding;
      const maxY = window.innerHeight - rect.height - padding;
      const x = Math.max(padding, Math.random() * maxX);
      const y = Math.max(padding, Math.random() * maxY);
      noBtn.style.position = "fixed";
      noBtn.style.left = x + "px";
      noBtn.style.top  = y + "px";
    }

    noBtn.addEventListener("mouseenter", moveNoButton);
    noBtn.addEventListener("touchstart", (e)=>{ e.preventDefault(); moveNoButton(); }, {passive:false});
    noBtn.addEventListener("click", () => {
      msg.textContent = "Nice try 😘 (No is not available)";
      moveNoButton();
    });
  </script>
</body>
</html>
