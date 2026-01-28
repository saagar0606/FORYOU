<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Aditi ❤️</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ff4d6d;
            --secondary: #ff758f;
            --bg: #0a0a0c;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            background: var(--bg);
            color: #fff;
            font-family: 'Poppins', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
        }

        #bg-canvas {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: -1;
        }

        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .page {
            display: none;
            width: 100%;
            max-width: 500px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            padding: 30px;
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            text-align: center;
            animation: fadeIn 0.5s ease forwards;
        }

        .active { display: block; }

        @keyframes fadeIn { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }

        h1 { font-family: 'Dancing Script', cursive; color: var(--primary); font-size: 2.2rem; margin-bottom: 15px; }
        
        .btn {
            background: var(--primary); color: white; border: none; padding: 12px 25px;
            border-radius: 25px; cursor: pointer; font-weight: 600; margin: 10px;
            transition: 0.3s;
        }

        /* Games */
        .grid-game { display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; margin: 20px 0; }
        .item { font-size: 2rem; cursor: pointer; padding: 10px; background: rgba(255,255,255,0.05); border-radius: 10px; }

        /* Letter & Box */
        .letter-box {
            background: #fffdf5; color: #333; padding: 20px; border-radius: 10px;
            text-align: left; box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: none; border-left: 5px solid var(--primary);
        }

        .photo-frame { width: 100%; border: 5px solid #fff; border-radius: 10px; margin-bottom: 15px; }

        /* Final Animation */
        #teddyAnimation {
            position: relative;
            height: 120px;
            margin: 20px 0;
            overflow: hidden;
            display: none;
        }
        .teddy { font-size: 3.5rem; position: absolute; transition: all 1.5s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
        #maleTeddy { left: -60px; }
        #femaleTeddy { right: -60px; }
        #proposal { display: none; font-size: 2rem; margin-top: -10px; }
        
        .floating-heart {
            position: absolute;
            animation: floatUp 1s ease-out forwards;
            font-size: 1.5rem;
        }
        @keyframes floatUp {
            from { transform: translateY(0); opacity: 1; }
            to { transform: translateY(-50px); opacity: 0; }
        }
    </style>
</head>
<body>

<canvas id="bg-canvas"></canvas>

<div class="container">
    <div class="page active" id="p1">
        <h1>Happy Birthday Betuuuu ❤️</h1>
        <button class="btn" onclick="nextPage(2)">Let's Start</button>
    </div>

    <div class="page" id="p2">
        <h1>Wanna play a game?</h1>
        <button class="btn" onclick="nextPage(3)">Yes</button>
        <button class="btn" onclick="alert('Oh come on! Click Yes! 😉')">No</button>
    </div>

    <div class="page" id="p3">
        <h1>Find 4 Hearts 🎈</h1>
        <div class="grid-game" id="balloonGrid"></div>
        <p>Score: <span id="hCount">0</span>/4</p>
    </div>

    <div class="page" id="p4">
        <h1>A Letter to My Soul</h1>
        <div id="closedLetter">
            <span style="font-size: 4rem;">✉️</span><br>
            <button class="btn" onclick="openLetter()">Open 3D Letter</button>
        </div>
        <div class="letter-box" id="openLetterBox">
            <p><strong>Happy Birthday my love ❤️</strong><br><br>
            This is our 4th birthday together and I feel so lucky to have you in my life. You are my happiness, my smile, and my biggest blessing. I pray that all your dreams come true and your life is filled with love and success. Thank you for loving me and standing by me always. I promise to always be with you, today and forever.<br><br>
            <strong>Happy Birthday my beautiful girl 💖</strong></p>
            <button class="btn" style="width:100%" onclick="nextPage(6)">Next Game</button>
        </div>
    </div>

    <div class="page" id="p6">
        <h1>Find 3 Teddies 📦</h1>
        <div class="grid-game" style="grid-template-columns: repeat(3, 1fr);" id="boxGrid"></div>
        <div id="teddyResult" style="display:none">
            <p>Wait for your gift... 🎁</p>
            <button class="btn" onclick="nextPage(7)">See Memories</button>
        </div>
    </div>

    <div class="page" id="p7">
        <h1>Bachpan Ki Aditi</h1>
        <img src="https://i.ibb.co/9mY93wLV/1.jpg" class="photo-frame">
        <button class="btn" onclick="nextPage(8)">Next</button>
    </div>

    <div class="page" id="p8">
        <h1>Miss Aditi Ji ✨</h1>
        <p style="font-size: 1.3rem; color: #ffb7c5; line-height: 1.8;">
            तेरा साथ ही मेरी सबसे बड़ी दुआ है,<br>
            तेरी मुस्कान ही मेरी पूरी दुनिया है।<br>
            चार साल से तू मेरी आदत बन गई है,<br>
            तेरे बिना ये दिल अधूरा सा लगता है।
        </p>
        <button class="btn" onclick="nextPage(9)">Photo Gallery</button>
    </div>

    <div class="page" id="p9">
        <h1>My Only One</h1>
        <img id="galleryImg" src="" class="photo-frame">
        <button class="btn" onclick="rotateGallery()">Next Photo 📸</button>
        <button class="btn" id="galleryDone" style="display:none" onclick="nextPage(10)">Final Surprise</button>
    </div>

    <div class="page" id="p10">
        <div id="box2">
            <h1>Open for a Message</h1>
            <span style="font-size: 4rem; cursor:pointer;" onclick="openFinalBox()">🎁</span>
        </div>
        <div id="finalMsg" class="letter-box">
            <p><strong>Happy Birthday Aditi 💖</strong><br><br>
            Not every day brings a miracle, but the day you came into my life did. These 4 years with you are my most beautiful journey. You are the reason my heart believes in love and my smile feels real.</p>
            <button class="btn" style="width:100%" onclick="nextPage(11)">Last Message</button>
        </div>
    </div>

    <div class="page" id="p11">
        <h1>For My Bandariya 🐒</h1>
        <p style="font-size: 0.85rem; text-align: justify;">
            Happy birthday my Bandariya cutie! I am the happiest person because you are my love and my life. Aap khush raho bass... aapki sari problems meri. Maine bohut galti ki hai usko aapne maaf kiya hai toh aage bhi kar dena please kyuki aapke alawa koi nahi hai mera iss duniya mein. I love you madam ji! I miss you so much! I hate you 😁😘
        </p>
        
        <div id="finalGiftBox" style="font-size: 4rem; cursor:pointer;" onclick="startFinalAnimation()">🎁</div>

        <div id="teddyAnimation">
            <div id="proposal">🌹💍</div>
            <span id="maleTeddy" class="teddy">🧸</span>
            <span id="femaleTeddy" class="teddy">🧸🎀</span>
        </div>
        
        <button class="btn" style="display:none; margin-top:20px;" id="restartBtn" onclick="location.reload()">Restart ❤️</button>
    </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
    // --- 3D BACKGROUND ---
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById('bg-canvas'), alpha: true });
    renderer.setSize(window.innerWidth, window.innerHeight);
    const hearts = [];
    const heartShape = new THREE.Shape();
    heartShape.moveTo(0,0); heartShape.bezierCurveTo(0,0,-5,5,-5,10); heartShape.bezierCurveTo(-5,15,0,18,0,10); heartShape.bezierCurveTo(0,18,5,15,5,10); heartShape.bezierCurveTo(5,5,0,0,0,0);
    const geometry = new THREE.ShapeGeometry(heartShape);
    const material = new THREE.MeshBasicMaterial({ color: 0xff4d6d, transparent: true, opacity: 0.4 });
    for(let i=0; i<30; i++) {
        const h = new THREE.Mesh(geometry, material);
        h.position.set(Math.random()*100-50, Math.random()*100-50, Math.random()*100-50);
        h.rotation.z = Math.PI; h.scale.set(0.3,0.3,0.3); scene.add(h); hearts.push(h);
    }
    camera.position.z = 50;
    function animate() { requestAnimationFrame(animate); hearts.forEach(h => { h.position.y -= 0.05; if(h.position.y < -50) h.position.y = 50; }); renderer.render(scene, camera); }
    animate();

    // --- LOGIC ---
    function nextPage(n) {
        document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
        document.getElementById('p'+n).classList.add('active');
        if(n===3) initBalloons(); if(n===6) initBoxes(); if(n===9) rotateGallery();
    }

    function initBalloons() {
        let count = 0; const grid = document.getElementById('balloonGrid'); grid.innerHTML = '';
        const sequence = [true,true,true,true,false,false,false,false].sort(() => Math.random()-0.5);
        sequence.forEach(h => {
            const d = document.createElement('div'); d.className = 'item'; d.innerHTML = '🎈';
            d.onclick = function() {
                if(h) { this.innerHTML = '❤️'; count++; document.getElementById('hCount').innerText = count; if(count>=4) setTimeout(()=>nextPage(4),800); }
                else this.innerHTML = '💥'; this.onclick = null;
            }; grid.appendChild(d);
        });
    }

    function openLetter() { document.getElementById('closedLetter').style.display='none'; document.getElementById('openLetterBox').style.display='block'; }

    function initBoxes() {
        let count = 0; const grid = document.getElementById('boxGrid'); grid.innerHTML = '';
        const seq = [true,true,true,false,false,false].sort(() => Math.random()-0.5);
        seq.forEach(t => {
            const d = document.createElement('div'); d.className = 'item'; d.innerHTML = '📦';
            d.onclick = function() {
                if(t) { this.innerHTML = '🧸'; count++; if(count>=3) document.getElementById('teddyResult').style.display='block'; }
                else this.innerHTML = '❌'; this.onclick = null;
            }; grid.appendChild(d);
        });
    }

    const photoLinks = ["https://i.ibb.co/5Wtn4QqN/1.jpg", "https://i.ibb.co/jkhdVQtk/2.jpg", "https://i.ibb.co/9m6CST5P/3.jpg", "https://i.ibb.co/mCwSj5cm/4.jpg", "https://i.ibb.co/cK6Ccx6X/5.jpg", "https://i.ibb.co/sJgWGCX8/6.jpg", "https://i.ibb.co/Nn6kH0Ht/7.jpg", "https://i.ibb.co/b5kT5xds/8.jpg", "https://i.ibb.co/prXPV1hM/9.jpg", "https://i.ibb.co/JRfvCKcB/10.jpg", "https://i.ibb.co/ymQm5jf0/11.jpg", "https://i.ibb.co/K8SXK5f/12.jpg", "https://i.ibb.co/JR2qym8Y/13.jpg", "https://i.ibb.co/FjRPkF6/14.jpg", "https://i.ibb.co/yBqp3G78/15.jpg", "https://i.ibb.co/p5cnM31/16.jpg", "https://i.ibb.co/VY6vtJQt/17.jpg"];
    let gIdx = 0;
    function rotateGallery() {
        if(gIdx < photoLinks.length) { document.getElementById('galleryImg').src = photoLinks[gIdx]; gIdx++; if(gIdx===photoLinks.length) document.getElementById('galleryDone').style.display='inline-block'; }
    }

    function openFinalBox() { document.getElementById('box2').style.display='none'; document.getElementById('finalMsg').style.display='block'; }

    function startFinalAnimation() {
        document.getElementById('finalGiftBox').style.display = 'none';
        const anim = document.getElementById('teddyAnimation');
        const male = document.getElementById('maleTeddy');
        const female = document.getElementById('femaleTeddy');
        const proposal = document.getElementById('proposal');
        
        anim.style.display = 'block';
        setTimeout(() => { 
            male.style.left = '30%'; 
            female.style.right = '30%'; 
        }, 100);

        setTimeout(() => {
            proposal.style.display = 'block';
            male.innerHTML = "🧸💋";
            female.innerHTML = "💋🧸🎀";
            for(let i=0; i<5; i++) {
                const h = document.createElement('div'); h.className = 'floating-heart'; h.innerHTML = '❤️';
                h.style.left = (45 + Math.random()*10) + '%'; h.style.top = '20px';
                anim.appendChild(h);
            }
            document.getElementById('restartBtn').style.display = 'inline-block';
        }, 1600);
    }
</script>
</body>
</html>
