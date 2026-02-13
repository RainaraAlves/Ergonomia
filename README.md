<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Plataforma PIAE</title>

<style>
body{
    font-family: Arial, sans-serif;
    margin:0;
    background:#eef2f7;
}

.container{
    width:90%;
    max-width:1000px;
    margin:auto;
    padding:20px;
}

.card{
    background:white;
    padding:20px;
    margin-top:20px;
    border-radius:10px;
    box-shadow:0 4px 10px rgba(0,0,0,0.1);
}

input, textarea, select{
    width:100%;
    padding:8px;
    margin:8px 0 15px 0;
}

button{
    padding:10px 20px;
    cursor:pointer;
    font-size:16px;
}

.hidden{
    display:none;
}
</style>
</head>

<body>

<div class="container">

<!-- ================= PÁGINA 1 – DADOS ================= -->

<div id="paginaDados" class="card">
<h2>Cadastro da Avaliação – PIAE</h2>

<label>Nome do Avaliador</label>
<input type="text" id="avaliador">

<label>Empresa</label>
<input type="text" id="empresa">

<label>Setor</label>
<input type="text" id="setor">

<label>Função</label>
<input type="text" id="funcao">

<label>Nome do Trabalhador</label>
<input type="text" id="trabalhador">

<label>Idade</label>
<input type="number" id="idade">

<label>Sexo</label>
<select id="sexo">
<option value="">Selecione</option>
<option>Masculino</option>
<option>Feminino</option>
<option>Outro</option>
</select>

<label>Tempo na Função</label>
<input type="text" id="tempoFuncao">

<label>Descrição da Atividade</label>
<textarea id="descricao"></textarea>

<label>Foto da Atividade</label>
<input type="file" id="foto">

<button onclick="iniciarAvaliacao()">Iniciar Avaliação</button>
</div>

<!-- ================= PÁGINA 2 – AVALIAÇÃO ================= -->

<div id="paginaAvaliacao" class="card hidden">
<h2>Avaliação Postural – PIAE</h2>

<label>Flexão do Pescoço</label>
<select id="pescoco">
<option value="0">Selecione</option>
<option value="1">0 a 10°</option>
<option value="2">10 a 20°</option>
<option value="3">+20°</option>
<option value="4">Extensão</option>
</select>

<label>Tronco</label>
<select id="tronco">
<option value="0">Selecione</option>
<option value="1">0 a 10°</option>
<option value="2">10 a 20°</option>
<option value="3">20 a 60°</option>
<option value="4">+60°</option>
</select>

<label>Braços</label>
<select id="bracos">
<option value="0">Selecione</option>
<option value="1">0 a 20°</option>
<option value="2">20 a 45°</option>
<option value="3">+90°</option>
</select>

<br><br>
<button onclick="calcular()">Calcular</button>

<h3 id="resultado"></h3>

<button onclick="voltar()">Voltar</button>
</div>

</div>

<script>

function iniciarAvaliacao(){
    document.getElementById("paginaDados").classList.add("hidden");
    document.getElementById("paginaAvaliacao").classList.remove("hidden");
}

function voltar(){
    document.getElementById("paginaAvaliacao").classList.add("hidden");
    document.getElementById("paginaDados").classList.remove("hidden");
}

function calcular(){
    let total = 0;
    total += parseInt(document.getElementById("pescoco").value);
    total += parseInt(document.getElementById("tronco").value);
    total += parseInt(document.getElementById("bracos").value);

    document.getElementById("resultado").innerText = "Resultado Parcial: " + total;
}

</script>

</body>
</html>
