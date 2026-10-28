# happy-birthday-phil
phils birthday try no 2
Got it. We’ll ignore that part.

Here’s the clean final version with:

- More boyish / masculine dark navy background  
- YouTube music (“Sweet” by Cigarettes After Sex)  
- Your final emotional letter signed **Kwansma**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happy Birthday Phil 🎂</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      min-height: 100vh;
      background: linear-gradient(160deg, #0b1120 0%, #1e293b 45%, #0f172a 100%);
      font-family: 'Segoe UI', system-ui, sans-serif;
      color: #e2e8f0;
      overflow-x: hidden;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px;
    }
    .particle {
      position: fixed;
      width: 3px;
      height: 3px;
      background: rgba(148, 163, 184, 0.35);
      border-radius: 50%;
      animation: floatUp 11s linear infinite;
      pointer-events: none;
      z-index: 0;
    }
    @keyframes floatUp {
      0% { transform: translateY(100vh); opacity: 0; }
      15% { opacity: 0.5; }
      85% { opacity: 0.3; }
      100% { transform: translateY(-40px); opacity: 0; }
    }
    #gift-screen {
      text-align: center;
      z-index: 10;
      transition: opacity 0.6s, transform 0.6s;
    }
    #gift-screen.hidden {
      opacity: 0;
      transform: scale(0.85);
      pointer-events: none;
      position: absolute;
    }
    .gift {
      width: 170px;
      height: 150px;
      margin: 0 auto 28px;
      position: relative;
      cursor: pointer;
      transition: transform 0.3s;
    }
    .gift:hover { transform: scale(1.04); }
    .gift-lid {
      width: 190px;
      height: 38px;
      background: #334155;
      position: absolute;
      top: -18px;
      left: -10px;
      border-radius: 6px 6px 0 0;
      box-shadow: 0 4px 12px rgba(0,0,0,0.4);
      transition: transform 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
      transform-origin: bottom center;
      z-index: 2;
    }
    .gift-lid::before {
      content: '';
      position: absolute;
      width: 26px;
      height: 50px;
      background: #64748b;
      left: 50%;
      top: -26px;
      transform: translateX(-50%);
      border-radius: 3px;
    }
    .gift-box {
      width: 170px;
      height: 130px;
      background: #1e293b;
      border-radius: 0 0 10px 10px;
      position: relative;
      box-shadow: 0 8px 25px rgba(0,0,0,0.5);
      border: 1px solid #334155;
    }
    .gift-box::before {
      content: '';
      position: absolute;
      width: 26px;
      height: 100%;
      background: #64748b;
      left: 50%;
      transform: translateX(-50%);
    }
    .gift.open .gift-lid {
      transform: rotateX(-110deg) translateY(-18px);
    }
    h1 {
      font-size: 2rem;
      margin-bottom: 8px;
      color: #f1f5f9;
      font-weight: 600;
    }
    .tap-hint {
      font-size: 1rem;
      opacity: 0.7;
      animation: pulse 1.8s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 0.55; }
      50% { opacity: 0.9; }
    }
    #main-content {
      display: none;
      flex-direction: column;
      align-items: center;
      text-align: center;
      max-width: 500px;
      z-index: 10;
      animation: fadeIn 0.9s ease;
    }
    #main-content.show { display: flex; }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(25px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .name {
      font-size: 2.2rem;
      color: #f8fafc;
      margin-bottom: 6px;
      font-weight: 700;
    }
    .cake {
      position: relative;
      width: 190px;
      height: 150px;
      margin: 18px 0 28px;
    }
    .cake-layer {
      position: absolute;
      border-radius: 8px 8px 5px 5px;
      left: 50%;
      transform: translateX(-50%);
    }
    .layer1 { width: 170px; height: 48px; background: #475569; bottom: 0; }
    .layer2 { width: 140px; height: 42px; background: #334155; bottom: 42px; }
    .layer3 { width: 110px; height: 38px; background: #1e293b; bottom: 78px; }
    .frosting {
      position: absolute;
      width: 100%;
      height: 13px;
      background: #94a3b8;
      border-radius: 50%;
      top: -6px;
      left: 0;
    }
    .candle {
      position: absolute;
      width: 7px;
      height: 32px;
      background: linear-gradient(to bottom, #e2e8f0 70%, #fbbf24);
      border-radius: 2px;
      bottom: 110px;
      cursor: pointer;
      transition: opacity 0.4s;
    }
    .candle:nth-child(1) { left: 50px; }
    .candle:nth-child(2) { left: 80px; }
    .candle:nth-child(3) { left: 110px; }
    .candle:nth-child(4) { left: 140px; }
    .flame {
      position: absolute;
      width: 11px;
      height: 16px;
      background: radial-gradient(ellipse at bottom, #fbbf24, #f59e0b);
      border-radius: 50% 50% 20% 20%;
      top: -14px;
      left: -2px;
      animation: flicker 0.3s infinite alternate;
      box-shadow: 0 0 10px #fbbf24;
    }
    .candle.out .flame { display: none; }
    .candle.out { opacity: 0.35; }
    @keyframes flicker {
      from { transform: scale(1) rotate(-2deg); }
      to { transform: scale(1.1) rotate(2deg); }
    }
    .letter {
      background: rgba(15, 23, 42, 0.75);
      backdrop-filter: blur(10px);
      border-radius: 14px;
      padding: 26px 28px;
      margin: 20px 0;
      border: 1px solid #334155;
      line-height: 1.65;
      font-size: 1.02rem;
      text-align: left;
      max-width: 460px;
    }
    .letter p { margin-bottom: 13px; }
    .letter .signature {
      margin-top: 18px;
      font-style: italic;
      text-align: right;
      opacity: 0.9;
    }
    .btn {
      background: #334155;
      color: #f1f5f9;
      border: 1px solid #475569;
      padding: 12px 28px;
      border-radius: 40px;
      font-size: 1rem;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.2s;
    }
    .btn:hover {
      background: #475569;
      transform: translateY(-2px);
    }
    .music-note {
      position: fixed;
      bottom: 22px;
      right: 22px;
      background: rgba(30, 41, 59, 0.8);
      border: 1px solid #475569;
      width: 48px;
      height: 48px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      cursor: pointer;
      z-index: 100;
      transition: all 0.25s;
    }
    .music-note:hover { background: #334155; }
    #yt-player {
      position: fixed;
      bottom: -9999px;
      left: -9999px;
      width: 1px;
      height: 1px;
      opacity: 0;
    }
  </style>
</head>
<body>
  <div id="particles"></div>
  <div id="yt-player"></div>
  <div class="music-note" id="music-btn" onclick="toggleMusic()">🎵</div>

  <div id="gift-screen">
    <h1>A little gift for you</h1>
    <p class="tap-hint">Tap the gift to open</p>
    <div class="gift" id="gift" onclick="openGift()">
      <div class="gift-lid"></div>
      <div class="gift-box"></div>
    </div>
  </div>

  <div id="main-content">
    <div class="name">Happy Birthday, Phil</div>
    <p style="opacity:0.75; margin-bottom:8px; font-size:0.95rem;">Make a wish and blow out the candles</p>

    <div class="cake">
      <div class="cake-layer layer1"><div class="frosting"></div></div>
      <div class="cake-layer layer2"><div class="frosting"></div></div>
      <div class="cake-layer layer3"><div class="frosting"></div></div>
      <div class="candle" onclick="blowCandle(this)"><div class="flame"></div></div>
      <div class="candle" onclick="blowCandle(this)"><div class="flame"></div></div>
      <div class="candle" onclick="blowCandle(this)"><div class="flame"></div></div>
      <div class="candle" onclick="blowCandle(this)"><div class="flame"></div></div>
    </div>

    <button class="btn" onclick="blowAll()">Blow out the candles</button>

    <div class="letter">
      <p>My dearest Phil,</p>
      <p>Happy Birthday, my love.</p>
      <p>Today is yours — the man who keeps choosing me even when I make it hard.<br>
      I know I’ve run. I know I’ve made you doubt us more times than I can count. And every time you stayed, every time you quietly said “I’m still here,” it made me realise that you actually don’t want to hurt me and you mean what you say.</p>
      <p>I feel safer with you every single day.<br>
      Safer than I ever thought I could feel.<br>
      And I’m so grateful I decided to stay. I’m so grateful I get to love you.</p>
      <p>I’m not always good with big emotions. I don’t always know how to say the things I feel. But today I need you to know:</p>
      <p>I’m so sorry for all the nights I made you go to sleep doubting us.<br>
      Doubting yourself. Doubting if I would still choose you in the morning.<br>
      You never deserved to carry that uncertainty alone.</p>
      <p>We’re long distance. There will be hard days and uncertainties. But I choose you.<br>
      I will keep choosing you.<br>
      There is no one else.</p>
      <p>On your birthday, I just want you to feel how deeply you are loved.<br>
      You are my safest place, my favourite person, and the best decision I’ve ever made.</p>
      <p>Happy Birthday, Phil.<br>
      I love you more than I know how to show.</p>
      <p class="signature">Always yours,<br>Kwansma</p>
    </div>
  </div>

  <script src="https://www.youtube.com/iframe_api"></script>
  <script>
    let player;
    let isPlaying = false;

    function onYouTubeIframeAPIReady() {
      player = new YT.Player('yt-player', {
        height: '1',
        width: '1',
        videoId: 'pZ31pyTZdh0',
        playerVars: {
          autoplay: 0,
          controls: 0,
          loop: 1,
          playlist: 'pZ31pyTZdh0'
        }
      });
    }

    function toggleMusic() {
      if (!player) return;
      if (isPlaying) {
        player.pauseVideo();
        document.getElementById('music-btn').textContent = '🎵';
      } else {
        player.playVideo();
        document.getElementById('music-btn').textContent = '⏸️';
      }
      isPlaying = !isPlaying;
    }

    function createParticles() {
      const container = document.getElementById('particles');
      for (let i = 0; i < 18; i++) {
        const p = document.createElement('div');
        p.className = 'particle';
        p.style.left = Math.random() * 100 + 'vw';
        p.style.animationDuration = (8 + Math.random() * 7) + 's';
        p.style.animationDelay = Math.random() * 6 + 's';
        container.appendChild(p);
      }
    }
    createParticles();

    function openGift() {
      document.getElementById('gift').classList.add('open');
      if (player) {
        player.playVideo();
        isPlaying = true;
        document.getElementById('music-btn').textContent = '⏸️';
      }
      setTimeout(() => {
        document.getElementById('gift-screen').classList.add('hidden');
        document.getElementById('main-content').classList.add('show');
        launchConfetti();
      }, 850);
    }

    function blowCandle(el) {
      el.classList.add('out');
      checkAllOut();
    }

    function blowAll() {
      document.querySelectorAll('.candle').forEach(c => c.classList.add('out'));
      launchConfetti();
    }

    function checkAllOut() {
      if ([...document.querySelectorAll('.candle')].every(c => c.classList.contains('out'))) {
        launchConfetti();
      }
    }

    function launchConfetti() {
      const colors = ['#64748b', '#94a3b8', '#cbd5e1', '#fbbf24', '#e2e8f0'];
      for (let i = 0; i < 50; i++) {
        const conf = document.createElement('div');
        conf.style.cssText = `
          position: fixed; width: 8px; height: 8px; top: -20px;
          left: ${Math.random()*100}vw; background: ${colors[Math.floor(Math.random()*colors.length)]};
          border-radius: ${Math.random()>0.5?'50%':'2px'}; z-index: 100;
          animation: fall ${2+Math.random()*2.5}s linear forwards;
        `;
        document.body.appendChild(conf);
        setTimeout(() => conf.remove(), 4500);
      }
    }

    // Add fall animation
    const style = document.createElement('style');
    style.textContent = `@keyframes fall { to { transform: translateY(100vh) rotate(720deg); opacity: 0; } }`;
    document.head.appendChild(style);
  </script>
</body>
</html>
```
