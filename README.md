<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Love</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), 
                        url('https://lh3.googleusercontent.com/d/1XyO3V_6mI_zBwN3R-tQnNf9lJ_m9l5C8');
            background-size: cover;
            background-position: center;
            font-family: 'Georgia', serif;
            text-align: center;
            overflow: hidden;
        }

        .container {
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(12px);
            padding: 3rem;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4);
            max-width: 400px;
            width: 85%;
            z-index: 100; /* Keeps the box above the hearts */
        }

        h1 { color: #b31b1b; margin-bottom: 2rem; font-size: 1.8rem; }

        .buttons { display: flex; justify-content: center; gap: 20px; }

        button {
            padding: 12px 30px;
            font-size: 1.1rem;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            font-weight: bold;
            transition: transform 0.2s;
        }

        #yesBtn { background-color: #d32f2f; color: white; }
        #noBtn { background-color: #f0f0f0; color: #333; position: relative; }

        /* --- Floating Hearts Animation --- */
        .heart {
            position: absolute;
            color: rgba(255, 255, 255, 0.7);
            font-size: 20px;
            top: 100%;
            pointer-events: none;
            animation: float 5s linear forwards;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="container">
        <h1 id="question">Will you be my Valentine? ❤️</h1>
        <div class="buttons">
            <button id="yesBtn" onclick="celebrate()">Yes</button>
            <button id="noBtn" onmouseover="moveButton()" onclick="moveButton()">No</button>
        </div>
    </div>

    <script>
        function celebrate() {
            document.getElementById('question').innerHTML = "I knew you'd say yes! 🥰 <br><br> See you on the 14th!";
            document.querySelector('.buttons').style.display = 'none';
            // Extra heart burst on Yes
            for(let i=0; i<30; i++) { setTimeout(createHeart, i * 100); }
        }

        function moveButton() {
            const
