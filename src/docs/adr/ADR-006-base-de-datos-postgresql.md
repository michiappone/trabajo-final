# ADR-006 — PostgreSQL como base de datos

## Estado

Aceptado

## Fecha

13/09/2026

## Reemplaza

Este ADR reemplaza al [ADR-002 — MySQL como base de datos](ADR-002-base-de-datos-mysql.md).

## Contexto

Inicialmente se seleccionó MySQL como base de datos relacional para el sistema.

Durante la revisión de las decisiones técnicas se reconsideró esta elección y se evaluó PostgreSQL como alternativa para almacenar la información de transformadores, materiales, ubicaciones, usuarios y movimientos.

El sistema será desarrollado con Java, Spring Boot y Spring Data JPA, tecnologías compatibles con ambas bases de datos.

## Alternativas consideradas

### Opción 1 — Mantener MySQL

Ventajas:

- Es una base de datos relacional ampliamente utilizada.
- Posee integración con Spring Data JPA.
- El equipo cuenta con conocimientos previos sobre su utilización.

Desventajas:

- Ofrece menos flexibilidad para algunas consultas y tipos de datos avanzados.
- La decisión inicial no había sido revisada considerando el crecimiento futuro del sistema.

### Opción 2 — Utilizar PostgreSQL

Ventajas:

- Es una base de datos relacional de código abierto.
- Posee una integración adecuada con Spring Boot y Spring Data JPA.
- Ofrece integridad, estabilidad y funciones avanzadas para consultas.
- Permite ampliar el sistema sin cambiar la tecnología de persistencia.

Desventajas:

- Requiere configurar e instalar PostgreSQL en el equipo donde se desplegará el sistema.
- El equipo deberá familiarizarse con sus herramientas de administración y respaldo.

## Decisión

Se utilizará PostgreSQL como base de datos del sistema.

## Justificación

PostgreSQL se adapta al modelo relacional del proyecto, es compatible con las tecnologías seleccionadas y ofrece una base sólida para almacenar el historial de movimientos y ampliar el sistema en el futuro.

## Consecuencias

- MySQL deja de formar parte del stack tecnológico.
- Se deberá instalar PostgreSQL en el equipo servidor.
- El backend deberá utilizar el controlador y la configuración correspondientes a PostgreSQL.
- Las copias de seguridad y restauración se realizarán con herramientas compatibles con PostgreSQL.
- La propuesta y la documentación técnica deberán mantenerse coherentes con esta decisión.