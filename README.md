<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>MÉTODO PIAE</title>

<style>
body{
    font-family: Arial, Helvetica, sans-serif;
    background:#f2f4f8;
    margin:0;
}

header{
    background:#1f3c88;
    color:white;
    text-align:center;
    padding:20px;
    font-size:26px;
    font-weight:bold;
}

.container{
    padding:30px;
    max-width:900px;
    margin:auto;
}

.card{
    background:white;
    padding:20px;
    border-radius:8px;
    box-shadow:0 4px 12px rgba(0,0,0,0.1);
    margin-bottom:25px;
}

h2{
    background:#e8edf7;
    padding:10px;
    border-left:5px solid #1f3c88;
}

label{
    font-weight:bold;
    display:block;
    margin-top:15px;
}

select{
    width:100%;
    padding:8px;
    margin-top:5px;
    border-radius:5px;
    border:1px solid #ccc;
}

button{
    background:#1f3c88;
    color:white;
    padding:12px 25px;
    border:none;
    border-radius:6px;
    font-size:16px;
    cursor:pointer;
    margin-top:20px;
}

button:hover{
    background:#162d66;
}

.resultado{
    font-size:18px;
    font-weight:bold;
    margin-top:15px;
}
</style>
</head>

<body>

<header>MÉTODO PIAE</header>

<div class="container">

<div class="card">

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
    <option value="1">Inclinação lateral</option>
</select>

</div>


<div class="card">

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

<button onclick="calcular()">Calcular</button>

<div class="resultado" id="resultado"></div>

</div>


<script>
function calcular(){

    let neck = parseInt(document.getElementById("neckFlexion").value);
    let neckCorr = parseInt(document.getElementById("neckCorrection").value);

    let arm = parseInt(document.getElementById("armPosition").value);
    let armCorr = parseInt(document.getElementById("armCorrection").value);

    let scoreNeck = neck + neckCorr;
    let scoreArm = arm + armCorr;

    let total = scoreNeck + scoreArm;

    document.getElementById("resultado").innerHTML =
        "Score Pescoço: " + scoreNeck +
        " | Score Braços: " + scoreArm +
        " | Score Parcial Total: " + total;
}
</script>

</body>
</html>
