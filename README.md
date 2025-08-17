<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Nuestro Amor</title>
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script&family=Great+Vibes&family=Poppins:wght@400;700&display=swap" rel="stylesheet" />

<style>
  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: black;
  }

  /* Pantallas */
  .screen {
    position: absolute;
    top: 0; left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: opacity 1s ease;
  }

  .hidden {
    opacity: 0;
    pointer-events: none;
  }

  /* Pantalla inicio: letras E ❤️ K */
  .start-letters {
    font-family: 'Great Vibes', cursive;
    font-size: 5rem;
    color: white;
    display: flex;
    align-items: center;
    gap: 20px;
    margin-bottom: 30px;
  }

  /* Panel de contraseña y pregunta */
  .password-box {
    background: rgba(255,0,50,0.8);
    padding: 20px 30px;
    border-radius: 15px;
    box-shadow: 0 0 20px pink;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
  }

  .password-box .question {
    font-family: 'Great Vibes', cursive;
    font-size: 1.5rem;
    color: white;
    margin-bottom: 15px;
  }

  .password-box .options {
    display: flex;
    gap: 20px;
    margin-bottom: 30px;
  }

  .password-box .options button {
    padding: 8px 15px;
    font-size: 1.2rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    background: white;
    color: #C70039;
    font-weight: bold;
    transition: 0.3s;
  }

  .password-box .options button.selected {
    background: #C70039;
    color: white;
  }

  .password-box .options button:hover {
    background: #C70039;
    color: white;
  }

  .password-box input {
    padding: 10px;
    font-size: 1.2rem;
    border: none;
    border-radius: 8px;
    outline: none;
    text-align: center;
    margin-bottom: 15px;
  }

  .password-box button.submit-btn {
    padding: 8px 20px;
    font-size: 1rem;
    border: none;
    background: black;
    color: pink;
    border-radius: 8px;
    cursor: pointer;
    font-weight: bold;
    transition: transform 0.3s ease;
  }

  .password-box button.submit-btn:hover {
    transform: scale(1.1);
    background: violet;
    color: black;
  }

  /* Pantalla contador */
  #counterScreen {
    background: black;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    padding: 30px 20px;
    height: 100vh;
    overflow-y: auto;
  }

  .counter-box {
    padding: 30px 50px;
    border-radius: 30px;
    text-align: center;
    width: 90%;
    max-width: 1200px;
    background: linear-gradient(270deg, #C70039, #FF007F, #FF007F, #C70039);
    background-size: 600% 600%;
    animation: gradientMove 10s ease infinite;
    color: white;
    margin-bottom: 30px;
  }

  @keyframes gradientMove {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  .counter-title {
    font-size: 3rem;
    margin-bottom: 15px;
    font-family: 'Great Vibes', cursive;
  }

  .counter {
    font-size: 4rem;
    font-weight: bold;
    letter-spacing: 2px;
  }

  .counter-sub {
    margin-top: 20px;
    font-size: 2.5rem;
    font-family: 'Great Vibes', cursive;
  }

  /* Línea flotante */
  .divider {
    width: 80%;
    height: 4px;
    background: #C70039;
    margin: 60px 0 10px 0;
    border-radius: 2px;
  }

  /* Mensaje “Para el amor de mi vida” */
  .love-message {
    margin-top: 10px;
    align-self: flex-start;
    margin-left: 20px;
    font-family: 'Great Vibes', cursive;
    font-size: 2rem;
    color: white;
  }

  /* Poema */
  .poem {
    max-width: 900px;
    margin: 20px auto 40px;
    font-family: 'Dancing Script', cursive;
    font-size: 2.2rem;
    color: white;
    line-height: 1.4;
    text-align: center;
    white-space: pre-line;
    padding: 0 20px;
  }

  /* Pantalla mensaje K */
  #kMessage {
    background: black;
    color: red;
    font-size: 4rem;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100vh;
    position: absolute;
    top: 0; left: 0;
    flex-direction: column;
    font-style: italic;
  }
</style>
</head>
<body>

<!-- Pantalla inicio -->
<div class="screen" id="startScreen">
  <div class="start-letters">
    E <span class="heart-flecha">❤️</span> K
  </div>
  <div class="password-box">
    <div class="question">¿Quién ama más el uno al otro?</div>
    <div class="options">
      <button onclick="selectAnswer('E', this)">E</button>
      <button onclick="selectAnswer('K', this)">K</button>
    </div>
    <input type="password" id="password" placeholder="Contraseña" maxlength="7" />
    <button class="submit-btn" onclick="checkPassword()">Entrar</button>
  </div>
</div>

<!-- Pantalla contador -->
<div class="screen hidden" id="counterScreen">
  <div class="counter-box">
    <div class="counter-title">Nuestro amor lleva</div>
    <div class="counter" id="timeCounter">Cargando...</div>
    <div class="counter-sub">Juntos</div>
  </div>
  <div class="divider"></div>
  <div class="love-message">Para el amor de mi vida 💌</div>
  
  <div class="poem">
Cuando te veo, mis problemas desaparecen,<br>
como el sol que disuelve la niebla al amanecer.<br>
En tu mirada encontré mi paz, mi refugio,<br>
y en tu sonrisa, la esperanza que renace sin fin.<br><br>

Desde que te conocí, conocí el amor verdadero,<br>
ese que transforma el alma y colorea los días grises.<br>
Eres el latido constante que me da vida,<br>
el susurro dulce que calma mis tempestades.<br><br>

Amarte es un viaje sin mapas ni destinos,<br>
donde cada instante a tu lado es un tesoro infinito.<br>
El mundo se vuelve más hermoso y luminoso,<br>
porque tú lo llenas con la magia de tu esencia.<br><br>

No hay palabra suficiente para describir<br>
lo especial que eres, ni cuánto valoro<br>
el abrazo que me sostiene y el amor que me das,<br>
un regalo eterno que guardo en lo más profundo.<br><br>

Para ti, mi amor, que haces que mi vida brille,<br>
que me enseñaste qué es amar de verdad,<br>
gracias por ser el sueño hecho realidad,<br>
mi eterno refugio y mi felicidad.
  </div>
</div>

<!-- Pantalla mensaje K -->
<div id="kMessage" class="hidden">Aww que ilusa amor jiji</div>

<script>
  const PASSWORD = "010822";
  let selectedAnswer = null;

  function selectAnswer(answer, btn) {
    selectedAnswer = answer;
    document.querySelectorAll('.options button').forEach(b => b.classList.remove('selected'));
    btn.classList.add('selected');
  }

  function checkPassword() {
    const pass = document.getElementById("password").value;

    if (selectedAnswer === null) {
      alert("Por favor selecciona una opción");
      return;
    }

    if (pass === PASSWORD && selectedAnswer === 'E') {
      document.getElementById("startScreen").classList.add("hidden");
      document.getElementById("counterScreen").classList.remove("hidden");
      updateCounter();
      setInterval(updateCounter, 60000);
    } else if (pass === PASSWORD && selectedAnswer === 'K') {
      document.getElementById("startScreen").classList.add("hidden");
      const kScreen = document.getElementById("kMessage");
      kScreen.classList.remove("hidden");
      setTimeout(() => {
        kScreen.classList.add("hidden");
        document.getElementById("startScreen").classList.remove("hidden");
        resetInputs();
      }, 2000);
    } else if (pass !== PASSWORD && selectedAnswer === 'E') {
      alert("Contraseña incorrecta 💔");
      resetInputs();
    } else {
      alert("Contraseña incorrecta 💔 y opción incorrecta 💔");
      resetInputs();
    }
  }

  function resetInputs() {
    document.getElementById("password").value = "";
    selectedAnswer = null;
    document.querySelectorAll('.options button').forEach(b => b.classList.remove('selected'));
  }

  function updateCounter() {
    const startDate = new Date(2022,7,1,21,0,0); // Agosto es mes 7 (0-index)
    const now = new Date();

    let years = now.getFullYear() - startDate.getFullYear();
    let months = now.getMonth() - startDate.getMonth();
    let days = now.getDate() - startDate.getDate();

    if(days < 0){
      months--;
      const prevMonth = new Date(now.getFullYear(), now.getMonth(), 0).getDate();
      days += prevMonth;
    }
    if(months < 0){
      years--;
      months += 12;
    }

    document.getElementById("timeCounter").innerHTML =
        `${years} años, ${months} meses, ${days} días`;
  }
</script>

</body>
</html>
