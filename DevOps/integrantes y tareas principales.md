# ⚙️ Capa Transversal — DevOps / Integración

<div align="center">

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![ENV](https://img.shields.io/badge/Env_Variables-ECD53F?style=for-the-badge&logo=dotenv&logoColor=black)

</div>

---

## 🎯 Objetivo

Garantizar que **todos los servicios corran de forma reproducible y consistente** en cualquier entorno. Docker para todo, variables de entorno bien gestionadas, pipeline simple de build + run, y documentación clara para que cualquier integrante pueda levantar el proyecto desde cero.

---

## 👥 Integrantes

| Integrante | Rol |
|-----------|-----|
| Gabriel Pedreros | DevOps · Docker · CI/CD |
| Fernado Ibañez | DevOps · Docker · CI/CD |
| pablo cocio | DevOps · Docker · CI/CD |


| Tecnología | Uso |
|-----------|-----|
|  Docker | Contenerización de servicios |
|  Docker Compose | Orquestación multi-servicio |
|  `.env` files | Variables de entorno por servicio |
|  GitHub Actions | Pipeline CI/CD |
|  Makefile | Comandos unificados |

---

##  Tareas Clave

### 01 · Docker para Todo
Cada servicio tiene su propio `Dockerfile` optimizado:
- `db/Dockerfile` — PostgreSQL con init scripts
- `backend/Dockerfile` — FastAPI + Uvicorn
- `frontend/Dockerfile` — Angular build + Nginx

### 02 · Docker Compose
Archivo `docker-compose.yml` que levanta todos los servicios juntos:
- Red interna compartida entre contenedores
- Volúmenes persistentes para la base de datos
- Orden de arranque con `depends_on`

### 03 · Variables de Entorno
Cada servicio tiene su propio `.env.example` versionado. Las variables reales van en `.env` (ignorado por git). Variables críticas:
- `DATABASE_URL` — Conexión a PostgreSQL
- `SECRET_KEY` — Firma de tokens JWT
- `SPEECH_API_KEY` — Servicio de voz
- `FRONTEND_URL` — CORS del backend

### 04 · Pipeline Simple (Build + Run)
Pipeline en **GitHub Actions** que se ejecuta en cada push a `main`:
- Build de imágenes Docker
- Ejecución de tests
- Verificación de migraciones



##  Estructura esperada del proyecto

```
proyecto/
├── docker-compose.yml
├── .env.example
├── .env                  # ← no commitear
├── db/
│   ├── Dockerfile
│   ├── migrations/
│   └── seeds/
├── backend/
│   ├── Dockerfile
│   ├── .env.example
│   └── app/
└── frontend/
    ├── Dockerfile
    ├── .env.example
    └── src/
```

---

##  Pipeline GitHub Actions

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build images
        run: docker compose build
      - name: Run migrations
        run: docker compose run backend alembic upgrade head
      - name: Run tests
        run: docker compose run backend pytest
```

---

##  Entregables

-  `Dockerfile` por cada servicio
-  `docker-compose.yml` funcional
-  `.env.example` por servicio
- Pipeline CI configurado
- README claro con instrucciones de setup

---

##  Dependencias

-  Todos los equipos deben exponer su `Dockerfile`
-  Puertos acordados entre servicios
-  Variables de entorno definidas por cada equipo

---

>  **Importante:** Esta capa es transversal — afecta a todos los equipos. Ningún servicio debería funcionar solo en la máquina local de quien lo desarrolló. El criterio de éxito es: **cualquier integrante puede clonar el repo y levantar todo con `docker compose up`**.

---

<div align="center">
  <sub>README · DevOps / Integración · Capa Transversal · Todos los equipos</sub>
</div>