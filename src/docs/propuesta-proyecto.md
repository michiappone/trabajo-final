# Propuesta de Proyecto

## Nombre del proyecto

Sistema web de trazabilidad de materiales en áreas productivas.

## Problema

La propuesta surge a partir de una problemática real observada en una fábrica de transformadores.

Cuando los materiales salen de depósito e ingresan a producción, pueden ser montados, desmontados, trasladados, enviados a retrabajo o quedar pendientes de colocación.

El problema aparece cuando un material se separa del conjunto correspondiente a su transformador y se pierde el registro de su ubicación.

Esto puede provocar que, al momento de necesitarlo nuevamente, no se sepa dónde se encuentra y se termine utilizando un material perteneciente a otro transformador, generando una cadena de faltantes.

## Solución propuesta

Desarrollar una aplicación web que permita registrar y consultar la ubicación de materiales asociados a transformadores dentro de áreas productivas.

Cada transformador contará con:

- Código identificador.
- Número UN.
- Materiales asociados.
- Ubicación principal.
- Historial de movimientos.

También existirán ubicaciones temporales para almacenar materiales separados del transformador.

Estas ubicaciones podrán identificarse mediante códigos QR.

## Caso principal

El sistema se desarrollará utilizando el área de Terminación como caso principal.

Sin embargo, las áreas serán configurables, permitiendo extender el sistema posteriormente a:

- Bobinado.
- Montaje Parte Activa.
- Preestabilizado.
- Otras áreas.

## Usuarios

### Administrador

Podrá gestionar:

- Áreas.
- Ubicaciones.
- Transformadores.
- Números UN.
- Materiales.
- Usuarios.

### Operario

Podrá:

- Consultar transformadores.
- Consultar materiales.
- Registrar movimientos.
- Consultar ubicaciones.
- Registrar materiales en ubicaciones temporales.
- Agregar observaciones.
- Consultar historial.

## Alcance

El sistema estará enfocado en la trazabilidad de materiales dentro del proceso productivo.

Quedan fuera del alcance inicial:

- Planificación de producción.
- Ensayos.
- Calidad.
- Compras.
- Proveedores.
- Mantenimiento.
- Stock general.
- Gestión completa de depósito.

## Tecnologías

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
- MySQL

### API
- REST

### Documentación
- Swagger / OpenAPI

### Control de versiones
- Git
- GitHub

## Plataforma

La aplicación será web y responsive, permitiendo utilizarla desde computadora y celular.

Se prevé desplegar componentes del sistema en servicios online.

## Integrantes

- Enzo Chavez
- Michael Chiappone

## Tutor

- Santiago Fonzo