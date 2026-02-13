<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Plataforma PIAE</title>

<style>
body{
    font-family: Arial, sans-serif;
    background:#f4f6f9;
    margin:0;
    padding:20px;
}

h1{
    text-align:center;
    margin-bottom:30px;
}

.section{
    background:white;
    padding:20px;
    margin-bottom:20px;
    border-radius:8px;
    box-shadow:0 2px 8px rgba(0,0,0,0.1);
}

label{
    font-weight:bold;
    display:block;
    margin-top:10px;
}

select, input{
    width:100%;
    padding:8px;
    margin-top:5px;
    border-radius:6px;
    border:1px solid #ccc;
}

.result-box{
    display:flex;
    justify-content:space-around;
    margin-top:20px;
}

.card{
    background:#e9edf3;
    padding:20px;
    border-radius:10px;
    width:30%;
    text-align:center;
}

.score{
    font-size:28px;
    font-weight:bold;
    margin-top:10px;
}

button{
    margin-top:20px;
    padding:12px;
    width:100%;
    background:#1e3a8a;
    color:white;
    border:none;
    border-radius:8px;
    font-size:16px;
    cursor:pointer;
}

button:hover{
    background:#162d6a;
}
</style>
</head>

<body>

<h1>PLATAFORMA ERGONÔMICA INTEGRADA - PIAE</h1>

<div class="section">
<h2>DADOS DA AVALIAÇÃO</h2>

<label>Nome</label>
<input type="text" id="nome">

<label>Empresa</label>
<input type="text" id="empresa">

<label>Setor</label>
<input type="text" id="setor">

<label>Função</label>
<input type="text" id="funcao">
</div>

<div class="section">
<h2>PESCOÇO</h2>

<label>Flexão do Pescoço</label>
<select id="neckFlexion">
    <option value="0">Selecione</option>
    <option value="1">0 a 10°</option>
    <option value="2">10 a 20°</option>
    <option value="3">+20°</option>
    <option value="4">Extensão</option>
</select>

<label>Correções - Pescoço</label>
<select id="neckCorrection">
    <option value="0">Nenhuma</option>
    <option value="1">Torção (Rotação)</option>
    <option value="2">Inclinação lateral</option>
</select>
</div>

<div class="section">
<h2>BRAÇOS</h2>

<label>Descrição - Braços</label>
<select id="armPosition">
    <option value="0">Selecione</option>
    <option value="1">0 a 20 / extensão e flexão</option>
    <option value="2">Flexão +20 e extensão 20 e 45</option>
    <option value="3">Extensão 45 a 90</option>
    <option value="4">Extensão +90</option>
    <option value="5">Flexão +90</option>
    <option value="6">> 20 Extensão</option>
    <option value="7">Flexão 20 a 45</option>
    <option value="8">Um braço p cima</option>
    <option value="9">Dois braço p baixo</option>
</select>

<label>Correções - Braços</label>
<select id="armCorrection">
    <option value="0">Nenhuma</option>
    <option value="1">Aplicar correção</option>
</select>
</div>

<div class="section">
<button onclick="calcular()">CALCULAR RESULTADO</button>

<div class="result-box">
    <div class="card">
        <h3>REBA</h3>
        <div class="score" id="rebaScore">0</div>
    </div>

    <div class="card">
        <h3>RULA</h3>
        <div class="score" id="rulaScore">0</div>
    </div>

    <div class="card">
        <h3>OWAS</h3>
        <div class="score" id="owasScore">0</div>
    </div>
</div>

</div>

<script>
function calcular(){

    let neck = parseInt(document.getElementById("neckFlexion").value);
    let neckCorr = parseInt(document.getElementById("neckCorrection").value);
    let arm = parseInt(document.getElementById("armPosition").value);
    let armCorr = parseInt(document.getElementById("armCorrection").value);

    // ⚠️ AQUI depois vamos substituir pela lógica exata da planilha
    let reba = neck + neckCorr + arm + armCorr;
    let rula = (neck * 2) + arm;
    let owas = neck + armCorr;

    document.getElementById("rebaScore").innerText = reba;
    document.getElementById("rulaScore").innerText = rula;
    document.getElementById("owasScore").innerText = owas;
}
</script>

</body>
</html>
