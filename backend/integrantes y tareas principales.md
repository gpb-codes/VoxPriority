# Equipo Backend

<div align="center">

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-CC0000?style=for-the-badge&logo=python&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic_v2-E92063?style=for-the-badge&logo=pydantic&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![Python](https://img.shields.io/badge/Python_3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)

</div>

---

##  Objetivo

Desarrollar la **lógica de negocio completa** del sistema y exponer una **API REST robusta** con FastAPI. Incluye gestión de tareas, autenticación con JWT, módulo de comandos de voz y workers asíncronos, todo documentado automáticamente con **Swagger UI**.

---

##  Integrantes

| Integrante | Rol |
|-----------|-----|
| Gabriel Pedreros | Backend · FastAPI · JWT |
| Dante Correa | Backend · SQLAlchemy · Pydantic |

---

##  Stack Tecnológico

| Tecnología | Uso |
|-----------|-----|
| FastAPI | Framework principal |
| Uvicorn | Servidor ASGI |
| SQLAlchemy | ORM |
| Pydantic v2 | Validación de datos |
|  WT | Autenticación |
| Speech-to-Text | Módulo de voz |

---

##  Tareas Clave

### 01 · Estructura Base con FastAPI
Scaffolding inicial del proyecto: organización por módulos (`routers`, `services`, `models`, `schemas`), configuración de entornos y arranque del servidor con **Uvicorn**.

### 02 · Conexión a Base de Datos
Integración con **SQLAlchemy** como ORM. Configuración del engine, sesiones y pool de conexiones apuntando al esquema definido por el equipo de DB.

### 03 · CRUD de Tareas
Endpoints completos para la gestión de tareas:
- `POST /tasks` — Crear nueva tarea
- `GET /tasks` — Listar con filtros y paginación
- `PATCH /tasks/{id}` — Actualizar estado
- `DELETE /tasks/{id}` — Eliminar tarea

### 04 · Autenticación con JWT
Sistema de login con tokens **JWT** (access + refresh). Middleware de autenticación aplicado a rutas protegidas. Gestión de expiración y renovación de tokens.

### 05 · Módulo de Voz
Integración con servicio de **speech-to-text** para recibir audio y convertirlo a texto. Parser de comandos que interpreta frases como:
- `"crear tarea [nombre]"`
- `"eliminar tarea [id]"`
- `"listar mis tareas"`

### 06 · Worker Asíncrono
Uso de **Background Tasks** de FastAPI para procesar operaciones pesadas fuera del ciclo de request: audio, notificaciones y logs diferidos.

### 07 · Validación con Pydantic
Schemas de entrada y salida con **Pydantic v2**. Validación de tipos, longitudes, formatos y reglas de negocio. Respuestas y errores estandarizados.

### 08 · Logging y Manejo de Errores
Sistema centralizado de logs con niveles (`INFO`, `WARNING`, `ERROR`). Handlers globales para excepciones HTTP y errores inesperados. Formato de error consistente.

### 09 · Documentación Automática
**Swagger UI** generado automáticamente por FastAPI. Todos los endpoints con descripción, ejemplos de request/response y códigos de estado documentados.

---


##  Entregables

-  API funcional
-  Endpoints documentados en Swagger
-  Servicio corriendo local

---

##  Dependencias

-  Modelo de datos definido por el equipo DB
-  Requisitos UX del equipo frontend

---

>  **Bloqueo identificado:** El equipo de backend no puede finalizar los endpoints sin el esquema de base de datos definido. Los contratos de la API deben alinearse con los requisitos de UX del equipo frontend antes de implementar las respuestas.

---

<div align="center">
  <sub>README · Backend FastAPI · Fase 02 · Gabriel Pedreros &amp; Dante Correa</sub>
</div>