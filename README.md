<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Universidad Innova</title>
    <!-- Cargamos FontAwesome para los íconos (birretes, estrellas, palomitas, etc.) -->
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
            /* Fondo azul degradado inspirado en la primera imagen */
            background: linear-gradient(135deg, var(--bg-gradient-start) 0%, var(--bg-gradient-end) 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 3rem 2rem;
            color: var(--primary-blue);
        }
        .container {
            display: flex;
            flex-wrap: wrap;
            gap: 5rem;
            max-width: 1200px;
            width: 100%;
            justify-content: center;
            align-items: center;
        }
        /* ==========================================
           COLUMNA IZQUIERDA (Logo y Botones)
           ========================================== */
        .left-column {
            display: flex;
            align-items: flex-start;
            gap: 2rem;
        }
        .logo-container {
            text-align: left;
            margin-top: 20px;
        }
        .logo-container h1 {
            font-size: 4rem;
            font-weight: 900;
            line-height: 1;
            letter-spacing: -3px;
        }
        .logo-container p {
            font-size: 1rem;
            text-transform: uppercase;
            font-weight: 500;
            line-height: 1.2;
            letter-spacing: 0.5px;
        }
        .pill-menu {
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
        }
        /* Estilo 3D de los botones */
        .pill {
            background: #ffffff;
            color: var(--primary-blue);
            padding: 1.2rem 2.5rem;
            border-radius: 50px;
            font-size: 1.3rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 1.2rem;
            cursor: pointer;
            width: 280px;
            /* Sombra compleja para dar efecto de volumen 3D */
            box-shadow: 
                0 10px 15px rgba(0, 0, 0, 0.08), 
                0 4px 6px rgba(0, 0, 0, 0.04), 
                inset 0 -4px 5px rgba(0, 0, 0, 0.05),
                inset 0 4px 5px rgba(255, 255, 255, 0.8);
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .pill:hover {
            transform: translateY(-3px);
            box-shadow: 
                0 15px 20px rgba(0, 0, 0, 0.12), 
                0 6px 8px rgba(0, 0, 0, 0.06), 
                inset 0 -4px 5px rgba(0, 0, 0, 0.05);
        }
        .pill i {
            font-size: 1.5rem;
            width: 30px;
            text-align: center;
        }
        /* ==========================================
           COLUMNA DERECHA (Simulador de Navegador)
           ========================================== */
        .browser-mockup {
            background: #f8f9fa;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
            width: 100%;
            max-width: 650px;
            /* Borde simulando una tablet o monitor */
            border: 12px solid #1a1a1a;
        }
        .browser-header {
            background: #e9ecef;
            padding: 0.8rem;
            display: flex;
            align-items: center;
            border-bottom: 1px solid #dee2e6;
        }
        .browser-actions {
            display: flex;
            gap: 15px;
            color: #adb5bd;
            margin-right: 1.5rem;
        }
        .browser-url {
            background: #ffffff;
            padding: 0.4rem 1.5rem;
            border-radius: 20px;
            font-size: 0.9rem;
            color: #6c757d;
            flex-grow: 1;
            border: 1px solid #ced4da;
        }
        .browser-content {
            padding: 4rem 3rem;
            background: #f8f9fa;
        }
        .content-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2.5rem;
            border-bottom: 2px solid #e9ecef;
            padding-bottom: 2.5rem;
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
            box-shadow: inset 0 2px 4px rgba(255,255,255,0.3);
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
        @media (max-width: 1024px) {
            .container { flex-direction: column; gap: 3rem; }
            .left-column { flex-direction: column; align-items: center; text-align: center; }
            .logo-container { text-align: center; margin-bottom: 1rem; }
            .content-header h2 { font-size: 2.5rem; }
            .feature-item { font-size: 1.6rem; }
            .big-check-circle { width: 90px; height: 90px; }
            .big-check-circle i { font-size: 3.5rem; }
            .browser-content { padding: 2.5rem 1.5rem; }
        }
        @media (max-width: 480px) {
            .content-header { flex-direction: column; text-align: center; gap: 1.5rem; }
            .feature-item { font-size: 1.2rem; }
            .feature-item i { font-size: 1.8rem; }
            .pill { width: 100%; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- COLUMNA IZQUIERDA (Logo y Botones) -->
        <div class="left-column">
            <div class="logo-container">
                <h1>UNI</h1>
                <p>Universidad<br>Del País<br>Innova</p>
            </div>
            <div class="pill-menu">
                <div class="pill"><i class="fa-solid fa-graduation-cap"></i> Maestría</div>
                <div class="pill"><i class="fa-solid fa-star"></i> Especialidad</div>
                <div class="pill"><i class="fa-solid fa-graduation-cap"></i> Doctorado</div>
                <div class="pill"><i class="fa-solid fa-certificate"></i> Certificación</div>
                <div class="pill"><i class="fa-solid fa-book-open"></i> Cursos</div>
                <div class="pill"><i class="fa-solid fa-award"></i> Diplomado</div>
            </div>
        </div>
        <!-- COLUMNA DERECHA (Navegador y Texto) -->
        <div class="browser-mockup">
            <div class="browser-header">
                <div class="browser-actions">
                    <i class="fa-solid fa-arrow-left"></i>
                    <i class="fa-solid fa-arrow-right"></i>
                    <i class="fa-solid fa-rotate-right"></i>
                </div>
                <div class="browser-url">
                    formacion.com/habilidades
                </div>
            </div>
            <div class="browser-content">
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
    </div>

</body>
</html>
