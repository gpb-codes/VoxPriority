#  Equipo Base de Datos

<div align="center">

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-CC0000?style=for-the-badge&logo=python&logoColor=white)
![Alembic](https://img.shields.io/badge/Alembic-013243?style=for-the-badge&logo=python&logoColor=white)
![Python](https://img.shields.io/badge/Python_3.13+-3776AB?style=for-the-badge&logo=python&logoColor=white)

</div>

---

##  Objetivo

Construir un modelo de base de datos **sólido, consistente y escalable** que soporte todas las entidades del sistema: usuarios, tareas, comandos de voz y logs de auditoría. Se usa **PostgreSQL** como motor con normalización hasta 3FN, migraciones versionadas con **Alembic** y políticas de seguridad por roles.

---

##  Integrantes

| Integrante | Rol |
|-----------|-----|
| Fernando Ibañez | Base de Datos · DDL · Migraciones |
| Gonzalo Ramirez | Modelado ER · Seeds · Seguridad |

---

## Stack Tecnológico

| Tecnología | Uso |
|-----------|-----|
|  PostgreSQL | Motor principal |
|  SQLAlchemy | ORM / conexión |
|  Alembic | Migraciones versionadas |
|  pgcrypto | Extensión de seguridad |
|  uuid-ossp | UUIDs nativos |
|  Python 3.11+ | Scripts y seeds |

---

##  Tareas Clave

### 01 · Diagrama Entidad-Relación
Diseñar el modelo ER con las 4 entidades principales: **usuarios**, **tareas**, **comandos de voz** y **logs**. Define atributos, claves primarias/foráneas y la lógica de negocio detrás de cada relación.

### 02 · Definición de Motor
Se usará **PostgreSQL** como motor. Justificación: soporte nativo a JSONB, transacciones ACID, extensiones (pgcrypto, uuid-ossp) y excelente ecosistema en producción.

### 03 · Normalización y Relaciones
Aplicar normalización hasta **3FN**. Un usuario puede tener muchas tareas (1:N); una tarea puede tener varios comandos de voz (1:N). Se definen `ON DELETE` y `ON UPDATE` para cada FK.

### 04 · Esquema Inicial (DDL)
Escritura de los scripts `CREATE TABLE` con tipos de datos correctos, constraints (`NOT NULL`, `UNIQUE`, `CHECK`), valores por defecto y uso de UUID como clave primaria.

### 05 · Índices de Rendimiento
Crear índices sobre las columnas más consultadas: `user_id`, `created_at` y `status`. Evitar full table scans en listados y filtros del backend.

### 06 · Sistema de Migraciones
Implementar **Alembic** para control de versiones del esquema. Cada cambio queda registrado como migración reversible y trazable en el repositorio.

### 07 · Seeds de Prueba
Poblar la base con datos ficticios pero realistas: usuarios de ejemplo, tareas con distintos estados y fechas, y comandos de voz asociados.

### 08 · Seguridad por Roles
Definir 3 roles en PostgreSQL: **admin** (acceso total), **app_user** (lectura/escritura limitada) y **readonly** (solo consultas), aplicados con `GRANT`/`REVOKE`.

### 09 · Auditoría Simple
Tabla de logs que registra automáticamente cada acción relevante: quién ejecutó, qué operación (`INSERT`/`UPDATE`/`DELETE`), en qué tabla y cuándo. Implementado con **triggers**.

---



##  Entregables

-  Scripts SQL inicial
-  Diagrama ER
-  Migraciones versionadas
-  Dataset de prueba

---

##  Dependencias

-  Definiciones del equipo backend (qué datos necesita)
-  Modelos de datos requeridos
- Flujos de negocio definidos
---

>  **Bloqueo identificado:** Esta fase requiere que el equipo de backend defina qué datos necesita consumir (endpoints, entidades, filtros). Se recomienda una reunión de alineación antes de finalizar el DDL y las migraciones.

---

<div align="center">
  <sub>README · Base de Datos · Fase 01 · Fernando Ibañez &amp; Gonzalo Ramirez</sub>
</div>