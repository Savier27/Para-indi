<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Para Mi Reina</title>
  <style>
    body {
      background: linear-gradient(to right, #fceabb, #f8b500);
      display: flex;
      flex-direction: column;
      align-items: center;
      height: 100vh;
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
    }

    .mensaje {
      background-color: rgba(255, 255, 255, 0.85);
      padding: 40px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      margin-top: 60px;
      animation: entrar 1.5s ease;
    }

    h1 {
      color: #8a2be2;
      font-size: 1.8rem;
      margin: 0;
    }

    .gif {
      margin-top: 30px;
      animation: aparecer 2s ease;
    }

    .contenedor-video {
      position: fixed;
      bottom: 10px;
      left: 10px;
      width: 200px;
      height: 120px;
      transform: rotate(-10deg);
      opacity: 0.7;
      transition: transform 1s ease, opacity 0.5s ease;
      z-index: 999;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.4);
      border-radius: 10px;
      overflow: hidden;
      cursor: pointer;
    }

    .contenedor-video iframe {
      width: 100%;
      height: 100%;
      pointer-events: auto; /* ahora permite interacción */
    }

    .contenedor-video.activo {
      transform: rotate(0deg) scale(1.05);
      opacity: 1;
      box-shadow: 0 0 30px rgba(255, 255, 255, 0.3);
    }

    @keyframes entrar {
      from { transform: translateY(30px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    @keyframes aparecer {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }
  </style>
</head>
<body>
  <div class="contenedor-video" onclick="this.classList.add('activo')">
    <iframe
      src="https://www.youtube.com/embed/yl3GDni9WCQ?autoplay=1&mute=1&loop=1&playlist=yl3GDni9WCQ"
      frameborder="0"
      allow="autoplay; encrypted-media"
      allowfullscreen>
    </iframe>
  </div>

  <div class="mensaje">
    <h1>Todo estará bien, reina de mi vida.<br>Te mando un 💜 abrazo 💜🌙🔮🫂</h1>
  </div>

  <div class="gif">
    <img src="https://i.gifer.com/Pxer.gif" alt="Love and Glow" width="250">
  </div>
</body>
</html>
