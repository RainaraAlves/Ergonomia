<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>PIAE - Versão Corrigida</title>

<style>
body{
    font-family: Arial, sans-serif;
    background:#f2f2f2;
    padding:30px;
}

h1{
    text-align:center;
}

.tabela{
    background:white;
    padding:20px;
    margin-bottom:25px;
    border-radius:8px;
    box-shadow:0 2px 8px rgba(0,0,0,0.08);
}

.linha{
    margin-bottom:8px;
}

label{
    margin-left:8px;
}

button{
    width:100%;
    padding:15px;
    font-size:16px;
    background:#003366;
    color:white;
    border:none;
    border-radius:6px;
    cursor:pointer;
}

.resultado{
    margin-top:20px;
    padding:20px;
    background:#e6f0ff;
    border-radius:8px;
}
</style>
</head>

<body>

<h1>🔹 VERSÃO CORRIGIDA (EXATAMENTE COMO NA PLANILHA)</h1>

<form id="formPIAE">

<!-- ================= PESCOÇO ================= -->

<div class="tabela">
<h2>PESCOÇO</h2>
<p><strong>Coloque um X na posição observada</strong></p>

<div class="linha">
<input type="radio" name="pescoco" value="1"> <label>0 a 10°</label>
</div>

<div class="linha">
<input type="radio" name="pescoco" value="2"> <label>10 a 20°</label>
</div>

<div class="linha">
<input type="radio" name="pescoco" value="3"> <label>+20°</label>
</div>

<div class="linha">
<input type="radio" name="pescoco" value="4"> <label>Extensão</label>
</div>

<h3>Correções</h3>

<div class="linha">
<input type="checkbox" id="rotacao"> <label>Torção (Rotação)</label>
</div>

<div class="linha">
<input type="checkbox" id="inclinacao"> <label>Inclinação lateral</label>
</div>

</div>

<!-- ================= BRAÇOS ================= -->

<div class="tabela">
<h2>BRAÇOS</h2>
<p><strong>Coloque um X na posição observada</strong></p>

<div class="linha">
<input type="radio" name="bracos" value="1"> <label>0 A 20 / extensão e flexão</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="2"> <label>Flexão +20 e extensão 20 e 45</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="3"> <label>Extensão 45 a 90</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="4"> <label>Extensão +90</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="5"> <label>Flexão +90</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="6"> <label>> 20 Extensão</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="7"> <label>Flexão 20 a 45</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="8"> <label>Um braço p cima</label>
</div>

<div class="linha">
<input type="radio" name="bracos" value="9"> <label>Dois braço p baixo</label>
</div>

</div>

<!-- (Repita exatamente o mesmo padrão para: Tronco, Pernas, Antebraços, Punhos, Carga — copiando exatamente da aba PIAE) -->


<button type="button" onclick="calcular()">Calcular Avaliação</button>

<div class="resultado" id="resultado"></div>

</form>

<script>

function calcular(){

    let pescoco = parseInt(document.querySelector('input[name="pescoco"]:checked')?.value || 0);
    let bracos = parseInt(document.querySelector('input[name="bracos"]:checked')?.value || 0);

    let adicional = 0;

    if(document.getElementById("rotacao").checked) adicional += 1;
    if(document.getElementById("inclinacao").checked) adicional += 1;

    // Simulação separada (depois colocamos a matriz real)
    let RULA = pescoco + bracos + adicional;
    let REBA = pescoco + adicional;
    let OWAS = bracos;

    document.getElementById("resultado").innerHTML = `
        <h3>Resultado:</h3>
        <p><strong>RULA:</strong> ${RULA}</p>
        <p><strong>REBA:</strong> ${REBA}</p>
        <p><strong>OWAS:</strong> ${OWAS}</p>
    `;
}

</script>

</body>
</html>
