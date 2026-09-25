# Registro General de Cambios

Este archivo registra los principales cambios, decisiones y avances realizados durante el proyecto.

## Índice

- [30/08/2026](#30082026)
- [13/09/2026](#13092026)
- [25/09/2026](#25092026)

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

## 13/09/2026

### Propuesta

- Se incorporó una medición inicial del impacto causado por la búsqueda de materiales.
- Se agregó una estimación de entre 10 minutos y 4 horas perdidas por jornada.
- Se agregaron objetivos generales y específicos verificables.
- Se definieron las funcionalidades incluidas y excluidas de la primera versión.
- Se incorporó el análisis de viabilidad técnica, temporal y del dominio.
- Se agregó el análisis de alternativas consideradas.
- Se documentó el relevamiento de infraestructura del área de Terminación.
- Se incorporaron los riesgos del proyecto y sus medidas de mitigación.
- Se aclaró que los movimientos pueden ser registrados por operarios de diferentes turnos.

### Arquitectura y despliegue

- Se mantuvo la decisión de desarrollar una aplicación web responsive, documentada en el `ADR-001`.
- Se decidió ejecutar la aplicación dentro de la red local de la fábrica.
- Se estableció que la empresa deberá proporcionar el equipo donde se ejecutará el sistema.
- Se definió que el equipo estará ubicado en el área de Terminación.
- Se estableció que un administrador designado será responsable de mantener el equipo en funcionamiento.
- Se definieron copias de seguridad automáticas semanales almacenadas en un servidor local diferente.
- Se creó el `ADR-005` para documentar el despliegue web dentro de la red local.

### Base de datos

- Se reemplazó la elección inicial de MySQL por PostgreSQL.
- Se marcó el `ADR-002` como reemplazado.
- Se creó el `ADR-006` para documentar la utilización de PostgreSQL.
- Se actualizaron la propuesta y el README para reflejar el cambio.

### Gestión del proyecto

- Se organizó el desarrollo en un roadmap de doce semanas.
- Se incorporaron fechas de vencimiento y duraciones estimadas para cada tarea.
- Se estableció que los responsables, revisores y estados se administrarán desde Trello.
- Se creó el tablero de Trello para registrar el avance y las evidencias.
- Se estableció la elaboración de un reporte semanal.

## 25/09/2026

### Revisión de documentación

- Se aplicaron las observaciones recibidas sobre la documentación de la Semana 1.
- Se reorganizó el README principal para utilizarlo como presentación e índice del repositorio.
- Se incorporaron índices internos en la documentación.
- Se separaron las alternativas consideradas de las soluciones existentes en el mercado.
- Se agregó un cuadro comparativo de alternativas.
- Se incorporó una conclusión sobre la solución seleccionada.
- Se agregaron enlaces desde la propuesta hacia los ADR correspondientes.
- Se corrigió la descripción de la identificación UN, aclarando que se encuentra grabada en los materiales según el estándar del proveedor y no es generada por el sistema.
- Se revisó la consistencia entre la propuesta del proyecto y las decisiones registradas en los ADR.