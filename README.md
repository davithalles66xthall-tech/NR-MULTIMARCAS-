<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>NR MULTIMARCAS</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@700&display=swap');

*{margin:0;padding:0;box-sizing:border-box;font-family:Orbitron;font-weight:700}

body{background:black;color:white}

header{text-align:center;padding:40px}
.logo{font-size:42px}
.logo span{color:#00b3ff}

.section{padding:30px;display:flex;justify-content:center}
.box{width:90%;border:1px solid #00b3ff;border-radius:20px;padding:30px;text-align:center}

.produto{border:1px solid #00b3ff;padding:15px;margin:10px;border-radius:10px}

button{border:2px solid #00b3ff;background:none;color:#00b3ff;padding:10px 25px;border-radius:25px}

.cart-btn{position:fixed;bottom:20px;right:20px;background:#00b3ff;color:black;padding:15px;border-radius:50%}

.fullcart{
position:fixed;
inset:0;
background:black;
display:none;
padding:20px;
z-index:999;
}

input{width:100%;padding:10px;margin:8px 0;background:black;color:white;border:1px solid #00b3ff}

.notice{
position:fixed;
top:20px;
left:50%;
transform:translateX(-50%);
background:#00b3ff;
color:black;
padding:10px 20px;
border-radius:20px;
display:none;
}
</style>
</head>

<body>

<div class="notice" id="notice"></div>

<header>
<div class="logo">NR <span>MULTIMARCAS</span></div>
<p style="color:#00b3ff">ENTREGAMOS NOVA LIMA E REGIÃO</p>
</header>

<div class="section">
<div class="box">

<h2>🩳 BERMUDAS</h2>

<div class="produto">Bermuda Boss R$65 <br><button onclick="add('Boss',65)">Adicionar</button></div>
<div class="produto">Empório Armani R$65 <br><button onclick="add('Armani',65)">Adicionar</button></div>
<div class="produto">Mizuno Vermelha R$65 <br><button onclick="add('Mizuno',65)">Adicionar</button></div>
<div class="produto">EA7 Preta R$65 <br><button onclick="add('EA7',65)">Adicionar</button></div>
<div class="produto">Boss Preta R$65 <br><button onclick="add('Boss Preta',65)">Adicionar</button></div>
<div class="produto">Jeans Clara R$70 <br><button onclick="add('Jeans',70)">Adicionar</button></div>

</div>
</div>

<div class="cart-btn" onclick="openCart()">🛒</div>

<div class="fullcart" id="cart">

<h2>CARRINHO</h2>
<div id="lista"></div>
<div id="total"></div>

<br>
<button onclick="finalizar()">FINALIZAR PEDIDO</button>

<div id="loading" style="display:none;margin-top:20px">CARREGANDO...</div>

<div id="form" style="display:none">

<input id="cpf" placeholder="CPF">
<input id="nome" placeholder="NOME COMPLETO">
<input id="bairro" placeholder="BAIRRO">
<input id="rua" placeholder="RUA">
<input id="num" placeholder="N° CASA">

<button onclick="pagar()">PROSSEGUIR PAGAMENTO</button>

</div>

</div>

<div class="fullcart" id="pixTela"></div>

<script>

let soma=0,itens=[];

function add(nome,valor){
itens.push(nome);
soma+=valor;
lista.innerHTML+=nome+"<br>";
total.innerHTML="TOTAL R$ "+soma;

notice.style.display="block";
notice.innerText="ADICIONADO: "+nome;

setTimeout(()=>notice.style.display="none",1500);
}

function openCart(){
cart.style.display="block";
}

function finalizar(){
loading.style.display="block";
setTimeout(()=>{
loading.style.display="none";
form.style.display="block";
},4000);
}

function pagar(){

if(!cpf.value||!nome.value||!bairro.value||!rua.value||!num.value){
alert("PREENCHA TODOS OS CAMPOS");
return;
}

pixTela.style.display="block";
pixTela.innerHTML="GERANDO PIX...";

setTimeout(()=>{
pixTela.innerHTML=`
<div style="text-align:center;margin-top:100px">

<img src="https://upload.wikimedia.org/wikipedia/commons/5/5e/Pix_logo.png" width="120"><br><br>

<h2>PIX: 31993022071</h2><br>

<button onclick="navigator.clipboard.writeText('31993022071')">COPIAR PIX</button>

<p style="margin-top:20px;font-size:13px">
APÓS PAGAMENTO ENVIE COMPROVANTE PARA<br>
31993022071<br><br>
ENVIE PRINT DO PEDIDO
</p>

</div>`;
},3000);
}
</script>

</body>
</html>
