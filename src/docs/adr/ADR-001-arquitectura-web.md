# ADR-001 — Aplicación web en lugar de JavaFX

## Estado

Aceptado

## Fecha

30/08/2026

## Contexto

Inicialmente se consideró desarrollar una aplicación de escritorio utilizando JavaFX.

Sin embargo, el sistema también necesita permitir el acceso desde dispositivos móviles mediante códigos QR.

Desarrollar JavaFX para la computadora y una segunda interfaz web para celulares implicaría mantener dos clientes distintos.

## Alternativas consideradas

### Opción 1 — JavaFX + interfaz web móvil

Ventajas:

- Aplicación de escritorio dedicada.
- Interfaz específica para computadora.

Desventajas:

- Requiere aprender JavaFX.
- Obliga a desarrollar una segunda interfaz para celulares.
- Aumenta el tiempo y complejidad del proyecto.

### Opción 2 — Aplicación web responsive

Ventajas:

- Una sola aplicación para computadora y celular.
- Facilita el acceso mediante QR.
- Reduce la cantidad de tecnologías nuevas.
- El equipo ya posee experiencia previa con desarrollo web.

Desventajas:

- Requiere conexión a la aplicación web.
- La interfaz debe diseñarse correctamente para distintos tamaños de pantalla.

## Decisión

Se desarrollará una aplicación web responsive.

## Justificación

La aplicación web permite utilizar el mismo sistema desde computadoras y dispositivos móviles, reduciendo la complejidad del desarrollo y evitando mantener dos interfaces diferentes.

## Consecuencias

- Se descarta JavaFX.
- El frontend deberá adaptarse a computadora y celular.
- Los QR podrán abrir directamente páginas del sistema.