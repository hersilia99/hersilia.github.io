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
    $destinatario = "hersilia.ec@outlook.com"; // Tu correo
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
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>HERSILIA - Centro Psicológico Integral</title>
  <!-- Fuente personalizada y Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" 
        integrity="sha512-pVn+7Wn6O0Kly2Nw+1FxXb4RxjPdP/vp3+SW7jCkZCEwZt2z9hFJAZ4xGXwxh6+8ZldLqkVXhT++5IuHnF3n0g==" 
        crossorigin="anonymous" referrerpolicy="no-referrer" />
  <style>
    /* =======================
       ESTILOS GLOBALES
    ======================= */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Open Sans', sans-serif;
      background-color: #F6F7FB;
      color: #333;
      line-height: 1.6;
    }
    a {
      text-decoration: none;
      color: inherit;
      transition: color 0.3s ease;
    }
    a:hover {
      color: #0050D0;
    }
    img {
      max-width: 100%;
      display: block;
    }
    .container {
      width: 90%;
      max-width: 1200px;
      margin: auto;
      padding: 20px;
    }
    /* =======================
       HEADER Y NAVBAR
    ======================= */
    header {
      background-color: #fff;
      border-bottom: 3px solid #0025FC;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      padding: 10px 0;
    }
    .header-container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
    }
    .logo {
      display: flex;
      align-items: center;
      gap: 15px;
    }
    .logo img {
      width: 60px;
    }
    .logo h1 {
      font-size: 1.8em;
      color: #0025FC;
      text-transform: uppercase;
    }
    nav {
      display: flex;
      gap: 20px;
      align-items: center;
      font-weight: 600;
    }
    /* =======================
       HERO
    ======================= */
    .hero {
      background-color: #0025FC;
      color: #fff;
      text-align: center;
      padding: 80px 20px;
      position: relative;
      overflow: hidden;
    }
    .hero::after {
      content: "";
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0, 37, 252, 0.4);
      z-index: 1;
    }
    .hero .hero-content {
      position: relative;
      z-index: 2;
      max-width: 800px;
      margin: auto;
      animation: fadeIn 1.5s ease-in-out;
    }
    .hero h1 {
      font-size: 2.5em;
      margin-bottom: 10px;
    }
    .hero p {
      font-size: 1.2em;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    /* =======================
       SECCIONES GENERALES
    ======================= */
    section {
      padding: 60px 20px;
      margin-bottom: 20px;
    }
    section h2 {
      text-align: center;
      font-size: 2em;
      color: #0025FC;
      margin-bottom: 20px;
      position: relative;
      display: inline-block;
    }
    section h2::after {
      content: "";
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      bottom: -5px;
      width: 50%;
      height: 3px;
      background-color: #0025FC;
      border-radius: 2px;
    }
    section p {
      font-size: 1.1em;
      margin-bottom: 15px;
      text-align: justify;
    }
    /* =======================
       SOBRE NOSOTROS
    ======================= */
    #nosotros .content {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      align-items: center;
      justify-content: center;
    }
    #nosotros .content img {
      flex: 1;
      min-width: 300px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
      transition: transform 0.3s ease;
    }
    #nosotros .content img:hover {
      transform: scale(1.03);
    }
    #nosotros .text {
      flex: 1;
      min-width: 300px;
    }
    /* =======================
       MISIÓN, VISIÓN Y VALORES
    ======================= */
    .mvv {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
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
      text-align: center;
    }
    .mvv-item h3 {
      color: #0025FC;
      margin-bottom: 10px;
    }
    /* =======================
       TESTIMONIOS
    ======================= */
    #testimonios .testimonials-container {
      display: flex;
      flex-wrap: wrap;
      gap: 30px;
      justify-content: center;
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
      margin-bottom: 10px;
      text-align: justify;
    }
    .testimonial h4 {
      font-size: 1.1em;
      font-weight: 600;
      color: #0025FC;
      text-align: right;
    }
    /* =======================
       GALERÍA
    ======================= */
    #galeria .gallery-container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 20px;
      margin-top: 20px;
    }
    .gallery-item {
      overflow: hidden;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      transition: transform 0.3s ease;
    }
    .gallery-item:hover {
      transform: scale(1.02);
    }
    /* =======================
       CONTACTO
    ======================= */
    #contacto .contact-wrapper {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      justify-content: center;
      align-items: flex-start;
    }
    .contact-info, .contact-form {
      flex: 1;
      min-width: 300px;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .contact-info ul {
      list-style: none;
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
      gap: 15px;
    }
    .contact-form input,
    .contact-form textarea {
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 1em;
      width: 100%;
    }
    .contact-form button {
      background-color: #0025FC;
      color: #fff;
      border: none;
      padding: 15px;
      font-size: 1.1em;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    .contact-form button:hover {
      background-color: #001bb8;
    }
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
       MAPA EMBEBIDO
    ======================= */
    #mapa {
      width: 100%;
      max-width: 1200px;
      margin: 40px auto;
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
    ======================= */
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
       RESPONSIVIDAD
    ======================= */
    @media (max-width: 768px) {
      .header-container, .contact-wrapper {
        flex-direction: column;
        text-align: center;
      }
      .hero h1 {
        font-size: 2em;
      }
      .hero p {
        font-size: 1em;
      }
    }
  </style>
</head>
<body>
  <!-- HEADER -->
  <header>
    <div class="container header-container">
      <div class="logo">
        <!-- Imagen de logo reemplazada -->
        <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Logo Hersilia Fundación">
        <h1>HERSILIA</h1>
      </div>
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
    <div class="container hero-content">
      <h1>Un legado de amor, un futuro de salud</h1>
      <p>En HERSILIA nos dedicamos a brindar apoyo integral en salud mental, con profesionales comprometidos con tu bienestar y el de tu familia.</p>
    </div>
  </section>

  <!-- SECCIÓN SOBRE NOSOTROS -->
  <section id="nosotros">
    <div class="container">
      <h2>Sobre Nosotros</h2>
      <div class="content">
        <!-- Imagen reemplazada -->
        <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Nuestro Equipo">
        <div class="text">
          <h3>Nuestra Historia</h3>
          <p>
            HERSILIA nace con la visión de transformar vidas a través de la atención psicológica y el acompañamiento emocional. Durante años, hemos desarrollado programas de salud mental dirigidos a niños, adolescentes, adultos y personas de la tercera edad.
          </p>
          <p>
            Nuestro equipo multidisciplinario ofrece terapias individuales, de pareja y familiar, así como talleres y capacitaciones en salud mental.
          </p>
        </div>
      </div>
      <!-- MISIÓN, VISIÓN Y VALORES -->
      <div class="mvv">
        <div class="mvv-item">
          <h3>Misión</h3>
          <p>
            Brindar atención psicológica de calidad, promoviendo la salud mental y el bienestar integral con un enfoque humano y ético.
          </p>
        </div>
        <div class="mvv-item">
          <h3>Visión</h3>
          <p>
            Ser un referente nacional en prevención y promoción de la salud mental, mejorando la calidad de vida de las personas y sus familias.
          </p>
        </div>
        <div class="mvv-item">
          <h3>Valores</h3>
          <p>
            Compasión, Respeto, Honestidad y Excelencia son los pilares que guían nuestro quehacer diario.
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
          <p>"Gracias a HERSILIA, encontré la ayuda que necesitaba para superar mis miedos y recuperar mi confianza."</p>
          <h4>- María, 28 años</h4>
        </div>
        <div class="testimonial">
          <p>"El acompañamiento psicológico mejoró la comunicación en mi familia. ¡Lo recomiendo al 100%!"</p>
          <h4>- Carlos, 45 años</h4>
        </div>
        <div class="testimonial">
          <p>"Excelente equipo de profesionales, siempre dispuestos a escuchar y brindar la mejor orientación."</p>
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
        Descubre algunos momentos destacados en nuestros eventos y talleres.
      </p>
      <div class="gallery-container">
        <!-- Todas las imágenes usan la imagen única -->
        <div class="gallery-item">
          <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 1">
        </div>
        <div class="gallery-item">
          <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 2">
        </div>
        <div class="gallery-item">
          <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 3">
        </div>
        <div class="gallery-item">
          <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 4">
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
          <h3>Información de Contacto</h3>
          <ul>
            <li>
              <strong>Teléfono:</strong>
              <a href="https://wa.me/593981811831" target="_blank">0981811831 (WhatsApp)</a>
            </li>
            <li>
              <strong>Email:</strong>
              <a href="mailto:hersilia.ec@outlook.com">hersilia.ec@outlook.com</a>
            </li>
            <li>
              <strong>Dirección:</strong>
              Hersilia Centro Psicológico Integral
            </li>
            <li>
              <strong>Facebook:</strong>
              <a href="https://www.facebook.com/centropsicologicointegralhersilia" target="_blank">
                Centro Psicológico Integral Hersilia
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
            <input type="text" name="name" placeholder="Nombre completo" required>
            <input type="email" name="email" placeholder="Correo electrónico" required>
            <input type="tel" name="phone" placeholder="Número de teléfono">
            <input type="text" name="subject" placeholder="Asunto">
            <textarea name="message" rows="5" placeholder="Tu mensaje" required></textarea>
            <button type="submit">Enviar Mensaje</button>
            <button type="button" onclick="window.open('https://wa.me/593981811831?text=Hola%20HERSILIA,%20deseo%20información','_blank')">
              Enviar por WhatsApp
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- SECCIÓN MAPA EMBEBIDO -->
  <div id="mapa">
    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3989.7537095953417!2d-78.44977349999999!3d-0.3260724!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x91d5bd00024aabd9%3A0x483eb49bac9ebcba!2sHersilia%20Centro%20Psicol%C3%B3gico%20Integral!5e0!3m2!1ses-419!2sec!4v1743216528010!5m2!1ses-419!2sec" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
  </div>

  <!-- FOOTER -->
  <footer>
    <p>&copy; 2025 Hersilia. Todos los derechos reservados.</p>
    <p>Un legado de amor, un futuro de salud.</p>
  </footer>
</body>
</html>
