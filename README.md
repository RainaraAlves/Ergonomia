<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>MÉTODO PIAE</title>

<style>
body{
    font-family: Arial, Helvetica, sans-serif;
    background-color:#f4f6f9;
    margin:0;
}

header{
    background:#1f3c88;
    color:white;
    padding:20px;
    text-align:center;
    font-size:28px;
    font-weight:bold;
}

.container{
    padding:30px;
}

.card{
    background:white;
    border-radius:8px;
    box-shadow:0 4px 10px rgba(0,0,0,0.1);
    margin-bottom:30px;
    padding:20px;
}

.titulo-bloco{
    background:#e9eef7;
    padding:10px;
    font-weight:bold;
    font-size:18px;
    border-left:6px solid #1f3c88;
    margin-bottom:20px;
}

.grid-opcoes{
    display:flex;
    gap:40px;
    align-items:center;
}

.imagem-postura{
    width:180px;
}

.opcoes{
    display:grid;
    grid-template-columns: repeat(2, 1fr);
    gap:15px;
}

.opcao{
    background:#f8f9fb;
    padding:10px;
    border-radius:6px;
    border:1px solid #dcdcdc;
}

.opcao input{
    margin-right:8px;
}

.botao{
    background:#1f3c88;
    color:white;
    padding:12px 25px;
    border:none;
    border-radius:6px;
    font-size:16px;
    cursor:pointer;
}
.botao:hover{
    background:#162d66;
}
</style>
</head>

<body>

<header>
    MÉTODO PIAE – Plataforma Integrada de Análise Ergonômica
</header>

<div class="container">

    <!-- IDENTIFICAÇÃO -->
    <div class="card">
        <div class="titulo-bloco">IDENTIFICAÇÃO</div>

        Nome: <input type="text" style="width:300px;"><br><br>
        Empresa: <input type="text" style="width:300px;"><br><br>
        Setor: <input type="text" style="width:300px;"><br><br>
        Função: <input type="text" style="width:300px;">
    </div>


    <!-- PESCOÇO -->
    <div class="card">
        <div class="titulo-bloco">POSTURA DO PESCOÇO</div>

        <div class="grid-opcoes">

            <img src="img/pescoco_0_10.png" class="imagem-postura">

            <div class="opcoes">

                <!-- 🔹 VERSÃO CORRIGIDA (EXATAMENTE COMO NA PLANILHA) -->
                <label class="opcao">
                    <input type="radio" name="pescoco" value="0-10">
                    0º a 10º de flexão
                </label>

                <label class="opcao">
                    <input type="radio" name="pescoco" value="10-20">
                    10º a 20º de flexão
                </label>

                <label class="opcao">
                    <input type="radio" name="pescoco" value="20+">
                    +20º de flexão
                </label>

                <label class="opcao">
                    <input type="radio" name="pescoco" value="extensao">
                    Extensão
                </label>

            </div>

        </div>
    </div>


    <!-- BRAÇOS -->
    <div class="card">
        <div class="titulo-bloco">POSTURA DOS BRAÇOS</div>

        <div class="opcoes">

            <!-- 🔹 VERSÃO CORRIGIDA (EXATAMENTE COMO NA PLANILHA) -->

            <label class="opcao">
                <input type="radio" name="bracos">
                0 a 20 / extensão e flexão
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                Flexão +20 e extensão 20 e 45
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                Extensão 45 a 90
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                Extensão +90
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                Flexão +90
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                > 20 Extensão
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                Flexão 20 a 45
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                Um braço p cima
            </label>

            <label class="opcao">
                <input type="radio" name="bracos">
                Dois braço p baixo
            </label>

        </div>
    </div>

    <button class="botao">Calcular</button>

</div>

</body>
</html>
