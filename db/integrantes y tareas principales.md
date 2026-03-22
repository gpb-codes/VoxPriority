<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Proyecto — Base de Datos</title>
<link href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;600;800;900&family=Nunito:wght@400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0b0c10;
    --surface: #13151c;
    --border: #1f2230;
    --accent: #00e5ff;
    --accent2: #ff4d6d;
    --green: #00ffaa;
    --text: #e8eaf0;
    --muted: #5a5f7a;
    --tag-bg: #1a1d2e;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Nunito', sans-serif;
    min-height: 100vh;
    padding: 48px 24px 80px;
  }

  /* noise overlay */
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
  .subtitle {
    font-size: 13px;
    color: var(--muted);
  }

  /* ── team card ── */
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
    font-weight: 800; font-size: 14px; color: #000;
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
    padding: 28px 28px;
    margin-bottom: 40px;
    animation: fadeUp .6s .15s ease both;
  }
  .objetivo p {
    font-size: 14px; line-height: 1.75; color: var(--text);
  }
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
    padding: 18px 18px;
    transition: transform .2s, border-color .2s;
    animation: fadeUp .5s ease both;
  }
  .task-card:hover { transform: translateY(-3px); border-color: var(--accent); }
  .task-num {
    font-size: 10px; color: var(--accent); letter-spacing: .1em;
    margin-bottom: 8px;
  }
  .task-title {
    font-family: 'Raleway', sans-serif;
    font-size: 13px; font-weight: 700;
    color: #fff; margin-bottom: 6px;
  }
  .task-desc { font-size: 12px; color: var(--muted); line-height: 1.75; }
  .task-desc em { color: #a0a8c8; font-style: normal; }

  /* stagger */
  .task-card:nth-child(1) { animation-delay:.2s }
  .task-card:nth-child(2) { animation-delay:.25s }
  .task-card:nth-child(3) { animation-delay:.3s }
  .task-card:nth-child(4) { animation-delay:.35s }
  .task-card:nth-child(5) { animation-delay:.4s }
  .task-card:nth-child(6) { animation-delay:.45s }
  .task-card:nth-child(7) { animation-delay:.5s }
  .task-card:nth-child(8) { animation-delay:.55s }
  .task-card:nth-child(9) { animation-delay:.6s }

  /* ── two column ── */
  .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 40px; }
  @media(max-width:600px){ .two-col { grid-template-columns: 1fr; } }

  .panel {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
    animation: fadeUp .6s .45s ease both;
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
  .panel h3 .dot.red { background: var(--accent2); }

  .pill-list { display: flex; flex-wrap: wrap; gap: 8px; }
  .pill {
    background: var(--tag-bg);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 5px 10px;
    font-size: 11px;
    color: var(--text);
    transition: border-color .2s, color .2s;
  }
  .pill:hover { border-color: var(--green); color: var(--green); }
  .pill.red:hover { border-color: var(--accent2); color: var(--accent2); }

  /* ── dependency ── */
  .dep-block {
    background: linear-gradient(135deg, #13151c 0%, #0f1118 100%);
    border: 1px solid var(--border);
    border-left: 4px solid var(--accent2);
    border-radius: 8px;
    padding: 22px 24px;
    font-size: 13px; line-height: 1.7; color: var(--muted);
    margin-bottom: 56px;
    animation: fadeUp .6s .55s ease both;
  }
  .dep-block strong { color: var(--accent2); }

  /* ── footer ── */
  footer {
    text-align: center;
    font-size: 11px; color: var(--muted);
    border-top: 1px solid var(--border);
    padding-top: 28px;
    animation: fadeUp .6s .65s ease both;
  }
  footer span { color: var(--accent); }

  /* ── keyframes ── */
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
    <p class="eyebrow">// Fase 1 — Base de Datos</p>
    <h1>Modelo Sólido,<br/><span>Consistente</span> y Escalable.</h1>
    <p class="subtitle">Diseño e implementación de la capa de persistencia del sistema.</p>
  </header>

  <!-- team -->
  <p class="section-label">Equipo</p>
  <div class="team">
    <div class="member">
      <div class="avatar">FI</div>
      <div>
        <div class="member-name">Fernando Ibañez</div>
        <div class="member-role">Integrante</div>
      </div>
    </div>
    <div class="member">
      <div class="avatar">GR</div>
      <div>
        <div class="member-name">Gonzalo Ramirez</div>
        <div class="member-role">Integrante</div>
      </div>
    </div>
  </div>

  <!-- objetivo -->
  <p class="section-label">Objetivo</p>
  <div class="objetivo">
    <p>Construir un modelo de base de datos <strong>sólido, consistente y escalable</strong> que soporte todas las entidades del sistema: usuarios, tareas, comandos de voz y logs de auditoría, utilizando <strong>PostgreSQL</strong> como motor principal con normalización adecuada y políticas de seguridad por roles.</p>
  </div>

  <!-- tasks -->
  <p class="section-label">Tareas Clave</p>
  <div class="tasks-grid">
    <div class="task-card">
      <div class="task-num">01</div>
      <div class="task-title">Diagrama Entidad-Relación</div>
      <div class="task-desc">Diseñar el modelo ER con las 4 entidades principales: <em>usuarios</em>, <em>tareas</em>, <em>comandos de voz</em> y <em>logs</em>. Define atributos, claves primarias/foráneas y la lógica de negocio detrás de cada relación.</div>
    </div>
    <div class="task-card">
      <div class="task-num">02</div>
      <div class="task-title">Definición de Motor</div>
      <div class="task-desc">Se usará <em>PostgreSQL</em> como motor de base de datos. Justificación: soporte nativo a JSONB, transacciones ACID, extensiones (pgcrypto, uuid-ossp) y excelente ecosistema en producción.</div>
    </div>
    <div class="task-card">
      <div class="task-num">03</div>
      <div class="task-title">Normalización y Relaciones</div>
      <div class="task-desc">Aplicar normalización hasta 3FN. Un usuario puede tener muchas tareas (1:N); una tarea puede tener varios comandos de voz asociados (1:N). Se definen ON DELETE y ON UPDATE para cada FK.</div>
    </div>
    <div class="task-card">
      <div class="task-num">04</div>
      <div class="task-title">Esquema Inicial (DDL)</div>
      <div class="task-desc">Escritura de los scripts <em>CREATE TABLE</em> con tipos de datos correctos, constraints (NOT NULL, UNIQUE, CHECK), valores por defecto y uso de UUID como clave primaria donde corresponda.</div>
    </div>
    <div class="task-card">
      <div class="task-num">05</div>
      <div class="task-title">Índices de Rendimiento</div>
      <div class="task-desc">Crear índices compuestos y simples sobre las columnas más consultadas: <em>user_id</em>, <em>created_at</em> y <em>status</em>. Evitar full table scans en listados y filtros del backend.</div>
    </div>
    <div class="task-card">
      <div class="task-num">06</div>
      <div class="task-title">Sistema de Migraciones</div>
      <div class="task-desc">Implementar <em>Alembic</em> para control de versiones del esquema. Cada cambio (agregar columna, nuevo índice, etc.) queda registrado como una migración reversible y trazable en el repositorio.</div>
    </div>
    <div class="task-card">
      <div class="task-num">07</div>
      <div class="task-title">Seeds de Prueba</div>
      <div class="task-desc">Poblar la base con datos ficticios pero realistas: usuarios de ejemplo, tareas con distintos estados y fechas, y comandos de voz asociados. Permite que el backend pruebe sus endpoints sin datos vacíos.</div>
    </div>
    <div class="task-card">
      <div class="task-num">08</div>
      <div class="task-title">Seguridad por Roles</div>
      <div class="task-desc">Definir al menos 3 roles en PostgreSQL: <em>admin</em> (acceso total), <em>app_user</em> (lectura/escritura limitada) y <em>readonly</em> (solo consultas). Se aplican con GRANT/REVOKE sobre cada tabla.</div>
    </div>
    <div class="task-card">
      <div class="task-num">09</div>
      <div class="task-title">Auditoría Simple</div>
      <div class="task-desc">Tabla de logs que registra automáticamente cada acción relevante: quién ejecutó, qué operación (INSERT/UPDATE/DELETE), en qué tabla y cuándo. Se puede implementar con triggers de PostgreSQL.</div>
    </div>
  </div>

  <!-- deliverables + dependencies -->
  <div class="two-col">
    <div class="panel">
      <h3><span class="dot"></span>Entregables</h3>
      <div class="pill-list">
        <span class="pill">Scripts SQL inicial</span>
        <span class="pill">Diagrama ER</span>
        <span class="pill">Migraciones versionadas</span>
        <span class="pill">Dataset de prueba</span>
      </div>
    </div>
    <div class="panel">
      <h3><span class="dot red"></span>Dependencias</h3>
      <div class="pill-list">
        <span class="pill red">Definiciones del backend</span>
        <span class="pill red">Modelos de datos requeridos</span>
        <span class="pill red">Flujos de negocio</span>
      </div>
    </div>
  </div>

  <!-- dependency note -->
  <div class="dep-block">
    ⚠ <strong>Bloqueo identificado:</strong> Esta fase requiere que el equipo de backend defina qué datos necesita consumir (endpoints, entidades, filtros). Se recomienda una reunión de alineación antes de finalizar el DDL y las migraciones.
  </div>

  <footer>
    Proyecto — Base de Datos &nbsp;·&nbsp; Fase <span>01</span> &nbsp;·&nbsp; Fernando Ibañez &amp; Gonzalo Ramirez
  </footer>

</div>
</body>
</html>