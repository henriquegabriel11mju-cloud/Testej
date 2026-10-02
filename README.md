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
  background: linear-gradient(135deg,#090016,#19002e,#08000f);
  color: white;
  font-family: Arial, sans-serif;
  text-align: center;
}

.container {
  max-width: 650px;
  margin: auto;
  padding: 25px 18px 60px;
}

h1 {
  color: #d9a7ff;
  font-size: 34px;
  text-shadow: 0 0 15px #9d45ff;
}

h2 {
  color: #e5c7ff;
}

p {
  color: #ddd;
  line-height: 1.6;
}

.card {
  background: rgba(255,255,255,.07);
  border: 1px solid rgba(210,150,255,.35);
  border-radius: 22px;
  padding: 28px 20px;
  margin-top: 25px;
  box-shadow: 0 0 25px rgba(150,50,255,.18);
}

.hidden {
  display: none !important;
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
  cursor: pointer;
}

button:active {
  transform: scale(.96);
}

.choice {
  width: 90%;
  display: block;
  margin: 12px auto;
}

.next {
  margin-top: 20px;
}

.big {
  font-size: 30px;
  color: #e4b8ff;
  font-weight: bold;
}

.progress {
  color: #b889d8;
  font-size: 14px;
  margin-top: 10px;
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
  cursor: pointer;
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

.reveal {
  animation: aparecer 1s ease;
}

@keyframes aparecer {
  from {
    opacity: 0;
    transform: scale(.7);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
</style>
</head>

<body>

<div class="container">

<!-- INÍCIO -->
<div id="inicio" class="card">
  <h1>🎁 MISSÃO PRESENTE</h1>

  <h2>Operação: 15 anos</h2>

  <p>
    Você recebeu acesso a um arquivo confidencial.
    Existe um presente escondido nessa missão...
  </p>

  <button onclick="iniciar()">
    🚀 INICIAR MISSÃO
  </button>
</div>


<!-- ETAPA 1 -->
<div id="etapa1" class="card hidden">

  <div class="progress">ETAPA 1 DE 4</div>

  <h2>📁 ARQUIVO CONFIDENCIAL</h2>

  <p>
    Antes de descobrir o presente,
    você precisa escolher como começar a investigação.
  </p>

  <p><b>Qual será sua estratégia?</b></p>

  <button class="choice" onclick="escolha(1)">
    🎀 Quero descobrir logo
  </button>

  <button class="choice" onclick="escolha(2)">
    🕵️ Quero investigar primeiro
  </button>

  <button class="choice" onclick="escolha(3)">
    😈 Vou tentar descobrir sozinho
  </button>

  <p id="resultadoEscolha"></p>

  <button id="btnEtapa2" class="hidden next"
          onclick="irEtapa(1,2)">
    CONTINUAR ➡️
  </button>

</div>


<!-- ETAPA 2 -->
<div id="etapa2" class="card hidden">

  <div class="progress">ETAPA 2 DE 4</div>

  <h2>🔐 PISTA SECRETA</h2>

  <p>
    Você encontrou um arquivo escondido.
  </p>

  <p>
    Mas ele está bloqueado...
  </p>

  <button onclick="liberarPista()">
    🔓 DESBLOQUEAR PISTA
  </button>

  <p id="pista" class="hidden">
    👀 <b>PISTA:</b><br><br>
    O presente tem alguma coisa a ver
    com aquilo que você gosta de fazer.
  </p>

  <button id="btnEtapa3" class="hidden next"
          onclick="irEtapa(2,3)">
    PRÓXIMA ETAPA ➡️
  </button>

</div>


<!-- ETAPA 3 -->
<div id="etapa3" class="card hidden">

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

  <button id="btnEtapa4" class="hidden next"
          onclick="irEtapa(3,4)">
    CONTINUAR ➡️
  </button>

</div>


<!-- ETAPA 4 -->
<div id="etapa4" class="card hidden">

  <div class="progress">ETAPA 4 DE 4</div>

  <h2>🧩 ÚLTIMA ETAPA</h2>

  <p>
    O arquivo final está protegido.
  </p>

  <p>
    Clique no botão para reconstruir a mensagem.
  </p>

  <button onclick="descriptografar()">
    🔓 DESCRIPTOGRAFAR
  </button>

  <p id="codigo" class="big"></p>

  <button id="btnFinal" class="hidden next"
          onclick="mostrarFinal()">
    REVELAR PRESENTE 🎁
  </button>

</div>


<!-- FINAL -->
<div id="final" class="card hidden reveal">

  <h1>🎉 MISSÃO CONCLUÍDA!</h1>

  <p>
    Todas as pistas foram descobertas.
  </p>

  <p>
    O arquivo secreto revelou finalmente o presente...
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
     target="_blank"
     style="text-decoration:none;">

    <button>
      👟 VER A CHUTEIRA
    </button>

  </a>

</div>

</div>


<script>

function esconderTudo() {

  document.getElementById("inicio").classList.add("hidden");
  document.getElementById("etapa1").classList.add("hidden");
  document.getElementById("etapa2").classList.add("hidden");
  document.getElementById("etapa3").classList.add("hidden");
  document.getElementById("etapa4").classList.add("hidden");
  document.getElementById("final").classList.add("hidden");

}


function iniciar() {

  esconderTudo();

  document.getElementById("etapa1")
    .classList.remove("hidden");

  window.scrollTo({
    top: 0,
    behavior: "smooth"
  });

}


function escolha(numero) {

  let mensagem = "";

  if(numero === 1) {
    mensagem =
      "👀 Calma... a missão ainda está só começando.";
  }

  if(numero === 2) {
    mensagem =
      "🕵️ Boa escolha. Investigador detectado!";
  }

  if(numero === 3) {
    mensagem =
      "😈 Tentando descobrir sozinho? Vamos ver se consegue...";
  }

  document.getElementById("resultadoEscolha")
    .innerText = mensagem;

  document.getElementById("btnEtapa2")
    .classList.remove("hidden");

}


function irEtapa(atual, proxima) {

  document.getElementById("etapa" + atual)
    .classList.add("hidden");

  document.getElementById("etapa" + proxima)
    .classList.remove("hidden");

  window.scrollTo({
    top: 0,
    behavior: "smooth"
  });

}


function liberarPista() {

  document.getElementById("pista")
    .classList.remove("hidden");

  document.getElementById("btnEtapa3")
    .classList.remove("hidden");

}


function raspar() {

  const caixa =
    document.getElementById("scratch");

  caixa.classList.add("revealed");

  caixa.innerHTML =
    "✨ PISTA REVELADA ✨";

  document.getElementById("textoRaspadinha")
    .innerHTML =
    "👟 Parece que o presente tem alguma coisa a ver com os seus pés...";

  document.getElementById("btnEtapa4")
    .classList.remove("hidden");

}


let passos = 0;

function descriptografar() {

  passos++;

  let texto = "";

  if(passos === 1) {
    texto = "P...";
  }

  else if(passos === 2) {
    texto = "PR...";
  }

  else if(passos === 3) {
    texto = "PRE...";
  }

  else if(passos === 4) {
    texto = "PRES...";
  }

  else if(passos === 5) {
    texto = "PRESENTE...";
  }

  else {
    texto = "🎁 PRESENTE ENCONTRADO!";
  }

  document.getElementById("codigo")
    .innerText = texto;

  if(passos >= 6) {

    document.getElementById("btnFinal")
      .classList.remove("hidden");

  }

}


function mostrarFinal() {

  document.getElementById("etapa4")
    .classList.add("hidden");

  document.getElementById("final")
    .classList.remove("hidden");

  window.scrollTo({
    top: 0,
    behavior: "smooth"
  });

  comemorar();

}


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

    const confete =
      document.createElement("div");

    confete.className = "confete";

    confete.innerText =
      emojis[
        Math.floor(Math.random() * emojis.length)
      ];

    confete.style.left =
      Math.random() * 100 + "vw";

    confete.style.animationDuration =
      (2 + Math.random() * 3) + "s";

    document.body.appendChild(confete);

    setTimeout(() => {
      confete.remove();
    }, 5000);

  }

}

</script>

</body>
</html>
