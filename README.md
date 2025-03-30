<?php
// ========================
// PROCESAMIENTO DEL FORMULARIO
// ========================
if ($_SERVER["REQUEST_METHOD"] === "POST") {
    // 1. Recibir y sanitizar los datos del formulario
    $nombre   = htmlspecialchars($_POST["name"] ?? '');
    $correo   = htmlspecialchars($_POST["email"] ?? '');
    $telefono = htmlspecialchars($_POST["phone"] ?? '');
    $asunto   = htmlspecialchars($_POST["subject"] ?? '');
    $mensaje  = htmlspecialchars($_POST["message"] ?? '');

    // 2. Configuración del correo
    $destinatario = "hersilia.ec@outlook.com"; // <--- Tu correo
    $titulo       = "Nuevo mensaje desde la web de Hersilia Fundación";

    // Cuerpo del correo
    $contenido    = "Nombre: $nombre\n"
                  . "Correo: $correo\n"
                  . "Teléfono: $telefono\n"
                  . "Asunto: $asunto\n"
                  . "Mensaje:\n$mensaje";

    // Cabeceras
    $headers      = "From: $correo\r\n"
                  . "Reply-To: $correo\r\n"
                  . "X-Mailer: PHP/" . phpversion();

    // 3. Enviar el correo
    if (mail($destinatario, $titulo, $contenido, $headers)) {
        $mensaje_exito = "¡Mensaje enviado exitosamente!";
    } else {
        $mensaje_exito = "Hubo un error al enviar el mensaje. Inténtalo de nuevo.";
    }
}
?>
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Hersilia Fundación</title>

  <style>
    /* =======================
       ESTILOS GENERALES
    ======================== */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: Arial, sans-serif;
      color: #333;
      line-height: 1.6;
      background-color: #F6F7FB; /* Fondo suave para todo el sitio */
    }
    a {
      text-decoration: none;
      color: inherit;
    }
    ul {
      list-style: none;
      padding-left: 0;
    }
    img {
      max-width: 100%;
      height: auto;
      display: block;
    }
    h1, h2, h3 {
      font-weight: 600;
      margin-bottom: 10px;
    }

    /* =======================
       ALERTA ÉXITO O ERROR
    ======================== */
    .alert {
      padding: 15px;
      margin-bottom: 15px;
      border-radius: 4px;
      font-weight: 600;
      text-align: center;
    }
    .alert-success {
      background-color: #d4edda;
      color: #155724;
    }
    .alert-error {
      background-color: #f8d7da;
      color: #721c24;
    }

    /* =======================
       HEADER & NAVBAR
    ======================== */
    header {
      background-color: #0025FC; /* Color principal */
      color: #fff;
      padding: 20px 0;
      margin-bottom: 40px;
    }
    .header-container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
    }
    .logo {
      display: flex;
      align-items: center;
    }
    .logo img {
      width: 80px;
      margin-right: 15px;
    }
    .logo h1 {
      font-size: 1.8em;
      margin: 0;
    }
    nav {
      display: flex;
      gap: 20px;
    }
    nav a {
      color: #fff;
      font-weight: 500;
      transition: color 0.3s;
    }
    nav a:hover {
      color: #e0e0e0;
    }

    /* =======================
       SECCIÓN HERO
    ======================== */
    .hero {
      position: relative;
      height: 400px;
      background: url('https://drive.google.com/file/d/1-kO9QiaOVwYKcEMB_rMl4h1gWcOn4Z4U/view?usp=sharing')
                  no-repeat center center/cover;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #fff;
      text-align: center;
      margin-bottom: 40px;
    }
    .hero::after {
      content: "";
      position: absolute;
      top: 0; left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 37, 252, 0.4); /* Superposición azul */
      z-index: 1;
    }
    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
    }
    .hero-content h2 {
      font-size: 2.5em;
      margin-bottom: 20px;
    }
    .hero-content p {
      font-size: 1.2em;
    }

    /* =======================
       SECCIONES GENERALES
    ======================== */
    section {
      padding: 40px 20px;
      margin-bottom: 20px;
    }
    .container {
      max-width: 1200px;
      margin: 0 auto;
      background-color: #fff; /* Fondo blanco para secciones */
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      padding: 30px;
    }
    section h2 {
      font-size: 2em;
      margin-bottom: 10px;
      color: #0025FC; /* Título en color principal */
      text-align: center;
    }

    /* =======================
       SOBRE NOSOTROS
    ======================== */
    #nosotros .content {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      align-items: center;
    }
    #nosotros .content img {
      flex: 1;
      min-width: 300px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    }
    #nosotros .text {
      flex: 1;
      min-width: 300px;
    }
    #nosotros .text p {
      font-size: 1.1em;
      text-align: justify;
      margin-bottom: 15px;
    }

    /* =======================
       MISIÓN, VISIÓN, VALORES
    ======================== */
    .mvv {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      gap: 30px;
      margin-top: 30px;
    }
    .mvv-item {
      background: #f2f2f2;
      border-radius: 8px;
      padding: 20px;
      flex: 1;
      min-width: 250px;
      max-width: 350px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .mvv-item h3 {
      margin-bottom: 10px;
      color: #0025FC;
    }
    .mvv-item p {
      text-align: justify;
      font-size: 1em;
    }

    /* =======================
       TESTIMONIOS
    ======================== */
    #testimonios {
      background-color: transparent;
      box-shadow: none;
    }
    .testimonials-container {
      display: flex;
      flex-wrap: wrap;
      gap: 30px;
      justify-content: space-around;
      margin-top: 20px;
    }
    .testimonial {
      background: #fff;
      border-radius: 8px;
      padding: 20px;
      flex: 1;
      min-width: 250px;
      max-width: 350px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      position: relative;
    }
    .testimonial p {
      font-size: 1em;
      text-align: justify;
      margin-bottom: 10px;
    }
    .testimonial h4 {
      font-size: 1.1em;
      font-weight: 600;
      color: #0025FC;
    }

    /* =======================
       GALERÍA
    ======================== */
    #galeria {
      background-color: transparent;
      box-shadow: none;
    }
    #galeria .gallery-container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 20px;
      margin-top: 20px;
    }
    .gallery-item {
      overflow: hidden;
      position: relative;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .gallery-item img {
      transition: transform 0.3s ease;
    }
    .gallery-item:hover img {
      transform: scale(1.05);
    }

    /* =======================
       CONTACTO
    ======================== */
    #contacto {
      background-color: transparent;
      box-shadow: none;
    }
    #contacto .contact-wrapper {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      margin-top: 20px;
    }
    .contact-info, .contact-form {
      flex: 1;
      min-width: 300px;
    }
    .contact-info ul {
      margin-top: 15px;
    }
    .contact-info li {
      margin-bottom: 10px;
      font-size: 1.1em;
    }
    .contact-info a {
      color: #0025FC;
      font-weight: 600;
    }
    .contact-form form {
      display: flex;
      flex-direction: column;
    }
    .contact-form input,
    .contact-form textarea {
      padding: 12px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 1em;
    }
    .contact-form button {
      background-color: #0025FC;
      color: #fff;
      padding: 12px;
      border: none;
      border-radius: 4px;
      font-size: 1.1em;
      cursor: pointer;
      transition: background-color 0.3s ease;
      margin-bottom: 10px; /* Espacio entre botones */
    }
    .contact-form button:hover {
      background-color: #001bb8;
    }

    /* =======================
       MAPA ABAJO
    ======================== */
    #mapa {
      width: 100%;
      max-width: 1200px;
      margin: 0 auto 40px auto;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    #mapa iframe {
      width: 100%;
      height: 400px;
      border: none;
      display: block;
    }

    /* =======================
       FOOTER
    ======================== */
    footer {
      background-color: #0025FC;
      color: #fff;
      text-align: center;
      padding: 20px;
    }
    footer p {
      margin: 5px 0;
      font-size: 0.95em;
    }

    /* =======================
       RESPONSIVE
    ======================== */
    @media (max-width: 768px) {
      .mvv {
        flex-direction: column;
        align-items: center;
      }
      .hero {
        height: 300px;
      }
      .hero-content h2 {
        font-size: 2em;
      }
      .container {
        padding: 20px;
      }
    }
  </style>
