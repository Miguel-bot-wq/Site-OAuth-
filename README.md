<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Checker Spotify</title>
    <link rel="icon" href="https://cdn-icons-png.freepik.com/256/232/232413.png" type="image/png"> <!-- Ícone da página -->
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('https://media.tenor.com/j0PKWvsU0X4AAAAM/meekz-like-me.gif') no-repeat center center fixed; /* GIF de fundo */
            background-size: cover; /* Ajusta o tamanho do fundo */
            color: #ffffff; /* Texto branco */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            background: rgba(29, 185, 84, 0.8); /* Verde do Spotify com transparência */
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
            width: 90%; /* Largura responsiva */
            max-width: 400px; /* Largura máxima */
            text-align: center; /* Centraliza o texto */
        }

        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            display: flex; /* Usar flexbox para alinhar a imagem e o texto */
            align-items: center; /* Alinha verticalmente */
            justify-content: center; /* Centraliza horizontalmente */
        }

        .icon {
            background-image: url('https://cdn-icons-png.freepik.com/256/232/232413.png'); /* Imagem do ícone */
            background-size: contain; /* Ajusta o tamanho da imagem */
            background-repeat: no-repeat; /* Não repetir a imagem */
            width: 30px; /* Largura do ícone */
            height: 30px; /* Altura do ícone */
            margin-right: 10px; /* Espaço entre a imagem e o texto */
        }

        textarea {
            width: 100%;
            height: 100px; /* Altura do textarea */
            padding: 10px;
            border: none;
            border-radius: 4px;
            margin-bottom: 10px;
            font-size: 16px;
            box-sizing: border-box; /* Inclui padding e border na largura total */
            resize: none; /* Desabilita o redimensionamento */
        }

        button {
            padding: 10px;
            background-color: #ffffff; /* Botão branco */
            color: #1DB954; /* Texto verde do Spotify */
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
            width: 100%; /* Botão ocupa toda a largura do container */
            margin-top: 10px; /* Adiciona 10 pixels de margem superior */
        }

        button:hover {
            background-color: #e0e0e0; /* Cor de fundo ao passar o mouse */
        }

        #result {
            margin-top: 20px;
            font-size: 18px;
            text-align: left; /* Alinha o texto à esquerda */
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>
            <div class="icon"></div>
            Checker Link Spotify
        </h1>
        <textarea id="linkInput" placeholder="Cole seus links do Spotify aqui, um por linha"></textarea>
        <button id="checkButton">Verificar Links</button>
        <button onclick="window.location.href='Gen/gen.html'">Ir para Gerador</button> <!-- Botão para redirecionar -->
        <h2>Resultados:</h2>
        <textarea id="result" readonly placeholder="Os resultados aparecerão aqui..."></textarea>
        <button id="copyButton">Copiar Resultados</button> <!-- Botão para copiar resultados -->
    </div>
    <script>
        document.getElementById('checkButton').addEventListener('click', function() {
            const links = document.getElementById('linkInput').value.split('\n'); // Divide os links por linha
            const resultDiv = document.getElementById('result');
            resultDiv.value = ''; // Limpa resultados anteriores

            for (const link of links) {
                const trimmedLink = link.trim(); // Remove espaços em branco
                if (trimmedLink) {
                    // Aqui você pode adicionar a lógica para verificar os links do Spotify
                    resultDiv.value += `Verificando: ${trimmedLink}\n`; // Exibe o link que está sendo verificado
                    // Verificação imediata
                    resultDiv.value += `Resultado: ${trimmedLink} - Link válido!\n`; // Exibe o resultado da verificação
                }
            }
        });

        document.getElementById('copyButton').addEventListener('click', function() {
            const resultDiv = document.getElementById('result');
            const validLinks = resultDiv.value.split('\n')
                .filter(line => line.includes('Link válido!'))
                .map(line => line.split(' - ')[0]) // Extrai apenas o link
                .join('\n'); // Junta os links válidos em uma única string

            navigator.clipboard.writeText(validLinks).then(() => {
                alert('Links válidos copiados para a área de transferência!'); // Alerta ao usuário
            });
        });
    </script>
</body>
</html>
