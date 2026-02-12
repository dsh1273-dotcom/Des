<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>💘 For You</title>
  <style>
    :root{
      --bg1:#0b1026;
      --bg2:#240a2b;
      --accent:#ff4d8d;
      --accent2:#ffcc70;
      --text:#f7f7ff;
      --muted:rgba(247,247,255,.75);
      --card:rgba(255,255,255,.08);
      --stroke:rgba(255,255,255,.14);
      --shadow: 0 20px 60px rgba(0,0,0,.55);
      --glow: 0 0 25px rgba(255,77,141,.45), 0 0 60px rgba(255,204,112,.18);
      --radius: 26px;
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji";
      color:var(--text);
      overflow:hidden;
      background: radial-gradient(1200px 800px at 20% 15%, rgba(255,77,141,.22), transparent 55%),
                  radial-gradient(900px 700px at 80% 75%, rgba(255,204,112,.15), transparent 60%),
                  linear-gradient(135deg, var(--bg1), var(--bg2));
    }

    /* subtle moving grain */
    .grain{
      position:fixed; inset:-30%;
      background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='160' height='160'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='160' height='160' filter='url(%23n)' opacity='.35'/%3E%3C/svg%3E");
      mix-blend-mode:overlay;
      opacity:.14;
      pointer-events:none;
      animation: drift 14s linear infinite;
    }
    @keyframes drift{to{transform:translate3d(6%,4%,0)}}

    /* floating bokeh */
    .orb{
      position:absolute;
      border-radius:999px;
      filter: blur(6px);
      opacity:.18;
      animation: floaty 10s ease-in-out infinite;
      background: radial-gradient(circle at 30% 30%, rgba(255,255,255,.9), rgba(255,77,141,.65), transparent 70%);
    }
    .orb.o2{
      opacity:.14;
      background: radial-gradient(circle at 30% 30%, rgba(255,255,255,.85), rgba(255,204,112,.55), transparent 70%);
      animation-duration: 12s;
    }
    @keyframes floaty{
      0%,100%{transform:translateY(0) translateX(0) scale(1)}
      50%{transform:translateY(-18px) translateX(12px) scale(1.03)}
    }

    /* Layout */
    .wrap{
      position:relative;
      height:100%;
      display:grid;
      place-items:center;
      padding: 26px;
    }

    .card{
      width:min(980px, 94vw);
      min-height: min(620px, 86vh);
      background: linear-gradient(180deg, rgba(255,255,255,.10), rgba(255,255,255,.06));
      border:1px solid var(--stroke);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      backdrop-filter: blur(18px);
      -webkit-backdrop-filter: blur(18px);
      overflow:hidden;
      position:relative;
    }

    .header{
      padding: 26px 28px 0 28px;
      display:flex;
      justify-content:space-between;
      align-items:center;
      gap:12px;
    }

    .badge{
      display:inline-flex;
      align-items:center;
      gap:10px;
      padding:10px 14px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,.16);
      background: rgba(0,0,0,.18);
      color: var(--muted);
      font-size: 13px;
      letter-spacing:.2px;
    }
    .dot{
      width:10px;height:10px;border-radius:50%;
      background: radial-gradient(circle at 30% 30%, #fff, var(--accent));
      box-shadow: 0 0 12px rgba(255,77,141,.7);
    }

    .content{
      display:grid;
      grid-template-columns: 1.1fr .9fr;
      gap: 18px;
      padding: 18px 28px 28px 28px;
      height: calc(100% - 72px);
    }

    @media (max-width: 880px){
      body{overflow:auto}
      .wrap{height:auto; min-height:100%; padding:16px}
      .card{min-height:unset}
      .content{grid-template-columns: 1fr; height:auto}
    }

    .left{
      padding: 10px 6px 6px 6px;
    }

    h1{
      margin: 6px 0 10px 0;
      font-size: clamp(34px, 4.2vw, 54px);
      line-height:1.05;
      letter-spacing:-.6px;
      text-shadow: 0 10px 40px rgba(0,0,0,.45);
    }
    .grad{
      background: linear-gradient(90deg, #fff, var(--accent), var(--accent2));
      -webkit-background-clip:text;
      background-clip:text;
      color:transparent;
      filter: drop-shadow(0 0 18px rgba(255,77,141,.22));
    }
    .sub{
      margin: 0 0 18px 0;
      color: var(--muted);
      font-size: 16px;
      line-height: 1.6;
      max-width: 52ch;
    }

    .grid{
      display:grid;
      grid-template-columns: repeat(2, minmax(0,1fr));
      gap: 12px;
      margin-top: 16px;
    }
    @media (max-width: 520px){
      .grid{grid-template-columns:1fr}
    }

    .tile{
      background: rgba(255,255,255,.06);
      border:1px solid rgba(255,255,255,.14);
      border-radius: 18px;
      padding: 14px 14px;
      position:relative;
      overflow:hidden;
    }
    .tile:before{
      content:"";
      position:absolute; inset:-60%;
      background: radial-gradient(circle at 30% 30%, rgba(255,77,141,.22), transparent 60%),
                  radial-gradient(circle at 70% 70%, rgba(255,204,112,.18), transparent 60%);
      transform: rotate(25deg);
      opacity:.75;
    }
    .tile > *{position:relative}
    .tile h3{
      margin:0 0 6px 0;
      font-size: 14px;
      letter-spacing:.2px;
      color: rgba(255,255,255,.9);
      display:flex;
      gap:10px;
      align-items:center;
    }
    .tile p{
      margin:0;
      font-size: 13px;
      color: var(--muted);
      line-height:1.5;
    }
    .icon{
      width:26px;height:26px;border-radius:10px;
      display:grid;place-items:center;
      background: rgba(0,0,0,.22);
      border: 1px solid rgba(255,255,255,.14);
      box-shadow: 0 0 22px rgba(255,77,141,.12);
    }

    /* Right panel */
    .right{
      display:flex;
      flex-direction:column;
      gap: 12px;
    }

    .panel{
      background: rgba(0,0,0,.18);
      border:1px solid rgba(255,255,255,.14);
      border-radius: 22px;
      padding: 16px;
      box-shadow: 0 14px 40px rgba(0,0,0,.35);
      position:relative;
      overflow:hidden;
    }
    .panel:after{
      content:"";
      position:absolute; inset:-2px;
      border-radius: 22px;
      background: radial-gradient(800px 260px at 20% 0%, rgba(255,77,141,.18), transparent 55%),
                  radial-gradient(700px 250px at 80% 30%, rgba(255,204,112,.14), transparent 55%);
      pointer-events:none;
    }
    .panel > *{position:relative}

    .step{
      display:none;
      animation: pop .5s ease forwards;
    }
    .step.active{display:block}
    @keyframes pop{
      from{opacity:0; transform: translateY(10px) scale(.985)}
      to{opacity:1; transform: translateY(0) scale(1)}
    }

    .question{
      font-size: 18px;
      font-weight: 600;
      margin: 0 0 10px 0;
      letter-spacing: -.2px;
    }
    .hint{
      color: var(--muted);
      margin: 0 0 14px 0;
      font-size: 14px;
      line-height: 1.55;
    }

    .btnRow{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      align-items:center;
    }

    button{
      border:0;
      cursor:pointer;
      padding: 12px 14px;
      border-radius: 14px;
      font-weight: 650;
      letter-spacing:.15px;
      transition: transform .12s ease, filter .12s ease, box-shadow .12s ease, background .12s ease;
      user-select:none;
    }
    button:active{transform: translateY(1px) scale(.99)}
    .primary{
      color: #190011;
      background: linear-gradient(90deg, var(--accent), #ff6aa4, var(--accent2));
      box-shadow: var(--glow);
    }
    .primary:hover{filter:brightness(1.03)}
    .ghost{
      color: rgba(255,255,255,.9);
      background: rgba(255,255,255,.06);
      border:1px solid rgba(255,255,255,.16);
    }
    .ghost:hover{background: rgba(255,255,255,.09)}
    .tiny{
      padding: 10px 12px;
      border-radius: 12px;
      font-weight: 600;
    }

    .divider{
      height:1px;
      background: rgba(255,255,255,.12);
      margin: 14px 0;
    }

    .loveNote{
      font-size: 14px;
      line-height: 1.6;
      color: rgba(255,255,255,.88);
      margin: 0;
    }
    .sig{
      margin-top: 10px;
      color: var(--muted);
      font-size: 13px;
    }

    /* big final */
    .big{
      text-align:center;
      padding: 18px 10px 6px 10px;
    }
    .big .ask{
      font-size: clamp(26px, 3.2vw, 40px);
      margin: 6px 0 6px 0;
      letter-spacing:-.4px;
    }
    .big .spark{
      display:inline-block;
      padding: 10px 14px;
      border-radius: 999px;
      border:1px solid rgba(255,255,255,.16);
      background: rgba(0,0,0,.22);
      color: var(--muted);
      font-size: 13px;
    }

    /* confetti hearts */
    canvas{
      position:fixed;
      inset:0;
      pointer-events:none;
    }

    /* small footer */
    .footer{
      position:absolute;
      left: 22px; bottom: 16px;
      color: rgba(255,255,255,.55);
      font-size: 12px;
      letter-spacing:.2px;
    }
  </style>
</head>

<body>
  <div class="grain"></div>
  <canvas id="fx"></canvas>

  <!-- background orbs -->
  <div class="orb" style="width:220px;height:220px; left:-40px; top:80px;"></div>
  <div class="orb o2" style="width:260px;height:260px; right:-70px; top:40px;"></div>
  <div class="orb" style="width:180px;height:180px; right:120px; bottom:40px; animation-duration: 11s;"></div>

  <div class="wrap">
    <div class="card">
      <div class="header">
        <div class="badge"><span class="dot"></span> A little page made just for you</div>
        <div class="badge" id="today"></div>
      </div>

      <div class="content">
        <!-- LEFT -->
        <section class="left">
          <h1>
            Hey <span class="grad" id="herName">Destiny</span> 💘<br/>
            I have something to ask you…
          </h1>
          <p class="sub">
            I wanted to do this in a way that feels special — because you are.
            So I made a tiny experience just for us. Ready?
          </p>

          <div class="grid">
            <div class="tile">
              <h3><span class="icon">✨</span> Why you</h3>
              <p id="reason1">You make ordinary days feel like something I actually look forward to.</p>
            </div>
            <div class="tile">
              <h3><span class="icon">🫶</span> My favorite thing</h3>
              <p id="reason2">The way you care about your goals and still make time for the people you love inspires me.</p>
            </div>
            <div class="tile">
              <h3><span class="icon">📍</span> Our vibe</h3>
              <p id="reason3">I can be completely myself around you, and that’s the best feeling in the world.</p>
            </div>
            <div class="tile">
              <h3><span class="icon">🌹</span> Today’s mission</h3>
              <p>Make you smile… and ask you a very important question 😌</p>
            </div>
          </div>

          <div class="footer">Tip: edit the text in the HTML to personalize it ✍️</div>
        </section>

        <!-- RIGHT -->
        <aside class="right">
          <div class="panel">
            <!-- Step 1 -->
            <div class="step active" data-step="1">
              <p class="question">Quick warm-up 🥰</p>
              <p class="hint">Before the question… choose the option that describes us best.</p>
              <div class="btnRow">
                <button class="ghost tiny" onclick="pick('Soulmates 💫')">Soulmates 💫</button>
                <button class="ghost tiny" onclick="pick('The Power Couple 🫂 ')">The Power Couple 🫂 </button>
                <button class="ghost tiny" onclick="pick('The cutest duo 🤍')">The cutest duo 🤍</button>
              </div>
              <div class="divider"></div>
              <button class="primary" onclick="nextStep()">Continue</button>
            </div>

            <!-- Step 2 -->
            <div class="step" data-step="2">
              <p class="question">One more thing…</p>
              <p class="hint">Tap the button to reveal a note I wrote for you.</p>
              <div class="btnRow">
                <button class="primary" onclick="revealNote()">Reveal note 💌</button>
                <button class="ghost" onclick="nextStep()">Skip</button>
              </div>
              <div class="divider"></div>
              <p class="loveNote" id="note" style="display:none;">
                Destiny, I’m really grateful for you. You bring peace, laughter, and motivation into my life in a way nobody else does.
                I love spending time with you, growing with you, and making memories with you. 🤍
              </p>
              <p class="sig" id="sig" style="display:none;">— Love, Dillon</p>
            </div>

            <!-- Step 3 -->
            <div class="step" data-step="3">
              <div class="big">
                <div class="spark" id="picked">✨</div>
                <p class="ask"><span class="grad">Will you be my Valentine?</span> 💘</p>
                <p class="hint">Choose wisely 😌</p>
                <div class="btnRow" style="justify-content:center">
                  <button class="primary" onclick="sayYes()">YES 💖</button>
                  <button class="ghost" id="noBtn" onclick="nope()">No 😭</button>
                </div>
              </div>
            </div>

            <!-- Step 4 -->
            <div class="step" data-step="4">
              <div class="big">
                <p class="ask">AYEEE THAT’S MY VALENTINE 💞</p>
                <p class="hint" id="finalLine">
                  Now come here so I can give you the biggest hug, Destiny 💞
                </p>
                <div class="btnRow" style="justify-content:center">
                  <button class="primary" onclick="burst()">Celebrate 🎉</button>
                  <button class="ghost" onclick="resetAll()">Replay 🔁</button>
                </div>
              </div>
            </div>

          </div>

          <div class="panel">
            <p class="question" style="margin-bottom:8px;">Personalize it (optional)</p>
            <p class="hint" style="margin-top:0">
              Type her name + 3 short reasons. It updates instantly.
            </p>

            <div style="display:grid; gap:10px;">
              <input id="nameInput" placeholder="Her name (e.g., Destiny)" style="padding:12px 12px;border-radius:14px;border:1px solid rgba(255,255,255,.16);background:rgba(0,0,0,.22);color:var(--text);outline:none;">
              <input id="r1" placeholder="Reason #1" style="padding:12px 12px;border-radius:14px;border:1px solid rgba(255,255,255,.16);background:rgba(0,0,0,.22);color:var(--text);outline:none;">
              <input id="r2" placeholder="Reason #2" style="padding:12px 12px;border-radius:14px;border:1px solid rgba(255,255,255,.16);background:rgba(0,0,0,.22);color:var(--text);outline:none;">
              <input id="r3" placeholder="Reason #3" style="padding:12px 12px;border-radius:14px;border:1px solid rgba(255,255,255,.16);background:rgba(0,0,0,.22);color:var(--text);outline:none;">
              <button class="ghost" onclick="applyCustom()">Apply ✍️</button>
            </div>
          </div>
        </aside>
      </div>
    </div>
  </div>

  <script>
    // ===== Date badge =====
    const todayEl = document.getElementById("today");
    const now = new Date();
    const opts = { weekday:"long", month:"short", day:"numeric" };
    todayEl.textContent = now.toLocaleDateString(undefined, opts);

    // ===== Steps =====
    let step = 1;
    const steps = [...document.querySelectorAll(".step")];
    function showStep(n){
      step = n;
      steps.forEach(s => s.classList.toggle("active", Number(s.dataset.step) === n));
    }
    function nextStep(){
      showStep(Math.min(step + 1, 4));
    }

    // ===== Pick line =====
    const pickedEl = document.getElementById("picked");
    function pick(text){
      pickedEl.textContent = "✨ " + text;
      // tiny sparkle
      burst(18, true);
    }

    // ===== Note =====
    function revealNote(){
      document.getElementById("note").style.display = "block";
      document.getElementById("sig").style.display = "block";
      burst(30, true);
    }

    // ===== NO button dodges =====
    const noBtn = document.getElementById("noBtn");
    let dodges = 0;
    function nope(){
      dodges++;
      const maxX = Math.max(0, window.innerWidth - noBtn.offsetWidth - 40);
      const maxY = Math.max(0, window.innerHeight - noBtn.offsetHeight - 40);
      const x = Math.floor(Math.random() * maxX);
      const y = Math.floor(Math.random() * maxY);

      noBtn.style.position = "fixed";
      noBtn.style.left = x + "px";
      noBtn.style.top  = y + "px";

      if(dodges >= 5){
        noBtn.textContent = "Okay fine 😭";
      }
      burst(10, true);
    }

    function sayYes(){
      showStep(4);
      burst(120);
      // gentle pulse on background
      document.body.animate(
        [{filter:"brightness(1)"},{filter:"brightness(1.06)"},{filter:"brightness(1)"}],
        {duration:900, easing:"ease-in-out"}
      );
    }

    function resetAll(){
      dodges = 0;
      noBtn.textContent = "No 😭";
      noBtn.style.position = "";
      noBtn.style.left = "";
      noBtn.style.top  = "";
      document.getElementById("note").style.display = "none";
      document.getElementById("sig").style.display = "none";
      pickedEl.textContent = "✨";
      showStep(1);
    }

    // ===== Personalization =====
    const herName = document.getElementById("herName");
    const reason1 = document.getElementById("reason1");
    const reason2 = document.getElementById("reason2");
    const reason3 = document.getElementById("reason3");

    function applyCustom(){
      const n = document.getElementById("nameInput").value.trim();
      const a = document.getElementById("r1").value.trim();
      const b = document.getElementById("r2").value.trim();
      const c = document.getElementById("r3").value.trim();

      if(n) herName.textContent = n;
      if(a) reason1.textContent = a;
      if(b) reason2.textContent = b;
      if(c) reason3.textContent = c;

      burst(40, true);
    }

    // ===== Hearts/Confetti Canvas =====
    const canvas = document.getElementById("fx");
    const ctx = canvas.getContext("2d");
    let W, H;
    function resize(){
      W = canvas.width = window.innerWidth * devicePixelRatio;
      H = canvas.height = window.innerHeight * devicePixelRatio;
      canvas.style.width = window.innerWidth + "px";
      canvas.style.height = window.innerHeight + "px";
    }
    window.addEventListener("resize", resize);
    resize();

    const particles = [];
    function heartPath(x, y, s){
      ctx.save();
      ctx.translate(x, y);
      ctx.scale(s, s);
      ctx.beginPath();
      ctx.moveTo(0, -2.2);
      ctx.bezierCurveTo(2.2, -4.8, 6.2, -3.2, 6.2, 0.8);
      ctx.bezierCurveTo(6.2, 3.6, 3.2, 5.6, 0, 7.4);
      ctx.bezierCurveTo(-3.2, 5.6, -6.2, 3.6, -6.2, 0.8);
      ctx.bezierCurveTo(-6.2, -3.2, -2.2, -4.8, 0, -2.2);
      ctx.closePath();
      ctx.restore();
    }

    function burst(count=80, subtle=false){
      for(let i=0;i<count;i++){
        const angle = Math.random()*Math.PI*2;
        const speed = (subtle? 2.2 : 4.2) + Math.random()*(subtle? 2.2 : 5.5);
        particles.push({
          x: (window.innerWidth/2) * devicePixelRatio,
          y: (window.innerHeight/2) * devicePixelRatio,
          vx: Math.cos(angle)*speed*devicePixelRatio,
          vy: Math.sin(angle)*speed*devicePixelRatio - (subtle? 1.5: 3.5)*devicePixelRatio,
          g: (subtle? 0.10: 0.14)*devicePixelRatio,
          life: 70 + Math.random()*40,
          size: (subtle? 0.9: 1.2) + Math.random()*1.2,
          rot: Math.random()*Math.PI*2,
          vr: (Math.random()-.5)*0.18,
          t: Math.random(),
        });
      }
    }

    function loop(){
      ctx.clearRect(0,0,W,H);

      for(let i=particles.length-1; i>=0; i--){
        const p = particles[i];
        p.vy += p.g;
        p.x += p.vx;
        p.y += p.vy;
        p.rot += p.vr;
        p.life -= 1;

        const alpha = Math.max(0, Math.min(1, p.life/90));
        ctx.save();
        ctx.globalAlpha = alpha;
        ctx.translate(p.x, p.y);
        ctx.rotate(p.rot);

        // gradient fill
        const grd = ctx.createRadialGradient(0,0,1*devicePixelRatio, 0,0,10*devicePixelRatio);
        grd.addColorStop(0, "rgba(255,255,255,.95)");
        grd.addColorStop(0.35, "rgba(255,77,141,.92)");
        grd.addColorStop(1, "rgba(255,204,112,.0)");
        ctx.fillStyle = grd;

        heartPath(0,0, p.size*devicePixelRatio);
        ctx.fill();
        ctx.restore();

        if(p.life <= 0) particles.splice(i,1);
      }

      requestAnimationFrame(loop);
    }
    loop();

    // first sparkle
    setTimeout(()=>burst(40,true), 650);
  </script>
</body>
</html>