</head>
<body>

  <!-- HEADER -->
  <header>
    <div class="header-container">
      <!-- LOGO -->
      <div class="logo">
        <!-- Usa tu imagen de Drive -->
        <img src="https://drive.google.com/uc?export=view&id=1-kO9QiaOVwYKcEMB_rMl4h1gWcOn4Z4U" alt="Logo Hersilia Fundación">
        <h1>Hersilia Centro Psicológico Integral</h1>
      </div>
      <!-- NAVBAR -->
      <nav>
        <a href="#inicio">Inicio</a>
        <a href="#nosotros">Nosotros</a>
        <a href="#testimonios">Testimonios</a>
        <a href="#galeria">Galería</a>
        <a href="#contacto">Contacto</a>
      </nav>
    </div>
  </header>

  <!-- SECCIÓN HERO -->
  <section class="hero" id="inicio">
    <div class="hero-content">
      <h2>Un legado de amor, un futuro de salud</h2>
      <p>En Hersilia Fundación, nos dedicamos a brindar apoyo integral en salud mental, con profesionales comprometidos con tu bienestar y el de tu familia.</p>
    </div>
  </section>

  <!-- SECCIÓN SOBRE NOSOTROS -->
  <section id="nosotros">
    <div class="container">
      <h2>Sobre Nosotros</h2>
      <div class="content">
        <img src="https://drive.google.com/uc?export=view&id=1-kO9QiaOVwYKcEMB_rMl4h1gWcOn4Z4U" alt="Nuestro Equipo">
        <div class="text">
          <h3>Nuestra Historia</h3>
          <p>
            Hersilia Fundación nace con la visión de transformar vidas a través de la atención psicológica y el acompañamiento 
            emocional. Durante años, hemos desarrollado programas de salud mental dirigidos a diferentes grupos, como niños, 
            adolescentes, adultos y personas de la tercera edad.
          </p>
          <p>
            Contamos con un equipo multidisciplinario de profesionales con experiencia en terapia individual, de pareja y 
            familiar, así como en talleres de desarrollo personal y capacitación en salud mental.
          </p>
        </div>
      </div>
      <!-- MISIÓN, VISIÓN Y VALORES -->
      <div class="mvv">
        <div class="mvv-item">
          <h3>Misión</h3>
          <p>
            Brindar atención psicológica de calidad, promoviendo la salud mental y el bienestar integral de las personas a 
            través de un enfoque humano, ético y comprometido con la comunidad.
          </p>
        </div>
        <div class="mvv-item">
          <h3>Visión</h3>
          <p>
            Ser un referente a nivel nacional en la prevención, cuidado y promoción de la salud mental, impactando de manera 
            positiva en la calidad de vida de las personas y sus familias.
          </p>
        </div>
        <div class="mvv-item">
          <h3>Valores</h3>
          <p>
            <strong>Compasión, Respeto, Honestidad y Excelencia</strong> son los pilares que guían nuestro quehacer diario, 
            asegurando un servicio centrado en la persona y en su bienestar integral.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- SECCIÓN TESTIMONIOS -->
  <section id="testimonios">
    <div class="container">
      <h2>Testimonios</h2>
      <div class="testimonials-container">
        <div class="testimonial">
          <p>"Gracias a Hersilia Fundación, encontré la ayuda que necesitaba para superar mis miedos y recuperar mi confianza."</p>
          <h4>- María, 28 años</h4>
        </div>
        <div class="testimonial">
          <p>"El acompañamiento psicológico fue fundamental para mejorar la comunicación en mi familia. ¡Lo recomiendo al 100%!"</p>
          <h4>- Carlos, 45 años</h4>
        </div>
        <div class="testimonial">
          <p>"Excelente equipo de profesionales, siempre dispuestos a escuchar y a brindar la mejor orientación."</p>
          <h4>- Andrea, 34 años</h4>
        </div>
      </div>
    </div>
  </section>

  <!-- SECCIÓN GALERÍA -->
  <section id="galeria">
    <div class="container">
      <h2>Galería</h2>
      <p style="text-align:center; margin-bottom: 20px;">
        Descubre algunos momentos que hemos compartido en nuestros talleres, eventos y consultas.
      </p>
      <div class="gallery-container">
        <!-- TODAS las imágenes usando el mismo enlace de Drive -->
        <div class="gallery-item">
          <img src="https://drive.google.com/uc?export=view&id=1-kO9QiaOVwYKcEMB_rMl4h1gWcOn4Z4U" alt="Evento 1">
        </div>
        <div class="gallery-item">
          <img src="https://drive.google.com/uc?export=view&id=1-kO9QiaOVwYKcEMB_rMl4h1gWcOn4Z4U" alt="Evento 2">
        </div>
        <div class="gallery-item">
          <img src="https://drive.google.com/uc?export=view&id=1-kO9QiaOVwYKcEMB_rMl4h1gWcOn4Z4U" alt="Evento 3">
        </div>
        <div class="gallery-item">
          <img src="https://drive.google.com/uc?export=view&id=1-kO9QiaOVwYKcEMB_rMl4h1gWcOn4Z4U" alt="Evento 4">
        </div>
      </div>
    </div>
  </section>

  <!-- SECCIÓN CONTACTO -->
  <section id="contacto">
    <div class="container">
      <h2>Contacto</h2>
      <div class="contact-wrapper">
        <!-- Información de contacto -->
        <div class="contact-info">
          <h3>Información de contacto</h3>
          <ul>
            <li>
              <strong>Teléfono:</strong>
              <a href="https://wa.me/message/ND45PNPD3NSMC1" target="_blank">
                WhatsApp
              </a>
            </li>
            <li>
              <strong>Dirección:</strong>
              <!-- Enlace corto al mapa (no es embed) -->
              <a href="https://maps.app.goo.gl/wLhuDJaFefDF1MyQ7" target="_blank">
                Ver mapa
              </a>
            </li>
            <li>
              <strong>Facebook:</strong>
              <a href="https://www.facebook.com/centropsicologicointegralhersilia" target="_blank">
                Centro Psicologico Integral Hersilia
              </a>
            </li>
            <li>
              <strong>Instagram:</strong>
              <a href="https://www.instagram.com/hersilia.ec" target="_blank">
                @hersilia.ec
              </a>
            </li>
            <li>
              <strong>TikTok:</strong>
              <a href="https://www.tiktok.com/@hersilia.ec" target="_blank">
                @hersilia.ec
              </a>
            </li>
            <li>
              <strong>Sitio web:</strong>
              <a href="http://www.hersilia.ec.com" target="_blank">
                www.hersilia.ec.com
              </a>
            </li>
          </ul>
        </div>

        <!-- Formulario de contacto -->
        <div class="contact-form">
          <h3>Envíanos un mensaje</h3>
          <?php if (isset($mensaje_exito)): ?>
            <div class="alert <?php echo ($mensaje_exito === '¡Mensaje enviado exitosamente!') ? 'alert-success' : 'alert-error'; ?>">
              <?php echo $mensaje_exito; ?>
            </div>
          <?php endif; ?>
          <form action="#contacto" method="POST">
            <input type="text"   name="name"    placeholder="Nombre completo"    required />
            <input type="email"  name="email"   placeholder="Correo electrónico" required />
            <input type="tel"    name="phone"   placeholder="Número de teléfono" />
            <input type="text"   name="subject" placeholder="Asunto" />
            <textarea name="message" rows="5" placeholder="Tu mensaje" required></textarea>
            <!-- Botón para enviar al correo -->
            <button type="submit">Enviar Mensaje</button>
            <!-- Botón para abrir WhatsApp con un mensaje prellenado (cambia el número) -->
            <button type="button"
              onclick="window.open('https://wa.me/593999999999?text=Hola%20Hersilia%2C%20deseo%20información%20por%20favor','_blank')">
              Enviar por WhatsApp
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- SECCIÓN MAPA EMBEBIDO ABAJO (Opcional, si deseas ver el mapa grande) -->
<div id="mapa">
  <!-- Reemplaza este iframe con el tuyo propio si quieres un mapa incrustado distinto -->
  <iframe
    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3989.7537095953417!2d-78.44977349999999!3d-0.3260724!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x91d5bd00024aabd9%3A0x483eb49bac9ebcba!2sHersilia%20Centro%20Psicol%C3%B3gico%20Integral!5e0!3m2!1ses-419!2sec!4v1743216528010!5m2!1ses-419!2sec"
    width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade">
  </iframe>
</div>


  <!-- FOOTER -->
  <footer>
    <p>&copy; 2025 Hersilia. Todos los derechos reservados.</p>
    <p>Un legado de amor, un futuro de salud.</p>
  </footer>

</body>
</html>
