# ADR-002 — Uso de MySQL como base de datos

## Estado

Aceptado

## Fecha

30/08/2026

## Contexto

El sistema necesita almacenar información relacionada con:

- Transformadores.
- Materiales.
- Áreas.
- Ubicaciones.
- Movimientos.
- Observaciones.
- Usuarios.

La información presenta relaciones claras entre entidades, por lo que se considera apropiado utilizar una base de datos relacional.

## Alternativas consideradas

### PostgreSQL

Ventajas:

- Base de datos relacional robusta.
- Buen soporte para consultas complejas.
- Amplio uso en sistemas backend.

### MySQL

Ventajas:

- Base de datos relacional ampliamente utilizada.
- Compatible con Spring Boot, JPA e Hibernate.
- El equipo ya posee experiencia previa utilizando MySQL.
- Adecuada para los requerimientos del sistema.

## Decisión

Se utilizará MySQL.

## Justificación

MySQL cubre las necesidades del proyecto y permite aprovechar conocimientos previos del equipo, reduciendo la curva de aprendizaje.

## Consecuencias

La persistencia del backend se implementará sobre MySQL utilizando Spring Data JPA y Hibernate.