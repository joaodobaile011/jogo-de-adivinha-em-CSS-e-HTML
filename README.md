# jogo-de-adivinha-em-CSS-e-HTML
jogo de adivinha para crianças em ingles
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jogo de Adivinhação de Cores</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(45deg, #ff6ec7, #f7a8b8);
            color: white;
            text-align: center;
        }
        h1 {
            font-size: 3rem;
            margin-bottom: 20px;
        }
        .color-box {
            width: 300px;
            height: 300px;
            margin: 20px 0;
            border-radius: 15px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.3);
        }
        .btn {
            padding: 10px 20px;
            font-size: 1.2rem;
            margin: 5px;
            cursor: pointer;
            border: none;
            border-radius: 10px;
            background-color: #ff5f52;
            color: white;
            transition: transform 0.2s;
        }
        .btn:hover {
            transform: scale(1.1);
        }
        .result {
            font-size: 1.5rem;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <div>
        <h1>Adivinha a cor!</h1>
        <div id="colorBox" class="color-box"></div>
        <input type="text" id="guessInput" placeholder="Digite a cor..." style="padding: 10px; font-size: 1rem; border-radius: 10px;">
        <div class="btn" onclick="checkGuess()">Verificar</div>
        <div class="result" id="resultText"></div>
        <div class="btn" onclick="newColor()">Nova cor</div>
    </div>

    <script>
        const colors = ["red", "green", "blue", "yellow", "pink", "purple", "orange", "cyan", "lime", "brown"];
        let currentColor;

        // Função para gerar uma cor aleatória
        function generateRandomColor() {
            const randomIndex = Math.floor(Math.random() * colors.length);
            currentColor = colors[randomIndex];
            document.getElementById("colorBox").style.backgroundColor = currentColor;
        }

        // Função para verificar a adivinhação do usuário
        function checkGuess() {
            const userGuess = document.getElementById("guessInput").value.toLowerCase();
            const resultText = document.getElementById("resultText");

            if (userGuess === currentColor) {
                resultText.textContent = "Você acertou!";
                resultText.style.color = "green";
            } else {
                resultText.textContent = "Errou! A cor era " + currentColor;
                resultText.style.color = "red";
            }
        }

        // Função para carregar uma nova cor
        function newColor() {
            generateRandomColor();
            document.getElementById("guessInput").value = ""; // Limpar o campo de entrada
            document.getElementById("resultText").textContent = ""; // Limpar resultado anterior
        }

        // Gerar a primeira cor quando a página for carregada
        window.onload = newColor;
    </script>
</body>
</html>

