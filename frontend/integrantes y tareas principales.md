# Equipo Frontend

<div align="center">

![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![RxJS](https://img.shields.io/badge/RxJS-B7178C?style=for-the-badge&logo=reactivex&logoColor=white)

</div>

---

##  Objetivo

Construir una **interfaz usable y rápida** que consuma la API del backend. La app principal se desarrolla en **Angular** con manejo de estado reactivo via RxJS, complementada por un **widget de voz en React** para grabación y procesamiento de comandos.

---

##  Integrantes

| Integrante | Rol |
|-----------|-----|
| Pablo Cocio | Frontend · Angular · React |
| Gonzalo Ramirez | Frontend · TypeScript · RxJS |
| Gabriel Pedreros | Frontend · TypeScript · RxJS |


---

##  Stack Tecnológico

| Tecnología | Uso |
|-----------|-----|
|  Angular | Framework principal |
|  React | Widget de voz |
|  TypeScript | Tipado estático |
|  RxJS | Manejo de estado |
|  HTTP Client | Integración API |
|  Web Speech API | Grabación de voz |

---

## Tareas Clave

### 01 · Setup en Angular
Inicialización del proyecto con **Angular CLI**: estructura de módulos, routing, configuración de entornos (dev/prod) y conexión inicial al servidor backend.

### 02 · Diseño UI — Dashboard
Vista principal con listado de tareas. Filtros por estado, ordenamiento y buscador. Diseño limpio con indicadores visuales de prioridad y fecha.

### 03 · Crear / Editar Tareas
Formularios reactivos para creación y edición de tareas. Validación en tiempo real. Modal o página dedicada con campos: título, descripción, estado y fecha límite.

### 04 · Estados de Tarea
Gestión visual de estados: **pendiente**, **en progreso** y **completado**. Cambio de estado desde el listado con feedback inmediato sin recargar la página.

### 05 · Integración API
Servicios Angular con **HttpClient** para consumir todos los endpoints del backend. Interceptores para adjuntar el token JWT a cada request automáticamente.

### 06 · Manejo de Estado
Estado global de la app con **RxJS** (BehaviorSubject) o servicios singleton. Sincronización reactiva entre componentes sin prop drilling.

### 07 · Widget de Voz (React)
Componente React embebido en la app Angular con:
- Botón de grabación con estado activo
- Feedback visual — grabando / procesando
- Envío del audio al endpoint de voz
- Respuesta parseada como acción en la UI

### 08 · UX Básica
Loader global durante requests, skeleton screens en listados. Mensajes de error legibles para el usuario. Confirmación antes de eliminar tareas.

### 09 · Autenticación
Pantalla de **login simple** con email y contraseña. Almacenamiento del token JWT en memoria o sessionStorage. Guard de rutas para proteger vistas privadas.

### 10 · Responsive Básico
Layout adaptable a móvil y desktop. El dashboard colapsa a una sola columna en pantallas pequeñas. El widget de voz es accesible desde cualquier dispositivo.



##  Entregables

-  App funcional conectada al backend
-  Widget de voz integrado

---

## Dependencias

-  API backend disponible
-  Definición de endpoints

---

> **Bloqueo identificado:** El equipo frontend no puede integrar la API hasta que el backend entregue los endpoints documentados. Se recomienda usar **mocks locales** mientras tanto para avanzar en paralelo con el desarrollo de la UI.

---

<div align="center">
  <sub>README · Frontend Angular + React · Fase 03 · Pablo Cocio &amp; Gonzalo Ramirez</sub>
</div>
