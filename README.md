
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#000000">
<title>LOVE.exe — Only Yours</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Special+Elite&family=Share+Tech+Mono&display=swap');

:root{
 --black:#000;--dark:#090909;--gray:#292929;
 --white:#e8e5e5;--red:#8b001b;--wine:#42000e;
 --mono:'Share Tech Mono',monospace;
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{
 margin:0;background:#000;color:var(--white);
 font-family:var(--mono);font-size:14px;overflow-x:hidden;
 background-image:repeating-linear-gradient(0deg,transparent 0 3px,#ffffff05 4px);
}
body:before{
 content:"";position:fixed;inset:0;pointer-events:none;z-index:20;
 background:repeating-linear-gradient(0deg,#0000 0 3px,#0008 4px);
 opacity:.27;
}
::selection{background:#8b001b;color:white}
button{font:inherit;cursor:pointer}
a{color:#c6a9af}
header{
 display:flex;align-items:center;justify-content:space-between;
 gap:12px;padding:12px 5%;border-bottom:1px solid #383838;
 background:#050505;
}
.logo{color:#c3c3c3;letter-spacing:3px;font-size:15px}
.logo b{color:#9c1734}
.status{font-size:11px;color:#777}
.status i{display:inline-block;width:6px;height:6px;
 background:#9c1734;border-radius:50%;margin-right:6px;
 box-shadow:0 0 8px #a00;animation:blink 1.5s infinite}
main{width:min(950px,94%);margin:auto}
.hero{text-align:center;padding:30px 0 18px}
.eyebrow{font-size:10px;letter-spacing:4px;color:#8e2339}
h1{font-family:'Special Elite',var(--mono);font-size:clamp(27px,6vw,46px);
 font-weight:400;letter-spacing:2px;margin:13px 0;color:#eee;
 text-shadow:2px 2px #50000c}
h1 span{color:#94001d}
.subtitle{font-size:11px;letter-spacing:2px;color:#666}
.desktop-window{
 border:1px solid #484848;background:#080808;
 box-shadow:0 0 25px #000,0 0 40px #25000830;
 margin:22px auto;position:relative;
}
.titlebar{
 display:flex;align-items:center;justify-content:space-between;
 background:#191919;border-bottom:1px solid #444;
 padding:8px 10px;font-size:11px;color:#aaa;gap:8px;
}
.window-controls{display:flex;gap:5px}
.window-controls span{width:12px;height:12px;border:1px solid #555;
 display:block;background:#222}
.window-controls span:last-child{background:#510014}
.inner{padding:20px}
.character-area{
 min-height:290px;display:flex;justify-content:center;
 align-items:center;position:relative;overflow:hidden;
 background:radial-gradient(ellipse,#181818 0%,#080808 45%,#020202 80%);
 border:1px solid #242424;
}
.character-area:after{
 content:"";position:absolute;inset:0;pointer-events:none;
 background:repeating-linear-gradient(90deg,transparent 0 65px,#fff04 66px);
 opacity:.3;
}
.crosshair{position:absolute;color:#4b151e;font-size:22px}
.crosshair.one{top:15px;left:18px}
.crosshair.two{right:18px;bottom:12px}
#character{
 width:190px;height:260px;position:relative;z-index:1;
 cursor:pointer;touch-action:manipulation;
 transition:transform .3s;filter:drop-shadow(0 0 16px #48000d45);
}
#character:hover{transform:translateY(-3px)}
.hair-back{
 position:absolute;top:18px;left:15px;width:160px;height:202px;
 background:linear-gradient(90deg,#050505,#242424 48%,#050505);
 border-radius:48% 48% 24% 24%;
 box-shadow:inset 0 0 0 1px #393939;
}
.neck{position:absolute;top:168px;left:76px;width:38px;height:48px;
 background:#777;border:2px solid #292929}
.shoulders{
 position:absolute;bottom:0;left:18px;width:154px;height:70px;
 background:linear-gradient(100deg,#090909,#292929,#080808);
 border-radius:55% 55% 4px 4px;border:1px solid #353535;
}
.face{
 position:absolute;top:48px;left:32px;width:126px;height:143px;
 background:linear-gradient(110deg,#5b5b5b,#aaa 45%,#444);
 border:2px solid #292929;border-radius:45% 45% 47% 47%;
 clip-path:polygon(0 0,100% 0,100% 72%,80% 91%,50% 100%,20% 91%,0 72%);
}
.fringe{
 position:absolute;z-index:4;top:17px;left:25px;width:143px;height:86px;
 background:linear-gradient(110deg,#080808,#202020 50%,#050505);
 clip-path:polygon(0 0,100% 0,96% 65%,78% 45%,70% 92%,
 56% 56%,44% 100%,30% 60%,16% 79%,8% 53%,0 75%);
 filter:drop-shadow(0 3px 2px #000);
}
.ear{position:absolute;top:105px;width:15px;height:27px;
 background:#777;border:2px solid #333;border-radius:50%}
.ear.left{left:25px}.ear.right{right:25px}
.eye-row{
 position:absolute;top:102px;left:43px;z-index:5;
 display:flex;gap:17px;
}
.eye{
 width:39px;height:29px;background:#e9e9e9;
 border:2px solid #090909;border-radius:48% 48% 42% 42%;
 overflow:hidden;position:relative;
 clip-path:polygon(0 0,100% 0,90% 80%,50% 100%,10% 80%);
}
.pupil{
 width:15px;height:20px;background:#080808;border-radius:50%;
 position:absolute;left:10px;top:4px;transition:transform .05s;
 box-shadow:0 0 0 2px #777;
}
.pupil:after{
 content:"";position:absolute;top:3px;left:4px;width:4px;height:5px;
 background:white;border-radius:50%;
}
.brow{
 position:absolute;top:94px;width:38px;height:4px;
 background:#101010;z-index:5;
}
.brow.left{left:44px;transform:rotate(-7deg)}
.brow.right{right:44px;transform:rotate(7deg)}
.nose{
 position:absolute;z-index:5;top:133px;left:91px;
 width:8px;height:13px;border-right:1px solid #444;
 transform:rotate(8deg);
}
.mouth{
 position:absolute;z-index:5;top:156px;left:82px;width:24px;height:8px;
 border-bottom:2px solid #30000b;border-radius:50%;
}
.blush{
 position:absolute;z-index:6;top:137px;width:25px;height:10px;
 background:repeating-linear-gradient(110deg,#8b001b 0 2px,transparent 2px 5px);
 opacity:0;transition:opacity .2s;
}
.blush.left{left:43px}.blush.right{right:43px}
#character.blushing .blush{opacity:.9}
#character.blushing .mouth{border-bottom:3px solid #79001a}
#character.sad .eye{height:23px}
#character.sad .brow{background:#90001d;transform:rotate(15deg)}
#character.sad .mouth{border-bottom:0;border-top:2px solid #40000d;
 border-radius:50% 50% 0 0}
.character-caption{position:absolute;bottom:9px;font-size:9px;
 color:#555;letter-spacing:2px;z-index:2}
.dialogue{
 margin-top:14px;padding:16px 12px;border:1px solid #373737;
 background:#030303;min-height:82px;text-align:center;
 display:flex;flex-direction:column;justify-content:center;gap:8px;
}
.dialogue-label{font-size:9px;color:#8d243b;letter-spacing:3px}
#dialogueText{font-family:'Special Elite',var(--mono);font-size:17px;
 color:#ddd;transition:opacity .3s}
.dialogue-footer{font-size:9px;color:#555}
.controls-row{display:flex;justify-content:center;gap:8px;
 flex-wrap:wrap;margin-top:14px}
.retro-btn{
 border:1px solid #555;background:#111;color:#ccc;
 padding:10px 14px;font-size:11px;transition:.2s;
}
.retro-btn:hover{border-color:#a00022;color:white;background:#24000a}
.section-heading{font-size:18px;font-weight:normal;letter-spacing:2px;
 font-family:'Special Elite',var(--mono)}
.section-heading span{color:#a00024}
.section-sub{font-size:11px;color:#777;line-height:1.7}
.game-window{margin:25px auto}
.game-info{display:flex;align-items:center;justify-content:space-between;
 flex-wrap:wrap;gap:10px;padding:12px;border-bottom:1px solid #292929}
.score{font-size:12px;color:#aaa}
.score strong{font-size:20px;color:#eee}
.score strong span{color:#9d0022}
#gameState{color:#777;font-size:10px}
#game{
 height:350px;position:relative;overflow:hidden;
 background:radial-gradient(ellipse at center,#10080a,#030303 75%);
 border:1px solid #292929;touch-action:manipulation;
}
#game:before{
 content:"";position:absolute;inset:0;pointer-events:none;
 background-image:linear-gradient(#ffffff08 1px,transparent 1px),
 linear-gradient(90deg,#ffffff08 1px,transparent 1px);
 background-size:24px 24px;
}
.game-target{
 position:absolute;z-index:2;border:1px solid #555;
 background:#090909;width:42px;height:42px;
 display:flex;align-items:center;justify-content:center;
 font-size:25px;cursor:pointer;user-select:none;
 touch-action:manipulation;animation:appear .15s;
}
.game-target.heart{color:#ddd;text-shadow:0 0 10px #800019}
.game-target.eye-target{color:#eee}
.game-target.danger{color:#a00024;border-color:#5b0014}
.game-target:active{transform:scale(.8)}
.game-target:hover{border-color:#a00024}
#gameOverlay{
 position:absolute;inset:0;z-index:5;background:#050000eF;
 display:none;flex-direction:column;align-items:center;
 justify-content:center;text-align:center;padding:20px;
}
#gameOverlay.show{display:flex}
#overlayTitle{font-family:'Special Elite',var(--mono);
 font-size:clamp(25px,6vw,42px);color:#d0002b;
 animation:blink .65s steps(2,end) infinite;
 text-shadow:0 0 15px #78001b;margin:10px 0}
#overlayText{font-size:11px;color:#aaa;line-height:1.8;max-width:350px}
#restartBtn{margin-top:18px;max-width:100%;
 animation:pulse 2s infinite}
.floating-heart{
 position:absolute;z-index:10;pointer-events:none;
 font-size:22px;animation:floatUp 1.2s ease-out forwards;
 color:#080808;text-shadow:0 0 5px #9d001e;
}
#flash{position:fixed;inset:0;background:#8b001b;z-index:30;
 pointer-events:none;opacity:0}
#flash.active{animation:glitch .32s steps(2,end)}
.game-help{padding:12px;font-size:10px;color:#666;line-height:1.8}
.warning{color:#851329}
footer{margin-top:30px;border-top:1px solid #292929;
 padding:20px 10px;text-align:center;font-size:10px;
 color:#555;line-height:2}
footer span{color:#842038}
.glitch{animation:glitch .2s steps(2,end)}
@keyframes blink{50%{opacity:.35}}
@keyframes pulse{50%{box-shadow:0 0 14px #640016}}
@keyframes appear{from{transform:scale(.5)}to{transform:scale(1)}}
@keyframes floatUp{
 0%{transform:translateY(0) scale(.8);opacity:1}
 100%{transform:translateY(-100px) scale(1.4);opacity:0}
}
@keyframes glitch{
 0%{opacity:0;transform:translateX(0)}
 20%{opacity:.6;transform:translateX(-4px)}
 40%{opacity:.2;transform:translateX(4px)}
 60%{opacity:.7;transform:translateX(-2px)}
 100%{opacity:0;transform:translateX(0)}
}
@media(max-width:500px){
 header{padding:11px 4%}.logo{font-size:12px;letter-spacing:1px}
 .status{font-size:9px}.inner{padding:11px}
 .character-area{min-height:270px}
 #character{transform:scale(.9)}
 #character:hover{transform:scale(.9)}
 .dialogue{padding:13px 8px}
 #dialogueText{font-size:15px}
 #game{height:330px}
 .game-target{width:44px;height:44px}
 .section-heading{font-size:16px}
}
@media(prefers-reduced-motion:reduce){
 *,*:before,*:after{animation-duration:.01ms!important;
 animation-iteration-count:1!important;scroll-behavior:auto!important}
}
</style>
</head>
<body>
<div id="flash"></div>

<header>
 <div class="logo">LOVE<span style="color:#a00024">.exe</span></div>
 <div class="status"><i></i>SYSTEM ONLINE</div>
 <div class="status">v. 00.13.666</div>
</header>

<main>
 <section class="hero">
  <div class="eyebrow">[ PERSONAL FILE // 001 ]</div>
  <h1>ONLY <span>YOURS</span></h1>
  <div class="subtitle">WELCOME TO MY LITTLE WORLD.</div>
 </section>

 <section class="desktop-window">
  <div class="titlebar">
   <span>♥ CHARACTER.exe — [ ONLINE ]</span>
   <div class="window-controls"><span></span><span></span><span></span></div>
  </div>
  <div class="inner">
   <div class="character-area" id="characterArea">
    <span class="crosshair one">†</span>
    <span class="crosshair two">✕</span>

    <div id="character" role="button" tabindex="0"
         aria-label="Interactuar con el personaje">
     <div class="hair-back"></div>
     <div class="shoulders"></div>
     <div class="neck"></div>
     <div class="ear left"></div>
     <div class="ear right"></div>
     <div class="face"></div>
     <div class="fringe"></div>
     <div class="brow left"></div>
     <div class="brow right"></div>
     <div class="eye-row">
      <div class="eye"><div class="pupil"></div></div>
      <div class="eye"><div class="pupil"></div></div>
     </div>
     <div class="nose"></div>
     <div class="mouth"></div>
     <div class="blush left"></div>
     <div class="blush right"></div>
    </div>
    <div class="character-caption">DON'T LOOK AWAY.</div>
   </div>

   <div class="dialogue">
    <div class="dialogue-label">♥ INCOMING MESSAGE ♥</div>
    <div id="dialogueText" aria-live="polite">Te estaba esperando...</div>
    <div class="dialogue-footer">FROM: YOUR SECRET ADMIRER // 00:00:00</div>
   </div>

   <div class="controls-row">
    <button class="retro-btn" id="talkBtn">[ TALK TO ME ]</button>
    <button class="retro-btn" id="affectionBtn">[ TOUCH MY FACE ♥ ]</button>
   </div>
  </div>
 </section>

 <section>
  <h2 class="section-heading">01 // <span>DON'T IGNORE ME</span></h2>
  <p class="section-sub">
   Mis ojos siempre te encuentran. Mueve el cursor o desliza el dedo
   por la pantalla. Toca mi rostro para descubrir qué ocurre.
  </p>
 </section>

 <section class="desktop-window game-window">
  <div class="titlebar">
   <span>GAME.exe — ATRAPA MI CORAZÓN OBSESIVO</span>
   <div class="window-controls"><span></span><span></span><span></span></div>
  </div>
  <div class="game-info">
   <div class="score">SCORE: <strong><span id="score">0</span></strong></div>
   <div class="score">MISSED: <strong id="missed">0</strong> / 3</div>
   <div id="gameState">● READY?</div>
  </div>

  <div id="game" aria-label="Zona del minijuego">
   <div id="gameOverlay" role="dialog" aria-live="assertive">
    <div class="eyebrow">[ CONNECTION LOST ]</div>
    <div id="overlayTitle">¿POR QUÉ ME IGNORAS?</div>
    <div id="overlayText">
     Me dejaste esperando... ¿De verdad pensabas que iba a olvidarlo?
    </div>
    <button class="retro-btn" id="restartBtn">
     Vuelve a intentarlo, no tienes opción ♥
    </button>
   </div>
  </div>

  <div class="game-help">
   <span class="warning">♥ CORAZONES / ◉ OJOS:</span> +10 PTS por cada acierto.<br>
   <span class="warning">♟ CRIATURAS:</span> −20 PTS si las tocas.<br>
   Si dejas escapar 3 corazones, la partida se detiene.
  </div>
  <div class="controls-row" style="padding:0 10px 15px">
   <button class="retro-btn" id="startBtn">[ START GAME ]</button>
   <button class="retro-btn" id="resetBtn">[ RESET SCORE ]</button>
  </div>
 </section>

 <footer>
  <div>♥ MADE WITH <span>OBSESSION</span> ♥</div>
  <div>YOU ARE VISITOR NO. <span id="visitor">000013</span></div>
  <div>© LOVE.exe — YOUR LITTLE DARK CORNER OF THE INTERNET</div>
 </footer>
</main>

<script>
(() => {
 "use strict";

 // ====== PERSONAJE Y SEGUIMIENTO OCULAR ======
 const character = document.getElementById("character");
 const characterArea = document.getElementById("characterArea");
 const pupils = [...document.querySelectorAll(".pupil")];
 const dialogueText = document.getElementById("dialogueText");

 const phrases = [
  "Te amo demasiado...",
  "Eres mi pequeño secreto favorito. ♥",
  "Te pertenezco en cada vida.",
  "No quiero que olvides mi nombre.",
  "Siempre encuentro el camino hacia ti.",
  "¿Me regalarías un poquito de tu atención?",
  "Quédate un ratito más conmigo...",
  "Tu presencia hace que mi mundo exista.",
  "Tengo tantas cosas que decirte...",
  "No apartes la mirada todavía. ♥",
  "Incluso el silencio me recuerda a ti.",
  "Volvería a encontrarte mil veces."
 ];
 let phraseIndex = 0;
 let phraseTimer;
 let blushTimer;

 function nextPhrase(){
  dialogueText.style.opacity = "0";
  setTimeout(() => {
   phraseIndex = (phraseIndex + 1) % phrases.length;
   dialogueText.textContent = phrases[phraseIndex];
   dialogueText.style.opacity = "1";
  }, 250);
 }

 function setRandomPhrase(){
  let next;
  do {
   next = Math.floor(Math.random() * phrases.length);
  } while(phrases.length > 1 && next === phraseIndex);
  phraseIndex = next;
  dialogueText.textContent = phrases[phraseIndex];
  dialogueText.style.opacity = "1";
 }

 function startPhraseTimer(){
  clearInterval(phraseTimer);
  phraseTimer = setInterval(setRandomPhrase, 5000);
 }

 function trackEyes(x, y){
  pupils.forEach(pupil => {
   const eye = pupil.parentElement.getBoundingClientRect();
   const cx = eye.left + eye.width / 2;
   const cy = eye.top + eye.height / 2;
   const angle = Math.atan2(y - cy, x - cx);
   const distance = Math.min(7, Math.hypot(x - cx, y - cy) / 15);
   pupil.style.transform =
    `translate(${Math.cos(angle)*distance}px,${Math.sin(angle)*distance}px)`;
  });
 }

 document.addEventListener("pointermove", e => {
  trackEyes(e.clientX, e.clientY);
 }, {passive:true});

 function heartBurst(x, y){
  for(let i=0; i<9; i++){
   const heart = document.createElement("span");
   heart.className = "floating-heart";
   heart.textContent = Math.random() > .25 ? "♥" : "♡";
   heart.style.left = (x + (Math.random()-.5)*90) + "px";
   heart.style.top = (y + (Math.random()-.5)*35) + "px";
   heart.style.fontSize = (14 + Math.random()*18) + "px";
   heart.style.animationDuration = (.8 + Math.random()*.7) + "s";
   document.body.appendChild(heart);
   heart.addEventListener("animationend", () => heart.remove());
  }
 }

 function touchFace(){
  character.classList.remove("sad");
  character.classList.add("blushing");
  const rect = character.getBoundingClientRect();
  heartBurst(rect.left + rect.width/2, rect.top + rect.height/2);
  dialogueText.textContent = "¿Me estás acariciando...? ♥";
  dialogueText.style.opacity = "1";
  clearTimeout(blushTimer);
  blushTimer = setTimeout(() => {
   character.classList.remove("blushing");
   nextPhrase();
  }, 2200);
 }

 character.addEventListener("click", touchFace);
 character.addEventListener("keydown", e => {
  if(e.key === "Enter" || e.key === " "){
   e.preventDefault();
   touchFace();
  }
 });
 document.getElementById("affectionBtn").addEventListener("click", touchFace);
 document.getElementById("talkBtn").addEventListener("click", () => {
  setRandomPhrase();
  startPhraseTimer();
 });

 startPhraseTimer();

 // ====== MINIJUEGO ======
 const game = document.getElementById("game");
 const scoreEl = document.getElementById("score");
 const missedEl = document.getElementById("missed");
 const gameState = document.getElementById("gameState");
 const overlay = document.getElementById("gameOverlay");
 const overlayTitle = document.getElementById("overlayTitle");
 const overlayText = document.getElementById("overlayText");
 const flash = document.getElementById("flash");

 let score = 0;
 let missed = 0;
 let running = false;
 let targets = [];
 let spawnTimer = null;
 let animationFrame = null;
 let lastTime = 0;
 let spawnElapsed = 0;
 let speed = 1;

 function updateScore(){
  scoreEl.textContent = score;
  missedEl.textContent = missed;
 }

 function clearTargets(){
  targets.forEach(t => t.el.remove());
  targets = [];
 }

 function showFlash(){
  flash.classList.remove("active");
  void flash.offsetWidth;
  flash.classList.add("active");
  document.body.classList.remove("glitch");
  void document.body.offsetWidth;
  document.body.classList.add("glitch");
  setTimeout(() => document.body.classList.remove("glitch"), 250);
 }

 function stopGame(){
  running = false;
  clearInterval(spawnTimer);
  cancelAnimationFrame(animationFrame);
  spawnTimer = null;
  animationFrame = null;
  clearTargets();
 }

 function endGame(){
  stopGame();
  character.classList.remove("blushing");
  character.classList.add("sad");
  overlayTitle.textContent = "¿POR QUÉ ME IGNORAS?";
  overlayText.textContent =
   "Me dejaste esperando... ¿De verdad pensabas que iba a olvidarlo? " +
   "Tu partida no ha terminado para siempre. Inténtalo otra vez.";
  overlay.classList.add("show");
  gameState.textContent = "● CONNECTION LOST";
  showFlash();
 }

 function spawnTarget(){
  if(!running) return;

  const el = document.createElement("button");
  el.type = "button";
  el.className = "game-target";

  // Los corazones y ojos dan puntos; las criaturas restan.
  const danger = Math.random() < .23;
  const eyeTarget = !danger && Math.random() < .22;
  const type = danger ? "danger" : (eyeTarget ? "eye-target" : "heart");

  el.classList.add(type);
  el.textContent = danger
   ? (Math.random() < .5 ? "♟" : "〰")
   : (eyeTarget ? "◉" : "♥");
  el.setAttribute("aria-label", danger ? "Criatura peligrosa" :
   (eyeTarget ? "Atrapar ojo" : "Atrapar corazón"));

  const width = 44;
  const maxX = Math.max(0, game.clientWidth - width);
  const x = Math.random() * maxX;
  el.style.left = x + "px";
  el.style.top = "-48px";
  game.appendChild(el);

  const item = {
   el, type, x, y:-48,
   vy:(65 + Math.random()*45) * speed,
   caught:false
  };
  targets.push(item);

  el.addEventListener("click", e => {
   e.stopPropagation();
   if(!running || item.caught) return;
   item.caught = true;

   if(item.type === "danger"){
    score = Math.max(0, score - 20);
    showFlash();
    gameState.textContent = "● WRONG CHOICE";
   } else {
    score += 10;
    heartBurst(
     el.getBoundingClientRect().left + el.offsetWidth/2,
     el.getBoundingClientRect().top
    );
    gameState.textContent = "♥ GOOD CHOICE";
   }

   updateScore();
   el.remove();
   targets = targets.filter(t => t !== item);
  });
 }

 function tick(timestamp){
  if(!running) return;
  if(!lastTime) lastTime = timestamp;
  const dt = Math.min((timestamp-lastTime)/1000, .05);
  lastTime = timestamp;
  spawnElapsed += dt;

  // Aparición gradual de elementos.
  const interval = Math.max(.48, 1.05 - score/500);
  if(spawnElapsed >= interval){
   spawnElapsed = 0;
   spawnTarget();
  }

  for(let i=targets.length-1; i>=0; i--){
   const item = targets[i];
   if(item.caught) continue;
   item.y += item.vy * dt;
   item.el.style.top = item.y + "px";

   if(item.y > game.clientHeight){
    item.el.remove();
    targets.splice(i, 1);

    if(item.type === "heart"){
     missed++;
     updateScore();
     if(missed >= 3){
      endGame();
      return;
     }
    }
   }
  }
  animationFrame = requestAnimationFrame(tick);
 }

 function startGame(){
  stopGame();
  score = 0;
  missed = 0;
  speed = 1;
  lastTime = 0;
  spawnElapsed = 0;
  updateScore();
  overlay.classList.remove("show");
  character.classList.remove("sad");
  character.classList.remove("blushing");
  gameState.textContent = "● PLAYING";
  running = true;
  animationFrame = requestAnimationFrame(tick);
 }

 document.getElementById("startBtn").addEventListener("click", () => {
  if(!running) startGame();
 });

 document.getElementById("restartBtn").addEventListener("click", startGame);

 document.getElementById("resetBtn").addEventListener("click", () => {
  stopGame();
  score = 0;
  missed = 0;
  updateScore();
  overlay.classList.remove("show");
  character.classList.remove("sad");
  gameState.textContent = "● READY?";
 });

 // Inicia automáticamente después de un momento.
 setTimeout(() => {
  if(!running && !overlay.classList.contains("show")) startGame();
 }, 1200);

 // Evita que los objetivos sigan fuera del juego si cambia su tamaño.
 window.addEventListener("resize", () => {
  targets.forEach(item => {
   item.x = Math.min(item.x, game.clientWidth - 44);
   item.el.style.left = Math.max(0, item.x) + "px";
  });
 });

})();
</script>
</body>
</html>

