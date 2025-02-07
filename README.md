<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine?</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: pink;
            font-family: Arial, sans-serif;
            flex-direction: column;
            overflow: hidden;
        }
        .container {
            text-align: center;
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            animation: fadeIn 2s ease-in-out;
        }
        h1 {
            color: red;
        }
        .buttons {
            margin-top: 20px;
            position: relative;
        }
        button {
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: 0.3s;
        }
        .yes {
            background-color: #ff4d4d;
            color: white;
            font-size: 16px;
            transition: 0.3s ease-in-out;
        }
        .yes:hover {
            background-color: #ff0000;
            transform: scale(1.2);
            box-shadow: 0 0 15px red;
        }
        .no {
            background-color: gray;
            color: white;
            position: absolute;
        }
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: scale(0.8);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }
        @keyframes floatingHearts {
            0% {
                transform: translateY(0) scale(1);
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) scale(0.5);
                opacity: 0;
            }
        }
        .heart {
            position: absolute;
            bottom: -10px;
            font-size: 24px;
            color: red;
            animation: floatingHearts 5s linear infinite;
        }
        .message {
            display: none;
            font-size: 24px;
            color: red;
            font-weight: bold;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <audio id="loveSong" loop>
        <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mpeg">
    </audio>

    <div class="container">
        <h1>Will You Be My Valentine? ❤️</h1>
        <div class="buttons">
            <button class="yes" onclick="showMessage()">Yes</button>
            <button class="no">No</button>
        </div>
        <p class="message">Yay! You’re my Valentine! 💕🥰</p>
    </div>

    <script>
        let moveCount = 0;
        const noButton = document.querySelector('.no');

        // Move "No" Button Up to 5 Times
        noButton.addEventListener('mouseover', function () {
            if (moveCount < 5) {
                this.style.left = Math.random() * window.innerWidth + 'px';
                this.style.top = Math.random() * window.innerHeight + 'px';
                moveCount++;
            }
        });

        // Floating Hearts Effect
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }
        setInterval(createHeart, 300);

        // Display Love Message on "Yes"
        function showMessage() {
            document.querySelector('.message').style.display = 'block';
            document.getElementById("loveSong").play();
        }
    </script>
</body>
</html>
