# Trabajo Final Integrador

## Sistema web de trazabilidad de materiales en áreas productivas

Repositorio correspondiente al Trabajo Final Integrador de la Tecnicatura Universitaria en Programación.

El proyecto propone desarrollar una aplicación web para mejorar la trazabilidad de materiales asociados a transformadores dentro de áreas productivas, utilizando el área de Terminación como caso principal.

## Índice del repositorio

### Código fuente

- Backend: `src/backend/`
- Frontend: `src/frontend/`
- Base de datos: `src/database/`

### Documentación

- [Propuesta del proyecto](src/docs/propuesta-proyecto.md)
- [Requisitos del sistema](src/docs/requisitos.md)
- [Casos de uso](src/docs/casos-de-uso.md)
- [Modelo de datos y diagrama de clases](src/docs/modelo-datos.md)
- [Arquitectura del sistema](src/docs/arquitectura.md)
- [Roadmap](src/docs/roadmap.md)
- [Registro general de cambios](src/docs/changelog.md)
- - [Módulos del sistema](src/docs/modulos.md)
- ADR: `src/docs/adr/`

## Integrantes

- Enzo Chavez
- Michael Chiappone

## Tutor

- Santiago Fonzo

## Descripción

La aplicación permitirá registrar y consultar:

- Transformadores.
- Materiales asociados.
- Identificación del proveedor asociada a cada transformador y grabada físicamente en sus materiales.
- Ubicaciones principales y temporales.
- Movimientos de materiales.
- Observaciones.
- Historial de movimientos.
- Ubicaciones mediante códigos QR.

La identificación del proveedor no será generada por la aplicación. Cada transformador tendrá asociada una identificación existente, que puede presentarse con formatos como UN20 o K486 y se encuentra grabada físicamente en sus materiales.

La primera versión estará enfocada en el área de Terminación y funcionará dentro de la red local de la fábrica.

## Tecnologías previstas

### Backend

- Java
- Spring Boot
- Spring Web
- Spring Data JPA
- Hibernate

### Frontend

- HTML
- CSS
- JavaScript

### Base de datos

- PostgreSQL

### API y documentación

- REST
- Swagger / OpenAPI

### Control de versiones

- Git
- GitHub

## Estructura del repositorio

```text
trabajo-final/
├── src/
│   ├── backend/
│   ├── database/
│   ├── docs/
│   │   ├── adr/
│   │   │   ├── ADR-001-arquitectura-web.md
│   │   │   ├── ADR-002-base-de-datos-mysql.md
│   │   │   ├── ADR-003-stack-backend.md
│   │   │   ├── ADR-004-uso-de-qr.md
│   │   │   ├── ADR-005-despliegue-web-local.md
│   │   │   ├── ADR-006-base-de-datos-postgresql.md
│   │   │   └── ADR-007-modelo-ubicaciones-movimientos.md
│   │   ├── arquitectura.md
│   │   ├── casos-de-uso.md
│   │   ├── changelog.md
│   │   ├── modelo-datos.md
│   │   ├── propuesta-proyecto.md
│   │   ├── requisitos.md
│   │   └── roadmap.md
│   ├── frontend/
│   └── Main.java
├── .gitignore
└── README.md
```