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
            position: relative; /* Permite posicionamento absoluto dos planetas */
            width: 80vh; /* Largura do diâmetro da órbita - ajustável */
            height: 80vh; /* Altura do diâmetro da órbita - igual à largura para ser circular */
            animation: rotate 365s linear infinite; /* Animação de rotação do sistema */
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
            width: 10vh; /* Diâmetro do Sol - ajustável */
            height: 10vh; /* Diâmetro do Sol - igual à largura para ser circular */
            background-color: #ffc107; /* Cor do Sol - amarelo */
            border-radius: 50%;
            box-shadow: 0 0 20px #ffc107; /* Brilho do Sol - ajustável */
            transform: translate(-50%, -50%); /* Centraliza o Sol */
            z-index: 100; /* Garante que o Sol está acima dos outros elementos */
        }

        .planet {
            position: absolute;
            border-radius: 50%;
            top: 50%; /* Posição inicial no topo da órbita */
            left: 50%; /* Posição inicial no centro da órbita */
            transform: translate(-50%, -50%); /* Centraliza o planeta no seu ponto de órbita */
        }

        /* Cores e tamanhos dos planetas */
        #mercury {
            background-color: #4a148c; /* Roxo escuro */
            width: 1vh;
            height: 1vh;
        }
        #venus {
            background-color: #ff6f61; /* Laranja avermelhado */
            width: 1.2vh;
            height: 1.2vh;
        }
        #earth {
            background-color: #2196f3; /* Azul */
            width: 1.4vh;
            height: 1.4vh;
        }
        #mars {
            background-color: #d34836; /* Vermelho */
            width: 1.1vh;
            height: 1.1vh;
        }
        #jupiter {
            background-color: #f57c00; /* Laranja */
            width: 4vh;
            height: 4vh;
        }
        #saturn {
            background-color: #ffb300; /* Amarelo dourado */
            width: 3.5vh;
            height: 3.5vh;
        }
        #uranus {
            background-color: #00bcd4; /* Turquesa */
            width: 2vh;
            height: 2vh;
        }
        #neptune {
            background-color: #311b92; /* Roxo muito escuro */
            width: 2vh;
            height: 2vh;
        }

        /* Órbitas dos planetas */
        .orbit {
            position: absolute;
            top: 50%;
            left: 50%;
            border-radius: 50%;
            border: 1px solid rgba(255, 255, 255, 0.3); /* Cor da órbita - branco semi-transparente */
            transform: translate(-50%, -50%); /* Centraliza a órbita */
        }

        /* Tamanhos das órbitas (ajustados para não se sobreporem e espaçamento visual) */
        #orbit-mercury { width: 15vh; height: 15vh; }
        #orbit-venus { width: 20vh; height: 20vh; }
        #orbit-earth { width: 25vh; height: 25vh; }
        #orbit-mars { width: 30vh; height: 30vh; }
        #orbit-jupiter { width: 40vh; height: 40vh; }
        #orbit-saturn { width: 50vh; height: 50vh; }
        #orbit-uranus { width: 60vh; height: 60vh; }
        #orbit-neptune { width: 70vh; height: 70vh; }

        /* Velocidades de animação dos planetas (quanto menor, mais rápido) */
        #mercury { animation: orbit 67.6s linear infinite; } /* 88 / 1.3 = 67.6 */
        #venus { animation: orbit 173.08s linear infinite; } /* 225 / 1.3 = 173.08 */
        #earth { animation: orbit 280.77s linear infinite; } /* 365 / 1.3 = 280.77 */
        #mars { animation: orbit 528.46s linear infinite; } /* 687 / 1.3 = 528.46 */
        #jupiter { animation: orbit 3331.54s linear infinite; } /* 4331 / 1.3 = 3331.54 */
        #saturn { animation: orbit 8266.92s linear infinite; } /* 10747 / 1.3 = 8266.92 */
        #uranus { animation: orbit 23530s linear infinite; } /* 30589 / 1.3 = 23530 */
        #neptune { animation: orbit 46000s linear infinite; } /* 59800 / 1.3 = 46000 */

        @keyframes orbit {
            from {
                transform: rotate(0deg) translate(calc(var(--orbit-radius) / 2)) rotate(0deg);
            }
            to {
                transform: rotate(360deg) translate(calc(var(--orbit-radius) / 2)) rotate(-360deg);
            }
        }

        /* Correção para garantir que os planetas sigam suas órbitas corretamente */
        #mercury { --orbit-radius: 15vh; }
        #venus { --orbit-radius: 20vh; }
        #earth { --orbit-radius: 25vh; }
        #mars { --orbit-radius: 30vh; }
        #jupiter { --orbit-radius: 40vh; }
        #saturn { --orbit-radius: 50vh; }
        #uranus { --orbit-radius: 60vh; }
        #neptune { --orbit-radius: 70vh; }

        /* Estrela de fundo sutil */
        .star {
            position: absolute;
            background-color: #fff;
            border-radius: 50%;
            opacity: 0.5; /* Ajuste a opacidade para mais ou menos estrelas */
            animation: twinkle 2s infinite alternate; /* Animação de brilho */
        }

        @keyframes twinkle {
            from { opacity: 0.2; }
            to { opacity: 0.7; }
        }

        /* Estrelas cadentes */
        @keyframes shooting-star {
            from {
                transform: translateX(-100px) translateY(-100px);
                opacity: 0;
            }
            to {
                transform: translateX(100vw) translateY(100vh);
                opacity: 0;
            }
        }

        .shooting-star {
            position: absolute;
            background-color: #fff;
            border-radius: 50%;
            width: 2px;
            height: 2px;
            opacity: 0.8;
            animation: shooting-star 3s ease-out infinite; /* Ajuste a duração e o timing */
            /* Adicionei esses estilos para controlar o rastro */
            box-shadow: 0 0 6px rgba(255, 255, 255, 0.6); /* Brilho da estrela cadente */
            &::after {
                content: '';
                position: absolute;
                top: 0;
                left: 0;
                width: 60px; /* Comprimento do rastro */
                height: 1px; /* Espessura do rastro */
                background: linear-gradient(to right, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0)); /* Gradiente para o rastro */
                transform: rotate(-45deg); /* Incline o rastro */
                transform-origin: 0 0; /* Garante que a rotação começa do início do rastro */
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="sun"></div>
        <div class="orbit" id="orbit-mercury"></div>
        <div class="planet" id="mercury"></div>
        <div class="orbit" id="orbit-venus"></div>
        <div class="planet" id="venus"></div>
        <div class="orbit" id="orbit-earth"></div>
        <div class="planet" id="earth"></div>
        <div class="orbit" id="orbit-mars"></div>
        <div class="planet" id="mars"></div>
        <div class="orbit" id="orbit-jupiter"></div>
        <div class="planet" id="jupiter"></div>
        <div class="orbit" id="orbit-saturn"></div>
        <div class="planet" id="saturn"></div>
        <div class="orbit" id="orbit-uranus"></div>
        <div class="planet" id="uranus"></div>
        <div class="orbit" id="orbit-neptune"></div>
        <div class="planet" id="neptune"></div>
    </div>

    <script>
        const container = document.querySelector('.container');

        // Adiciona estrelas de fundo
        function addStars() {
            for (let i = 0; i < 200; i++) { // Ajuste o número de estrelas conforme necessário
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = `${Math.random() * 100}vw`;
                star.style.top = `${Math.random() * 100}vh`;
                star.style.width = `${Math.random() * 2 + 1}px`; // Tamanho aleatório
                star.style.height = `${Math.random() * 2 + 1}px`; // Tamanho aleatório
                container.appendChild(star);
            }
        }
        addStars();

        // Função para criar estrela cadente
        function createShootingStar() {
            const shootingStar = document.createElement('div');
            shootingStar.className = 'shooting-star';
            shootingStar.style.left = `${Math.random() * 100}vw`;
            shootingStar.style.top = `${Math.random() * 100}vh`;
            container.appendChild(shootingStar);

            // Remove a estrela cadente após a animação terminar
            setTimeout(() => {
                shootingStar.remove();
            }, 3000); // Corresponde à duração da animação
        }

        // Cria estrelas cadentes em intervalos aleatórios
        setInterval(createShootingStar, 2000); // Ajuste a frequência das estrelas cadentes
    </script>
</body>
</html>
