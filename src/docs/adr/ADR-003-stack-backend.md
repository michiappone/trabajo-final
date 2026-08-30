# ADR-003 — Uso de Java y Spring Boot para el backend

## Estado

Aceptado

## Fecha

30/08/2026

## Contexto

El sistema necesita un backend que permita:

- Gestionar transformadores.
- Gestionar materiales.
- Gestionar ubicaciones.
- Registrar movimientos.
- Mantener historial.
- Aplicar reglas de negocio.
- Exponer información al frontend.

## Alternativas consideradas

### Java + Spring Boot

Ventajas:

- Conocimientos previos del equipo.
- Facilita el desarrollo de API REST.
- Integración con JPA e Hibernate.
- Arquitectura clara mediante Controller, Service y Repository.

### Node.js + Express

Ventajas:

- Desarrollo rápido.
- Uso de JavaScript en frontend y backend.

Desventajas:

- El equipo posee mayor experiencia con Java y Spring Boot.

## Decisión

Se utilizará Java con Spring Boot.

## Justificación

El equipo ya posee experiencia trabajando con Java, Spring Boot, arquitectura por capas, API REST y JPA.

Esto permite reducir riesgos y concentrar el esfuerzo en la solución del problema.

## Consecuencias

El backend utilizará una arquitectura basada en:

Controller → Service → Repository → Base de datos.