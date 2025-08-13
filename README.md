<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A cada toque...</title>
<style>
    body {
        margin: 0;
        height: 100vh;
        background: linear-gradient(135deg, #ffb6c1, #ffc0cb, #ff69b4);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-family: 'Arial', sans-serif;
        color: white;
        overflow: hidden;
        position: relative;
    }

    h1 {
        font-size: 2rem;
        text-align: center;
        margin: 20px;
        text-shadow: 2px 2px 5px rgba(0,0,0,0.3);
    }

    .mensagem {
        font-size: 1.5rem;
        text-align: center;
        font-weight: bold;
        min-height: 50px;
        transition: opacity 0.5s ease;
    }

    /* Corações no fundo */
    .coracao {
        position: absolute;
        color: pink;
        font-size: 1.5rem;
        animation: flutuar 6s linear infinite;
        opacity: 0.7;
    }

    @keyframes flutuar {
        0% {
            transform: translateY(100vh) scale(1);
            opacity: 0.7;
        }
        100% {
            transform: translateY(-10vh) scale(1.5);
            opacity: 0;
        }
    }
</style>
</head>
<body>

<h1>A cada toque na tela eu sinto...</h1>
<div class="mensagem" id="mensagem"></div>

<script>
    const mensagens = [
        "saudades do seu abraço",
        "a sua falta no meu dia",
        "vontade de te beijar",
        "orgulho de quem você é!",
        "uma vontade de te ligar",
        "vontade de te fazer sorrir",
        "vontade de te fazer feliz"
    ];

    let indice = 0;
    const msgEl = document.getElementById("mensagem");

    document.body.addEventListener("click", () => {
        msgEl.style.opacity = 0;
        setTimeout(() => {
            msgEl.textContent = mensagens[indice];
            msgEl.style.opacity = 1;
            indice = (indice + 1) % mensagens.length;
        }, 300);

        criarCoracao();
    });

    function criarCoracao() {
        const coracao = document.createElement("div");
        coracao.classList.add("coracao");
        coracao.textContent = "❤";
        coracao.style.left = Math.random() * 100 + "vw";
        coracao.style.fontSize = (Math.random() * 20 + 15) + "px";
        document.body.appendChild(coracao);

        setTimeout(() => {
            coracao.remove();
        }, 6000);
    }
</script>

</body>
</html>
