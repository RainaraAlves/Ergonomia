<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>PIAE - Plataforma Ergonômica</title>

<style>
body{
    font-family: Arial, sans-serif;
    background:#f2f4f8;
    padding:20px;
}

h2{
    text-align:center;
}

.section{
    background:white;
    padding:20px;
    margin-bottom:30px;
    border-radius:10px;
    box-shadow:0 4px 12px rgba(0,0,0,0.1);
}

.options{
    display:flex;
    justify-content:space-around;
    flex-wrap:wrap;
    margin-top:20px;
}

.card{
    border:2px solid #ccc;
    border-radius:10px;
    padding:10px;
    text-align:center;
    width:180px;
    cursor:pointer;
    transition:0.3s;
}

.card:hover{
    border-color:#007bff;
}

.card img{
    width:100px;
    height:140px;
}

.card input{
    margin-top:10px;
}
</style>
</head>

<body>

<div class="section">
<h2>POSTURA DO PESCOÇO</h2>

<div class="options">

<div class="card">
<img src="imagens/pescoco_0_10.png">
<p>0° a 10°</p>
<input type="radio" name="pescoco" value="1">
</div>

<div class="card">
<img src="imagens/pescoco_10_20.png">
<p>10° a 20°</p>
<input type="radio" name="pescoco" value="2">
</div>

<div class="card">
<img src="imagens/pescoco_20.png">
<p>+20°</p>
<input type="radio" name="pescoco" value="3">
</div>

<div class="card">
<img src="imagens/pescoco_extensao.png">
<p>Extensão</p>
<input type="radio" name="pescoco" value="4">
</div>

</div>
</div>

</body>
</html>
