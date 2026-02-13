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

.result-area{
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
</style>
</head>

<body>

<h1>PLATAFORMA ERGONÔMICA INTEGRADA - PIAE</h1>

<div class="section">
<h2>DADOS DA AVALIAÇÃO</h2>
<label>Nome</label>
<input type="text">
<label>Empresa</label>
<input type="text">
<label>Setor</label>
<input type="text">
<label>Função</label>
<input type="text">
</div>

<!-- ================= PESCOÇO ================= -->
<div class="section">
<h2>PESCOÇO</h2>

<label>Flexão do Pescoço</label>
<select>
<option>Selecione</option>
<option>0 a 10°</option>
<option>10 a 20°</option>
<option>+20°</option>
<option>Extensão</option>
</select>

<label>Correções</label>
<select>
<option>Nenhuma</option>
<option>Torção (Rotação)</option>
<option>Inclinação lateral</option>
</select>
</div>

<!-- ================= TRONCO ================= -->
<div class="section">
<h2>TRONCO</h2>

<label>Posição do Tronco</label>
<select>
<option>Selecione</option>
<option>0 a 10°</option>
<option>10 a 20°</option>
<option>20 a 60°</option>
<option>>60°</option>
<option>Extensão</option>
</select>

<label>Correções</label>
<select>
<option>Nenhuma</option>
<option>Torção</option>
<option>Inclinação lateral</option>
</select>
</div>

<!-- ================= PERNAS ================= -->
<div class="section">
<h2>PERNAS</h2>

<label>Postura das Pernas</label>
<select>
<option>Selecione</option>
<option>Em pé com ambas estendidas</option>
<option>Em pé com peso em uma perna</option>
<option>Agachado</option>
<option>Sentado</option>
</select>
</div>

<!-- ================= BRAÇOS ================= -->
<div class="section">
<h2>BRAÇOS</h2>

<label>Descrição</label>
<select>
<option>Selecione</option>
<option>0 a 20 / extensão e flexão</option>
<option>Flexão +20 e extensão 20 e 45</option>
<option>Extensão 45 a 90</option>
<option>Extensão +90</option>
<option>Flexão +90</option>
<option>> 20 Extensão</option>
<option>Flexão 20 a 45</option>
<option>Um braço p cima</option>
<option>Dois braço p baixo</option>
</select>

<label>Correções</label>
<select>
<option>Nenhuma</option>
<option>Aplicar correção</option>
</select>
</div>

<!-- ================= ANTEBRAÇOS ================= -->
<div class="section">
<h2>ANTEBRAÇOS</h2>

<label>Posição</label>
<select>
<option>Selecione</option>
<option>60° a 100°</option>
<option>< 60°</option>
<option>> 100°</option>
</select>
</div>

<!-- ================= PUNHOS ================= -->
<div class="section">
<h2>PUNHOS</h2>

<label>Posição</label>
<select>
<option>Selecione</option>
<option>0°</option>
<option>Flexão</option>
<option>Extensão</option>
</select>

<label>Desvio</label>
<select>
<option>Nenhum</option>
<option>Desvio ulnar/radial</option>
</select>
</div>

<!-- ================= ATIVIDADE MUSCULAR ================= -->
<div class="section">
<h2>ATIVIDADE MUSCULAR</h2>

<select>
<option>Selecione</option>
<option>1 ou mais partes do corpo estáticas</option>
<option>Repetições pequenas frequentes</option>
<option>Mudanças rápidas e grandes na postura</option>
</select>
</div>

<!-- ================= FORÇA / CARGA ================= -->
<div class="section">
<h2>FORÇA / CARGA APLICADA</h2>

<select>
<option>Selecione</option>
<option>Carga menor que 5kg</option>
<option>Entre 5 e 10kg</option>
<option>Maior que 10kg</option>
</select>
</div>

<!-- ================= INTERFACE ================= -->
<div class="section">
<h2>INTERFACE</h2>

<select>
<option>Selecione</option>
<option>Boa</option>
<option>Aceitável</option>
<option>Pobre</option>
<option>Inaceitável</option>
</select>
</div>

<!-- RESULTADOS -->
<div class="section">
<h2>RESULTADOS</h2>

<div class="result-area">
<div class="card">
<h3>REBA</h3>
<div class="score">0</div>
</div>

<div class="card">
<h3>RULA</h3>
<div class="score">0</div>
</div>

<div class="card">
<h3>OWAS</h3>
<div class="score">0</div>
</div>
</div>

</div>

</body>
</html>
