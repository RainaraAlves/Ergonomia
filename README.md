<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PIAE - Protocolo Integrado de Avaliação Ergonômica</title>
    <style>
        body { font-family: 'Segoe UI', Arial, sans-serif; background-color: #f0f2f5; display: flex; justify-content: center; padding: 20px; }
        .container { background: white; width: 100%; max-width: 500px; padding: 30px; border-radius: 12px; box-shadow: 0 8px 24px rgba(0,0,0,0.1); }
        h1 { color: #1a73e8; font-size: 22px; text-align: center; margin-bottom: 10px; }
        p.subtitle { text-align: center; color: #5f6368; font-size: 14px; margin-bottom: 25px; }
        
        .field { margin-bottom: 20px; }
        label { display: block; font-weight: 600; margin-bottom: 8px; color: #3c4043; }
        select { width: 100%; padding: 12px; border: 2px solid #dadce0; border-radius: 8px; font-size: 16px; outline: none; transition: border-color 0.2s; }
        select:focus { border-color: #1a73e8; }

        button { width: 100%; padding: 15px; background-color: #1a73e8; color: white; border: none; border-radius: 8px; font-size: 16px; font-weight: bold; cursor: pointer; transition: background 0.2s; }
        button:hover { background-color: #1557b0; }

        #resultado-box { margin-top: 25px; padding: 20px; border-radius: 8px; display: none; text-align: center; }
        .res-titulo { font-size: 14px; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 5px; }
        .res-nivel { font-size: 32px; font-weight: 900; margin: 0; }
        
        /* Cores dos Níveis de Ação */
        .na-1 { background-color: #ccffcc; color: #006600; border: 2px solid #006600; }
        .na-2 { background-color: #ffffcc; color: #666600; border: 2px solid #666600; }
        .na-3 { background-color: #ffebcc; color: #994d00; border: 2px solid #994d00; }
        .na-4 { background-color: #ffcccc; color: #990000; border: 2px solid #990000; }
    </style>
</head>
<body>

<div class="container">
    <h1>Protocolo PIAE</h1>
    <p class="subtitle">Insira as pontuações conforme a planilha do TCC</p>

    <div class="field">
        <label>Pontuação RULA / REBA:</label>
        <select id="rula_reba">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
            <option value="7">7 ou +</option>
        </select>
    </div>

    <div class="field">
        <label>Categoria de Risco OWAS:</label>
        <select id="owas">
            <option value="1">1 (Risco Normal)</option>
            <option value="2">2 (Requer Atenção)</option>
            <option value="3">3 (Mudanças em Breve)</option>
            <option value="4">4 (Mudanças Imediatas)</option>
        </select>
    </div>

    <button onclick="calcularPIAE()">Consultar Tabela PIAE</button>

    <div id="resultado-box">
        <p class="res-titulo">Nível de Ação Integrado</p>
        <p id="nivel-valor" class="res-nivel"></p>
        <p id="desc-acao" style="font-size: 13px; margin-top: 10px; font-weight: 500;"></p>
    </div>
</div>

<script>
    function calcularPIAE() {
        const rr = parseInt(document.getElementById('rula_reba').value);
        const ow = parseInt(document.getElementById('owas').value);
        const box = document.getElementById('resultado-box');
        const nivelTxt = document.getElementById('nivel-valor');
        const acaoTxt = document.getElementById('desc-acao');

        let na = 0;
        let acao = "";

        // LÓGICA DA MATRIZ DA PLANILHA (AJUSTE OS NÚMEROS ABAIXO)
        // Aqui simulamos o cruzamento de linhas e colunas
        if (ow === 1) {
            if (rr <= 2) na = 1;
            else if (rr <= 4) na = 2;
            else na = 3;
        } else if (ow === 2) {
            if (rr <= 3) na = 2;
            else na = 3;
        } else if (ow === 3) {
            if (rr <= 2) na = 2;
            else if (rr <= 6) na = 3;
            else na = 4;
        } else if (ow === 4) {
            na = 4;
        }

        // Definição das frases de ação baseadas no nível
        const orientacoes = [
            "",
            "Postura aceitável; nenhum risco imediato identificado.",
            "Investigar mais detalhadamente; implementar melhorias se possível.",
            "Mudanças necessárias no curto prazo para evitar afastamentos.",
            "Risco crítico! Interrupção ou alteração imediata da atividade."
        ];

        // Exibição do resultado
        box.style.display = 'block';
        box.className = 'na-' + na;
        nivelTxt.innerText = na;
        acaoTxt.innerText = orientacoes[na];
    }
</script>

</body>
</html>
