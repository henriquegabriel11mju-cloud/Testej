<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>🎁 Missão Presente</title>

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  background: linear-gradient(135deg, #080012, #1b0033, #08000f);
  color: white;
  font-family: Arial, sans-serif;
  text-align: center;
}

.container {
  max-width: 650px;
  margin: auto;
  padding: 25px 18px 60px;
}

.card {
  background: rgba(255,255,255,0.07);
  border: 1px solid rgba(210,150,255,0.35);
  border-radius: 22px;
  padding: 28px 20px;
  margin-top: 25px;
  box-shadow: 0 0 25px rgba(150,50,255,0.18);
}

h1 {
  color: #d9a7ff;
  text-shadow: 0 0 15px #9d45ff;
}

h2 {
  color: #e5c7ff;
}

p {
  color: #ddd;
  line-height: 1.6;
}

button {
  border: none;
  border-radius: 13px;
  padding: 15px 22px;
  margin: 8px;
  color: white;
  font-weight: bold;
  font-size: 15px;
  background: linear-gradient(135deg,#8d32ff,#c258ff);
  box-shadow: 0 5px 15px rgba(130,40,255,.35);
}

.choice {
  width: 90%;
  display: block;
  margin: 12px auto;
}

.progress {
  color: #b889d8;
  font-size: 14px;
}

.big {
  font-size: 30px;
  color: #e4b8ff;
  font-weight: bold;
}

#scratch {
  width: 280px;
  height: 105px;
  margin: 25px auto;
  border-radius: 16px;
  background: #777;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}

#scratch.revealed {
  background: linear-gradient(135deg,#6d20ff,#c457ff);
}

.confete {
  position: fixed;
  top: -30px;
  font-size: 25px;
  animation: cair 3s linear forwards;
  pointer-events: none;
}

@keyframes cair {
  to {
    transform: translateY(110vh) rotate(720deg);
    opacity: 0;
  }
}

</style>
</head>

<body>

<div class="container">

<!-- ================= INÍCIO ================= -->

<div id="inicio" class="card">

<h1>🎁 MISSÃO PRESENTE</h1>

<h2>Operação: 15 anos</h2>

<p>
Você recebeu acesso a um arquivo confidencial.
Existe um presente escondido nessa missão...
</p>

<button onclick="iniciarMissao()">
🚀 INICIAR MISSÃO
</button>

</div>


<!-- ================= ETAPA 1 ================= -->

<div id="etapa1" class="card" style="display:none;">

<div class="progress">ETAPA 1 DE 4</div>

<h2>📁 ARQUIVO CONFIDENCIAL</h2>

<p>
Antes de descobrir o presente,
você precisa escolher como começar a investigação.
</p>

<p><b>Qual será sua estratégia?</b></p>

<button class="choice" onclick="escolher(1)">
🎀 Quero descobrir logo
</button>

<button class="choice" onclick="escolher(2)">
🕵️ Quero investigar primeiro
</button>

<button class="choice" onclick="escolher(3)">
😈 Vou tentar descobrir sozinho
</button>

<p id="respostaEscolha"></p>

<button id="continuar1"
style="display:none;"
onclick="irPara(1,2)">
CONTINUAR ➡️
</button>

</div>


<!-- ================= ETAPA 2 ================= -->

<div id="etapa2" class="card" style="display:none;">

<div class="progress">ETAPA 2 DE 4</div>

<h2>🔐 PISTA SECRETA</h2>

<p>
Você encontrou um arquivo escondido.
</p>

<p>
Mas ele está bloqueado...
</p>

<button onclick="abrirPista()">
🔓 DESBLOQUEAR PISTA
</button>

<p id="pista"
style="display:none;">

👀 <b>PISTA:</b>

<br><br>

O presente tem alguma coisa a ver
com aquilo que você gosta de fazer.

</p>

<button id="continuar2"
style="display:none;"
onclick="irPara(2,3)">
PRÓXIMA ETAPA ➡️
</button>

</div>


<!-- ================= ETAPA 3 ================= -->

<div id="etapa3" class="card" style="display:none;">

<div class="progress">ETAPA 3 DE 4</div>

<h2>🎟️ RASPADINHA SECRETA</h2>

<p>
Uma última pista foi escondida.
</p>

<p>
Toque no cartão para revelar.
</p>

<div id="scratch" onclick="raspar()">

🔒 TOQUE PARA REVELAR

</div>

<p id="textoRaspadinha"></p>

<button id="continuar3"
style="display:none;"
onclick="irPara(3,4)">
CONTINUAR ➡️
</button>

</div>


<!-- ================= ETAPA 4 ================= -->

<div id="etapa4" class="card" style="display:none;">

<div class="progress">ETAPA 4 DE 4</div>

<h2>🧩 ÚLTIMA ETAPA</h2>

<p>
O arquivo final está protegido.
</p>

<p>
Clique no botão várias vezes para reconstruir
a mensagem.
</p>

<button onclick="descriptografar()">
🔓 DESCRIPTOGRAFAR
</button>

<p id="codigo" class="big"></p>

<button id="revelar"
style="display:none;"
onclick="mostrarFinal()">
🎁 REVELAR PRESENTE
</button>

</div>


<!-- ================= FINAL ================= -->

<div id="final" class="card" style="display:none;">

<h1>🎉 MISSÃO CONCLUÍDA!</h1>

<p>
Todas as pistas foram descobertas.
</p>

<p>
O arquivo secreto finalmente revelou o presente...
</p>

<p class="big">
⚽ UMA CHUTEIRA ⚽
</p>

<p>
👟 O presente estava escondido o tempo todo.
</p>

<button onclick="comemorar()">
🎊 COMEMORAR
</button>

<br>

<a href="https://br.shp.ee/pLKptgme"
target="_blank">

<button>
👟 VER A CHUTEIRA
</button>

</a>

</div>

</div>


<script>

/* =================================================
   FUNÇÃO PRINCIPAL PARA MOSTRAR APENAS UMA ETAPA
   ================================================= */

function mostrarSomente(id) {

  document.getElementById("inicio").style.display = "none";

  document.getElementById("etapa1").style.display = "none";
  document.getElementById("etapa2").style.display = "none";
  document.getElementById("etapa3").style.display = "none";
  document.getElementById("etapa4").style.display = "none";

  document.getElementById("final").style.display = "none";

  document.getElementById(id).style.display = "block";

  window.scrollTo(0,0);
}


/* =================================================
   COMEÇAR
   ================================================= */

function iniciarMissao() {

  mostrarSomente("etapa1");

}


/* =================================================
   ESCOLHA DA PRIMEIRA ETAPA
   ================================================= */

function escolher(numero) {

  let texto = "";

  if(numero == 1) {

    texto =
    "👀 Calma... a missão ainda está só começando.";

  }

  if(numero == 2) {

    texto =
    "🕵️ Boa escolha. Investigador detectado!";

  }

  if(numero == 3) {

    texto =
    "😈 Tentando descobrir sozinho? Vamos ver se consegue...";

  }

  document.getElementById("respostaEscolha").innerText = texto;

  document.getElementById("continuar1").style.display = "inline-block";

}


/* =================================================
   IR PARA PRÓXIMA ETAPA
   ================================================= */

function irPara(atual, proxima) {

  mostrarSomente("etapa" + proxima);

}


/* =================================================
   PISTA
   ================================================= */

function abrirPista() {

  document.getElementById("pista").style.display = "block";

  document.getElementById("continuar2").style.display =
  "inline-block";

}


/* =================================================
   RASPADINHA
   ================================================= */

function raspar() {

  let caixa =
  document.getElementById("scratch");

  caixa.classList.add("revealed");

  caixa.innerHTML =
  "✨ PISTA REVELADA ✨";

  document.getElementById("textoRaspadinha").innerHTML =
  "👟 Parece que o presente tem alguma coisa a ver com os seus pés...";

  document.getElementById("continuar3").style.display =
  "inline-block";

}


/* =================================================
   DESCRIPTOGRAFAR
   ================================================= */

let passos = 0;

function descriptografar() {

  passos++;

  let mensagem = "";

  if(passos == 1) {

    mensagem = "P...";

  }

  else if(passos == 2) {

    mensagem = "PR...";

  }

  else if(passos == 3) {

    mensagem = "PRE...";

  }

  else if(passos == 4) {

    mensagem = "PRES...";

  }

  else if(passos == 5) {

    mensagem = "PRESENTE...";

  }

  else {

    mensagem = "🎁 PRESENTE ENCONTRADO!";

    document.getElementById("revelar").style.display =
    "inline-block";

  }

  document.getElementById("codigo").innerText =
  mensagem;

}


/* =================================================
   FINAL
   ================================================= */

function mostrarFinal() {

  mostrarSomente("final");

  comemorar();

}


/* =================================================
   CONFETES
   ================================================= */

function comemorar() {

  const emojis = [
    "🎉",
    "🎊",
    "✨",
    "💜",
    "⚽",
    "👟"
  ];

  for(let i = 0; i < 50; i++) {

    let confete =
    document.createElement("div");

    confete.className =
    "confete";

    confete.innerText =
    emojis[
      Math.floor(Math.random() * emojis.length)
    ];

    confete.style.left =
    Math.random() * 100 + "vw";

    confete.style.animationDuration =
    (2 + Math.random() * 3) + "s";

    document.body.appendChild(confete);

    setTimeout(function() {

      confete.remove();

    },5000);

  }

}

</script>

</body>
</html>
