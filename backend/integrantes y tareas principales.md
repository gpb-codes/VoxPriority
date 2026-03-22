<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Proyecto — Backend FastAPI</title>
<link href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;600;800;900&family=Nunito:wght@400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0b0b10;
    --surface: #12111c;
    --border: #1e1a2e;
    --accent: #a855f7;
    --accent2: #f472b6;
    --green: #c084fc;
    --text: #e8e4f0;
    --muted: #5a5470;
    --tag-bg: #181426;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Nunito', sans-serif;
    min-height: 100vh;
    padding: 48px 24px 80px;
  }

  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0;
  }

  .wrapper { max-width: 860px; margin: 0 auto; position: relative; z-index: 1; }

  /* ── header ── */
  header {
    border-left: 3px solid var(--accent);
    padding-left: 20px;
    margin-bottom: 56px;
    animation: fadeUp .6s ease both;
  }
  .eyebrow {
    font-size: 11px;
    letter-spacing: .2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 10px;
  }
  h1 {
    font-family: 'Raleway', sans-serif;
    font-size: clamp(2.4rem, 7vw, 4rem);
    font-weight: 900;
    letter-spacing: -.01em;
    line-height: 1.1;
    color: #fff;
    margin-bottom: 16px;
  }
  h1 span { color: var(--accent); }
  .subtitle { font-size: 13px; color: var(--muted); }

  /* ── team ── */
  .team {
    display: flex; gap: 12px; flex-wrap: wrap;
    margin-bottom: 52px;
    animation: fadeUp .6s .1s ease both;
  }
  .member {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 20px;
    display: flex; align-items: center; gap: 12px;
    transition: border-color .2s;
  }
  .member:hover { border-color: var(--accent); }
  .avatar {
    width: 36px; height: 36px; border-radius: 50%;
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
    display: grid; place-items: center;
    font-family: 'Raleway', sans-serif;
    font-weight: 800; font-size: 14px; color: #fff;
    flex-shrink: 0;
  }
  .member-name { font-size: 13px; color: var(--text); }
  .member-role { font-size: 11px; color: var(--muted); margin-top: 2px; }

  /* ── section label ── */
  .section-label {
    font-size: 10px;
    letter-spacing: .18em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 20px;
    display: flex; align-items: center; gap: 10px;
  }
  .section-label::after {
    content: ''; flex: 1;
    height: 1px; background: var(--border);
  }

  /* ── objetivo ── */
  .objetivo {
    background: var(--surface);
    border: 1px solid var(--border);
    border-top: 3px solid var(--accent);
    border-radius: 10px;
    padding: 28px;
    margin-bottom: 40px;
    animation: fadeUp .6s .15s ease both;
  }
  .objetivo p { font-size: 14px; line-height: 1.75; color: var(--text); }
  .objetivo p strong { color: var(--accent); font-weight: 600; }

  /* ── tasks grid ── */
  .tasks-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 14px;
    margin-bottom: 40px;
  }
  .task-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 18px;
    transition: transform .2s, border-color .2s;
    animation: fadeUp .5s ease both;
  }
  .task-card:hover { transform: translateY(-3px); border-color: var(--accent); }
  .task-num { font-size: 10px; color: var(--accent); letter-spacing: .1em; margin-bottom: 8px; }
  .task-title {
    font-family: 'Raleway', sans-serif;
    font-size: 13px; font-weight: 700;
    color: #fff; margin-bottom: 6px;
  }
  .task-desc { font-size: 12px; color: var(--muted); line-height: 1.75; }
  .task-desc em { color: #c4a8f0; font-style: normal; }

  /* subtareas dentro de tarjeta */
  .subtask-list {
    margin-top: 8px;
    padding-left: 0;
    list-style: none;
    display: flex; flex-direction: column; gap: 4px;
  }
  .subtask-list li {
    font-size: 11px; color: #7a6e99;
    padding-left: 14px; position: relative; line-height: 1.5;
  }
  .subtask-list li::before {
    content: '›';
    position: absolute; left: 0;
    color: var(--accent);
  }

  /* stagger */
  .task-card:nth-child(1)  { animation-delay:.20s }
  .task-card:nth-child(2)  { animation-delay:.25s }
  .task-card:nth-child(3)  { animation-delay:.30s }
  .task-card:nth-child(4)  { animation-delay:.35s }
  .task-card:nth-child(5)  { animation-delay:.40s }
  .task-card:nth-child(6)  { animation-delay:.45s }
  .task-card:nth-child(7)  { animation-delay:.50s }
  .task-card:nth-child(8)  { animation-delay:.55s }
  .task-card:nth-child(9)  { animation-delay:.60s }
  .task-card:nth-child(10) { animation-delay:.65s }

  /* ── two column ── */
  .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 40px; }
  @media(max-width:600px){ .two-col { grid-template-columns: 1fr; } }

  .panel {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
    animation: fadeUp .6s .55s ease both;
  }
  .panel h3 {
    font-family: 'Raleway', sans-serif;
    font-size: 14px; font-weight: 700;
    color: #fff; margin-bottom: 16px;
    display: flex; align-items: center; gap: 8px;
  }
  .panel h3 .dot {
    width: 8px; height: 8px; border-radius: 50%;
    background: var(--green); flex-shrink: 0;
  }
  .panel h3 .dot.pink { background: var(--accent2); }

  .pill-list { display: flex; flex-wrap: wrap; gap: 8px; }
  .pill {
    background: var(--tag-bg);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 5px 10px;
    font-size: 11px; color: var(--text);
    transition: border-color .2s, color .2s;
  }
  .pill:hover { border-color: var(--green); color: var(--green); }
  .pill.pink:hover { border-color: var(--accent2); color: var(--accent2); }

  /* ── dep block ── */
  .dep-block {
    background: linear-gradient(135deg, #12111c 0%, #0e0c18 100%);
    border: 1px solid var(--border);
    border-left: 4px solid var(--accent2);
    border-radius: 8px;
    padding: 22px 24px;
    font-size: 13px; line-height: 1.7; color: var(--muted);
    margin-bottom: 56px;
    animation: fadeUp .6s .65s ease both;
  }
  .dep-block strong { color: var(--accent2); }

  /* ── footer ── */
  footer {
    text-align: center;
    font-size: 11px; color: var(--muted);
    border-top: 1px solid var(--border);
    padding-top: 28px;
    animation: fadeUp .6s .75s ease both;
  }
  footer span { color: var(--accent); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- header -->
  <header>
    <p class="eyebrow">// Fase 2 — Equipo Backend</p>
    <h1>Lógica de Negocio<br/>+ API <span>Robusta.</span></h1>
    <p class="subtitle">Construcción del servidor con FastAPI, autenticación, voz y workers asíncronos.</p>
  </header>

  <!-- team -->
  <p class="section-label">Equipo Backend</p>
  <div class="team">
    <div class="member">
      <div class="avatar">BE</div>
      <div>
        <div class="member-name">Equipo Backend</div>
        <div class="member-role">FastAPI · SQLAlchemy · Pydantic</div>
      </div>
    </div>
  </div>

  <!-- objetivo -->
  <p class="section-label">Objetivo</p>
  <div class="objetivo">
    <p>Desarrollar la <strong>lógica de negocio completa</strong> del sistema y exponer una <strong>API REST robusta</strong> con FastAPI. Incluye gestión de tareas, autenticación con JWT, módulo de comandos de voz y workers asíncronos, todo documentado automáticamente con Swagger.</p>
  </div>

  <!-- tasks -->
  <p class="section-label">Tareas Clave</p>
  <div class="tasks-grid">

    <div class="task-card">
      <div class="task-num">01</div>
      <div class="task-title">Estructura Base con FastAPI</div>
      <div class="task-desc">Scaffolding inicial del proyecto: organización por módulos (routers, services, models, schemas), configuración de entornos y arranque del servidor con <em>Uvicorn</em>.</div>
    </div>

    <div class="task-card">
      <div class="task-num">02</div>
      <div class="task-title">Conexión a Base de Datos</div>
      <div class="task-desc">Integración con <em>SQLAlchemy</em> como ORM. Configuración del engine, sesiones, y pool de conexiones apuntando al esquema definido por el equipo de DB.</div>
    </div>

    <div class="task-card">
      <div class="task-num">03</div>
      <div class="task-title">CRUD de Tareas</div>
      <div class="task-desc">Endpoints completos para la gestión de tareas:</div>
      <ul class="subtask-list">
        <li>POST /tasks — Crear nueva tarea</li>
        <li>GET /tasks — Listar con filtros y paginación</li>
        <li>PATCH /tasks/{id} — Actualizar estado</li>
        <li>DELETE /tasks/{id} — Eliminar tarea</li>
      </ul>
    </div>

    <div class="task-card">
      <div class="task-num">04</div>
      <div class="task-title">Autenticación con JWT</div>
      <div class="task-desc">Sistema de login con tokens <em>JWT</em> (access + refresh). Middleware de autenticación aplicado a rutas protegidas. Gestión de expiración y renovación de tokens.</div>
    </div>

    <div class="task-card">
      <div class="task-num">05</div>
      <div class="task-title">Módulo de Voz</div>
      <div class="task-desc">Integración con servicio de <em>speech-to-text</em> para recibir audio y convertirlo a texto. Parser de comandos que interpreta frases como:</div>
      <ul class="subtask-list">
        <li>"crear tarea [nombre]"</li>
        <li>"eliminar tarea [id]"</li>
        <li>"listar mis tareas"</li>
      </ul>
    </div>

    <div class="task-card">
      <div class="task-num">06</div>
      <div class="task-title">Worker Asíncrono</div>
      <div class="task-desc">Uso de <em>Background Tasks</em> de FastAPI para procesar operaciones pesadas fuera del ciclo de request (ej: procesamiento de audio, envío de notificaciones, logs diferidos).</div>
    </div>

    <div class="task-card">
      <div class="task-num">07</div>
      <div class="task-title">Validación con Pydantic</div>
      <div class="task-desc">Schemas de entrada y salida con <em>Pydantic v2</em>. Validación de tipos, longitudes, formatos y reglas de negocio. Respuestas estandarizadas y mensajes de error claros.</div>
    </div>

    <div class="task-card">
      <div class="task-num">08</div>
      <div class="task-title">Logging y Manejo de Errores</div>
      <div class="task-desc">Sistema centralizado de logs con niveles (INFO, WARNING, ERROR). Handlers globales para excepciones HTTP y errores inesperados. Formato de respuesta de error consistente.</div>
    </div>

    <div class="task-card">
      <div class="task-num">09</div>
      <div class="task-title">Documentación Automática</div>
      <div class="task-desc"><em>Swagger UI</em> generado automáticamente por FastAPI. Todos los endpoints con descripción, ejemplos de request/response y códigos de estado documentados.</div>
    </div>

  </div>

  <!-- entregables + dependencias -->
  <div class="two-col">
    <div class="panel">
      <h3><span class="dot"></span>Entregables</h3>
      <div class="pill-list">
        <span class="pill">API funcional</span>
        <span class="pill">Endpoints documentados</span>
        <span class="pill">Servicio corriendo local</span>
      </div>
    </div>
    <div class="panel">
      <h3><span class="dot pink"></span>Dependencias</h3>
      <div class="pill-list">
        <span class="pill pink">Modelo de datos (DB)</span>
        <span class="pill pink">Requisitos UX del frontend</span>
      </div>
    </div>
  </div>

  <!-- dep note -->
  <div class="dep-block">
    ⚠ <strong>Bloqueo identificado:</strong> El equipo de backend no puede finalizar los endpoints sin el esquema de base de datos definido. Además, los contratos de la API deben alinearse con los requisitos de UX del equipo frontend antes de implementar las respuestas.
  </div>

  <footer>
    Proyecto — Backend FastAPI &nbsp;·&nbsp; Fase <span>02</span> &nbsp;·&nbsp; Equipo Backend
  </footer>

</div>
</body>
</html>