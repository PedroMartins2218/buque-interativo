
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Um buquê (versão 2.0) 🌸</title>
  <meta name="description" content="Um mini-presente interativo — leve, fofo e sem pressão.">
  <style>
    :root{
      --bg:#fcfcfd;
      --card:#ffffff;
      --ink:#222;
      --muted:#6b7280;
      --accent:#e879f9;
      --accent-2:#a78bfa;
      --ring:rgba(167,139,250,.35);
      --shadow:0 8px 24px rgba(0,0,0,.08);
      --radius:16px;
    }
    * { box-sizing: border-box; }
    html, body { height: 100%; }
    body{
      margin:0;
      font-family: ui-sans-serif, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji";
      color:var(--ink);
      background: linear-gradient(180deg, #fff, var(--bg));
      display:grid;
      place-items:center;
      overflow-x:hidden;
    }
    main{
      width:min(680px, 92vw);
      background:var(--card);
      border-radius:var(--radius);
      padding:clamp(20px, 3vw, 32px);
      box-shadow:var(--shadow);
      position:relative;
      z-index:1;
      border:1px solid #eee;
    }
    h1{
      font-size:clamp(22px, 4.5vw, 32px);
      line-height:1.2;
      margin:0 0 8px;
    }
    p.lead{
      margin:0 0 20px;
      color:var(--muted);
      font-size:clamp(14px, 2.5vw, 16px);
    }
    .bouquet{
      display:grid;
      grid-template-columns: 88px 1fr;
      gap:18px;
      align-items:center;
      margin:18px 0 8px;
    }
    .emoji{
      font-size:64px;
      filter: drop-shadow(0 6px 14px rgba(0,0,0,.08));
      transform-origin:center;
      animation: float 4s ease-in-out infinite;
    }
    @keyframes float{
      0%,100%{ transform: translateY(0) rotate(0deg); }
      50%{ transform: translateY(-6px) rotate(-3deg); }
    }
    .card{
      background:#f9f5ff;
      border:1px solid #efe8ff;
      border-radius:12px;
      padding:14px 16px;
    }
    .options{
      display:grid;
      grid-template-columns: 1fr;
      gap:10px;
      margin-top:14px;
    }
    @media (min-width:540px){
      .options{ grid-template-columns: repeat(3, 1fr); }
    }
    button, a.button{
      appearance:none;
      border:none;
      border-radius:10px;
      padding:12px 14px;
      font-size:15px;
      background:linear-gradient(135deg, var(--accent), var(--accent-2));
      color:white;
      cursor:pointer;
      transition: transform .05s ease, box-shadow .2s ease, filter .2s ease;
      box-shadow: 0 8px 18px var(--ring);
      text-decoration:none;
      text-align:center;
      display:inline-block;
      outline-offset:3px;
    }
    button:hover, a.button:hover{ filter:saturate(1.05) brightness(1.02); }
    button:active, a.button:active{ transform: translateY(1px) scale(.998); }
    .ghost{
      background:#fff;
      color:var(--ink);
      border:1px solid #eee;
      box-shadow:none;
    }
    .tiny{
      font-size:12px;
      color:var(--muted);
      margin-top:8px;
    }
    .petal{
      position: fixed;
      top: -10vh;
      width: 14px;
      height: 14px;
      background: radial-gradient(circle at 30% 30%, #ffd6f2, #ff8bd9);
      border-radius: 60% 40% 65% 35% / 60% 35% 65% 40%;
      opacity:.7;
      animation: fall linear forwards;
      z-index:0;
      filter: blur(.2px);
    }
    @keyframes fall {
      to {
        transform: translate3d(var(--x-move), 110vh, 0) rotate(540deg);
        opacity:.9;
      }
    }
    .footer{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:8px;
      margin-top:18px;
    }
    .footer small{ color:var(--muted); }
    .switch{
      display:inline-flex; align-items:center; gap:8px;
      font-size:14px; color:var(--muted);
    }
    .switch input{ width: 40px; height: 22px; appearance: none; background:#e8e8ef; border-radius:999px; position:relative; outline:none; cursor:pointer; }
    .switch input::after{
      content:''; position:absolute; inset:3px;
      width:16px; height:16px; background:white; border-radius:50%;
      transform: translateX(0);
      transition: transform .2s ease, background .2s ease;
      box-shadow: 0 1px 3px rgba(0,0,0,.25);
    }
    .switch input:checked{ background:#d9d6ff; }
    .switch input:checked::after{ transform: translateX(18px); background:#fff; }
    .hidden{ display:none; }
  </style>
</head>
<body>
  <main role="main" aria-labelledby="titulo">
    <h1 id="titulo">Oi! Lembra das flores? 🌷</h1>
    <p class="lead">Fiz um mini-presente digital pra você — prometo que é leve, sem pressão, e com sorrisos inclusos.</p>

    <section class="bouquet" aria-label="Cartão com flores virtuais">
      <div class="emoji" aria-hidden="true">💐</div>
      <div class="card">
        <p style="margin:0 0 6px">Se você topa, eu queria <strong>te convidar</strong> para algo simples:</p>
        <ul style="margin:0 0 8px 18px; padding:0; color:#4b5563;">
          <li>play jump</li>
          <li>um jantar</li>
          <li>um treino (de sua preferência)</li>
        </ul>
        <p style="margin:0; color:#4b5563">Escolha um — e se preferir, tem a opção “só rir e continuar o papo”.</p>
      </div>
    </section>

    <div class="options" role="group" aria-label="Opções de encontro">
      <a class="button" href="#" data-choice="play jump">Play Jump 🤸🏻</a>
      <a class="button" href="#" data-choice="jantar">jantar 🍽️</a>
      <a class="button" href="#" data-choice="treino">Treino 🏋🏻‍♂️</a>
      <a class="button ghost" href="#" data-choice="conversar">Só conversar 😄</a>
      <a class="button ghost" href="#" data-choice="talvez">Talvez outro dia ✨</a>
      <a class="button ghost" href="#" data-choice="ideia">Tenho outra ideia 💡</a>
    </div>

    <div class="footer">
      <small>Sem cadastro, sem pegadinhas — só carinho em HTML + CSS.</small>
      <label class="switch" for="petals-toggle">
        <input id="petals-toggle" type="checkbox" aria-label="Ativar pétalas" checked />
        <span>Pétalas</span>
      </label>
    </div>

    <p class="tiny">Se clicar em alguma opção, abre um rascunho de mensagem (você revisa antes de enviar!).</p>
  </main>

  <script>
    // Falling petals (purely cosmetic)
    const MAX_PETALS = 24;
    const petalsToggle = document.querySelector('#petals-toggle');
    let petalsOn = true;

    function spawnPetal(){
      if(!petalsOn) return;
      const petal = document.createElement('div');
      petal.className = 'petal';
      const x = Math.random() * 100; // vw
      const duration = 9 + Math.random()*6;
      const delay = Math.random()*-8;
      const drift = (Math.random() * 40 - 20) + 'vw';
      petal.style.left = x + 'vw';
      petal.style.animationDuration = duration + 's';
      petal.style.animationDelay = delay + 's';
      petal.style.setProperty('--x-move', drift);
      document.body.appendChild(petal);
      setTimeout(()=>petal.remove(), (duration+2)*1000);
    }
    let petalInterval = setInterval(spawnPetal, 600);
    for(let i=0;i<12;i++) spawnPetal();

    petalsToggle.addEventListener('change', (e)=>{
      petalsOn = e.target.checked;
      if(petalsOn){
        petalInterval = setInterval(spawnPetal, 600);
      }else{
        clearInterval(petalInterval);
      }
    });

    // Smart WhatsApp links (no external libs)
    const btns = document.querySelectorAll('a.button');
    btns.forEach(btn=>{
      btn.addEventListener('click', (e)=>{
        e.preventDefault();
        const choice = btn.dataset.choice;
        const map = {
          "play jump": "Abriu um parque de trampolim incrível aqui em santos! que tal irmos esse fds?",
          "jantar": "Que tal um jantar gostoso e tranquilo? Conheço um lugar ótimo!",
          "treino": "Falamos tanto de treino... mas nunca marcamos um! Bora?",
          "conversar": "Só rir e continuar o papo é ótimo também!",
          "talvez": "Tudo bem, sem pressa! A gente se fala quando der.",
          "ideia": "Tô aberto a novas ideias! Qual seria o melhor mini- date pra gente?"
        };
        const msg = map[choice] || "Bora combinar algo simples e legal?";
        // Prefill WhatsApp without forcing a send
        const text = encodeURIComponent("\n\n" + msg);
        const wa = `https://wa.me/13991496607?text=${text}`;
        window.open(wa, '_blank', 'noopener');
      });
    });
  </script>
</body>
</html>
