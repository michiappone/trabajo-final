# Registro General de Cambios

Este archivo registra los principales cambios, decisiones y avances realizados durante el proyecto.

## 30/08/2026

### Definición inicial

- Se definió el problema principal del proyecto.
- Se estableció el alcance inicial.
- Se definió Terminación como área principal de aplicación.
- Se decidió que el sistema deberá ser escalable a otras áreas.
- Se creó el repositorio único de GitHub.

### Arquitectura

- Inicialmente se evaluó desarrollar una aplicación de escritorio con JavaFX.
- Se descartó JavaFX.
- Se decidió desarrollar una aplicación web responsive.
- Se definió Java + Spring Boot para el backend.
- Se definió MySQL como base de datos.
- Se definió HTML, CSS y JavaScript para el frontend.
- Se decidió utilizar una API REST.

### Trazabilidad

- Se definió que los códigos QR se utilizarán en ubicaciones físicas y no en materiales.
- Los QR permitirán consultar la ubicación y registrar materiales.
- Se definió el concepto de ubicación principal y ubicación temporal.
- Se decidió registrar historial de movimientos.
- Se decidió permitir observaciones opcionales sobre materiales.
- Se definió que el sistema mostrará advertencias cuando un material sea utilizado en otro transformador.

### Documentación

- Se reemplazó la documentación en PDF por archivos Markdown.
- Se incorporó el uso de ADR para registrar decisiones relevantes.
- Se creó un roadmap con fechas estimadas.