# Integrantes de este equipo
- Fernando Ibañez []
- Gonzalo Ramirez []

# primera parte a hacer
## Objetivo: modelo solido, consistente y escalable.

### tareas claves
- Diseño del modelo entidad-relacion (usuarios, tareas, comandos de voz, logs)
- Definir motor (PostgreSQL recomendado).
- Normalizacion y relaciones (1:N tareas, N1: usuarios, etc)
- creacion de esquema inicial (DDL).
- indices para el rendimiento ( Busqueda por usuario, fecha, estado).
- Sistema de migraciones (Alambric).
- Seeds de prueba.
- Politicas de seguridad ( roles, permisos basicos).
- auditoria simple ( logs de acciones)

### entregables
- scrips SQL inicial.
- Diagrama ER.
- Migraciones versionadas.
- Datatest de prueba-

### Dependencias:
- requiere definiciones del backend ( que datos necesita)