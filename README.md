# floramarilla
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Para ti, bonita</title>
  <style>
    /* Estilo del fondo */
    body {
      margin: 0;
      padding: 0;
      background-color: #87CEEB; /* Azul cielo */
      background-image: radial-gradient(white 5%, transparent 5%);
      background-size: 50px 50px;
      font-family: 'Arial', sans-serif;
      overflow: hidden;
    }

    /* Contenedor para centrar el contenido */
    .container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      position: relative;
    }

    /* Estilo del texto en el centro */
    h1 {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: white;
      font-size: 48px;
      text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
    }

    /* Estilo de los girasoles */
    svg {
      width: 50px;
      height: 50px;
      position: absolute;
      animation: float 4s ease-in-out infinite;
    }

    /* Animación de los girasoles flotando */
    @keyframes float {
      0% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(-20px);
      }
      100% {
        transform: translateY(0);
      }
    }

    /* Generar girasoles con posición y retraso de animación aleatorios */
    .sunflower {
      animation-duration: calc(3s + (1s * (random())));
      left: calc(100% * (random()));
      top: calc(100% * (random()));
    }

    /* Función de valor aleatorio */
    @keyframes random {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); }
    }

  </style>
</head>
<body>
  <div class="container">
    <!-- Texto central -->
    <h1>Para ti, bonita</h1>

    <!-- Girasoles generados -->
    <div id="girasoles"></div>
  </div>

  <script>
    // Función para crear un girasol en SVG
    function createSunflower() {
      const svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
      svg.setAttribute("viewBox", "0 0 200 200");
      svg.classList.add("sunflower");
      
      const center = document.createElementNS("http://www.w3.org/2000/svg", "circle");
      center.setAttribute("cx", "100");
      center.setAttribute("cy", "100");
      center.setAttribute("r", "30");
      center.setAttribute("fill", "brown");
      
      const petals = [
        {cx: 100, cy: 50}, {cx: 50, cy: 100}, {cx: 150, cy: 100}, {cx: 100, cy: 150},
        {cx: 135, cy: 65}, {cx: 65, cy: 65}, {cx: 135, cy: 135}, {cx: 65, cy: 135}
      ];
      
      petals.forEach(petal => {
        const petalCircle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
        petalCircle.setAttribute("cx", petal.cx);
        petalCircle.setAttribute("cy", petal.cy);
        petalCircle.setAttribute("r", "20");
        petalCircle.setAttribute("fill", "yellow");
        svg.appendChild(petalCircle);
      });
      
      svg.appendChild(center);
      return svg;
    }

    // Función para añadir girasoles
    function addSunflowers(number) {
      const container = document.getElementById('girasoles');
      for (let i = 0; i < number; i++) {
        const sunflower = createSunflower();
        sunflower.style.top = `${Math.random() * 100}vh`;
        sunflower.style.left = `${Math.random() * 100}vw`;
        sunflower.style.animationDelay = `${Math.random() * 4}s`;
        container.appendChild(sunflower);
      }
    }

    // Añadir 80 girasoles a la página
    addSunflowers(80);
  </script>
</body>
</html>


