<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Confirmação do Futebol</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; text-align: center; background: #eef2f3; padding: 20px; color: #333; }
        .container { max-width: 400px; background: white; padding: 30px; margin: auto; border-radius: 15px; box-shadow: 0 10px 25px rgba(0,0,0,0.05); }
        h2 { margin-top: 0; color: #1e3c72; }
        input[type="text"] { width: 90%; padding: 12px; margin-bottom: 15px; border: 2px solid #ddd; border-radius: 8px; font-size: 16px; outline: none; }
        input[type="text"]:focus { border-color: #2a5298; }
        button { background: #28a745; color: white; border: none; padding: 12px 25px; font-size: 16px; border-radius: 8px; cursor: pointer; width: 96%; font-weight: bold; }
        button:hover { background: #218838; }
        .status { font-weight: bold; font-size: 18px; padding: 15px; margin: 20px 0; border-radius: 8px; }
        .confirmado { background: #d4edda; color: #155724; border: 1px solid #c3e6cb; }
        .cancelado { background: #f8d7da; color: #721c24; border: 1px solid #f5c6cb; }
        ul { list-style: none; padding: 0; text-align: left; margin-top: 20px; }
        li { padding: 12px; border-bottom: 1px solid #eee; display: flex; justify-content: space-between; font-size: 16px; }
        .btn-limpar { background: none; border: none; color: #dc3545; cursor: pointer; font-size: 14px; text-decoration: underline; margin-top: 20px; }
    </style>
</head>
<body>
    <div class="container">
        <h2>⚽ Lista do Futebol</h2>
        <p>Digite seu nome para confirmar presença na partida de hoje.</p>
        
        <input type="text" id="nomeJogador" placeholder="Seu nome completo">
        <button onclick="confirmarPresenca()">Confirmar Minha Presença</button>

        <div id="statusFut" class="status cancelado">❌ FUT CANCELADO! Faltam 10 jogadores.</div>

        <h3>Confirmados (<span id="total">0</span>/10)</h3>
        <ul id="lista"></ul>
        
        <button class="btn-limpar" onclick="limparLista()">Limpar Lista para Próximo Jogo</button>
    </div>

    <script>
        let jogadores = JSON.parse(localStorage.getItem('futebol_jogadores')) || [];

        function atualizarTela() {
            const listaElement = document.getElementById('lista');
            const totalElement = document.getElementById('total');
            const statusElement = document.getElementById('statusFut');
            
            listaElement.innerHTML = '';
            jogadores.forEach(nome => {
                listaElement.innerHTML += `<li><span>🏃 ${nome}</span></li>`;
            });

            totalElement.innerText = jogadores.length;

            if (jogadores.length >= 10) {
                statusElement.innerText = "⚽ FUT CONFIRMADO! Podem reservar a quadra!";
                statusElement.className = "status confirmado";
            } else {
                statusElement.innerText = `❌ FUT CANCELADO! Faltam ${10 - jogadores.length} jogadores.`;
                statusElement.className = "status cancelado";
            }
            
            localStorage.setItem('futebol_jogadores', JSON.stringify(jogadores));
        }

        function confirmarPresenca() {
            const campoNome = document.getElementById('nomeJogador');
            const nome = campoNome.value.trim();
            
            if (nome === '') {
                alert('Por favor, digite o seu nome!');
                return;
            }
            
            if (jogadores.includes(nome)) {
                alert('Você já está confirmado nesta lista!');
                return;
            }

            jogadores.push(nome);
            campoNome.value = '';
            atualizarTela();
        }

        function limparLista() {
            if (confirm('Tem certeza que deseja apagar todos os nomes e começar uma nova lista?')) {
                jogadores = [];
                atualizarTela();
            }
        }

        atualizarTela();
    </script>
</body>
</html>
