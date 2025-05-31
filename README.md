<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mensaje Especial</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: Arial, sans-serif;
            text-align: center;
            position: relative;
            animation: fondoCambio 6s infinite ease-in-out;
            background: linear-gradient(to bottom, #ff0000, #4b0082);
        }

        @keyframes fondoCambio {
            0% { background: #ffcc00; }
            40% { background: #000000; }
            60% { background: #000000; }
            100% { background: #ffcc00; }
        }

        .carta {
            width: 80%;
            max-width: 600px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.6);
            text-align: center;
            backdrop-filter: blur(10px);
            opacity: 0;
            transform: scale(0.8);
            transition: opacity 2s ease-in, transform 2s ease-in;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px;
        }

        .content h1 {
            font-size: 2em; /* Tamaño reducido */
            position: absolute;
            top: 25%; /* Sube la frase grande */
            left: 50%;
            transform: translate(-50%, -50%);
            text-shadow: 0 0 10px rgba(255, 255, 150, 0.9);
            margin-top: 10px; /* Espaciado corregido */
        }

        .content p {
            font-size: 1.2em; /* Tamaño normal */
            position: absolute;
            top: 70%; /* Baja la frase pequeña */
            left: 50%;
            transform: translate(-50%, -50%);
            margin-bottom: 10px; /* Espaciado corregido */
        }

.star {
            position: absolute;
            width: 5px;
            height: 5px;
            background: white;
            border-radius: 50%;
            opacity: 0;
            animation: twinkle 2s infinite alternate;
        }

        @keyframes twinkle {
            0% { opacity: 0.1; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1.2); }
        }

        button {
            padding: 15px 30px;
            font-size: 20px;
            cursor: pointer;
            background: white;
            color: black;
            border: none;
            border-radius: 10px;
            position: absolute;
            top: 30%;
            left: 50%;
            transform: translate(-50%, -50%);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        button:hover {
            transform: scale(1.1);
            box-shadow: 0px 0px 15px white;
        }
    </style>
</head>
<body>
    <audio id="backgroundAudio" loop>
        <source src="https://drive.google.com/uc?export=download&id=1l0ZKLdAOuVuN1oY6dE-Tn4MEGXi9nlMY" type="audio/mpeg">
    </audio>

    <script>
        function startExperience() {
            document.getElementById('backgroundAudio').play(); 
            let carta = document.getElementById("message");
            let boton = document.querySelector("button");

            if (carta) {
                carta.style.opacity = "1";
                carta.style.transform = "scale(1)";
                boton.style.display = "none"; // Oculta el botón tras activarse
            } else {
                console.error("No se encontró el elemento con ID 'message'");
            }
        }

        function createStars() {
            setInterval(() => {
                document.querySelectorAll(".star").forEach(star => star.remove());
                for (let i = 0; i < 50; i++) {
                    let star = document.createElement("div");
                    star.className = "star";
                    star.style.top = Math.random() * window.innerHeight + "px";
                    star.style.left = Math.random() * window.innerWidth + "px";
                    star.style.animationDuration = (Math.random() * 2 + 1) + "s";
                    document.body.appendChild(star);
                }
            }, 5000); // Regenera estrellas cada 5 segundos
        }
        createStars();
    </script>

    <canvas id="particlesCanvas"></canvas>
    <div class="content">
        <h1>💜Para la chica que conoceré❤️</h1>
        <button onclick="startExperience()">Descubre algo especial</button>
        <p>El tiempo trazará lo que está por venir.</p>
    </div>

    <div class="carta" id="message">
        <p>🌟Querida niña que llegó sorpresivamente, como si fuera un regalo de Dios, llegando a mí cálidamente con el amanecer.  
La verdad, no sé qué escribir en esta carta, porque aún el tiempo no ha coloreado nuestro encuentro. No queda más que idealizar ese día: tal vez sea uno común y corriente, o tal vez sea más que eso.  
La verdad, no me gustaría planearlo, prefiero que el destino juegue sus cartas con nosotros.  
En cuanto a ti… Solo puedo decir que cada texto que escribes para mí parecen líneas escritas por una estrella resplandeciente.  
Tu voz es tan hermosa como el cálido sonido de un instrumento musical, porque cada palabra que sale de tu voz suena como una melodía suave que calma mi alma cada vez que la escucho.  
Cada palabra, cada risa, se queda grabada en mi mente, y cada vez que recuerdo tu voz, me sacas una sonrisa.  
Espero que la vida sepa cruzar nuestros caminos en el momento indicado...  
Esperaré con ansias ese día y prepararé un abrazo para ti.  
Hasta entonces, seguiré hablándote, soñándote, imaginándote, conociéndote...  
Hasta que llegue el día en que pueda verte frente a mí. Y cuando ese día llegué,te abrazaré con todo el cariño que ya siento por ti, te quiero.🌟</p>
    </div>

<script>
        const canvas = document.getElementById('particlesCanvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let particles = [];

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 3 + 1;
                this.speedX = Math.random() * 2 - 1;
                this.speedY = Math.random() * 2 - 1;
                this.opacity = Math.random();
                this.fadeDirection = Math.random() < 0.5 ? -0.01 : 0.01;
            }

            update(mouseX, mouseY) {
                this.x += this.speedX;
                this.y += this.speedY;

                if (this.x <= 0 || this.x >= canvas.width) this.speedX *= -1;
                if (this.y <= 0 || this.y >= canvas.height) this.speedY *= -1;

                let dx = mouseX - this.x;
                let dy = mouseY - this.y;
                let distance = Math.sqrt(dx * dx + dy * dy);

                if (distance < 100) {
                    this.speedX += dx * 0.002;
                    this.speedY += dy * 0.002;
                }

                this.opacity += this.fadeDirection;
                if (this.opacity <= 0.1 || this.opacity >= 1) {
                    this.fadeDirection *= -1;
                }
            }

            draw() {
                ctx.fillStyle = `rgba(255, 255, 255, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function initParticles() {
            for (let i = 0; i < 100; i++) {
                particles.push(new Particle());
            }
        }

        function animateParticles(mouseX = canvas.width / 2, mouseY = canvas.height / 2) {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(particle => {
                particle.update(mouseX, mouseY);
                particle.draw();
            });
            setTimeout(() => animateParticles(mouseX, mouseY), 30); // Reduce sobrecarga con setTimeout
        }

        document.addEventListener('mousemove', event => {
            animateParticles(event.clientX, event.clientY);
        });

        initParticles();
        animateParticles();

        // 🔥 Corrección del fondo dinámico (ahora usa valores hexadecimales más estables)
        function toggleBackground() {
            let body = document.body;
            let currentColor = body.style.backgroundColor;

            if (currentColor === "rgb(0, 0, 0)" || currentColor === "#000000") {
                body.style.backgroundColor = "#ffcc00";
            } else {
                body.style.backgroundColor = "#000000";
            }
        }

        setInterval(toggleBackground, 6000); // Cambia cada 6 segundos
    </script>
</body>
</html>