<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Universidad Innova</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-blue: #021f54;
            --check-green: #22a033;
            /* Degradado ajustado a la imagen (azul más intenso a la izquierda, claro a la derecha) */
            --bg-gradient-start: #6ebcf0;
            --bg-gradient-end: #e6f5ff;
            --grey-circle: #8a9bb0;
            --text-grey: #333333;
        }
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }
        body {
            background: linear-gradient(to right, var(--bg-gradient-start) 0%, var(--bg-gradient-end) 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: var(--primary-blue);
            overflow-x: hidden;
            position: relative; /* Necesario para posicionar el logo libremente */
        }
        /* ==========================================
           LOGO (Posicionado arriba a la izquierda)
           ========================================== */
        .logo-container {
            position: absolute;
            top: 40px;
            left: 50px;
            text-align: left;
            z-index: 10;
        }
        .logo-container h1 {
            font-size: 4.5rem;
            font-weight: 900;
            line-height: 0.9;
            letter-spacing: -2px;
        }
        .logo-container p {
            font-size: 1.1rem;
            text-transform: uppercase;
            font-weight: 500;
            line-height: 1.1;
            margin-top: 5px;
            letter-spacing: 0.5px;
        }
        /* ==========================================
           MENÚ DE BOTONES (Centrado)
           ========================================== */
        .pill-menu {
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
            width: 100%;
            align-items: center;
            z-index: 5;
        }
        /* Estilo 3D idéntico a la imagen */
        .pill {
            background: #ffffff;
            color: var(--primary-blue);
            padding: 1.2rem 2.5rem;
            border-radius: 50px;
            font-size: 1.4rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 1.5rem;
            cursor: pointer;
            width: 100%;
            max-width: 320px;
            /* Sombra para efecto de pastilla 3D */
            box-shadow: 
                10px 10px 20px rgba(0, 0, 0, 0.1), 
                -5px -5px 15px rgba(255, 255, 255, 0.6),
                inset 0 -2px 5px rgba(0, 0, 0, 0.05);
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .pill:hover {
            transform: translateY(-3px);
            box-shadow: 
                12px 12px 25px rgba(0, 0, 0, 0.15), 
                -5px -5px 15px rgba(255, 255, 255, 0.7),
                inset 0 -2px 5px rgba(0, 0, 0, 0.05);
        }
        .pill:active {
            transform: translateY(0);
        }
        .pill i {
            font-size: 1.5rem;
            width: 30px;
            text-align: center;
        }
        /* ==========================================
           VENTANA APARTE (Modal Emergente)
           ========================================== */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(8px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.4s ease;
        }
        .modal-overlay.active {
            opacity: 1;
            pointer-events: auto;
        }
        .modal-window {
            background: #ffffff;
            padding: 3rem 4rem;
            border-radius: 24px;
            box-shadow: 0 30px 60px rgba(0,0,0,0.2);
            position: relative;
            max-width: 650px;
            width: 90%;
            transform: scale(0.8) translateY(20px);
            transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .modal-overlay.active .modal-window {
            transform: scale(1) translateY(0);
        }
        .close-btn {
            position: absolute;
            top: 20px;
            right: 25px;
            font-size: 2.5rem;
            color: #adb5bd;
            cursor: pointer;
            transition: color 0.2s, transform 0.2s;
        }
        .close-btn:hover {
            color: #ff4757;
            transform: rotate(90deg);
        }
        .content-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            border-bottom: 2px solid #f1f3f5;
            padding-bottom: 2rem;
        }
        .content-header h2 {
            font-size: 3.5rem;
            line-height: 1.1;
            color: var(--primary-blue);
        }
        .big-check-circle {
            background: var(--grey-circle);
            width: 120px;
            height: 120px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-shrink: 0;
            box-shadow: inset 0 2px 4px rgba(255,255,255,0.4);
        }
        .big-check-circle i {
            color: var(--check-green);
            font-size: 5rem;
            text-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        .feature-list {
            display: flex;
            flex-direction: column;
            gap: 1.8rem;
        }
        .feature-item {
            display: flex;
            align-items: center;
            gap: 1.5rem;
            font-size: 2.2rem;
            font-weight: 600;
            color: var(--text-grey);
        }
        .feature-item i {
            color: var(--check-green);
            font-size: 2.5rem;
        }
        /* Responsividad para móviles */
        @media (max-width: 768px) {
            body {
                flex-direction: column;
                justify-content: flex-start;
                padding-top: 2rem;
            }
            .logo-container {
                position: relative;
                top: 0; left: 0;
                margin-bottom: 3rem;
                text-align: center;
            }
            .content-header { flex-direction: column-reverse; text-align: center; gap: 1.5rem; }
            .content-header h2 { font-size: 2.5rem; }
            .feature-item { font-size: 1.5rem; justify-content: center; }
            .big-check-circle { width: 90px; height: 90px; }
            .big-check-circle i { font-size: 3.5rem; }
            .modal-window { padding: 2.5rem 1.5rem; }
            .close-btn { top: 10px; right: 15px; font-size: 2rem; }
        }
    </style>
</head>
<body>
    <div class="logo-container">
        <h1>UNI</h1>
        <p>Universidad<br>Del País<br>Innova</p>
    </div>  
    <div class="pill-menu">
        <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-graduation-cap"></i> Maestría</div>
        <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-star"></i> Especialidad</div>
        <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-graduation-cap"></i> Doctorado</div>
        <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-certificate"></i> Certificación</div>
        <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-book-open"></i> Cursos</div>
        <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-award"></i> Diplomado</div>
    </div>
    <div class="modal-overlay" id="ventanaAparte" onclick="cerrarVentanaFondo(event)">
        <div class="modal-window">         
            <i class="fa-solid fa-xmark close-btn" onclick="cerrarVentana()"></i>
            <div class="content-header">
                <h2>Fortalece<br>tu habilidad</h2>
                <div class="big-check-circle">
                    <i class="fa-solid fa-check"></i>
                </div>
            </div>          
            <div class="feature-list">
                <div class="feature-item">
                    <i class="fa-solid fa-check"></i> Contenido práctico
                </div>
                <div class="feature-item">
                    <i class="fa-solid fa-check"></i> Enfoque profesional
                </div>
                <div class="feature-item">
                    <i class="fa-solid fa-check"></i> Aplicación real
                </div>
            </div>
        </div>
    </div>
    <script>
        const modal = document.getElementById('ventanaAparte');
        function abrirVentana() {
            modal.classList.add('active');
        }
        function cerrarVentana() {
            modal.classList.remove('active');
        }
        function cerrarVentanaFondo(event) {
            if (event.target === modal) {
                cerrarVentana();
            }
        }
    </script>

</body>
</html>
