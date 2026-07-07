<!DOCTYPEhtml>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Universidad Innova</title>
    <!-- Cargamos FontAwesome para los íconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            /* Colores extraídos de las imágenes */
            --primary-blue: #021f54;
            --check-green: #22a033;
            --bg-gradient-start: #83cbfd;
            --bg-gradient-end: #d8f1ff;
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
            /* Fondo azul degradado */
            background: linear-gradient(135deg, var(--bg-gradient-start) 0%, var(--bg-gradient-end) 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 2rem;
            color: var(--primary-blue);
            overflow-x: hidden;
        }
        /* ==========================================
           PANTALLA PRINCIPAL (Logo y Botones)
           ========================================== */
        .main-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 3rem;
            max-width: 800px;
            width: 100%;
        }
        .logo-container {
            text-align: center;
        }
        .logo-container h1 {
            font-size: 5rem;
            font-weight: 900;
            line-height: 1;
            letter-spacing: -3px;
            text-shadow: 2px 2px 5px rgba(0,0,0,0.1);
        }
        .logo-container p {
            font-size: 1.2rem;
            text-transform: uppercase;
            font-weight: 500;
            line-height: 1.2;
            letter-spacing: 0.5px;
        }
        .pill-menu {
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
            width: 100%;
            align-items: center;
        }
        /* Estilo 3D de los botones */
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
            max-width: 350px;
            box-shadow: 
                0 10px 15px rgba(0, 0, 0, 0.08), 
                0 4px 6px rgba(0, 0, 0, 0.04), 
                inset 0 -4px 5px rgba(0, 0, 0, 0.05),
                inset 0 4px 5px rgba(255, 255, 255, 0.8);
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .pill:hover {
            transform: translateY(-4px);
            box-shadow: 
                0 15px 20px rgba(0, 0, 0, 0.12), 
                0 6px 8px rgba(0, 0, 0, 0.06), 
                inset 0 -4px 5px rgba(0, 0, 0, 0.05);
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
            backdrop-filter: blur(8px); /* Efecto de cristal esmerilado en el fondo */
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
            transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); /* Animación de rebote suave */
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
        /* Contenido de la ventana aparte */
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
    <!-- PANTALLA PRINCIPAL -->
    <div class="main-container">
        <div class="logo-container">
            <h1>UNI</h1>
            <p>Universidad<br>Del País<br>Innova</p>
        </div>
        <!-- Al hacer clic en cualquier botón, se abre la ventana aparte -->
        <div class="pill-menu">
            <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-graduation-cap"></i> Maestría</div>
            <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-star"></i> Especialidad</div>
            <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-graduation-cap"></i> Doctorado</div>
            <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-certificate"></i> Certificación</div>
            <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-book-open"></i> Cursos</div>
            <div class="pill" onclick="abrirVentana()"><i class="fa-solid fa-award"></i> Diplomado</div>
        </div>
    <!-- VENTANA APARTE (Modal Emergente) -->
    <div class="modal-overlay" id="ventanaAparte" onclick="cerrarVentanaFondo(event)">
        <div class="modal-window">
            <i class="fa-solid fa-xmark close-btn" onclick="cerrarVentana()"></i>
            <div class="content-header">
                <h2>Fortalece<br>tu habilidad</h2>
                <div class="big-check-circle">
                    <i class="fa-solid fa-check"></i>
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
        // Funciones para controlar la ventana aparte
        const modal = document.getElementById('ventanaAparte');
        function abrirVentana() {
            modal.classList.add('active');
        }
        function cerrarVentana() {
            modal.classList.remove('active');
        }
        // Permite cerrar la ventana si el usuario hace clic fuera de la tarjeta blanca (en el fondo oscuro)
        function cerrarVentanaFondo(event) {
            if (event.target === modal) {
                cerrarVentana();
            }
        }
    </script>
</body>
</html>
