// Select elements
const yesBtn = document.getElementById("yes-btn");
const noBtn = document.getElementById("no-btn");
const teaseText = document.getElementById("tease-text");
const music = document.getElementById("bg-music");
const toggle = document.getElementById("music-toggle");

let noClicks = 0;

// 💖 YES BUTTON CLICK
yesBtn.addEventListener("click", () => {
    document.body.innerHTML = `
        <div style="text-align:center; margin-top:100px; font-family:Nunito;">
            <h1 style="color:purple;">YAYYY 💕 I knew it!! 😘</h1>
            <p style="color:maroon; font-size:20px;">You just made my day ❤️</p>
        </div>
    `;
});

// 😈 NO BUTTON RUNS AWAY
noBtn.addEventListener("mouseover", () => {
    const x = Math.random() * 300 - 150;
    const y = Math.random() * 300 - 150;
    noBtn.style.transform = `translate(${x}px, ${y}px)`;
});

// 😂 IF USER SOMEHOW CLICKS NO
noBtn.addEventListener("click", () => {
    noClicks++;

    const messages = [
        "Are you sure? 🥺",
        "Think again 😭",
        "Pleaseee 💕",
        "I'll be sad 😢",
        "Don't do this 💔",
        "Last chance 😭💞"
    ];

    teaseText.innerText = messages[noClicks % messages.length];
});

// 🔊 MUSIC TOGGLE
toggle.addEventListener("click", () => {
    if (music.paused) {
        music.play();
        toggle.innerText = "🔊";
    } else {
        music.pause();
        toggle.innerText = "🔇";
    }
});

// 🎵 START MUSIC AFTER FIRST CLICK (browser rule fix)
document.addEventListener("click", () => {
    if (music.paused) {
        music.play().catch(() => {});
    }
}, { once: true });
