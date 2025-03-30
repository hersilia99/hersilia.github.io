<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>HERSILIA – Centro Psicológico Integral</title>
  <!-- Fuentes y Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600&family=Raleway:wght@400;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" 
        integrity="sha512-V4f/9L8W8b0x9v6Otvw+u1PZ1p9sZyWmKl2B6QeV+75xS4kRZL8T+Tdz2U9DIs2PZ8f8w4G9iYHc+1cF4z/+I3A==" crossorigin="anonymous" referrerpolicy="no-referrer" />
  <style>
    /* RESET Y BASE */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Open Sans', sans-serif;
      background-color: #fff;
      color: #333;
      line-height: 1.6;
      scroll-behavior: smooth;
    }
    a { text-decoration: none; color: inherit; transition: color 0.3s; }
    a:hover { color: #6683ff; }
    img { max-width: 100%; display: block; }
    .container { width: 90%; max-width: 1200px; margin: auto; padding: 20px; }
    
    /* HEADER */
    header {
      position: fixed;
      top: 0; left: 0;
      width: 100%;
      z-index: 1000;
      background: rgba(255,255,255,0.98);
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      transition: padding 0.3s;
      padding: 20px 0;
    }
    header.shrink { padding: 5px 0; }
    .header-inner {
      display: flex;
      flex-direction: column;
      align-items: center;
      transition: all 0.3s;
    }
    /* Logo a ancho completo inicialmente, luego se achica */
    .logo {
      width: 100%;
      text-align: center;
      transition: all 0.3s;
      margin-bottom: 10px;
    }
    .logo img { width: 100%; max-width: 400px; transition: width 0.3s; }
    header.shrink .logo img { width: 200px; }
    /* Menú de Navegación con Dropdown */
    nav {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      font-weight: 600;
      text-transform: uppercase;
      position: relative;
    }
    nav a { padding: 5px 10px; color: #0025FC; border-radius: 4px; }
    nav a:hover { background: #e0eaff; }
    .dropdown { position: relative; }
    .dropdown .dropbtn { cursor: pointer; }
    .dropdown-content {
      display: none;
      position: absolute;
      top: 35px;
      left: 0;
      background: #fff;
      box-shadow: 0 3px 8px rgba(0,0,0,0.15);
      border-radius: 4px;
      z-index: 1001;
      min-width: 180px;
    }
    .dropdown-content a {
      display: block;
      padding: 10px 15px;
      color: #0025FC;
    }
    .dropdown-content a:hover { background: #e0eaff; }
    .dropdown:hover .dropdown-content { display: block; }
    /* Espacio para evitar contenido oculto por el header */
    .spacer { height: 110px; }
    
    /* Botón Volver Arriba */
    #backToTop {
      position: fixed;
      bottom: 20px;
      right: 20px;
      display: none;
      padding: 10px 15px;
      background: #0025FC;
      color: #fff;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      z-index: 1100;
    }
    
    /* HERO */
    .hero {
      position: relative;
      height: 90vh;
      background: url('https://via.placeholder.com/1600x900/000033/ffffff?text=Fondo+Hero') center center/cover no-repeat;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      color: #fff;
    }
    .hero::after {
      content: "";
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0,0,0,0.5);
      z-index: 1;
    }
    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 800px;
      padding: 0 20px;
    }
    /* Contenedor de la frase con fondo distinto */
    .hero-text-bg {
      background: #9499ff; /* Color de fondo distinto */
      padding: 10px 20px;
      display: inline-block;
      border-radius: 4px;
      margin: 20px 0;
    }
    .hero h1 { font-size: 3em; margin-bottom: 15px; }
    .hero p { font-size: 1.4em; }
    
    /* SECCIONES GENERALES */
    section { padding: 80px 20px; }
    section h2 {
      text-align: center;
      font-size: 2.2em;
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
      width: 60%;
      height: 3px;
      background: #0025FC;
      border-radius: 2px;
    }
    section p { font-size: 1.1em; margin-bottom: 20px; text-align: justify; }
    
    /* SOBRE NOSOTROS */
    #nosotros .about-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      align-items: center;
      justify-content: center;
    }
    #nosotros .about-grid img {
      flex: 1;
      min-width: 300px;
      max-width: 500px;
      border-radius: 8px;
      box-shadow: 0 3px 8px rgba(0,0,0,0.15);
      transition: transform 0.3s;
    }
    #nosotros .about-grid img:hover { transform: scale(1.03); }
    #nosotros .about-text { flex: 1; min-width: 300px; max-width: 600px; }
    
    /* MISIÓN Y VISIÓN */
    #mision-vision {
      background: #9499ff; /* Fondo claro para Misión y Visión */
      padding: 60px 20px;
    }
    #mision-vision .mv-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      justify-content: center;
    }
    #mision-vision .mv-item {
      background: #fff;
      flex: 1;
      min-width: 280px;
      max-width: 500px;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 3px 8px rgba(0,0,0,0.1);
      text-align: center;
    }
    #mision-vision .mv-item h3 {
      color: #0025FC;
      margin-bottom: 10px;
      font-size: 1.5em;
    }
    #mision-vision .mv-item p { font-size: 1.1em; }
    
    /* SERVICIOS */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
    }
    .service {
      background: #fff;
      border-radius: 8px;
      padding: 20px;
      text-align: center;
      box-shadow: 0 3px 8px rgba(0,0,0,0.1);
      transition: transform 0.3s;
    }
    .service:hover { transform: scale(1.02); }
    .service i { font-size: 2.5em; color: #0045a0; margin-bottom: 15px; }
    .service h3 { font-size: 1.3em; color: #0025FC; margin-bottom: 10px; }
    
    /* TESTIMONIOS */
    .testimonials-container {
      display: flex;
      flex-wrap: wrap;
      gap: 30px;
      justify-content: center;
    }
    .testimonial {
      background: #fff;
      border-radius: 8px;
      padding: 20px;
      flex: 1;
      min-width: 250px;
      max-width: 350px;
      box-shadow: 0 3px 8px rgba(0,0,0,0.1);
      text-align: center;
    }
    .testimonial img {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      object-fit: cover;
      margin: 0 auto 15px;
    }
    .testimonial p { font-size: 1em; margin-bottom: 10px; }
    .testimonial h4 { font-size: 1.1em; font-weight: 600; color: #0025FC; }
    
    /* GALERÍA */
    .gallery-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }
    .gallery-item {
      overflow: hidden;
      border-radius: 8px;
      box-shadow: 0 3px 8px rgba(0,0,0,0.1);
      transition: transform 0.3s;
    }
    .gallery-item:hover { transform: scale(1.02); }
    
    /* CONTACTO */
    .contact-wrapper {
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
      box-shadow: 0 3px 8px rgba(0,0,0,0.1);
    }
    .contact-info ul { list-style: none; margin-top: 15px; }
    .contact-info li { margin-bottom: 10px; font-size: 1.1em; }
    .contact-info a { color: #0025FC; font-weight: 600; }
    .contact-form form { display: flex; flex-direction: column; gap: 15px; }
    .contact-form input,
    .contact-form textarea {
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 1em;
      width: 100%;
    }
    .contact-form button {
      background: #0025FC;
      color: #fff;
      border: none;
      padding: 15px;
      font-size: 1.1em;
      border-radius: 4px;
      cursor: pointer;
      transition: background 0.3s;
    }
    .contact-form button:hover { background: #001bb8; }
    
    /* MAPA FULL WIDTH */
    .mapa {
      width: 100%;
      margin: 40px 0;
    }
    .mapa iframe {
      width: 100%;
      height: 450px;
      border: 0;
    }
    
    /* FOOTER CON REDES SOCIALES */
    footer {
      background: #9499ff;
      padding: 20px;
      text-align: center;
      font-size: 0.9em;
      color: #555;
    }
    .socials {
      text-align: center;
      margin: 20px 0;
    }
    .socials a {
      margin: 0 10px;
      font-size: 1.3em;
      font-weight: 600;
      color: #0025FC;
      display: inline-flex;
      align-items: center;
      gap: 5px;
    }
    .socials a:hover { color: #9499ff; }
    
    /* RESPONSIVO */
    @media (max-width: 768px) {
      .about-grid { flex-direction: column; text-align: center; }
      nav { flex-direction: column; gap: 10px; }
      .dropdown-content { position: static; box-shadow: none; }
    }
  </style>
  <script>
    // Agregar clase "shrink" al header y mostrar botón volver arriba
    window.addEventListener("scroll", function() {
      const header = document.querySelector("header");
      if (window.scrollY > 100) {
        header.classList.add("shrink");
      } else {
        header.classList.remove("shrink");
      }
      const backBtn = document.getElementById("backToTop");
      backBtn.style.display = window.scrollY > 300 ? "block" : "none";
    });
    function scrollToTop() {
      window.scrollTo({ top: 0, behavior: "smooth" });
    }
  </script>
</head>
<body>

  <!-- HEADER -->
  <header id="inicio">
    <div class="container header-inner">
      <div class="logo">
        <!-- Logo a ancho completo inicialmente -->
        <a href="#inicio"><img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Logo Hersilia"></a>
      </div>
      <nav>
        <a href="#nosotros">Nosotros</a>
        <div class="dropdown">
          <a href="#servicios" class="dropbtn">Servicios</a>
          <div class="dropdown-content">
            <a href="#atencion">Atención Integral</a>
            <a href="#talleres">Talleres</a>
            <a href="#capacitaciones">Capacitaciones</a>
            <a href="#cursos">Cursos</a>
          </div>
        </div>
        <a href="#mision-vision">Misión y Visión</a>
        <a href="#testimonios">Testimonios</a>
        <a href="#galeria">Galería</a>
        <a href="#contacto">Contacto</a>
      </nav>
    </div>
  </header>
  <div class="spacer"></div>

  <!-- BOTÓN VOLVER ARRIBA -->
  <button id="backToTop" onclick="scrollToTop()">↑ Arriba</button>

  <!-- ICONO FLOTANTE DE WHATSAPP -->
  <a href="https://wa.me/593981811831?text=Hola%20Hersilia,%20deseo%20informaci%C3%B3n" target="_blank" 
     style="position: fixed; bottom: 20px; left: 20px; background: #25D366; color: #fff; padding: 15px; border-radius: 50%; z-index: 1100;">
    <i class="fab fa-whatsapp" style="font-size: 1.5em;"></i>
  </a>

  <!-- SECCIÓN HERO -->
  <section class="hero">
    <div class="container hero-content">
      <h1>Un legado de amor, un futuro de salud</h1>
      <!-- Imagen complementaria (puede ser la cara del centro) -->
      <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Imagen destacada" style="margin:20px auto; max-width:300px;">
      <p>En HERSILIA brindamos apoyo integral en salud mental con profesionales comprometidos.</p>
    </div>
  </section>

  <!-- SOBRE NOSOTROS -->
  <section id="nosotros">
    <div class="container">
      <h2>Sobre Nosotros</h2>
      <p><strong>Nuestra Historia:</strong> Hersilia nace con la visión de transformar vidas mediante la atención psicológica y el acompañamiento emocional. Desarrollamos programas para niños, adolescentes, adultos y la tercera edad.</p>
      <p><strong>Nuestro Equipo:</strong> Profesionales expertos en terapia individual, de pareja y familiar, además de talleres de desarrollo personal.</p>
    </div>
  </section>

  <!-- MISIÓN Y VISIÓN -->
  <section id="mision-vision">
    <div class="container">
      <h2>Misión y Visión</h2>
      <div class="mv-grid">
        <div class="mv-item">
          <h3>Misión</h3>
          <p>Brindar atención psicológica de calidad, promoviendo el bienestar integral con un enfoque humano y ético.</p>
        </div>
        <div class="mv-item">
          <h3>Visión</h3>
          <p>Ser un referente nacional en salud mental, impactando positivamente la calidad de vida de las personas y sus familias.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- SERVICIOS -->
  <section id="servicios">
    <div class="container">
      <h2>Servicios y Beneficios</h2>
      <div class="services-grid">
        <div class="service" id="atencion">
          <i class="fa fa-heartbeat"></i>
          <h3>Atención Integral</h3>
          <p>Soluciones personalizadas para cada necesidad.</p>
        </div>
        <div class="service" id="talleres">
          <i class="fa fa-users"></i>
          <h3>Talleres</h3>
          <p>Espacios para desarrollar habilidades y fortalecer vínculos.</p>
        </div>
        <div class="service" id="capacitaciones">
          <i class="fa fa-chalkboard-teacher"></i>
          <h3>Capacitaciones</h3>
          <p>Formación continua para el crecimiento personal y profesional.</p>
        </div>
        <div class="service" id="cursos">
          <i class="fa fa-graduation-cap"></i>
          <h3>Cursos</h3>
          <p>Programas educativos para ampliar conocimientos y habilidades.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- TESTIMONIOS -->
  <section id="testimonios">
    <div class="container">
      <h2>Testimonios</h2>
      <blockquote>
        "Gracias a HERSILIA encontré la ayuda que necesitaba para superar mis miedos y recuperar mi confianza."
        <strong>- María, 28 años</strong>
      </blockquote>
      <blockquote>
        "El acompañamiento psicológico mejoró la comunicación en mi familia. ¡Lo recomiendo al 100%!"
        <strong>- Carlos, 45 años</strong>
      </blockquote>
      <blockquote>
        "Excelente equipo de profesionales, siempre dispuestos a escuchar y brindar la mejor orientación."
        <strong>- Andrea, 34 años</strong>
      </blockquote>
    </div>
  </section>

  <!-- GALERÍA -->
  <section id="galeria">
    <div class="container">
      <h2>Galería</h2>
      <div class="gallery-container">
        <!-- Reutilizamos la misma imagen de ejemplo -->
        <div class="gallery-item"><img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 1"></div>
        <div class="gallery-item"><img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 2"></div>
        <div class="gallery-item"><img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 3"></div>
        <div class="gallery-item"><img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Evento 4"></div>
      </div>
    </div>
  </section>

  <!-- CONTACTO -->
  <section id="contacto">
    <div class="container">
      <h2>Contacto</h2>
      <div class="contact-wrapper">
        <div class="contact-info">
          <h3>Información de Contacto</h3>
          <p><strong>Teléfono:</strong> <a href="https://wa.me/593981811831" target="_blank">(098) 181-1831 (WhatsApp)</a></p>
          <p><strong>Email:</strong> <a href="mailto:hersilia.ec@outlook.com">hersilia.ec@outlook.com</a></p>
          <p><strong>Dirección:</strong> <a href="https://goo.gl/maps/wLhuDJaFefDF1MyQ7" target="_blank">Ver en Google Maps</a></p>
        </div>
        <div class="contact-form">
          <h3>Envíanos un mensaje</h3>
          <form action="mailto:hersilia.ec@outlook.com" method="post" enctype="text/plain">
            <input type="text" name="nombre" placeholder="Nombre completo" required>
            <input type="email" name="correo" placeholder="Correo electrónico" required>
            <input type="tel" name="telefono" placeholder="Número de teléfono">
            <input type="text" name="asunto" placeholder="Asunto" required>
            <textarea name="mensaje" rows="5" placeholder="Tu mensaje" required></textarea>
            <button type="submit">Enviar Mensaje</button>
            <button type="button" onclick="window.open('https://wa.me/593981811831?text=Hola%20Hersilia,%20deseo%20informaci%C3%B3n','_blank')">Enviar por WhatsApp</button>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- MAPA FULL WIDTH -->
  <div class="mapa">
    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3989.7537095954717!2d-78.45234842503537!3d-0.32607239967071955!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x91d5bd00024aabd9%3A0x483eb49bac9ebcba!2sHersilia%20Centro%20Psicol%C3%B3gico%20Integral!5e0!3m2!1ses-419!2sec!4v1743294599307!5m2!1ses-419!2sec" 
      allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
  </div>

  <!-- FOOTER CON REDES SOCIALES -->
  <footer>
    <div class="container">
      <div class="socials">
        <!-- Se incluyen pequeños íconos para cada red, incluyendo WhatsApp -->
        <a href="https://www.facebook.com/people/Centro-Psicol%C3%B3gico-Integral-Hersilia/100064794828756/" target="_blank" aria-label="Facebook">
          <i class="fab fa-facebook"></i>
        </a>
        <a href="https://www.instagram.com/hersilia.ec/" target="_blank" aria-label="Instagram">
          <i class="fab fa-instagram"></i>
        </a>
        <a href="https://www.tiktok.com/@hersilia.ec" target="_blank" aria-label="TikTok">
          <i class="fab fa-tiktok"></i>
        </a>
        <a href="https://wa.me/593981811831?text=Hola%20Hersilia,%20deseo%20informaci%C3%B3n" target="_blank" aria-label="WhatsApp">
          <i class="fab fa-whatsapp"></i>
        </a>
      </div>
      <p>&copy; 2025 Hersilia - Centro Psicológico Integral</p>
      <p>Un legado de amor, un futuro de salud.</p>
    </div>
  </footer>

</body>
</html>
