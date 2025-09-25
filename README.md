<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Broken Crown - Aventura Épica</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            background: #0a0a0a;
            color: white;
            overflow-x: hidden;
        }

        /* NUEVO HEADER CINEMATOGRÁFICO */
        header {
            height: 100vh;
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: 
                radial-gradient(circle at 30% 20%, rgba(139, 0, 0, 0.4) 0%, transparent 50%),
                radial-gradient(circle at 70% 80%, rgba(75, 0, 130, 0.3) 0%, transparent 50%),
                linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #2d1b69 100%);
            overflow: hidden;
        }

        /* Efecto de niebla animada */
        .fog-layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 200%;
            height: 100%;
            background: 
                radial-gradient(ellipse 800px 400px at 0% 100%, rgba(255,255,255,0.03) 0%, transparent 70%),
                radial-gradient(ellipse 600px 300px at 100% 0%, rgba(255,255,255,0.02) 0%, transparent 70%);
            animation: fogDrift 20s infinite linear;
            z-index: 1;
        }

        @keyframes fogDrift {
            0% { transform: translateX(-50%); }
            100% { transform: translateX(0%); }
        }

        /* Corona 3D principal */
        .crown-3d {
            position: absolute;
            top: 30%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 400px;
            height: 300px;
            z-index: 2;
            filter: drop-shadow(0 0 30px rgba(255, 215, 0, 0.3));
            animation: crownRotate 15s infinite linear;
        }

        @keyframes crownRotate {
            0% { transform: translate(-50%, -50%) rotateY(0deg) scale(1); }
            50% { transform: translate(-50%, -50%) rotateY(180deg) scale(1.1); }
            100% { transform: translate(-50%, -50%) rotateY(360deg) scale(1); }
        }

        /* Título con efectos dramáticos */
        .main-title {
            font-size: 5rem;
            font-weight: 900;
            background: linear-gradient(135deg, #ffd700 0%, #ff8c00 30%, #dc143c 70%, #8b0000 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 
                0 0 40px rgba(255, 215, 0, 0.5),
                0 0 80px rgba(220, 20, 60, 0.3),
                0 5px 10px rgba(0,0,0,0.8);
            margin-bottom: 2rem;
            position: relative;
            z-index: 3;
            animation: titlePulse 4s infinite ease-in-out;
            letter-spacing: 0.1em;
        }

        @keyframes titlePulse {
            0%, 100% { 
                transform: scale(1); 
                filter: brightness(1);
            }
            50% { 
                transform: scale(1.02); 
                filter: brightness(1.2);
            }
        }

        /* Subtítulo épico */
        .subtitle {
            font-size: 1.5rem;
            color: rgba(255, 255, 255, 0.8);
            text-transform: uppercase;
            letter-spacing: 0.3em;
            margin-bottom: 3rem;
            position: relative;
            z-index: 3;
            animation: subtitleGlow 3s infinite alternate;
        }

        @keyframes subtitleGlow {
            0% { text-shadow: 0 0 10px rgba(255,255,255,0.3); }
            100% { text-shadow: 0 0 20px rgba(255,255,255,0.6); }
        }

        /* Botón de llamada a la acción */
        .cta-button {
            padding: 1rem 3rem;
            font-size: 1.2rem;
            background: linear-gradient(45deg, #8b0000, #dc143c, #ff4500);
            border: none;
            border-radius: 50px;
            color: white;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            cursor: pointer;
            position: relative;
            z-index: 3;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(220, 20, 60, 0.3);
            text-decoration: none;
            display: inline-block;
            font-weight: bold;
        }

        .cta-button:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 20px 50px rgba(220, 20, 60, 0.5);
            filter: brightness(1.2);
        }

        /* Rayos de energía */
        .energy-rays {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        .ray {
            position: absolute;
            width: 2px;
            height: 100px;
            background: linear-gradient(to bottom, transparent, #dc143c, transparent);
            animation: rayMove 8s infinite linear;
        }

        .ray:nth-child(1) { left: 10%; animation-delay: 0s; }
        .ray:nth-child(2) { left: 30%; animation-delay: 2s; }
        .ray:nth-child(3) { left: 50%; animation-delay: 4s; }
        .ray:nth-child(4) { left: 70%; animation-delay: 6s; }
        .ray:nth-child(5) { left: 90%; animation-delay: 1s; }

        @keyframes rayMove {
            0% { 
                top: -100px; 
                opacity: 0; 
                transform: rotate(45deg);
            }
            50% { 
                opacity: 1; 
            }
            100% { 
                top: 100vh; 
                opacity: 0;
                transform: rotate(45deg);
            }
        }

        /* Navegación moderna */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            padding: 1rem 2rem;
            background: rgba(10, 10, 10, 0.8);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 215, 0, 0.1);
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav.scrolled {
            background: rgba(10, 10, 10, 0.95);
            border-bottom: 1px solid rgba(220, 20, 60, 0.3);
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ffd700, #dc143c);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-btn {
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            padding: 0.5rem 1rem;
            border-radius: 25px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .nav-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(255, 215, 0, 0.2), rgba(220, 20, 60, 0.2));
            transition: left 0.3s ease;
            z-index: -1;
        }

        .nav-btn:hover::before {
            left: 0;
        }

        .nav-btn:hover {
            color: white;
            transform: translateY(-2px);
        }

        /* Secciones mejoradas */
        section {
            padding: 5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 3rem;
            text-align: center;
            margin-bottom: 3rem;
            background: linear-gradient(45deg, #ffd700, #ff8c00);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(45deg, #ffd700, #dc143c);
        }

        .story-content {
            font-size: 1.2rem;
            line-height: 1.8;
            text-align: justify;
            background: linear-gradient(135deg, rgba(255,255,255,0.05), rgba(255,255,255,0.02));
            padding: 3rem;
            border-radius: 20px;
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255,215,0,0.2);
            margin-bottom: 2rem;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        /* Grid de características rediseñado */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        /* Sección del Mapa */
        .map-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: 3rem;
        }

        .map-video {
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 25px 50px rgba(0,0,0,0.5);
            border: 2px solid rgba(255, 215, 0, 0.3);
            max-width: 800px;
            width: 100%;
        }

        .map-video video {
            width: 100%;
            height: auto;
            min-height: 400px;
            object-fit: cover;
            display: block;
            filter: sepia(10%) contrast(1.1) brightness(0.9);
        }

        .map-video video::-webkit-media-controls-panel {
            background-color: rgba(0, 0, 0, 0.8);
        }

        .map-video video::-webkit-media-controls {
            border-radius: 0 0 20px 20px;
        }

        .feature-card {
            background: linear-gradient(135deg, rgba(139, 0, 0, 0.1), rgba(75, 0, 130, 0.1));
            padding: 2.5rem;
            border-radius: 20px;
            backdrop-filter: blur(15px);
            border: 1px solid rgba(220, 20, 60, 0.2);
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(220, 20, 60, 0.1), transparent);
            transition: left 0.6s ease;
        }

        .feature-card:hover::before {
            left: 100%;
        }

        .feature-card:hover {
            transform: translateY(-10px) scale(1.02);
            border-color: #dc143c;
            box-shadow: 0 25px 50px rgba(220, 20, 60, 0.2);
        }

        .feature-icon {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            filter: drop-shadow(0 0 10px rgba(255, 215, 0, 0.5));
        }

        .feature-title {
            font-size: 1.8rem;
            color: #ffd700;
            margin-bottom: 1rem;
            font-weight: bold;
        }

        .feature-description {
            color: rgba(255,255,255,0.9);
            line-height: 1.6;
            font-size: 1.1rem;
        }

        /* Personaje rediseñado */
        .character-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
            margin-top: 3rem;
        }

        .character-image {
            width: 350px;
            height: 450px;
            background: linear-gradient(135deg, #1a1a2e, #16213e);
            border: 3px solid #ffd700;
            border-radius: 25px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 8rem;
            box-shadow: 
                0 25px 50px rgba(0,0,0,0.5),
                inset 0 0 50px rgba(255, 215, 0, 0.1);
            transition: all 0.4s ease;
            margin: 0 auto;
            position: relative;
            overflow: hidden;
        }

        .character-image::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 215, 0, 0.1), transparent);
            animation: characterGlow 3s infinite linear;
        }

        @keyframes characterGlow {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .character-image:hover {
            transform: scale(1.05);
            box-shadow: 
                0 30px 60px rgba(255, 215, 0, 0.3),
                inset 0 0 50px rgba(255, 215, 0, 0.2);
        }

        .character-info {
            background: linear-gradient(135deg, rgba(255,255,255,0.05), rgba(255,255,255,0.02));
            padding: 3rem;
            border-radius: 25px;
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255,215,0,0.3);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .character-name {
            font-size: 2.5rem;
            background: linear-gradient(45deg, #ffd700, #ff8c00);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 1.5rem;
            text-shadow: 0 0 20px rgba(255, 215, 0, 0.3);
        }

        .character-stats {
            margin-top: 2rem;
        }

        .stat {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 1rem 0;
            padding: 0.8rem;
            background: rgba(220, 20, 60, 0.1);
            border-radius: 10px;
            border-left: 3px solid #dc143c;
            transition: all 0.3s ease;
        }

        .stat:hover {
            background: rgba(220, 20, 60, 0.2);
            transform: translateX(10px);
        }

        /* Efectos de scroll mejorados */
        .fade-in {
            opacity: 0;
            transform: translateY(50px);
            transition: all 1s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Responsive mejorado */
        @media (max-width: 768px) {
            .main-title {
                font-size: 3rem;
            }
            
            .nav-links {
                gap: 1rem;
            }
            
            .character-section {
                grid-template-columns: 1fr;
                gap: 2rem;
            }
            
            .character-image {
                width: 280px;
                height: 350px;
                font-size: 6rem;
            }
            
            .crown-3d {
                width: 300px;
                height: 200px;
            }
        }
    </style>
</head>
<body>
    <!-- Navegación moderna -->
    <nav id="navbar">
        <div class="nav-container">
            <div class="logo">The Broken Crown</div>
            <div class="nav-links">
                <a href="#home" class="nav-btn">Inicio</a>
                <a href="#story" class="nav-btn">Historia</a>
                <a href="#features" class="nav-btn">Características</a>
                <a href="#map" class="nav-btn">Mapa</a>
                <a href="#character" class="nav-btn">Personaje</a>
            </div>
        </div>
    </nav>

    <!-- Nuevo header cinematográfico -->
    <header id="home">
        <div class="fog-layer"></div>
        
        <div class="energy-rays">
            <div class="ray"></div>
            <div class="ray"></div>
            <div class="ray"></div>
            <div class="ray"></div>
            <div class="ray"></div>
        </div>

        <h1 class="main-title">THE BROKEN CROWN</h1>
        <p class="subtitle">La Corona del Reino Caído</p>
        <a href="#story" class="cta-button">Descubre la Historia</a>
        </header>

    <!-- Historia -->
    <section id="story" class="fade-in">
        <h2 class="section-title">La Historia</h2>
        <div class="story-content">
            <p>Nuestra historia se va a tratar sobre la corrupción que hay en todos los pueblos y que también está sucediendo en la capital. Nuestro objetivo será descubrir qué está pasando en ese horrible lugar. Los pequeños detalles esconden grandes cosas: ese lugar no es lo que parece. Los dictadores ocultan su rostro debajo de muchas máscaras; detrás de esa fachada de ser un soldado bueno y respetar a las personas, hay corrupción.</p>
            
            <p>Nosotros seremos los héroes de esta historia.<br>
            ¿Habrá muertes? Sí.<br>
            ¿Habrá dolor? Sí.<br>
            Pero todos tenemos solo una vida, y esa hay que cuidarla. Solo hay una oportunidad para salvar esta capital y estos pueblos. Sé que hay más reinos afuera, con más destrucción y corrupción, pero por ahora mi prioridad es salvar a mi pueblo y a mi capital.</p>
            
            <p>Pero el tiempo se agota, y fuerzas misteriosas parecen estar trabajando en su contra. ¿Podrá nuestro héroe descubrir la verdad detrás de la corrupción y salvar no solo a Aethermoor, sino a todas las dimensiones existentes?</p>
        </div>
    </section>

    <!-- Características del Juego -->
    <section id="features" class="fade-in">
        <h2 class="section-title">Características del Juego</h2>
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">🏰</div>
                <h3 class="feature-title">Exploración Épica</h3>
                <p class="feature-description">Explora mazmorras peligrosas llenas de trampas y tesoros ocultos. Descubre lugares secretos que guardan los misterios más profundos del reino y sus antiguos secretos.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">📜</div>
                <h3 class="feature-title">Sistema de Misiones</h3>
                <p class="feature-description">Completa misiones principales que revelarán la verdad sobre la corrupción, misiones secundarias que te ayudarán a fortalecer tu personaje, y misiones secretas con recompensas únicas.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🛡️</div>
                <h3 class="feature-title">Comercio y Equipamiento</h3>
                <p class="feature-description">Compra objetos, armas y armaduras en diversos comerciantes. Prepárate estratégicamente para cada aventura con el equipo adecuado para enfrentar los peligros que te esperan.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🕵️</div>
                <h3 class="feature-title">Misterio Central</h3>
                <p class="feature-description">Descubre quién es el verdadero responsable de la corrupción en el reino. ¿Será el rey quien oculta un lado oscuro, o sus soldados de élite han traicionado su juramento?</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">⚔️</div>
                <h3 class="feature-title">Armamento Mítico</h3>
                <p class="feature-description">Consigue armaduras legendarias y espadas míticas forjadas por antiguos maestros herreros. Cada arma tiene poderes únicos que te ayudarán a purificar la corrupción.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">👥</div>
                <h3 class="feature-title">Compañeros de Aventura</h3>
                <p class="feature-description">Recluta asistentes valientes que te acompañarán en tu misión. Cada compañero tiene habilidades especiales que complementarán tu estilo de juego y estrategias de combate.</p>
            </div>
        </div>
    </section>

    <!-- Mapa del Juego -->
    <section id="map" class="fade-in">
        <h2 class="section-title">Mapa del Reino</h2>
        <div class="map-container">
            <div class="map-video">
                <video controls>
                    <source src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4
" type="video/mp4">
                    <source src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4
" type="video/webm">
                    Tu navegador no soporta el elemento de video.
                </video>
            </div>
        </div>
    </section>

    <!-- Personaje Principal -->
    <section id="character" class="fade-in">
        <h2 class="section-title">El Personaje Principal</h2>
        <div class="character-section">
            <div class="character-image" style="background-image: url('https://i.ibb.co/hFgmck42/personajeprincipal.png'); background-size: contain; background-position: center; background-repeat: no-repeat; font-size: 0;">
</div>
</div>
            <div class="character-info">
                <h3 class="character-name">Kaelen Marcaluces</h3>
                <p><strong>Edad:</strong> 22 años</p>
                <p><strong>Origen:</strong> Aldea de Luminar, en los Valles Dorados</p>
                <p><strong>Clase:</strong> Guardián de Marcadores</p>
                
                <p style="margin: 1rem 0;"><strong>Historia:</strong> Huérfano desde pequeño, Kaelen fue criado por el sabio ermitaño Eldric en las afueras de Luminar. Desde joven mostró una conexión especial con la magia de purificación, capaz de limpiar aguas contaminadas y sanar plantas marchitas con solo tocarlas.</p>
                
                <p><strong>Habilidad Especial:</strong> <em>Resonancia de Marcadores</em> - Puede sentir la presencia de los Marcadores Ancestrales y purificar su corrupción mediante rituales mágicos.</p>
                
                <div class="character-stats">
                    <h4 style="color: #ffd700; margin-bottom: 1rem;">Estadísticas:</h4>
                    <div class="stat">
                        <span>Fuerza:</span>
                        <span>75/100</span>
                    </div>
                    <div class="stat">
                        <span>Magia:</span>
                        <span>95/100</span>
                    </div>
                    <div class="stat">
                        <span>Agilidad:</span>
                        <span>80/100</span>
                    </div>
                    <div class="stat">
                        <span>Sabiduría:</span>
                        <span>88/100</span>
                    </div>
                    <div class="stat">
                        <span>Carisma:</span>
                        <span>70/100</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <script>
        // Navegación que cambia con scroll
        window.addEventListener('scroll', () => {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 100) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Scroll suave mejorado
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Animación de aparición mejorada
        function handleScroll() {
            const elements = document.querySelectorAll('.fade-in');
            elements.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 100;
                
                if (elementTop < window.innerHeight - elementVisible) {
                    element.classList.add('visible');
                }
            });
        }

        // Inicializar
        window.addEventListener('scroll', handleScroll);
        handleScroll();
    </script>
</body>
</html>

