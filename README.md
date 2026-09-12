<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Control de Asistencia - Moderno</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-blue: #00d2ff;
            --secondary-blue: #3a7bd5;
            --dark-bg: #0b0f19;
            --card-bg: rgba(15, 23, 42, 0.75);
            --border-glow: rgba(0, 210, 255, 0.4);
            --text-color: #f8fafc;
            --text-muted: #94a3b8;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Outfit', sans-serif;
        }

        body {
            background-color: var(--dark-bg);
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(58, 123, 213, 0.15) 0%, transparent 40%),
                radial-gradient(circle at 90% 80%, rgba(0, 210, 255, 0.15) 0%, transparent 40%);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
        }

        /* Fondo animado con partículas de luz */
        .background-glow {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -1;
        }

        .glow-orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.3;
            animation: floatOrb 10s infinite alternate ease-in-out;
        }

        .orb-1 {
            width: 300px;
            height: 300px;
            background: var(--primary-blue);
            top: -50px;
            left: -50px;
        }

        .orb-2 {
            width: 350px;
            height: 350px;
            background: var(--secondary-blue);
            bottom: -50px;
            right: -50px;
            animation-delay: -5s;
        }

        @keyframes floatOrb {
            0% { transform: translateY(0) scale(1); }
            100% { transform: translateY(30px) scale(1.1); }
        }

        /* Tarjeta principal con efecto Glassmorphism y Glow azul */
        .card {
            background: var(--card-bg);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(0, 210, 255, 0.2);
            padding: 35px 30px;
            border-radius: 20px;
            box-shadow: 0 0 30px rgba(0, 210, 255, 0.15), 
                        inset 0 0 15px rgba(0, 210, 255, 0.05);
            width: 100%;
            max-width: 420px;
            text-align: center;
            position: relative;
            animation: cardAppear 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes cardAppear {
            0% { opacity: 0; transform: translateY(20px) scale(0.95); }
            100% { opacity: 1; transform: translateY(0) scale(1); }
        }

        /* Estilos del Logo */
        .logo-container {
            margin-bottom: 20px;
            display: flex;
            justify-content: center;
        }

        .logo {
            width: 130px;
            height: auto;
            filter: drop-shadow(0 0 10px rgba(0, 210, 255, 0.6));
            animation: logoPulse 3s infinite ease-in-out;
        }

        @keyframes logoPulse {
            0%, 100% { filter: drop-shadow(0 0 8px rgba(0, 210, 255, 0.5)); transform: scale(1); }
            50% { filter: drop-shadow(0 0 16px rgba(0, 210, 255, 0.9)); transform: scale(1.03); }
        }

        h2 {
            color: var(--text-color);
            margin-bottom: 8px;
            font-size: 24px;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        p {
            color: var(--text-muted);
            font-size: 14px;
            margin-bottom: 25px;
        }

        /* Inputs modernos con brillo al enfocar */
        .input-group {
            position: relative;
            margin-bottom: 15px;
        }

        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 14px 16px;
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid rgba(148, 163, 184, 0.2);
            border-radius: 10px;
            color: var(--text-color);
            font-size: 15px;
            outline: none;
            transition: all 0.3s ease;
        }

        input[type="text"]::placeholder, input[type="password"]::placeholder {
            color: var(--text-muted);
        }

        input[type="text"]:focus, input[type="password"]:focus {
            border-color: var(--primary-blue);
            box-shadow: 0 0 15px rgba(0, 210, 255, 0.3);
            background: rgba(15, 23, 42, 0.9);
        }

        /* Botones principales con degradado y efectos glow */
        button, .file-btn {
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, var(--secondary-blue), var(--primary-blue));
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin-top: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 210, 255, 0.3);
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
            position: relative;
            overflow: hidden;
        }

        button::after, .file-btn::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(rgba(255,255,255,0.2), transparent);
            transform: rotate(45deg) translateY(-100px);
            transition: transform 0.6s ease;
        }

        button:hover::after, .file-btn:hover::after {
            transform: rotate(45deg) translateY(100px);
        }

        button:hover, .file-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 210, 255, 0.5);
        }

        button:active, .file-btn:active {
            transform: translateY(1px);
        }

        .file-btn {
            margin-top: 15px;
            text-align: center;
        }

        input[type="file"] { display: none; }

        .btn-secondary {
            background: rgba(148, 163, 184, 0.1);
            border: 1px solid rgba(148, 163, 184, 0.2);
            box-shadow: none;
            color: var(--text-muted);
            margin-top: 15px;
        }

        .btn-secondary:hover {
            background: rgba(148, 163, 184, 0.2);
            color: var(--text-color);
            box-shadow: 0 0 10px rgba(148, 163, 184, 0.2);
        }

        /* Clases de control */
        .hidden {
            display: none !important;
        }

        /* Alertas modernas */
        .alert {
            padding: 14px;
            border-radius: 10px;
            margin-top: 15px;
            font-weight: 500;
            font-size: 14px;
            animation: fadeIn 0.4s ease forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .success {
            background: rgba(16, 185, 129, 0.15);
            border: 1px solid rgba(16, 185, 129, 0.4);
            color: #34d399;
            box-shadow: 0 0 15px rgba(16, 185, 129, 0.1);
        }

        .error {
            background: rgba(239, 68, 68, 0.15);
            border: 1px solid rgba(239, 68, 68, 0.4);
            color: #f87171;
            box-shadow: 0 0 15px rgba(239, 68, 68, 0.1);
        }

        .loading-text {
            color: var(--primary-blue);
            font-weight: 500;
            margin-top: 12px;
            animation: pulseText 1.5s infinite ease-in-out;
        }

        @keyframes pulseText {
            0%, 100% { opacity: 0.6; }
            50% { opacity: 1; }
        }

        /* Transiciones de secciones */
        .section-animate {
            animation: slideUp 0.5s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="background-glow">
        <div class="glow-orb orb-1"></div>
        <div class="glow-orb orb-2"></div>
    </div>

    <div class="card">
        <!-- LOGO INSTITUCIONAL -->
        <div class="logo-container">
            <img src="https://juridicosvenezuela.com/wp-content/uploads/2022/09/1652804960832.png" alt="Logo" class="logo">
        </div>

        <!-- PANTALLA DE VERIFICACIÓN DE UBICACIÓN -->
        <div id="location-section" class="section-animate">
            <h2>Verificando ubicación</h2>
            <p>Estamos comprobando que te encuentres dentro del área permitida...</p>
            <div id="location-msg"><div class="loading-text">Obteniendo tu ubicación GPS...</div></div>
            <button onclick="verificarUbicacion()" class="btn-secondary" style="margin-top:20px;">Reintentar</button>
        </div>

        <!-- PANTALLA DE LOGIN -->
        <div id="login-section" class="hidden">
            <h2>Bienvenido</h2>
            <p>Ingresa tus credenciales para continuar</p>
            
            <div class="input-group">
                <input type="text" id="usuario" placeholder="Usuario" autocomplete="off">
            </div>
            <div class="input-group">
                <input type="password" id="password" placeholder="Contraseña">
            </div>
            
            <button onclick="realizarLogin()">Entrar al Sistema</button>
            <div id="login-msg"></div>
        </div>

        <!-- PANTALLA DE ESCANEO / PANEL -->
        <div id="app-section" class="hidden">
            <h2>Control de Asistencia</h2>
            <p>Toma una foto del código QR para registrar tu asistencia (entrada o salida).</p>
            
            <!-- Botón que abre la cámara y al capturar la foto ejecuta el registro directo -->
            <label class="file-btn">
                📸 Escanear QR y Registrar
                <input type="file" accept="image/*" capture="environment" id="qr-input" onchange="procesarFoto(event)">
            </label>

            <button onclick="cerrarSesion()" class="btn-secondary">Cerrar Sesión</button>
            <div id="app-msg"></div>
            <div id="debug-preview" style="margin-top:15px;"></div>
        </div>
    </div>

    <script>
        // PEGA AQUÍ TU URL DE GOOGLE APPS SCRIPT
        const WEB_APP_URL = "https://script.google.com/macros/s/AKfycbwepz20pwNoxMb8FLjWD2ppjSZLRzYhJ1uhLRfBKt2VkZKGNy_VA4YdAdhEv0zp_loq/exec";

        let usuarioActual = "";

        // ===================== VERIFICACIÓN DE UBICACIÓN =====================
        // Ubicación permitida
        const LAT_PERMITIDA = 10.128219;
        const LNG_PERMITIDA = -68.001825;
        const RADIO_PERMITIDO_METROS = 30;

        // Distancia entre dos coordenadas usando la fórmula de Haversine (en metros)
        function calcularDistanciaMetros(lat1, lng1, lat2, lng2) {
            const R = 6371000; // radio de la Tierra en metros
            const rad = (deg) => (deg * Math.PI) / 180;
            const dLat = rad(lat2 - lat1);
            const dLng = rad(lng2 - lng1);
            const a =
                Math.sin(dLat / 2) * Math.sin(dLat / 2) +
                Math.cos(rad(lat1)) * Math.cos(rad(lat2)) *
                Math.sin(dLng / 2) * Math.sin(dLng / 2);
            const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
            return R * c;
        }

        function mostrarSoloSeccion(idVisible) {
            ["location-section", "login-section", "app-section"].forEach((id) => {
                const el = document.getElementById(id);
                if (id === idVisible) {
                    el.classList.remove("hidden");
                } else {
                    el.classList.add("hidden");
                }
            });
        }

        function verificarUbicacion() {
            const locMsg = document.getElementById("location-msg");
            mostrarSoloSeccion("location-section");
            locMsg.innerHTML = '<div class="loading-text">Obteniendo tu ubicación GPS...</div>';

            if (!navigator.geolocation) {
                locMsg.innerHTML = '<div class="alert error">Tu navegador no soporta geolocalización. No es posible verificar el área permitida.</div>';
                return;
            }

            navigator.geolocation.getCurrentPosition(
                (posicion) => {
                    const lat = posicion.coords.latitude;
                    const lng = posicion.coords.longitude;
                    const distancia = calcularDistanciaMetros(lat, lng, LAT_PERMITIDA, LNG_PERMITIDA);

                    if (distancia <= RADIO_PERMITIDO_METROS) {
                        locMsg.innerHTML = '';
                        mostrarSoloSeccion("login-section");
                    } else {
                        locMsg.innerHTML = `<div class="alert error">fuera del area permitida</div>`;
                    }
                },
                (error) => {
                    let mensaje = "No se pudo obtener tu ubicación. Activa el GPS y otorga permiso de ubicación para continuar.";
                    if (error.code === error.PERMISSION_DENIED) {
                        mensaje = "Debes permitir el acceso a tu ubicación para poder ingresar al sistema.";
                    }
                    locMsg.innerHTML = `<div class="alert error">${mensaje}</div>`;
                },
                {
                    enableHighAccuracy: true,
                    timeout: 15000,
                    maximumAge: 0
                }
            );
        }

        // Verificar la ubicación apenas carga la página, antes de mostrar el login.
        // (El script está al final del <body>, así que el DOM ya está listo aquí;
        // llamamos la función directamente en lugar de esperar "DOMContentLoaded",
        // que para este punto ya se habría disparado y nunca se ejecutaría).
        verificarUbicacion();
        // ===================== FIN VERIFICACIÓN DE UBICACIÓN =====================

        async function realizarLogin() {
            const user = document.getElementById("usuario").value.trim();
            const pass = document.getElementById("password").value.trim();
            const msgDiv = document.getElementById("login-msg");

            if (!user || !pass) {
                msgDiv.innerHTML = '<div class="alert error">Completa todos los campos</div>';
                return;
            }

            msgDiv.innerHTML = '<div class="loading-text">Verificando credenciales...</div>';

            try {
                let response = await fetch(WEB_APP_URL, {
                    method: "POST",
                    body: JSON.stringify({ action: "login", usuario: user, password: pass })
                });
                let result = await response.json();

                if (result.success) {
                    usuarioActual = user;
                    
                    // Transición suave entre secciones
                    const loginSec = document.getElementById("login-section");
                    const appSec = document.getElementById("app-section");
                    
                    loginSec.style.opacity = "0";
                    setTimeout(() => {
                        loginSec.classList.add("hidden");
                        appSec.classList.remove("hidden");
                        appSec.classList.add("section-animate");
                        msgDiv.innerHTML = "";
                    }, 300);

                } else {
                    msgDiv.innerHTML = `<div class="alert error">${result.message}</div>`;
                }
            } catch (error) {
                msgDiv.innerHTML = '<div class="alert error">Error de conexión con el servidor.</div>';
            }
        }

        // Texto que debe contener el código QR válido para poder fichar
        const CODIGO_QR_ESPERADO = "LAZARUS_REGISTRO";

        // La librería jsQR se intenta cargar desde varias fuentes distintas por si
        // alguna está bloqueada en la red del usuario (empresa, universidad, operador móvil, etc.)
        const FUENTES_JSQR = [
            "https://cdnjs.cloudflare.com/ajax/libs/jsqr/1.4.0/jsQR.js",
            "https://cdn.jsdelivr.net/npm/jsqr@1.4.0/dist/jsQR.js",
            "https://unpkg.com/jsqr@1.4.0/dist/jsQR.js"
        ];

        let promesaJsQRCargado = null;

        function cargarScript(url, milisegundos) {
            return new Promise((resolve, reject) => {
                const script = document.createElement("script");
                const temporizador = setTimeout(() => {
                    script.remove();
                    reject(new Error("timeout"));
                }, milisegundos);
                script.src = url;
                script.onload = () => {
                    clearTimeout(temporizador);
                    resolve();
                };
                script.onerror = () => {
                    clearTimeout(temporizador);
                    script.remove();
                    reject(new Error("error de carga"));
                };
                document.head.appendChild(script);
            });
        }

        // Intenta cada fuente en orden hasta que una cargue jsQR correctamente
        async function asegurarJsQRCargado() {
            if (typeof jsQR !== "undefined") return;
            if (promesaJsQRCargado) return promesaJsQRCargado;

            promesaJsQRCargado = (async () => {
                for (const url of FUENTES_JSQR) {
                    try {
                        await cargarScript(url, 8000);
                        if (typeof jsQR !== "undefined") return;
                    } catch (err) {
                        // Intentar con la siguiente fuente
                    }
                }
                throw new Error("No se pudo cargar el lector de QR desde ninguna fuente. Revisa tu conexión a internet e intenta de nuevo.");
            })();

            return promesaJsQRCargado;
        }

        // Empieza a intentar cargarlo desde que arranca la página, para tenerlo listo antes de tomar la foto
        asegurarJsQRCargado().catch(() => {});

        // Carga la imagen tomada por la cámara en un canvas y usa jsQR para decodificar el QR.
        // onDebugImagen(dataUrl, ancho, alto) permite mostrar al usuario lo que realmente se analizó.
        async function decodificarQRDesdeArchivo(file, onDebugImagen) {
            // Nos aseguramos de que la librería esté disponible, probando varias fuentes si hace falta
            await asegurarJsQRCargado();

            return new Promise((resolve, reject) => {
                const reader = new FileReader();
                reader.onload = function (e) {
                    const img = new Image();
                    img.onload = function () {
                        try {
                            // Probamos varios tamaños: una foto enorme sin reducir puede tardar
                            // demasiado, pero reducirla de más puede borrar un QR chico en la escena
                            const tamañosAProbar = [1600, 1100, 750, 500];
                            let imagenDebugURL = null;
                            let encontrado = null;

                            for (const ladoMaximo of tamañosAProbar) {
                                let ancho = img.width;
                                let alto = img.height;
                                if (Math.max(ancho, alto) > ladoMaximo) {
                                    const escala = ladoMaximo / Math.max(ancho, alto);
                                    ancho = Math.round(ancho * escala);
                                    alto = Math.round(alto * escala);
                                }

                                const canvas = document.createElement("canvas");
                                canvas.width = ancho;
                                canvas.height = alto;
                                const ctx = canvas.getContext("2d", { willReadFrequently: true });
                                ctx.drawImage(img, 0, 0, ancho, alto);

                                if (!imagenDebugURL) {
                                    imagenDebugURL = canvas.toDataURL("image/jpeg", 0.7);
                                }

                                const imageData = ctx.getImageData(0, 0, ancho, alto);
                                const codigo = jsQR(imageData.data, imageData.width, imageData.height, {
                                    inversionAttempts: "attemptBoth"
                                });

                                if (codigo && codigo.data) {
                                    encontrado = codigo.data.trim();
                                    break;
                                }

                                // Si la foto original ya era más chica que este tamaño, no repetir
                                if (Math.max(img.width, img.height) <= ladoMaximo) break;
                            }

                            if (onDebugImagen && imagenDebugURL) {
                                onDebugImagen(imagenDebugURL, img.width, img.height);
                            }

                            if (encontrado) {
                                resolve(encontrado);
                            } else {
                                reject(new Error("No se detectó ningún código QR en la foto. Mira la imagen de abajo: si se ve borrosa, muy chica o con reflejos, acércate más y repite con buena luz."));
                            }
                        } catch (err) {
                            reject(new Error("Ocurrió un error al procesar la imagen. Intenta con otra foto."));
                        }
                    };
                    img.onerror = () => reject(new Error("No se pudo procesar la imagen capturada."));
                    img.src = e.target.result;
                };
                reader.onerror = () => reject(new Error("No se pudo leer la foto tomada."));
                reader.readAsDataURL(file);
            });
        }

        // Evita que el escaneo se quede "colgado" indefinidamente si algo no responde
        function conTiempoLimite(promesa, milisegundos, mensajeError) {
            return Promise.race([
                promesa,
                new Promise((_, reject) => setTimeout(() => reject(new Error(mensajeError)), milisegundos))
            ]);
        }

        async function procesarFoto(event) {
            const file = event.target.files[0];
            if (!file) return;

            const msgDiv = document.getElementById("app-msg");
            const debugDiv = document.getElementById("debug-preview");
            debugDiv.innerHTML = "";
            msgDiv.innerHTML = '<div class="loading-text">Escaneando código QR...</div>';

            // 1) Decodificar el QR de la foto (con límite de tiempo de 15 segundos)
            let textoQR;
            try {
                textoQR = await conTiempoLimite(
                    decodificarQRDesdeArchivo(file, (dataUrl, ancho, alto) => {
                        debugDiv.innerHTML = `
                            <p style="font-size:12px;color:var(--text-muted);margin-bottom:6px;">
                                Imagen analizada (original: ${ancho}×${alto}px):
                            </p>
                            <img src="${dataUrl}" style="max-width:100%;border-radius:8px;border:1px solid rgba(148,163,184,0.3);">
                        `;
                    }),
                    15000,
                    "El escaneo tardó demasiado. Intenta de nuevo con mejor luz y enfoque."
                );
            } catch (error) {
                msgDiv.innerHTML = `<div class="alert error">${error.message}</div>`;
                event.target.value = "";
                return;
            }

            // 2) Validar que el QR escaneado sea el autorizado
            if (textoQR.toUpperCase() !== CODIGO_QR_ESPERADO) {
                msgDiv.innerHTML = '<div class="alert error">Código QR no válido. Escanea el QR autorizado para registrar tu asistencia.</div>';
                event.target.value = "";
                return;
            }

            // 3) QR válido: registrar la hora en Google Sheets
            msgDiv.innerHTML = '<div class="loading-text">Registrando en Google Sheets...</div>';

            try {
                let response = await fetch(WEB_APP_URL, {
                    method: "POST",
                    body: JSON.stringify({ action: "fichar", usuario: usuarioActual })
                });
                let result = await response.json();

                if (result.success) {
                    msgDiv.innerHTML = `<div class="alert success">¡${result.tipo} registrada con éxito!<br>Fecha: ${result.fecha} | Hora: ${result.hora}</div>`;
                } else {
                    msgDiv.innerHTML = `<div class="alert error">${result.message}</div>`;
                }
            } catch (error) {
                msgDiv.innerHTML = '<div class="alert error">Error al registrar en el sistema.</div>';
            }

            // Limpiar input para permitir tomar otra foto si se desea
            event.target.value = "";
        }

        function cerrarSesion() {
            usuarioActual = "";
            document.getElementById("usuario").value = "";
            document.getElementById("password").value = "";
            document.getElementById("app-msg").innerHTML = "";
            document.getElementById("login-msg").innerHTML = "";
            
            const appSec = document.getElementById("app-section");
            const loginSec = document.getElementById("login-section");

            appSec.style.opacity = "0";
            setTimeout(() => {
                appSec.classList.add("hidden");
                loginSec.classList.remove("hidden");
                loginSec.style.opacity = "1";
            }, 300);
        }
    </script>
</body>
</html>
