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
- [Roadmap](src/docs/roadmap.md)
- [Registro general de cambios](src/docs/changelog.md)
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
- Identificación UN existente en cada material.
- Ubicaciones principales y temporales.
- Movimientos de materiales.
- Observaciones.
- Historial de movimientos.
- Ubicaciones mediante códigos QR.

La identificación UN no será generada por la aplicación. Corresponde a una identificación grabada físicamente en cada material según el estándar del proveedor.

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
│   │   ├── casos-de-uso.md
│   │   ├── changelog.md
│   │   ├── propuesta-proyecto.md
│   │   ├── requisitos.md
│   │   └── roadmap.md
│   ├── frontend/
│   └── Main.java
├── .gitignore
└── README.md
```