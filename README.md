<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>San Valentín 💖</title>

<style>
  body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #ff9ecf, #ff5fa2);
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
    overflow: hidden;
  }

  /* Corazones */
  .heart {
    position: fixed;
    top: -10%;
    animation: fall linear forwards;
    pointer-events: none;
  }

  @keyframes fall {
    to {
      transform: translateY(110vh);
      opacity: 0;
    }
  }

  .container {
    background: rgba(255,255,255,0.25);
    padding: 30px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 0 20px rgba(0,0,0,0.2);
    z-index: 10;
  }

  h1 {
    color: white;
    font-size: 2.4em;
    margin-bottom: 30px;
  }

  .buttons {
    display: flex;
    justify-content: center;
    gap: 20px;
  }

  button {
    border: none;
    border-radius: 30px;
    padding: 15px 30px;
    font-size: 1.2em;
    cursor: pointer;
    transition: transform 0.4s ease;
  }

  #yes {
    background: #ff2f92;
    color: white;
    z-index: 20;
  }

  #no {
    background: white;
    color: #ff2f92;
  }

  .full-screen {
    position: fixed;
    inset: 0;
    width: 100vw;
    height: 100vh;
    font-size: 4em;
    border-radius: 0;
    z-index: 999;
  }

  .final {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: white;
    font-size: 2.3em;
    padding: 20px;
    background: linear-gradient(135deg, #ff5fa2, #ff9ecf);
    gap: 20px;
  }

  .final img {
    width: 220px;
    max-width: 80%;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.3);
  }
</style>
</head>

<body>

<div class="container">
  <h1>¿Quieres ser mi San Valentín? 💕</h1>

  <div class="buttons">
    <button id="yes" onclick="accept()">Sí 💖</button>
    <button id="no" onclick="growYes()">No 😢</button>
  </div>
</div>

<script>
  /* Corazones cayendo */
  setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.textContent = "💖";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = Math.random() * 20 + 15 + "px";
    heart.style.animationDuration = Math.random() * 3 + 4 + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 7000);
  }, 400);

  /* Textos románticos */
  const textos = [
    "Sí 💖",
    "¿Segura que no? 😊",
    "Me harías muy feliz 💕",
    "Prometo cuidarte 💖",
    "Sería muy especial contigo ✨",
    "Di que sí 💘",
    "Ya sabes que quieres 😍",
    "Es un sí 💖"
  ];

  let size = 1;
  let clicks = 0;

  function growYes() {
    size += 0.15;
    clicks++;

    const yesBtn = document.getElementById("yes");
    yesBtn.style.transform = `scale(${size})`;

    const index = Math.min(clicks, textos.length - 1);
    yesBtn.textContent = textos[index];

    if (size >= 4.5) {
      yesBtn.classList.add("full-screen");
      document.getElementById("no").style.display = "none";
      yesBtn.textContent = "SÍ 💖";
    }
  }

  function accept() {
    document.body.innerHTML = `
      <div class="final">
        <div>
          💘 Sabía que dirías que sí niña 💘<br>
          Te amo 💖
        </div>

        <img src="https://imgur.com/pgA9gu8.png" alt="Chango con flores">
      </div>
    `;
  }
</script>

</body>
</html>
