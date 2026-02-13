<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PIAE - Avaliação Ergonômica</title>
    <style>
        :root {
            --primary: #2c3e50; --accent: #3498db; --bg: #f8f9fa;
        }
        body { font-family: 'Segoe UI', sans-serif; background: var(--bg); color: var(--primary); margin: 0; padding: 20px; }
        .container { max-width: 800px; margin: auto; background: white; padding: 25px; border-radius: 15px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
        h1 { text-align: center; border-bottom: 3px solid var(--accent); padding-bottom: 10px; }
        
        .metodo-section { margin-top: 30px; border: 1px solid #ddd; padding: 15px; border-radius: 10px; }
        .metodo-title { font-weight: bold; background: var(--primary); color: white; padding: 10px; margin: -15px -15px 15px -15px; border-radius: 10px 10px 0 0; }
        
        .pergunta { margin-bottom: 20px; }
        .pergunta label { display: block; margin-bottom: 8px; font-weight: 600; font-size: 14px; }
        
        /* Estilo dos Botões de Opção */
        .btn-group { display: flex; flex-wrap: wrap; gap: 10px; }
        .btn-option { 
            flex: 1; min-width: 100px; padding: 12px; border: 2px solid #ddd; 
            border-radius: 8px; background: white; cursor: pointer; text-align: center;
            transition: 0.3s; font-size: 13px; font-weight: 500;
        }
        .btn-option:hover { border-color: var(--accent); background: #f0f7ff; }
        .btn-option.active { background: var(--accent); color: white; border-color: var(--accent); }

        .btn-calcular { 
            width: 100%; padding: 20px; background: #27ae60; color: white; 
            border: none; border-radius: 10px; font-size: 18px; font-weight: bold; 
            cursor: pointer; margin-top: 30px; 
        }
        .btn-calcular:hover { background: #219150; }

        #resultado-piae { 
            margin-top: 30px; padding: 25px; border-radius: 10px; 
            display: none; text-align: center; 
        }
        .nivel-card { font-size: 40px; font-weight: 900; margin: 10px 0; }
    </style>
</head>
<body>

<div class="container">
    <h1>Protocolo PIAE</h1>
    <p style="text-align: center;">Preencha as posições observadas no posto de trabalho.</p>

    <div class="metodo-section">
        <div class="metodo-title">MÉTODO OWAS (Costas, Braços e Pernas)</div>
        
        <div class="pergunta">
            <label>Posição das Costas:</label>
            <div class="btn-group" id="owas_costas">
                <div class="btn-option" onclick="selectOpt(this, 'c1')">1. Ereta</div>
                <div class="btn-option" onclick="selectOpt(this, 'c2')">2. Inclinada</div>
                <div class="btn-option" onclick="selectOpt(this, 'c3')">3. Girada</div>
                <div class="btn-option" onclick="selectOpt(this, 'c4')">4. Inc./Girada</div>
            </div>
        </div>

        <div class="pergunta">
            <label>Braços:</label>
            <div class="btn-group" id="owas_bracos">
                <div class="btn-option" onclick="selectOpt(this, 'b1')">1. Ambos abaixo</div>
                <div class="btn-option" onclick="selectOpt(this, 'b2')">2. Um no nível/acima</div>
                <div class="btn-option" onclick="selectOpt(this, 'b3')">3. Ambos acima</div>
            </div>
        </div>
    </div>

    <div class="metodo-section">
        <div class="metodo-title">MÉTODO RULA / REBA (Membros Superiores)</div>
        
        <div class="pergunta">
            <label>Inclinação do Tronco:</label>
            <div class="btn-group" id="rula_tronco">
                <div class="btn-option" onclick="selectOpt(this, 't1')">Ereto (0°)</div>
                <div class="btn-option" onclick="selectOpt(this, 't2')">0-20°</div>
                <div class="btn-option" onclick="selectOpt(this, 't3')">20-60°</div>
                <div class="btn-option" onclick="selectOpt(this, 't4')">>60°</div>
            </div>
        </div>

        <div class="pergunta">
            <label>Esforço / Carga:</label>
            <div class="btn-group" id="rula_carga">
                <div class="btn-option" onclick="selectOpt(this, 'l1')">< 5kg</div>
                <div class="btn-option" onclick="selectOpt(this, 'l2')">5 a 10kg</div>
                <div class="btn-option" onclick="selectOpt(this, 'l3')">> 10kg</div>
            </div>
        </div>
    </div>

    <button class="btn-calcular" onclick="calcularPIAE()">CALCULAR RESULTADO INTEGRADO</button>

    <div id="resultado-piae">
        <div style="font-weight: bold; text-transform: uppercase;">Nível de Ação PIAE</div>
        <div id="nivel-num" class="nivel-card">--</div>
        <div id="nivel-desc"></div>
    </div>
</div>

<script>
    // Objeto para armazenar as seleções
    let selections = {};

    function selectOpt(el, val) {
        // Remove 'active' de todos os irmãos
        const parent = el.parentElement;
        Array.from(parent.children).forEach(child => child.classList.remove('active'));
        // Adiciona 'active' no clicado
        el.classList.add('active');
        // Salva valor
        selections[parent.id] = val;
    }

    function calcularPIAE() {
        // Validação simples
        if (Object.keys(selections).length < 4) {
            alert("Por favor, selecione todas as posições antes de calcular.");
            return;
        }

        // Lógica de cálculo (Simulação da Matriz da sua planilha)
        // No seu TCC, aqui entra a fórmula exata que cruza os dados
        let scoreRula = parseInt(selections.rula_tronco.replace('t','')) + parseInt(selections.rula_carga.replace('l',''));
        let catOwas = parseInt(selections.owas_costas.replace('c','')); 

        let naFinal = 1;
        
        // Exemplo de cruzamento de matriz PIAE
        if(catOwas >= 3 || scoreRula >= 5) naFinal = 4;
        else if(catOwas == 2 || scoreRula >= 3) naFinal = 3;
        else if(catOwas == 1 && scoreRula == 2) naFinal = 2;
        else naFinal = 1;

        // Exibir Resultado
        const resDiv = document.getElementById('resultado-piae');
        const numDiv = document.getElementById('nivel-num');
        const descDiv = document.getElementById('nivel-desc');
        
        resDiv.style.display = 'block';
        numDiv.innerText = naFinal;

        const cores = ["", "#2ecc71", "#f1c40f", "#e67e22", "#e74c3c"];
        const textos = [
            "",
            "RISCO BAIXO: Postura aceitável.",
            "RISCO MÉDIO: Necessita investigação.",
            "RISCO ALTO: Mudanças requeridas em breve.",
            "RISCO CRÍTICO: Mudanças imediatas!"
        ];

        resDiv.style.backgroundColor = cores[naFinal];
        resDiv.style.color = (naFinal == 2) ? 'black' : 'white';
        descDiv.innerText = textos[naFinal];
    }
</script>

</body>
</html>
