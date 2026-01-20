<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ronnie & Summer Forever ❤️</title>

<style>
    body {
        margin: 0;
        padding: 0;
        height: 100vh;
        overflow: hidden;
        background: linear-gradient(180deg, #ffd6e8, #fff);
        font-family: "Comic Sans MS", "Trebuchet MS", cursive;
        text-align: center;
    }

    h1 {
        margin-top: 45px;
        font-size: 2.3em;
        color: #ff4d6d;
    }

    h2 {
        font-size: 1.3em;
        color: #ff758f;
        margin: 8px 0;
    }

    #countdown {
        font-size: 1.15em;
        color: #444;
        margin-bottom: 10px;
    }

    p {
        font-size: 1.1em;
        color: #444;
        margin: 12px 20px;
        line-height: 1.4;
    }

    .falling {
        position: fixed;
        top: -50px;
        font-size: 2em;
        animation: fall linear forwards;
        pointer-events: none;
        z-index: 1;
    }

    @keyframes fall {
        to {
            transform: translateY(110vh) rotate(360deg);
            opacity: 0;
        }
    }

    .tap-heart {
        position: fixed;
        font-size: 2em;
        animation: pop 1.2s ease-out forwards;
        pointer-events: none;
        z-index: 2;
    }

    @keyframes pop {
        0% { transform: scale(0.5); opacity: 1; }
        100% { transform: translateY(-80px) scale(2); opacity: 0; }
    }

    #heartMessage {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        font-size: 1.8em;
        letter-spacing: 6px;
        opacity: 0;
        animation: heartText 6s ease-in-out infinite;
        z-index: 0;
        white-space: nowrap;
    }

    @keyframes heartText {
        0% { opacity: 0; transform: translate(-50%, -50%) scale(0.8); }
        20% { opacity: 1; }
        80% { opacity: 1; }
        100% { opacity: 0; transform: translate(-50%, -50%) scale(1.1); }
    }

    footer {
        position: fixed;
        bottom: 10px;
        width: 100%;
        color: #ff4d6d;
        font-size: 1em;
    }
</style>
</head>
<body>

<h1>Ronnie & Summer Forever ❤️</h1>
<h2>1 Year Anniversary — April 8, 2026</h2>
<div id="countdown">Loading countdown…</div>

<p>
Every day with you is my favorite place to be.<br>
I choose you — today, tomorrow, forever.
</p>

<div id="heartMessage">
❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️ ❤️
</div>

<footer>
I love you always,<br>
<strong>Ronnie ❤️</strong>
</footer>

<script>
// Falling pets & hearts
const fallingThings = ["🐱", "🐶", "❤️", "🐾", "🐕", "🐈", "💖"];
setInterval(() => {
    const item = document.createElement("div");
    item.className = "falling";
    item.textContent = fallingThings[Math.floor(Math.random() * fallingThings.length)];
    item.style.left = Math.random() * 100 + "vw";
    item.style.animationDuration = (4 + Math.random() * 4) + "s";
    document.body.appendChild(item);
    setTimeout(() => item.remove(), 8000);
}, 450);

// Tap / click hearts
function spawnHeart(x, y) {
    const heart = document.createElement("div");
    heart.className = "tap-heart";
    heart.textContent = "❤️";
    heart.style.left = x + "px";
    heart.style.top = y + "px";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 1200);
}

document.addEventListener("click", e => spawnHeart(e.clientX, e.clientY));
document.addEventListener("touchstart", e => {
    const t = e.touches[0];
    spawnHeart(t.clientX, t.clientY);
});

// Countdown
const countdownEl = document.getElementById("countdown");
const anniversary = new Date("April 8, 2026 00:00:00").getTime();

setInterval(() => {
    const now = new Date().getTime();
    const diff = anniversary - now;

    if (diff <= 0) {
        countdownEl.textContent = "Happy 1 Year Anniversary ❤️";
        return;
    }

    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
    const minutes = Math.floor((diff / (1000 * 60)) % 60);
    const seconds = Math.floor((diff / 1000) % 60);

    countdownEl.textContent =
        `${days} days • ${hours}h ${minutes}m ${seconds}s until forever 💕`;
}, 1000);

// Heart spelling message
const heartMessage = document.getElementById("heartMessage");
const phrase = "I LOVE YOU SUMMER";
let index = 0;

setInterval(() => {
    let output = "";
    for (let i = 0; i < phrase.length; i++) {
        output += phrase[i] === " " ? "   " : "❤️";
    }
    heartMessage.textContent = output;
}, 6000);
</script>

</body>
</html>
