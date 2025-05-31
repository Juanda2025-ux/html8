<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>UCV Dashboard Académico</title>
<style>
  * {
    box-sizing: border-box;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    background-color: #adcae7;
    margin: 0;
    padding: 20px;
    display: flex;
  }
  .sideber {
    width: 250px;
    background-color: #2c3e50;
    color: white;
    height: 100vh;
    padding: 20px;
    position: fixed;
  }
  .sideber h2 {
    text-align: center;
    margin-bottom: 20px;
    color: #f4f4f4;
  }
  .sideber ul {
    list-style-type: none;
    padding: 0;
  }
  .sideber ul li {
    margin: 15px 0;
  }
  .sideber ul li a {
    color: white;
    text-decoration: none;
    display: block;
    padding: 10px;
    border-radius: 5px;
    transition: background-color 0.3s ease;
  }
  .sideber ul li a:hover,
  .sideber ul li a.active {
    background-color: #ff0000;
    cursor: pointer;
    color: white;
    transform: scale(1.05);
  }
  .main-content {
    margin-left: 270px;
    padding: 20px;
    width: calc(100% - 270px);
  }
  .tab-content {
    display: none;
  }
  .tab-content.active {
    display: block;
  }
  h1 {
    text-align: center;
    color: #1475d6;
  }
  h2 {
    color: #2c3e50;
    text-align: center;
  }
  h3 {
    text-align: center;
    color: #2c3e50;
  }
  .dashboard {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    margin-top: 30px;
  }
  .card {
    background-color: rgb(255, 255, 255);
    border-radius: 10px;
    padding: 20px;
    box-shadow: 0 4px 8px #2c3e50;
    text-align: center;
    cursor: default;
  }
   .card:hover {
    transform: scale(1.05);
  }
  .card h2 {
    margin: 10px 0;
    color: #2c3e50;
  }
  .card p {
    font-size: 18px;
    color: #2c3e50;
  }
  .dashboard1 {
    max-width: 900px;
    margin: 30px auto;
    background-color: #fff;
    padding: 25px;
    border-radius: 10px;
    box-shadow: 0 0 12px rgba(0,0,0,0.1);
  }
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 25px;
  }
  th, td {
    padding: 14px;
    text-align: left;
    border-bottom: 1px solid #ddd;
  }
  th {
    background-color: #34495e;
    color: white;
  }
  tr:hover {
    background-color: #ff0000;
    cursor: pointer;
    color: white;
  }
  #Reportes .card {
    cursor: pointer;
  }
  #Reportes .card h2 {
    margin: 10px;
    color: rgb(0, 140, 255);
  }
  #Reportes .card p {
    font-size: 18px;
    color: rgb(0, 0, 0);
  }
  #Reportes .card img {
    margin-bottom: 10px;
  }
  #Galería {
    background-color: #f5f5f5;
    padding: 20px;
    border-radius: 10px;
  }
  #Galería h2 {
    margin-bottom: 30px;
    color: #333;
  }
  .container {
    max-width: 1200px;
    margin: 0 auto;
  }
  .gallery {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    justify-items: center;
  }
  .gallery a {
    display: block;
    max-width: 300px;
    width: 100%;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    transition: transform 0.3s ease;
  }
  .gallery a:hover {
    transform: scale(1.05);
  }
  .gallery img {
    width: 100%;
    height: auto;
    display: block;
  }
  @media (max-width: 768px) {
    .gallery {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  @media (max-width: 500px) {
    .gallery {
      grid-template-columns: 1fr;
    }
  }
  #Contacto {
    background-color: #f4f4f4;
    padding: 40px 20px;
  }
  #Contacto h1 {
    text-align: center;
    margin-bottom: 30px;
  }
  .form-container {
    max-width: 500px;
    margin: 0 auto;
    background-color: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }
  .form-group {
    margin-bottom: 20px;
  }
  .form-group label {
    display: block;
    margin-bottom: 8px;
    font-weight: bold;
  }
  .form-group input,
  .form-group textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 10px;
    box-sizing: border-box;
    font-size: 14px;
    color: #333;
  }
  .form-group textarea {
    resize: vertical;
    min-height: 100px;
  }
  ::placeholder {
    color: #999999;
    font-style: italic;
  }
  .form-group button {
    background-color: #00aaff;
    color: white;
    border: none;
    padding: 12px 20px;
    border-radius: 10px;
    font-size: 16px;
    cursor: pointer;
  }
  .form-group button:hover {
    background-color: #008fcc;
  }
  footer {
    background-color: black;
    color: white;
    text-align: center;
    padding: 15px;
    position: fixed;
    width: 100%;
    bottom: 0;
    left: 0;
  }
  @media (max-width: 600px) {
    body {
      flex-direction: column;
      padding: 0;
    }
    .sideber {
      width: 100%;
      height: auto;
      position: relative;
    }
    .main-content {
      margin-left: 0;
      width: 100%;
      padding: 20px;
    }
    .gallery {
      grid-template-columns: 1fr;
    }
  }
