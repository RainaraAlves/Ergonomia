<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>PIAE - Protocolo Integrado</title>
    <style>
        :root {
            --azul-pet: #1a73e8;
            --cinza-bg: #f1f3f4;
        }
        body { font-family: 'Segoe UI', Arial, sans-serif; background: var(--cinza-bg); padding: 20px; }
        .container { max-width: 900px; margin: auto; background: white; padding: 25px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); }
        
        h1 { color: var(--azul-pet); text-align: center; margin-bottom: 30px; font-size: 24px; border-bottom: 2px solid #ddd; padding-bottom: 10px; }
        
        .grid-container { display: grid; grid-template-columns: 1fr 1fr; gap: 30px; }
        .metodo-card { border: 1px solid #dadce0; border-radius: 8px; padding: 15px; }
        .metodo-card h3 { margin-top: 0; background: #f8f9fa; padding: 10px; border-radius: 4px; font-size: 16px; text-align: center; border-bottom: 2px solid #1a73e8; }

        .label-grupo { font-weight: bold; font-size: 13px; margin: 15px 0 8px 0; display: block; color: #5f6368; }
        
        /* Grade de Botões */
        .botoes-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 5px; }
        .btn-pos { 
            padding: 10px 5px; border: 1px solid #ccc; background: white; 
            cursor: pointer; font-size: 14px; font-weight: bold; border-radius: 4px;
            transition: 0.2s;
        }
        .btn-pos:hover { background: #e8f0fe; }
        .btn-pos.active { background: var(--azul-pet); color: white; border-color: var(--azul-pet); }

        /* Botão de Calcular */
        .btn-final { 
            grid-column: span 2; margin-top: 30px; padding: 15px; 
            background: #202124; color: white; border: none; border-radius: 4px; 
            font-size: 16px; font-weight: bold; cursor: pointer;
        }
        .btn-final:hover { background: #000; }

        /* Resultado */
        #resultado-piae { 
            margin-top: 25px; padding: 20px; border-radius: 8px; 
            display: none; text-align: center; border: 3px solid transparent;
        }
        .na-valor { font-size: 48px; font-weight: 900; margin: 5px 0; }
    </style>
</head>
<body>

<div class="container">
    <h1>Avaliação Ergonômica - Aba PIAE</h1>

    <div class="grid-container">
        <div class="metodo-card">
            <h3>SCORE FINAL RULA / REBA</h3>
            <span class="label-grupo">Selecione a pontuação obtida:</span>
            <div class="botoes-row" id="grupo-rr">
                <button class="btn-pos" onclick="setVal('rr', 1, this)">1</button>
                <button class="btn-pos" onclick="setVal('rr', 2, this)">2</button>
                <button class="btn-pos" onclick="setVal('rr', 3, this)">3</button>
                <button class="btn-pos" onclick="setVal('rr', 4, this)">4</button>
                <button class="btn-pos" onclick="setVal('rr', 5, this)">5</button>
                <button class="btn-pos" onclick="setVal('rr', 6, this)">6</button>
                <button class="btn-pos" onclick="setVal('rr', 7, this)">7+</button>
            </div>
        </div>

        <div class="metodo-card">
            <h3>CATEGORIA DE RISCO OWAS</h3>
            <span class="label-grupo">Selecione a categoria obtida:</span>
            <div class="botoes-row" id="grupo-ow">
                <button class="btn-pos" onclick="setVal('ow', 1, this)">1</button>
                <button class="btn-pos" onclick="setVal('ow', 2, this)">2</button>
                <button class="btn-pos" onclick="setVal('ow', 3, this)">3</button>
                <button class="btn-pos" onclick="setVal('ow', 4, this)">4</button>
            </div>
        </div>

        <button class="btn-final" onclick="processarPIAE()">GERAR NÍVEL DE AÇÃO INTEGRADO</button>
    </div>

    <div id="resultado-piae">
        <div style="font-weight: bold; text-transform: uppercase; letter-spacing: 1px;">Nível de Ação (PIAE)</div>
        <div class="na-valor" id="na-display">0</div>
        <div id="na-legenda" style="font-weight: bold;"></div>
    </div>
</div>

<script>
    let dados = { rr: 0, ow: 0 };

    function setVal(tipo, valor, el) {
        // Remove 'active' do grupo específico
        const botoes = el.parentElement.querySelectorAll('.btn-pos');
        botoes.forEach(b => b.classList.remove('active'));
        
        // Ativa o clicado
        el.classList.add('active');
        dados[tipo] = valor;
    }

    function processarPIAE() {
        if (dados.rr === 0 || dados.ow === 0) {
            alert("Selecione os valores de ambos os métodos!");
            return;
        }

        const resDiv = document.getElementById('resultado-piae');
        const naDisplay = document.getElementById('na-display');
        const naLegenda = document.getElementById('na-legenda');

        // Lógica da Matriz PIAE (Exatamente como na sua planilha)
        let na = 0;
        if (dados.ow === 1) {
            na = (dados.rr <= 2) ? 1 : (dados.rr <= 5) ? 2 : 3;
        } else if (dados.ow === 2) {
            na = (dados.rr <= 4) ? 2 : 3;
        } else if (dados.ow === 3) {
            na = (dados.rr <= 3) ? 2 : (dados.rr <= 6) ? 3 : 4;
        } else if (dados.ow === 4) {
            na = 4;
        }

        // Configuração visual do resultado
        resDiv.style.display = 'block';
        naDisplay.innerText = na;

        const config = [
            {},
            { cor: '#ccffcc', borda: '#008000', texto: 'NÍVEL 1: Baixo Risco - Postura Aceitável' },
            { cor: '#ffffcc', borda: '#b8b800', texto: 'NÍVEL 2: Médio Risco - Requer Atenção' },
            { cor: '#ffe5cc', borda: '#d35400', texto: 'NÍVEL 3: Alto Risco - Mudanças em Breve' },
            { cor: '#ffcccc', borda: '#c0392b', texto: 'NÍVEL 4: Crítico - Mudanças Imediatas' }
        ];

        resDiv.style.backgroundColor = config[na].cor;
        resDiv.style.borderColor = config[na].borda;
        resDiv.style.color = config[na].borda;
        naLegenda.innerText = config[na].texto;
    }
</script>

</body>
</html>
