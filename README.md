<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PIAE - Plataforma Inteligente de Análise Ergonômica</title>

<style>
body {
    font-family: Arial, sans-serif;
    background: #f4f6f9;
    padding: 30px;
}

h1 {
    text-align: center;
}

.section {
    background: white;
    padding: 20px;
    margin-bottom: 20px;
    border-radius: 8px;
    box-shadow: 0 3px 8px rgba(0,0,0,0.05);
}

select {
    width: 100%;
    padding: 8px;
    margin-top: 5px;
    margin-bottom: 15px;
}

button {
    width: 100%;
    padding: 15px;
    font-size: 16px;
    background: #004aad;
    color: white;
    border: none;
    border-radius: 6px;
    cursor: pointer;
}

.result {
    margin-top: 20px;
    padding: 20px;
    background: #e9f0ff;
    border-radius: 8px;
}
</style>
</head>

<body>

<h1>PIAE - Avaliação Ergonômica Integrada</h1>

<form id="ergonomicForm">

<!-- PESCOÇO -->
<div class="section">
<h2>Pescoço</h2>
<select id="pescoco">
    <option value="0">Selecione a posição observada</option>
</select>
</div>

<!-- TRONCO -->
<div class="section">
<h2>Tronco</h2>
<select id="tronco">
    <option value="0">Selecione a posição observada</option>
</select>
</div>

<!-- PERNAS -->
<div class="section">
<h2>Pernas</h2>
<select id="pernas">
    <option value="0">Selecione a posição observada</option>
</select>
</div>

<!-- BRAÇOS -->
<div class="section">
<h2>Braços</h2>
<select id="bracos">
    <option value="0">Selecione a posição observada</option>
</select>
</div>

<!-- ANTEBRAÇOS -->
<div class="section">
<h2>Antebraços</h2>
<select id="antebracos">
    <option value="0">Selecione a posição observada</option>
</select>
</div>

<!-- PUNHOS -->
<div class="section">
<h2>Punhos</h2>
<select id="punhos">
    <option value="0">Selecione a posição observada</option>
</select>
</div>

<!-- CARGA / FORÇA -->
<div class="section">
<h2>Carga / Força</h2>
<select id="carga">
    <option value="0">Selecione</option>
</select>
</div>

<button type="button" onclick="calculate()">Calcular Avaliação</button>

<div class="result" id="resultado"></div>

</form>

<script>

// -------- AQUI VOCÊ COLOCA AS OPÇÕES EXATAS DA PLANILHA PIAE --------

// Exemplo (substitua pelos textos EXATOS da planilha)
const opcoesPIAE = {
    pescoco: [
        {texto: "0 a 10°", valor: 1},
        {texto: "10 a 20°", valor: 2},
        {texto: "+20°", valor: 3},
        {texto: "Extensão", valor: 4}
    ],
    tronco: [
        {texto: "0 a 20°", valor: 1},
        {texto: "20 a 60°", valor: 2},
        {texto: "+60°", valor: 3}
    ],
    pernas: [
        {texto: "Sentado estável", valor: 1},
        {texto: "Em pé estável", valor: 2},
        {texto: "Instável", valor: 3}
    ],
    bracos: [
        {texto: "0 a 20 / extensão e flexão", valor: 1},
        {texto: "Flexão +20 e extensão 20 e 45", valor: 2},
        {texto: "Extensão 45 a 90", valor: 3}
    ],
    antebracos: [
        {texto: "60 a 100°", valor: 1},
        {texto: "<60°", valor: 2},
        {texto: ">100°", valor: 3}
    ],
    punhos: [
        {texto: "Neutro", valor: 1},
        {texto: "Flexão / extensão leve", valor: 2},
        {texto: "Desvio acentuado", valor: 3}
    ],
    carga: [
        {texto: "< 5kg", valor: 1},
        {texto: "5 a 10kg", valor: 2},
        {texto: "> 10kg", valor: 3}
    ]
};


// -------- GERAR AUTOMATICAMENTE OS SELECTS --------

function preencherSelect(id, opcoes) {
    const select = document.getElementById(id);
    opcoes.forEach(opcao => {
        const option = document.createElement("option");
        option.value = opcao.valor;
        option.textContent = opcao.texto;
        select.appendChild(option);
    });
}

for (let parte in opcoesPIAE) {
    preencherSelect(parte, opcoesPIAE[parte]);
}


// -------- CÁLCULO INTEGRADO --------

function calculate() {

    const valores = {
        pescoco: parseInt(document.getElementById("pescoco").value),
        tronco: parseInt(document.getElementById("tronco").value),
        pernas: parseInt(document.getElementById("pernas").value),
        bracos: parseInt(document.getElementById("bracos").value),
        antebracos: parseInt(document.getElementById("antebracos").value),
        punhos: parseInt(document.getElementById("punhos").value),
        carga: parseInt(document.getElementById("carga").value)
    };

    // Simulação de cálculo separado (você vai substituir pela lógica real)
    let rula = valores.pescoco + valores.bracos + valores.antebracos + valores.punhos;
    let reba = valores.tronco + valores.pernas + valores.carga;
    let owas = valores.tronco + valores.bracos + valores.pernas;

    document.getElementById("resultado").innerHTML = `
        <h3>Resultado:</h3>
        <p><strong>RULA:</strong> ${rula}</p>
        <p><strong>REBA:</strong> ${reba}</p>
        <p><strong>OWAS:</strong> ${owas}</p>
    `;
}

</script>

</body>
</html>
