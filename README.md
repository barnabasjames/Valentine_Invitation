<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Quicksand:wght@300;500&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary-pink: #ffafbd;
            --deep-red: #ff385c;
            --soft-white: #fff0f3;
        }

        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, var(--primary-pink), #ffc3a0);
            font-family: 'Quicksand', sans-serif;
            overflow-x: hidden;
        }

        .card {
            background: white;
            padding: 2rem;
            border-radius: 30px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.1);
            text-align: center;
            max-width: 400px;
            width: 90%;
            position: relative;
            z-index: 10;
        }

        .main-img {
            width: 100%;
            border-radius: 20px;
            margin-bottom: 1.5rem;
            border: 5px solid var(--soft-white);
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            color: var(--deep-red);
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        p {
            color: #777;
            line-height: 1.6;
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 2rem;
        }

        button {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s;
        }

        #yesBtn {
            background-color: var(--deep-red);
            color: white;
            font-size: 1.2rem;
        }

        #noBtn {
            background-color: #eee;
            color: #555;
            position: relative;
        }

        /* Floating Hearts Animation */
        .heart {
            position: fixed;
            color: rgba(255, 56, 92, 0.4);
            font-size: 20px;
            user-select: none;
            z-index: 1;
            animation: float 5s linear forwards;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="card">
        <img src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?auto=format&fit=crop&w=500" alt="Valentine" class="main-img">
        
        <h1>Will you be my Valentine?</h1>
        <p>They say home is a place, but to me, home is a person. And that person is you. ✨</p>

        <div class="buttons">
            <button id="yesBtn" onclick="celebrate()">Yes!</button>
            <button id="noBtn" onmouseover="moveButton()">No</button>
        </div>
    </div>

    <script>
        // Function to make the "No" button run away (Interactive/Playful)
        function moveButton() {
            const btn = document.getElementById('noBtn');
            const x = Math.random() * (window.innerWidth - btn.offsetWidth);
            const y = Math.random() * (window.innerHeight - btn.offsetHeight);
            btn.style.position = 'absolute';
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        // Success message
        function celebrate() {
            document.querySelector('.card').innerHTML = `
                <h1 style="font-size: 4rem;">Yay! ❤️</h1>
                <p>I knew you'd say yes! I can't wait to spend the day with you.</p>
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueG5xc2ZqbmZqbmZqbmZqbmZqbmZqbmZqbmZqbmZqbmZqJnB0X2VpZD1mZjkzYjM5/l41lH4ADDRQHhG3UA/giphy.gif" width="100%">
            `;
            setInterval(createHeart, 300);
        }

        // Heart generation logic
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 3 + 2) + 's';
            document.body.appendChild(heart);
            
            setTimeout(() => heart.remove(), 5000);
        }
    </script>
</body>
</html>
