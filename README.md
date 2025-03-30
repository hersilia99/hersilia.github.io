<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>HERSILIA – Centro Psicológico Integral</title>
  <!-- Fuente y animaciones -->
  <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600&family=Raleway:wght@400;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"/>
  <style>
    /* RESET Y ESTILOS GLOBALES */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Open Sans', sans-serif;
      background-color: #F6F7FB;
      color: #333;
      line-height: 1.6;
      scroll-behavior: smooth;
    }
    a { text-decoration: none; color: inherit; transition: color 0.3s ease; }
    a:hover { color: #0050D0; }
    img { max-width: 100%; display: block; }
    .container { width: 90%; max-width: 1200px; margin: auto; padding: 20px; }
    
    /* HEADER CON LOGO CENTRADO */
    header {
      position: sticky;
      top: 0;
      z-index: 1000;
      background: rgba(255,255,255,0.98);
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      padding: 15px 0;
    }
    .header-inner {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .logo {
      margin-bottom: 10px;
    }
    .logo img { width: 100px; }
    nav {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      font-weight: 600;
      text-transform: uppercase;
    }
    nav a {
      color: #0025FC;
      padding: 5px 10px;
      border-radius: 4px;
    }
    nav a:hover { background-color: #e0eaff; }
    
    /* SECCIÓN HERO */
    .hero {
      position: relative;
      background: url('https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg') no-repeat center center/cover;
      color: #fff;
      text-align: center;
      padding: 120px 20px 80px;
    }
    .hero::after {
      content: "";
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0, 37, 252, 0.4);
      z-index: 1;
    }
    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 800px;
      margin: auto;
      animation: fadeIn 1.5s ease-in-out;
    }
    .hero h1 { font-size: 2.8em; margin-bottom: 15px; }
    .hero p { font-size: 1.3em; }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    /* SECCIONES GENERALES */
    section { padding: 80px 20px; }
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
      width: 60%;
      height: 3px;
      background-color: #0025FC;
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
      margin-top: 30px;
    }
    #nosotros .about-grid img {
      flex: 1;
      min-width: 280px;
      max-width: 400px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
      transition: transform 0.3s ease;
    }
    #nosotros .about-grid img:hover { transform: scale(1.03); }
    #nosotros .about-text { flex: 1; min-width: 280px; max-width: 600px; }
    
    /* SERVICIOS / CAMPOS DE BENEFICIOS */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
      margin-top: 30px;
    }
    .service {
      background: #fff;
      border-radius: 8px;
      padding: 20px;
      text-align: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      transition: transform 0.3s ease;
    }
    .service:hover { transform: scale(1.02); }
    .service i { font-size: 2em; color: #0045a0; margin-bottom: 15px; }
    .service h3 { font-size: 1.3em; color: #0025FC; margin-bottom: 10px; }
    
    /* TESTIMONIOS – Utilizamos imagen circular para cada testimonio */
    .testimonials-container {
      display: flex;
      flex-wrap: wrap;
      gap: 30px;
      justify-content: center;
      margin-top: 30px;
    }
    .testimonial {
      background: #fff;
      border-radius: 8px;
      padding: 20px;
      flex: 1;
      min-width: 250px;
      max-width: 350px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
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
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
      margin-top: 30px;
    }
    .gallery-item {
      overflow: hidden;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      transition: transform 0.3s ease;
    }
    .gallery-item:hover { transform: scale(1.02); }
    
    /* CONTACTO */
    .contact-wrapper {
      display: flex;
      flex-wrap: wrap;
      gap: 40px;
      justify-content: center;
      align-items: flex-start;
      margin-top: 30px;
    }
    .contact-info, .contact-form {
      flex: 1;
      min-width: 300px;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
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
      background-color: #0025FC;
      color: #fff;
      border: none;
      padding: 15px;
      font-size: 1.1em;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    .contact-form button:hover { background-color: #001bb8; }
    
    /* FOOTER */
    footer {
      background-color: #0025FC;
      color: #fff;
      text-align: center;
      padding: 30px 20px;
      margin-top: 40px;
    }
    footer p { margin: 5px 0; font-size: 0.95em; }
    
    /* RESPONSIVIDAD */
    @media (max-width: 768px) {
      .about-grid { flex-direction: column; text-align: center; }
      nav { flex-direction: column; gap: 10px; }
    }
  </style>
  <script>
    // Opcional: botón "volver arriba"
    window.addEventListener("scroll", function() {
      const btn = document.getElementById("backToTop");
      if (window.scrollY > 300) {
        btn.style.display = "block";
      } else {
        btn.style.display = "none";
      }
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
        <a href="#inicio"><img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Logo Hersilia"></a>
      </div>
      <nav>
        <a href="#nosotros">Nosotros</a>
        <a href="#servicios">Servicios</a>
        <a href="#testimonios">Testimonios</a>
        <a href="#galeria">Galería</a>
        <a href="#contacto">Contacto</a>
      </nav>
    </div>
  </header>

  <!-- BOTÓN VOLVER ARRIBA -->
  <button id="backToTop" onclick="scrollToTop()" style="position:fixed;bottom:20px;right:20px;display:none;padding:10px 15px;background:#0025FC;color:#fff;border:none;border-radius:4px;cursor:pointer;">↑ Arriba</button>

  <!-- SECCIÓN HERO -->
  <section class="hero">
    <div class="container hero-content animate__animated animate__fadeInDown">
      <h1>Un Legado de Amor, un Futuro de Salud</h1>
      <p>Brindamos apoyo integral en salud mental con profesionales comprometidos.</p>
    </div>
  </section>

  <!-- SOBRE NOSOTROS -->
  <section id="nosotros">
    <div class="container">
      <h2>Sobre Nosotros</h2>
      <div class="about-grid">
        <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Equipo Hersilia">
        <div class="about-text">
          <h3>Nuestra Historia</h3>
          <p>
            Hersilia Fundación nace con la visión de transformar vidas mediante atención psicológica y acompañamiento emocional. Nuestro equipo multidisciplinario ofrece terapias individuales, familiares y talleres para potenciar el bienestar.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- SERVICIOS / BENEFICIOS -->
  <section id="servicios">
    <div class="container">
      <h2>Servicios y Beneficios</h2>
      <div class="services-grid">
        <div class="service animate__animated animate__bounceIn">
          <i class="fa fa-heartbeat"></i>
          <h3>Atención Integral</h3>
          <p>Profesionales altamente capacitados ofrecen soluciones personalizadas para cada necesidad.</p>
        </div>
        <div class="service animate__animated animate__bounceIn" style="animation-delay: 0.2s;">
          <i class="fa fa-users"></i>
          <h3>Trabajo Familiar</h3>
          <p>Fortalecemos vínculos afectivos y fomentamos la comunicación en el entorno familiar.</p>
        </div>
        <div class="service animate__animated animate__bounceIn" style="animation-delay: 0.4s;">
          <i class="fa fa-lightbulb-o"></i>
          <h3>Desarrollo Personal</h3>
          <p>Impulsamos el crecimiento y el bienestar emocional a través de estrategias innovadoras.</p>
        </div>
        <div class="service animate__animated animate__bounceIn" style="animation-delay: 0.6s;">
          <i class="fa fa-comments"></i>
          <h3>Consultas Online</h3>
          <p>Asesoría y seguimiento profesional desde la comodidad de tu hogar.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- TESTIMONIOS -->
  <section id="testimonios">
    <div class="container">
      <h2>Testimonios</h2>
      <div class="testimonials-container">
        <div class="testimonial animate__animated animate__fadeInUp">
          <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Testimonio 1">
          <p>"Gracias a Hersilia encontré la ayuda para superar mis miedos."</p>
          <h4>- María, 28 años</h4>
        </div>
        <div class="testimonial animate__animated animate__fadeInUp" style="animation-delay: 0.2s;">
          <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Testimonio 2">
          <p>"El acompañamiento familiar cambió la dinámica en mi hogar."</p>
          <h4>- Carlos, 45 años</h4>
        </div>
        <div class="testimonial animate__animated animate__fadeInUp" style="animation-delay: 0.4s;">
          <img src="https://i.postimg.cc/66YsLK0z/Sin-t-tulo-1.jpg" alt="Testimonio 3">
          <p>"Profesionales atentos y comprometidos. ¡Recomendados!"</p>
          <h4>- Andrea, 34 años</h4>
        </div>
      </div>
    </div>
  </section>

  <!-- GALERÍA -->
  <section id="galeria">
    <div class="container">
      <h2>Galería</h2>
      <div class="gallery-container">
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
        <!-- Información de contacto -->
        <div class="contact-info">
          <h3>Información de Contacto</h3>
          <ul>
            <li><strong>Teléfono:</strong> <a href="https://wa.me/593981811831" target="_blank">(098) 181-1831 (WhatsApp)</a></li>
            <li><strong>Email:</strong> <a href="mailto:hersilia.ec@outlook.com">hersilia.ec@outlook.com</a></li>
            <li><strong>Dirección:</strong> <a href="https://goo.gl/maps/wLhuDJaFefDF1MyQ7" target="_blank">Ver en Google Maps</a></li>
          </ul>
        </div>
        <!-- Formulario de contacto -->
        <div class="contact-form">
          <h3>Envíanos un mensaje</h3>
          <form action="mailto:hersilia.ec@outlook.com" method="post" enctype="text/plain">
            <input type="text" name="nombre" placeholder="Nombre completo" required>
            <input type="email" name="correo" placeholder="Correo electrónico" required>
            <input type="tel" name="telefono" placeholder="Número de teléfono">
            <input type="text" name="asunto" placeholder="Asunto">
            <textarea name="mensaje" rows="5" placeholder="Tu mensaje" required></textarea>
            <button type="submit">Enviar Mensaje</button>
            <button type="button" onclick="window.open('https://wa.me/593981811831?text=Hola%20Hersilia,%20deseo%20informaci%C3%B3n','_blank')">Enviar por WhatsApp</button>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="container">
      <p>&copy; 2025 Hersilia. Todos los derechos reservados.</p>
      <p>Un legado de amor, un futuro de salud.</p>
    </div>
  </footer>

</body>
</html>
