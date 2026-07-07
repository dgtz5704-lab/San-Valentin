
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
            --neon-blue: #00d2ff; /* Color azul brillante para el neón */
            --check-green: #22a033;
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
            position: relative;
        }
        /* ==========================================
           LOGO RECONSTRUIDO (Idéntico a la imagen)
           ========================================== */
        .logo-container {
            position: absolute;
            top: 40px;
            left: 50px;
            display: flex;
            flex-direction: column;
            z-index: 10;
        }
        .logo-uni {
            font-family: 'Arial Black', Impact, sans-serif; /* Letra ultra gruesa */
            font-size: 5.5rem;
            font-weight: 900;
            line-height: 0.75;
            letter-spacing: -4px;
            margin-bottom: 10px;
            color: var(--primary-blue);
        }
        .logo-sub {
            font-size: 1.05rem;
            font-weight: 400; /* Letra delgada */
            letter-spacing: 0.5px;
            line-height: 1.2;
            text-transform: uppercase;
        }
        .logo-innova {
            font-size: 1.45rem;
            font-weight: 800; /* Letra negrita */
            letter-spacing: 0.5px;
            line-height: 1.1;
            text-transform: uppercase;
            margin-top: 2px;
        }
        /* ==========================================
           MENÚ DE BOTONES
           ========================================== */
        .pill-menu {
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
            width: 100%;
            align-items: center;
            z-index: 5;
        }
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
            /* Agregamos un borde transparente para que no salte el tamaño al hacer hover */
            border: 2px solid transparent; 
            /* Sombra base 3D */
            box-shadow: 
                10px 10px 20px rgba(0, 0, 0, 0.1), 
                -5px -5px 15px rgba(255, 255, 255, 0.6),
                inset 0 -2px 5px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease; /* Transición suave para todos los efectos */
        }
        /* EFECTO NEÓN AL PASAR EL MOUSE */
        .pill:hover {
            transform: translateY(-4px) scale(1.02);
            border-color: var(--neon-blue); /* Borde azul brillante */
            box-shadow: 
                0 0 15px rgba(0, 210, 255, 0.6), /* Resplandor neón interior */
                0 0 30px rgba(0, 210, 255, 0.4), /* Resplandor neón exterior */
                12px 12px 25px rgba(0, 0, 0, 0.15), /* Sombra 3D pronunciada */
                -5px -5px 15px rgba(255, 255, 255, 0.7);
        }
        .pill:active {
            transform: translateY(0) scale(0.98);
            box-shadow: 0 0 10px rgba(0, 210, 255, 0.8);
        }
        .pill i {
            font-size: 1.5rem;
            width: 30px;
            text-align: center;
            transition: color 0.3s ease;
        }
        .pill:hover i {
            color: var(--neon-blue); /* El ícono también se ilumina un poco */
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
                align-items: center;
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
        <div class="logo-uni">UNI</div>
        <div class="logo-sub">UNIVERSIDAD</div>
        <div class="logo-sub">DEL PAÍS</div>
        <div class="logo-innova">INNOVA</div>
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
