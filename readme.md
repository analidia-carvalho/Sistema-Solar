<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animação do Sistema Solar</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            background-color: #000;
            overflow: hidden; /* Impede a barra de rolagem */
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        .container {
            position: relative;
            width: 80vh;
            height: 80vh;
            animation: rotate 365s linear infinite;
        }

        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }

        .sun {
            position: absolute;
            top: 50%;
            left: 50%;
            width: 10vh;
            height: 10vh;
            background-color: #ffc107;
            border-radius: 50%;
            box-shadow: 0 0 20px #ffc107;
            transform: translate(-50%, -50%);
            z-index: 100;
        }

        .planet {
            position: absolute;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        /* Cores e tamanhos dos planetas */
        #mercury { background-color: #4a148c; width: 1vh; height: 1vh; }
        #venus { background-color: #ff6f61; width: 1.2vh; height: 1.2vh; }
        #earth { background-color: #2196f3; width: 1.4vh; height: 1.4vh; }
        #mars { background-color: #d34836; width: 1.1vh; height: 1.1vh; }
        #jupiter { background-color: #f57c00; width: 4vh; height: 4vh; }
        #saturn { background-color: #ffb300; width: 3.5vh; height: 3.5vh; }
        #uranus { background-color: #00bcd4; width: 2vh; height: 2vh; }
        #neptune { background-color: #311b92; width: 2vh; height: 2vh; }

        /* Órbitas dos planetas */
        .orbit {
            position: absolute;
            top: 50%;
            left: 50%;
            border-radius: 50%;
            border: 1px solid rgba(255, 255, 255, 0.3);
            transform: translate(-50%, -50%);
        }

        #orbit-mercury { width: 15vh; height: 15vh; }
        #orbit-venus { width: 20vh; height: 20vh; }
        #orbit-earth { width: 25vh; height: 25vh; }
        #orbit-mars { width: 30vh; height: 30vh; }
        #orbit-jupiter { width: 40vh; height: 40vh; }
        #orbit-saturn { width: 50vh; height: 50vh; }
        #orbit-uranus { width: 60vh; height: 60vh; }
        #orbit-neptune { width: 70vh; height: 70vh; }

        /* Velocidades de animação dos planetas */
        #mercury { animation: orbit 67.6s linear infinite; }
        #venus { animation: orbit 173.08s linear infinite; }
        #earth { animation: orbit 280.77s linear infinite; }
        #mars { animation: orbit 528.46s linear infinite; }
        #jupiter { animation: orbit 3331.54s linear infinite; }
        #saturn { animation: orbit 8266.92s linear infinite; }
        #uranus { animation: orbit 23530s linear infinite; }
        #neptune { animation: orbit 46000s linear infinite; }

        @keyframes orbit {
            from {
                transform: rotate(0deg) translate(calc(var(--orbit-radius) / 2)) rotate(0deg);
            }
            to {
                transform: rotate(360deg) translate(calc(var(--orbit-radius) / 2)) rotate(-360deg);
            }
        }

        #mercury { --orbit-radius: 15vh; }
        #venus { --orbit-radius: 20vh; }
        #earth { --orbit-radius: 25vh; }
        #mars { --orbit-radius: 30vh; }
        #jupiter { --orbit-radius: 40vh; }
        #saturn { --orbit-radius: 50vh; }
        #uranus { --orbit-radius: 60vh; }
        #neptune { --orbit-radius: 70vh; }
    </style>
</head>
<body>
    <div class="container" role="region" aria-label="Sistema Solar animado">
        <div class="sun" aria-label="Sol"></div>
        <div class="orbit" id="orbit-mercury" aria-label="Órbita de Mercúrio"></div>
        <div class="planet" id="mercury" aria-label="Planeta Mercúrio"></div>
        <div class="orbit" id="orbit-venus" aria-label="Órbita de Vênus"></div>
        <div class="planet" id="venus" aria-label="Planeta Vênus"></div>
        <div class="orbit" id="orbit-earth" aria-label="Órbita da Terra"></div>
        <div class="planet" id="earth" aria-label="Planeta Terra"></div>
        <div class="orbit" id="orbit-mars" aria-label="Órbita de Marte"></div>
        <div class="planet" id="mars" aria-label="Planeta Marte"></div>
        <div class="orbit" id="orbit-jupiter" aria-label="Órbita de Júpiter"></div>
        <div class="planet" id="jupiter" aria-label="Planeta Júpiter"></div>
        <div class="orbit" id="orbit-saturn" aria-label="Órbita de Saturno"></div>
        <div class="planet" id="saturn" aria-label="Planeta Saturno"></div>
        <div class="orbit" id="orbit-uranus" aria-label="Órbita de Urano"></div>
        <div class="planet" id="uranus" aria-label="Planeta Urano"></div>
        <div class="orbit" id="orbit-neptune" aria-label="Órbita de Netuno"></div>
        <div class="planet" id="neptune" aria-label="Planeta Netuno"></div>
        <canvas id="stars" aria-hidden="true"></canvas>
    </div>

    <script>
        const canvas = document.getElementById('stars');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        function drawStars() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            for (let i = 0; i < 200; i++) {
                const x = Math.random() * canvas.width;
                const y = Math.random() * canvas.height;
                const size = Math.random() * 2;
                ctx.fillStyle = 'rgba(255, 255, 255, 0.8)';
                ctx.beginPath();
                ctx.arc(x, y, size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        drawStars();
    </script>
</body>
</html>
