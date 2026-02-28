<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday NIPA 💗</title>

<style>
body{
    margin:0;
    font-family:'Comic Sans MS',cursive;
    background:linear-gradient(135deg,#ffd6ec,#ffe6f7,#ffc2e2);
    overflow:hidden;
    text-align:center;
}

/* Slides */
.slide{
    display:none;
    height:100vh;
    padding-top:60px;
}
.active{
    display:block;
}

h1{
    font-size:55px;
    background:linear-gradient(to right,#ff1493,#ff69b4);
    -webkit-background-clip:text;
    color:transparent;
}

.message{
    width:80%;
    margin:auto;
    background:white;
    padding:25px;
    border-radius:20px;
    box-shadow:0 10px 25px rgba(0,0,0,0.15);
    font-size:20px;
    margin-top:20px;
}

button{
    padding:10px 20px;
    border:none;
    border-radius:15px;
    background:#ff69b4;
    color:white;
    font-size:16px;
    cursor:pointer;
    margin-top:20px;
}

/* Gift */
.gift{
    font-size:80px;
    cursor:pointer;
    margin-top:20px;
}

/* Falling 🥳 */
.falling{
    position:absolute;
    top:-50px;
    font-size:25px;
    animation:fall linear infinite;
}
@keyframes fall{
    0%{transform:translateY(0);}
    100%{transform:translateY(100vh);}
}

/* Confetti */
.confetti{
    position:fixed;
    width:8px;
    height:8px;
    top:0;
    animation:confettiFall 3s linear forwards;
}
@keyframes confettiFall{
    0%{transform:translateY(0) rotate(0deg);}
    100%{transform:translateY(100vh) rotate(720deg);}
}

/* Hearts */
.heart{
    position:fixed;
    font-size:20px;
    animation:heartUp 3s linear forwards;
}
@keyframes heartUp{
    0%{transform:translateY(0);opacity:1;}
    100%{transform:translateY(-200px);opacity:0;}
}

/* Popup */
.popup{
    display:none;
    position:fixed;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    background:white;
    padding:25px;
    border-radius:20px;
    box-shadow:0 10px 30px rgba(0,0,0,0.2);
}
</style>
</head>

<body onclick="confettiBlast()" ondblclick="heartBlast()">

<!-- Slide 1 -->
<div class="slide active">
    <h1>NIPA 💗</h1>
    <h2>Happy Birthday 🥳🌷</h2>
    <h3>1st March 2009 🧸</h3>
    <button onclick="nextSlide()">Next ➜</button>
</div>

<!-- Slide 2 -->
<div class="slide">
    <h1>For My Best Friend 🌸</h1>
    <div class="message" id="typing"></div>
    <button onclick="nextSlide()">Next ➜</button>
</div>

<!-- Slide 3 -->
<div class="slide">
    <h1>Special Wishes 💖</h1>
    <div class="message">
        🌷 May your life be filled with happiness and positivity.<br><br>
        💗 May success follow you in everything you do.<br><br>
        🧸 May you always stay healthy, confident and strong.<br><br>
        🥳 May your smile never fade and your dreams always grow bigger.<br><br>
        🌸 You deserve peace, joy, love and a beautiful future.
    </div>
    <div class="gift" onclick="openGift()">🎁</div>
</div>

<!-- Popup -->
<div class="popup" id="popup">
<h3>Surprise NIPA 🥳💗</h3>
<p>Never forget how special and valued you are! 🌷  
May this year bring growth, happiness and endless smiles 🧸✨</p>
<button onclick="closePopup()">Close 💌</button>
</div>

<script>

/* Slide control */
let currentSlide = 0;
const slides = document.querySelectorAll(".slide");

function nextSlide(){
    slides[currentSlide].classList.remove("active");
    currentSlide++;
    if(currentSlide >= slides.length) currentSlide = 0;
    slides[currentSlide].classList.add("active");
}

/* Typing animation */
const text = "Dear NIPA 💖, Happy Birthday to the most amazing best friend! 🥳🌷 You make life brighter with your kindness and laughter. May this new year bring you success, peace of mind, strong health, confidence and endless happiness. Keep shining always! 💗🧸✨";
let i=0;
function typeWriter(){
    if(i<text.length){
        document.getElementById("typing").innerHTML += text.charAt(i);
        i++;
        setTimeout(typeWriter,40);
    }
}
typeWriter();

/* Gift popup */
function openGift(){
    document.getElementById("popup").style.display="block";
    confettiBlast();
}
function closePopup(){
    document.getElementById("popup").style.display="none";
}

/* Falling 🥳 */
function createEmoji(){
    const emoji=document.createElement("div");
    emoji.classList.add("falling");
    emoji.innerText="🥳";
    emoji.style.left=Math.random()*100+"vw";
    emoji.style.animationDuration=(Math.random()*3+2)+"s";
    document.body.appendChild(emoji);
    setTimeout(()=>emoji.remove(),5000);
}
setInterval(createEmoji,300);

/* Confetti */
function confettiBlast(){
    for(let i=0;i<70;i++){
        const confetti=document.createElement("div");
        confetti.classList.add("confetti");
        confetti.style.left=Math.random()*100+"vw";
        confetti.style.backgroundColor=`hsl(${Math.random()*360},100%,50%)`;
        document.body.appendChild(confetti);
        setTimeout(()=>confetti.remove(),3000);
    }
}

/* Hearts */
function heartBlast(){
    for(let i=0;i<20;i++){
        const heart=document.createElement("div");
        heart.classList.add("heart");
        heart.innerText="💗";
        heart.style.left=Math.random()*100+"vw";
        heart.style.top=Math.random()*100+"vh";
        document.body.appendChild(heart);
        setTimeout(()=>heart.remove(),3000);
    }
}

/* Auto popup after 2 sec */
setTimeout(()=>{
    document.getElementById("popup").style.display="block";
},2000);

</script>

</body>
</html>
