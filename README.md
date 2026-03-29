# Happy-Birthday-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Birthday 💙</title>

<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    font-family: 'Quicksand', sans-serif;
    background: linear-gradient(135deg,#eaf4ff,#d6ebff,#f0f8ff);
    overflow: hidden;
}

/* 💖 glowing name */
.glow {
    font-family: 'Pacifico', cursive;
    font-size: 35px;
    color: #5aa9ff;
    animation: glow 2s infinite alternate;
}
@keyframes glow {
    from { text-shadow: 0 0 10px #7db8ff; }
    to { text-shadow: 0 0 25px #4da6ff; }
}

/* 💙 floating hearts */
.heart {
    position: absolute;
    animation: float 6s infinite;
}
@keyframes float {
    0% { transform: translateY(100vh); }
    100% { transform: translateY(-10vh); }
}

/* 🧸 teddy */
.teddy {
    position: absolute;
    bottom: 10px;
    right: 10px;
    font-size: 40px;
    animation: bounce 2s infinite alternate;
}
@keyframes bounce {
    to { transform: translateY(-15px); }
}

/* pages */
.page {
    display: none;
    text-align: center;
    padding: 40px;
}
.active { display: block; }

/* glass card */
.card {
    backdrop-filter: blur(10px);
    background: rgba(255,255,255,0.6);
    padding: 25px;
    border-radius: 25px;
    display: inline-block;
}

/* buttons */
button {
    padding: 12px 25px;
    border-radius: 30px;
    border: none;
    background: #7db8ff;
    color: white;
    cursor: pointer;
    box-shadow: 0 0 15px #7db8ff;
}

/* gifts */
.gifts img {
    width: 120px;
    margin: 20px;
    cursor: pointer;
    transition: 0.5s;
}
.gifts img.open {
    transform: scale(1.5);
    opacity: 0;
}

/* cake */
.cake {
    font-size: 120px;
}
.candle {
    cursor: pointer;
}

/* letter typing */
#typedText {
    min-height: 120px;
    font-size: 18px;
}

/* QR */
.qr img {
    width: 200px;
    border-radius: 20px;
}

/* sparkles */
.sparkle {
    position: absolute;
    animation: sparkle 1s forwards;
}
@keyframes sparkle {
    to { transform: scale(2); opacity: 0; }
}
</style>
</head>

<body>

<audio id="music" loop>
  <source src="https://pagalfree.com/musics/128-Pehla%20Pyaar%20-%20Kabir%20Singh%20128%20Kbps.mp3">
</audio>

<div class="teddy">🧸💙</div>

<script>
/* hearts */
for(let i=0;i<30;i++){
 let h=document.createElement("div");
 h.className="heart";
 h.innerHTML="💙";
 h.style.left=Math.random()*100+"vw";
 document.body.appendChild(h);
}
</script>

<!-- PAGE 1 -->
<div class="page active" id="page1">
<div class="card">
<h1 class="glow">Happy Birthday Abhuu 💙</h1>
<p>Click to begin 💫</p>
<button onclick="start()">Start 💖</button>
</div>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
<div class="card">
<h2>Pick your gift 🎁</h2>
<div class="gifts">
<img src="https://cdn-icons-png.flaticon.com/512/869/869636.png" onclick="openGift(this,event)">
<img src="https://cdn-icons-png.flaticon.com/512/869/869636.png" onclick="openGift(this,event)">
<img src="https://cdn-icons-png.flaticon.com/512/869/869636.png" onclick="openGift(this,event)">
</div>
</div>
</div>

<!-- PAGE 3 -->
<div class="page" id="page3">
<div class="card">
<h2>Blow the candle 🎂</h2>
<div class="cake">
<span class="candle" onclick="blow()">🕯️</span>🎂💙
</div>
<p id="cakeMsg"></p>
</div>
</div>

<!-- PAGE 4 -->
<div class="page" id="page4">
<div class="card">
<h2>From my heart 💌</h2>
<p id="typedText"></p>
<button onclick="nextPage(5)">Next 🎶</button>
</div>
</div>

<!-- PAGE 5 -->
<div class="page" id="page5">
<div class="card">
<h2>Song for you 🎶</h2>
<div class="qr">
<img src="https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=https://open.spotify.com/track/6uNwZ0v1mJcZtCzR8qz6Rg">
</div>
<button onclick="nextPage(1)">Restart 💙</button>
</div>
</div>

<script>
function start(){
 document.getElementById("music").play();
 nextPage(2);
}

function nextPage(n){
 document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
 document.getElementById("page"+n).classList.add("active");
 if(n==4) typeLetter();
}

function openGift(el,e){
 el.classList.add("open");
 sparkle(e);
 setTimeout(()=>nextPage(3),600);
}

function blow(){
 document.querySelector(".candle").innerHTML="✨";
 document.getElementById("cakeMsg").innerText="Wish made 💙";
 setTimeout(()=>nextPage(4),1000);
}

/* typing effect */
function typeLetter(){
 let text=`Happiest Birthday Abhuu 🫂🧿 I love you so muchhh meriii jaannn 😭 
Hameshaa mere saath rehna 💫 Tu bohot special hai mere liye and I love you so muchhh babyyyyy!!! 
Tu rota hai toh mujhe bilkul accha nahi lagta Orr tu jab hasta hai mere saath esa lagta hai duniya ki saari khushiyan mujhe mil gayi ho!!! 
Happiest Birthday my love 🎀💋♥️ May you get lots of happiness and my der saaraaa loveeee!!!! 
Heheee 👉🏻👈🏻`;

 let i=0;
 let speed=30;
 let box=document.getElementById("typedText");
 box.innerHTML="";

 function type(){
   if(i<text.length){
     box.innerHTML+=text.charAt(i);
     i++;
     setTimeout(type,speed);
   }
 }
 type();
}

/* sparkles */
function sparkle(e){
 for(let i=0;i<10;i++){
   let s=document.createElement("div");
   s.className="sparkle";
   s.innerHTML="✨";
   s.style.left=e.pageX+"px";
   s.style.top=e.pageY+"px";
   document.body.appendChild(s);
   setTimeout(()=>s.remove(),1000);
 }
}
</script>

</body>
</html>
