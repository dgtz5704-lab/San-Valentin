<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>🎂 ¡Feliz Cumpleaños Suegrita! 🎂</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap');
        * { 
            box-sizing: border-box; 
            touch-action: manipulation; 
            -webkit-tap-highlight-color: transparent;
        }
        body { 
            margin: 0; 
            height: 100vh; 
            overflow: hidden;
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(-45deg, #ff9a9e, #fecfef, #a1c4fd, #c2e9fb);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            display: flex; 
            justify-content: center; 
            align-items: center;
            color: #333;
        }
        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        /* Contenedores de pantallas */
        .screen {
            position: absolute;
            top: 0; left: 0; 
            width: 100%; height: 100%;
            display: flex; 
            flex-direction: column; 
            justify-content: center;
            align-items: center; 
            text-align: center; 
            padding: 20px;
            transition: opacity 0.8s ease, transform 0.8s ease;
            background: rgba(255, 255, 255, 0.4);
            backdrop-filter: blur(10px);
            z-index: 10;
        }
        .hidden { 
            opacity: 0; 
            pointer-events: none; 
            transform: scale(0.9);
            z-index: -1;
        }
        /* Tipografía y Textos */
        h1 { color: #ff4785; font-size: clamp(1.8rem, 6vw, 2.5rem); margin-bottom: 10px; text-shadow: 2px 2px 4px rgba(0,0,0,0.1); }
        h2 { color: #5a5a5a; font-size: clamp(1.2rem, 4vw, 1.5rem); font-weight: 400; }
        p { font-size: clamp(1rem, 3.5vw, 1.2rem); color: #444; line-height: 1.5; margin-bottom: 20px; }
        /* Icono de regalo animado */
        .gift-icon {
            font-size: 80px;
            cursor: pointer;
            animation: pulse 1.5s infinite;
            margin-bottom: 20px;
            user-select: none;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1) rotate(5deg); }
            100% { transform: scale(1); }
        }
        /* Botones */
        .btn {
            padding: 15px 30px; 
            font-size: 1.2rem; 
            font-weight: 600;
            border: none;
            border-radius: 50px; 
            cursor: pointer; 
            margin: 10px;
            transition: 0.2s; 
            box-shadow: 0 8px 15px rgba(0,0,0,0.15);
            font-family: 'Poppins', sans-serif;
            position: relative;
        }
        .btn:active { transform: scale(0.95); box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
        .btn-yes { background: linear-gradient(45deg, #1dd1a1, #10ac84); color: white; }
        .btn-no { background: linear-gradient(45deg, #ff6b6b, #ee5253); color: white; position: absolute; }
        .btn-action { background: white; color: #ff4785; border: 2px solid #ff4785; width: 80%; max-width: 300px; }
        .btn-action:hover { background: #ff4785; color: white; }
        /* Contenedor de la pantalla final */
        .celebration-box {
            background: rgba(255, 255, 255, 0.85);
            padding: 30px 20px;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            width: 95%;
            max-width: 500px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        /* Elementos flotantes (confeti, flores) */
        .particle {
            position: absolute;
            font-size: 25px;
            pointer-events: none;
            z-index: 100;
            animation: fall linear forwards;
        }
        @keyframes fall {
            0% { transform: translateY(-10vh) rotate(0deg) scale(1); opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg) scale(1.5); opacity: 0; }
        }
        /* Mensaje final oculto */
        #cartaMensaje {
            display: none;
            background: #fff0f3;
            padding: 15px;
            border-radius: 15px;
            border: 1px dashed #ff4785;
            margin-top: 20px;
            font-size: 0.95rem;
            color: #555;
            animation: fadeIn 1s;
        }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(-10px); } to { opacity: 1; transform: translateY(0); } }

    </style>
</head>
<body>
    <div id="pantalla1" class="screen">
        <div class="gift-icon" onclick="irPantalla2()">🎁</div>
        <h1>¡Hola, Suegrita!</h1>
        <h2>Hoy es un día muy especial...</h2>
        <p>Toca el regalito para abrir tu sorpresa.</p>
    </div>
    <div id="pantalla2" class="screen hidden">
        <h1>Una pregunta rápida... 🤔</h1>
        <p>Antes de ver su sorpresa, tiene que responder con total honestidad:</p>
        <h2 style="color: #ff4785; font-weight: 800; margin: 30px 0;">¿Verdad que quiere mucho a su yerno? 😇</h2>
        <div style="position: relative; width: 100%; height: 200px; display: flex; justify-content: center; align-items: center;">

<button class="btn btn-yes" onclick="irPantalla3()">¡sí! ❤️</button>
  
<button id="btnNo" class="btn btn-no" onmouseover="moverBotonNo()" ontouchstart="moverBotonNo()">No😒
            
</button>
</div>
    </div>
    <div id="pantalla3" class="screen hidden" style="background: transparent; backdrop-filter: none;">
        <div class="celebration-box">
            <h1>¡Feliz Cumpleaños! 🎂</h1>
            <h2 id="pastel">🎂🕯️✨</h2>
            <p>¡Sabía que diría que sí! Usted es la mejor suegrita del mundo. ¡Hora de celebrar!</p>
            <button class="btn btn-action" onclick="lanzarParticulas(['🌸','🌺','🌷','🌼'])">Lluvia de Flores 🌸</button>
            <button class="btn btn-action" onclick="lanzarParticulas(['🐻','🫂','💖','🥰'])">Mandar Abrazos 🐻</button>
            <button class="btn btn-action" onclick="apagarVelitas()">Apagar Velitas 💨</button>
            <button class="btn btn-action" style="background: #ff4785; color: white;" onclick="mostrarCarta()">Leer Mensaje Especial 💌</button>
            <div id="cartaMensaje">
                <strong>Querida Suegrita:</strong><br><br>
                Que este nuevo año de vida le traiga muchísima salud, paz, bendiciones y motivos para sonreír todos los días. 
                Gracias por su cariño y por abrirme las puertas de su familia. ¡Disfrute mucho su día, la queremos muchísimo! 🎉❤️
            </div>
        </div>
    </div>
    <script>
        // Funciones de navegación entre pantallas
        function irPantalla2() {
            document.getElementById('pantalla1').classList.add('hidden');
            document.getElementById('pantalla2').classList.remove('hidden');
        }
        function irPantalla3() {
            document.getElementById('pantalla2').classList.add('hidden');
            document.getElementById('pantalla3').classList.remove('hidden');
            lanzarParticulas(['🎉', '✨', '🎈', '🎊']); // Confeti inicial
        }
        // Función de la trampa del Yerno (El botón NO huye)
        function moverBotonNo() {
            const btn = document.getElementById('btnNo');
            // Calculamos el espacio disponible en la pantalla
            const maxX = window.innerWidth - btn.clientWidth - 20;
            const maxY = window.innerHeight - btn.clientHeight - 20;
            // Generamos posiciones aleatorias
            const randomX = Math.max(10, Math.random() * maxX);
            const randomY = Math.max(10, Math.random() * maxY);
            // Aplicamos posición absoluta
            btn.style.position = 'fixed';
            btn.style.left = randomX + 'px';
            btn.style.top = randomY + 'px';
        }
        // Función para lanzar emojis/confeti desde arriba
        function lanzarParticulas(arrayEmojis) {
            const cantidad = 30; // Número de partículas por clic
            for (let i = 0; i < cantidad; i++) {
                let p = document.createElement("div");
                p.className = "particle";
                // Elegir emoji aleatorio del array
                p.innerHTML = arrayEmojis[Math.floor(Math.random() * arrayEmojis.length)];
                // Posición horizontal inicial aleatoria
                p.style.left = Math.random() * 100 + "vw";
                // Duración de la caída aleatoria para que se vea natural
                p.style.animationDuration = (Math.random() * 2 + 2.5) + "s";
                // Retardo aleatorio para que no caigan todas de golpe
                p.style.animationDelay = (Math.random() * 0.5) + "s";
                document.body.appendChild(p);
                // Eliminar el elemento del DOM después de que termine la animación
                setTimeout(() => p.remove(), 4000);
            }
        }
        // Interacción del pastel
        function apagarVelitas() {
            document.getElementById('pastel').innerHTML = "🍰🎂✨";
            lanzarParticulas(['💨', '🎉', '👏', '🥳']);
            }
        // Mostrar el mensaje bonito al final
        function mostrarCarta() {
            const carta = document.getElementById('cartaMensaje');
            if(carta.style.display === 'block') {
carta.style.display = 'none';
            } else {
                carta.style.display = 'block';
                lanzarParticulas(['💌', '💖',
                                  '✨']);
            }
        }
    </script>
</body>
</html>
