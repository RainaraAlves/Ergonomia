<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Plataforma PIAE</title>

<style>
body{
    font-family: Arial, sans-serif;
    background:#eef2f7;
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
    margin-bottom:25px;
    border-radius:12px;
    box-shadow:0 4px 10px rgba(0,0,0,0.08);
}

.options{
    display:flex;
    flex-wrap:wrap;
    gap:15px;
}

.card{
    border:2px solid #ccc;
    border-radius:10px;
    padding:10px;
    width:180px;
    cursor:pointer;
    transition:0.3s;
    text-align:center;
}

.card:hover{
    border-color:#0066ff;
}

.card input{
    margin-top:10px;
}

.result{
    background:#222;
    color:white;
    padding:20px;
    border-radius:10px;
    text-align:center;
    font-size:20px;
}
button{
    padding:10px 20px;
    font-size:16px;
    cursor:pointer;
}
</style>
</head>

<body>

<h1>MÉTODO PIAE – Plataforma Integrada de Análise Ergonômica</h1>

<!-- ================= PESCOÇO ================= -->

<div class="section">
<h2>PESCOÇO</h2>
<div class="options">
<label class="card"><p>0 a 10°</p><input type="radio" name="pescoco" value="1"></label>
<label class="card"><p>10 a 20°</p><input type="radio" name="pescoco" value="2"></label>
<label class="card"><p>+20°</p><input type="radio" name="pescoco" value="3"></label>
<label class="card"><p>Extensão</p><input type="radio" name="pescoco" value="4"></label>
</div>

<h3>Correções</h3>
<div class="options">
<label class="card"><p>Torção</p><input type="checkbox" id="pescocoTor"></label>
<label class="card"><p>Inclinação lateral</p><input type="checkbox" id="pescocoLat"></label>
</div>
</div>

<!-- ================= TRONCO ================= -->

<div class="section">
<h2>TRONCO</h2>
<div class="options">
<label class="card"><p>0 a 10°</p><input type="radio" name="tronco" value="1"></label>
<label class="card"><p>10 a 20°</p><input type="radio" name="tronco" value="2"></label>
<label class="card"><p>20 a 60°</p><input type="radio" name="tronco" value="3"></label>
<label class="card"><p>>60°</p><input type="radio" name="tronco" value="4"></label>
</div>
</div>

<!-- ================= BRAÇOS ================= -->

<div class="section">
<h2>BRAÇOS</h2>
<div class="options">
<label class="card"><p>0 a 20°</p><input type="radio" name="bracos" value="1"></label>
<label class="card"><p>Flexão 20 a 45°</p><input type="radio" name="bracos" value="2"></label>
<label class="card"><p>Flexão +90°</p><input type="radio" name="bracos" value="3"></label>
<label class="card"><p>Extensão +90°</p><input type="radio" name="bracos" value="4"></label>
</div>
</div>

<!-- ================= ANTEBRAÇOS ================= -->

<div class="section">
<h2>ANTEBRAÇOS</h2>
<div class="options">
<label class="card"><p>60° a 100°</p><input type="radio" name="antebraco" value="1"></label>
<label class="card"><p><60°</p><input type="radio" name="antebraco" value="2"></label>
<label class="card"><p>>100°</p><input type="radio" name="antebraco" value="3"></label>
</div>
</div>

<!-- ================= PUNHOS ================= -->

<div class="section">
<h2>PUNHOS</h2>
<div class="options">
<label class="card"><p>Neutro</p><input type="radio" name="punho" value="1"></label>
<label class="card"><p>Flexão</p><input type="radio" name="punho" value="2"></label>
<label class="card"><p>Extensão</p><input type="radio" name="punho" value="3"></label>
<label class="card"><p>Desvio</p><input type="radio" name="punho" value="4"></label>
</div>
</div>

<!-- ================= PERNAS ================= -->

<div class="section">
<h2>PERNAS</h2>
<div class="options">
<label class="card"><p>Em pé</p><input type="radio" name="pernas" value="1"></label>
<label class="card"><p>Peso unilateral</p><input type="radio" name="pernas" value="2"></label>
<label class="card"><p>Agachado</p><input type="radio" name="pernas" value="3"></label>
<label class="card"><p>Sentado</p><input type="radio" name="pernas" value="4"></label>
</div>
</div>

<!-- ================= ATIVIDADE MUSCULAR ================= -->

<div class="section">
<h2>ATIVIDADE MUSCULAR</h2>
<div class="options">
<label class="card"><p>Postura estática</p><input type="checkbox" id="estatica"></label>
<label class="card"><p>Repetitiva</p><input type="checkbox" id="repetitiva"></label>
<label class="card"><p>Mudanças rápidas</p><input type="checkbox" id="mudancas"></label>
</div>
</div>

<!-- ================= FORÇA ================= -->

<div class="section">
<h2>FORÇA / CARGA</h2>
<div class="options">
<label class="card"><p><5 kg</p><input type="radio" name="forca" value="1"></label>
<label class="card"><p>5 a 10 kg</p><input type="radio" name="forca" value="2"></label>
<label class="card"><p>>10 kg</p><input type="radio" name="forca" value="3"></label>
</div>
</div>

<!-- ================= INTERFACE ================= -->

<div class="section">
<h2>INTERFACE</h2>
<div class="options">
<label class="card"><p>Boa</p><input type="radio" name="interface" value="0"></label>
<label class="card"><p>Aceitável</p><input type="radio" name="interface" value="1"></label>
<label class="card"><p>Pobre</p><input type="radio" name="interface" value="2"></label>
<label class="card"><p>Inaceitável</p><input type="radio" name="interface" value="3"></label>
</div>
</div>

<!-- ================= RESULTADO ================= -->

<div class="section result">
<button onclick="calcular()">Calcular PIAE</button>
<p id="resultado">Resultado: --</p>
</div>

<script>
function getRadioValue(name){
    let radios = document.getElementsByName(name);
    for(let r of radios){
        if(r.checked) return parseInt(r.value);
    }
    return 0;
}

function calcular(){
    let total = 0;

    total += getRadioValue("pescoco");
    total += getRadioValue("tronco");
    total += getRadioValue("bracos");
    total += getRadioValue("antebraco");
    total += getRadioValue("punho");
    total += getRadioValue("pernas");
    total += getRadioValue("forca");
    total += getRadioValue("interface");

    if(document.getElementById("estatica").checked) total +=1;
    if(document.getElementById("repetitiva").checked) total +=1;
    if(document.getElementById("mudancas").checked) total +=1;

    document.getElementById("resultado").innerText = "Resultado: " + total;
}
</script>

</body>
</html>