</style>
</head>
<body>
  <div class="sideber">
    <h2>UCV Arte & Diseño Gráfico Empresarial</h2>
    <ul>
      <li><a href="#Inicio" class="tab-link active">Inicio</a></li>
      <li><a href="#Reportes" class="tab-link">Reportes</a></li>
      <li><a href="#Galería" class="tab-link">Galería</a></li>
      <li><a href="#Contacto" class="tab-link">Contacto</a></li>
    </ul>
  </div>
  <div class="main-content">
    <div id="Inicio" class="tab-content active">
      <h1>Dashboard Académico de los alumnos de la carrera de Arte & Diseño Gráfico Empresarial de la UCV</h1>
      <div class="dashboard">
        <div class="card">
          <h2>Estudiantes</h2>
          <h1>1500</h1>
          <h3>Registrados</h3>
        </div>
        <div class="card">
          <h2>Profesores</h2>
          <h1>90</h1>
          <h3>Activos</h3>
        </div>
        <div class="card">
          <h2>Cursos</h2>
          <h1>50</h1>
          <h3>Disponibles</h3>
        </div>
      </div>
      <div class="dashboard1">
        <h2>Cursos de especialización</h2>
        <table>
          <thead>
            <tr>
              <th>Curso</th>
              <th>Profesor</th>
              <th>Créditos</th>
              <th>Horario</th>
            </tr>
          </thead>
          <tbody>
            <tr><td>Diseño Gráfico</td><td>Ing. Carlos Peña</td><td>2</td><td>8:00 - 9:30 am</td></tr>
            <tr><td>Publicidad y Marketing</td><td>Dr. Alberto Ruiz</td><td>3</td><td>9:30 - 11:00 am</td></tr>
            <tr><td>Fotografía</td><td>Arq. Sofía Medina</td><td>2</td><td>11:00 - 12:30 pm</td></tr>
            <tr><td>Diseño Web</td><td>Lic. Ana Valdez</td><td>3</td><td>1:00 - 2:30 pm</td></tr>
            <tr><td>Animación 3D</td><td>Ing. Miguel Torres</td><td>3</td><td>2:30 - 4:00 pm</td></tr>
          </tbody>
        </table>
      </div>
    </div>
    <div id="Reportes" class="tab-content">
      <h1>Reportes Académicos</h1>
      <div class="dashboard">
        <div class="card">
          <img src="Recursos/asistencia.jpg" alt="Asistencias" width="100" height="100" />
          <h2>Asistencias</h2>
          <p>Promedio de asistencia del semestre actual</p>
        </div>
        <div class="card">
          <img src="Recursos/calificaciones.jpg" alt="Calificaciones" width="120" height="120" />
          <h2>Calificaciones</h2>
          <p>Resumen de calificaciones y promedios</p>
        </div>
        <div class="card">
          <img src="Recursos/matricula.jpg" alt="Matrícula" width="100" height="100" />
          <h2>Matrícula</h2>
          <p>Estado de matrícula estudiantil</p>
        </div>
      </div>
    </div>
    <div id="Galería" class="tab-content">
      <h2>Galería Académica</h2>
      <div class="container">
        <div class="gallery">
          <a href="Premios.jpg" data-lightbox="models" data-title="Premios"><img src="Recursos/g1.jpg" alt="Premios"/></a>
          <a href="italia.jpg" data-lightbox="models" data-title="Italia"><img src="Recursos/g5.jpg" alt="Italia"/></a>
          <a href="exitosa.jpg" data-lightbox="models" data-title="Exitosa"><img src="Recursos/g3.jpg" alt="Exitosa"/></a>
          <a href="gastronomia.jpg" data-lightbox="models" data-title="Gastronomía"><img src="Recursos/g4.jpg" alt="Gastronomía"/></a>
          <a href="mexico ucv.jpg" data-lightbox="models" data-title="México UCV"><img src="Recursos/g2.jpg" alt="México UCV"/></a>
          <a href="ucv.jpg" data-lightbox="models" data-title="UCV"><img src="Recursos/g6.jpg" alt="UCV" /></a>
        </div>
      </div>
    </div>
    <div id="Contacto" class="tab-content">
      <h1>Contacto</h1>
      <div class="form-container">
        <form method="get" action="https://www.ucv.edu.pe/">
          <div class="form-group">
            <label for="nombre">Nombre</label>
            <input type="text" id="nombre" name="nombre" placeholder="Tu nombre" required />
          </div>
          <div class="form-group">
            <label for="correo">Correo Electrónico</label>
            <input type="email" id="correo" name="correo" placeholder="tu@email.com" required />
          </div>
          <div class="form-group">
            <label for="mensaje">Mensaje</label>
            <textarea id="mensaje" name="mensaje" placeholder="Escribe tu mensaje" required></textarea>
          </div>
          <div class="form-group">
            <button type="submit">Enviar</button>
          </div>
        </form>
      </div>
    </div>
  </div>
  <footer>
    © 2025* Dashboard Académico de la UCV - Escuela Profesional de Arte & Diseño Gráfico Empresarial. Todos los derechos reservados. <br />
    Integrantes: Alama Chinchay, José Manuel - Alarcón Santillán, Andrea Selenne - Matta Bernaola, Óscar Francisco - Silvera Nuñez, Juan David.
  </footer>
  <script>
    const links = document.querySelectorAll('.tab-link');
    const contents = document.querySelectorAll('.tab-content');
    links.forEach(link => {
      link.addEventListener('click', e => {
        e.preventDefault();
        const target = link.getAttribute('href').substring(1);
        links.forEach(l => l.classList.remove('active'));
        contents.forEach(c => c.classList.remove('active'));
        link.classList.add('active');
        document.getElementById(target).classList.add('active');
      });
    });
  </script>
</body>
</html>
