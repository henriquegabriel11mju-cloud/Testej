<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Missão Presente — 15 anos</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #08001a, #16002e, #05000d);
  color: white;
  text-align: center;
  min-height: 100vh;
  overflow-x: hidden;
}

.container {
  max-width: 700px;
  margin: auto;
  padding: 25px 18px 60px;
}

h1 {
  font-size: 38px;
  margin-top: 25px;
  color: #d8a7ff;
  text-shadow: 0 0 15px #9b4dff;
}

h2 {
  color: #e8c9ff;
}

p {
  line-height: 1.6;
  color: #ddd;
}

.card {
  background: rgba(255,255,255,0.08);
  border: 1px solid rgba(210,150,255,0.35);
  border-radius: 22px;
  padding: 25px;
  margin: 22px 0;
  box-shadow: 0 0 25px rgba(140,50,255,0.15);
  backdrop-filter: blur(8px);
}

button {
  border: none;
  border-radius: 14px;
  padding: 15px 22px;
  margin: 8px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  color: white;
  background: linear-gradient(135deg,#8d35ff,#c05cff);
  box-shadow: 0 5px 15px rgba(130,40,255,.35);
}

button:hover {
  transform: scale(1.04);
}

.hidden {
  display: none;
}

.choice {
  display: block;
  width: 100%;
  margin: 12px 0;
}

.secret {
  font-size: 20px;
  color: #f2d8ff;
  font-weight: bold;
}

#scratch {
  width: 280px;
  height: 100px;
  margin: 20px auto;
  background: #777;
  border-radius: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: white;
  font-weight: bold;
  user-select: none;
}

#scratch.revealed {
  background: linear-gradient(135deg,#681cff,#c95cff);
}

#final {
  animation: aparecer 1.2s ease;
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

.confete {
  position: fixed;
  top: -20px;
  font-size: 24px;
  animation: cair 3s linear forwards;
  pointer-events: none;
}

@keyframes cair {
  to {
    transform: translateY(110vh) rotate(720deg);
    opacity: 0;
  }
}

.big {
  font-size: 32px;
  color: #e6b7ff;
  font-weight: bold;
}
</style>
</head>

<body>

<div class="container">

  <h1>🎁 MISSÃO PRESENTE</h1>

  <div class="card">
    <h2>Operação: 15 anos</h2>
    <p>
      Você recebeu acesso a um arquivo confidencial.
      Existe um presente escondido nessa missão...
    </p>

    <button onclick="comecar()">INICIAR MISSÃO 🚀</button>
  </div>

  <div id="missao" class="hidden">

    <div class="card">
      <h2>📁 ARQUIVO CONFIDENCIAL</h2>

      <p>
        Antes de descobrir o presente, você precisa fazer algumas escolhas.
      </p>

      <p class="secret">
        Cuidado... algumas respostas podem revelar pistas.
      </p>

      <button class="choice" onclick="responder(1)">
        🎀 Quero descobrir logo
      </button>

      <button class="choice" onclick="responder(2)">
        🕵️ Quero investigar primeiro
      </button>

      <button class="choice" onclick="responder(3)">
        😈 Vou tentar descobrir sozinho
      </button>

      <p id="resposta"></p>
    </div>

    <div class="card">
      <h2>🔐 PISTA SECRETA</h2>

      <p>
        Nem tudo que parece ser o presente é realmente o presente.
      </p>

      <button onclick="mostrarPista()">DESBLOQUEAR PISTA</button>

      <p id="pista" class="hidden secret">
        O presente tem algo a ver com aquilo que você gosta de fazer.
      </p>
    </div>

    <div class="card">
      <h2>🎟️ RASPADINHA</h2>

      <p>
        Toque no cartão para revelar o que está escondido.
      </p>

      <div id="scratch" onclick="raspar()">
        🔒 TOQUE PARA REVELAR
      </div>

      <p id="scratchText"></p>
    </div>

    <div class="card">
      <h2>🧩 ÚLTIMA ETAPA</h2>

      <p>
        O arquivo final está protegido.
        Clique várias vezes para reconstruir a mensagem.
      </p>

      <button onclick="revelarPalavra()">DESCRIPTOGRAFAR 🔓</button>

      <p id="palavra" class="big"></p>
    </div>

    <div id="final" class="card hidden">

      <h2>🎉 MISSÃO CONCLUÍDA!</h2>

      <p>
        Depois de todas essas pistas...
      </p>

      <p class="big">
        O PRESENTE É:
      </p>

      <p class="big">
        ⚽ UMA CHUTEIRA ⚽
      </p>

      <p>
        Agora você descobriu o segredo. ❤️
      </p>

      <button onclick="confetes()">🎊 COMEMORAR</button>

      <br><br>

      <a
        href="https://br.shp.ee/pLKptgme"
        target="_blank"
        style="text-decoration:none;"
      >
        <button>👟 VER A CHUTEIRA</button>
      </a>

    </div>

  </div>

</div>

<script>

function comecar() {
  document.getElementById("missao").classList.remove("hidden");
  window.scrollTo({
    top: document.getElementById("missao").offsetTop,
    behavior: "smooth"
  });
}

function responder(numero) {

  let texto = "";

  if(numero === 1) {
    texto = "👀 Calma! A missão ainda está começando...";
  }

  if(numero === 2) {
    texto = "🕵️ Boa escolha. Investigador detectado!";
  }

  if(numero === 3) {
    texto = "😈 Hmm... tentando trapacear a missão?";
  }

  document.getElementById("resposta").innerText = texto;
}

function mostrarPista() {
  document.getElementById("pista").classList.remove("hidden");
}

function raspar() {

  const caixa = document.getElementById("scratch");

  caixa.classList.add("revealed");
  caixa.innerHTML = "✨ PISTA DESCOBERTA ✨";

  document.getElementById("scratchText").innerText =
    "👟 Tem alguma coisa esperando pelos seus pés...";
}

let etapa = 0;

function revelarPalavra() {

  etapa++;

  let texto = "";

  if(etapa === 1) texto = "EU";
  if(etapa === 2) texto = "EU QUERO";
  if(etapa === 3) texto = "EU QUERO UMA";
  if(etapa >= 4) {
    texto = "EU QUERO UMA CHUTEIRA";

    document.getElementById("final").classList.remove("hidden");

    setTimeout(() => {
      document.getElementById("final").scrollIntoView({
        behavior: "smooth"
      });
    }, 300);
  }

  document.getElementById("palavra").innerText = texto;

  if(etapa >= 4) {
    confetes();
  }
}

function confetes() {

  const emojis = ["🎉","🎊","✨","💜","⚽","👟"];

  for(let i = 0; i < 40; i++) {

    const confete = document.createElement("div");

    confete.className = "confete";

    confete.innerText =
      emojis[Math.floor(Math.random() * emojis.length)];

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
