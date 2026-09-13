# Propuesta de Proyecto

## Nombre del proyecto

Sistema web de trazabilidad de materiales en áreas productivas.

## Problema

La propuesta surge a partir de una problemática real observada en una fábrica de transformadores.

Cuando los materiales salen de depósito e ingresan a producción, pueden ser montados, desmontados, trasladados, enviados a retrabajo o quedar pendientes de colocación.

El problema aparece cuando un material se separa del conjunto correspondiente a su transformador y se pierde el registro de su ubicación.

Esto puede provocar que, al momento de necesitarlo nuevamente, no se sepa dónde se encuentra y se termine utilizando un material perteneciente a otro transformador, generando una cadena de faltantes.

### Medición del impacto actual

Según una estimación inicial basada en la experiencia de los operarios, la búsqueda de materiales puede ocasionar una pérdida de entre 10 minutos y 4 horas por jornada, dependiendo del tipo de material, su ubicación y la tarea que se esté realizando.

Esta información se considera una estimación preliminar. Durante el desarrollo del proyecto se realizará un registro semanal de los tiempos destinados a localizar materiales, con el objetivo de establecer una línea base y comparar posteriormente los resultados obtenidos con la utilización del sistema.

## Objetivos

### Objetivo general

Desarrollar una aplicación web que permita mejorar la trazabilidad de materiales asociados a transformadores dentro del área de Terminación, registrando su ubicación actual y sus movimientos durante el proceso productivo.

### Objetivos específicos

- Reducir al menos un 50 % el tiempo promedio destinado a buscar materiales durante la prueba piloto, en comparación con la medición inicial.
- Permitir consultar la ubicación actual de un material en menos de 2 minutos.
- Registrar cada movimiento indicando el material, el transformador asociado, el origen, el destino, la fecha, la hora y el usuario que realizó el registro.
- Mantener un historial de movimientos que permita reconstruir los cambios de ubicación de cada material.
- Advertir al operario cuando intente registrar un material asociado a un transformador diferente.
- Realizar una prueba piloto en el área de Terminación y registrar las observaciones de los operarios.

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

La primera versión del sistema estará enfocada en la trazabilidad de materiales dentro del área de Terminación.

### Funcionalidades incluidas

- Gestión de áreas y ubicaciones.
- Gestión de transformadores y números UN.
- Registro de materiales asociados a cada transformador.
- Consulta de la ubicación actual de los materiales.
- Registro de ingresos, traslados internos, devoluciones a depósito y pases a despacho.
- Registro del usuario que realizó cada movimiento.
- Consulta del historial de movimientos.
- Registro de observaciones.
- Uso de ubicaciones principales y temporales.
- Generación y lectura de códigos QR asociados a las ubicaciones.
- Advertencias cuando un material corresponda a otro transformador.
- Acceso desde computadoras y dispositivos móviles conectados a la red local.

### Exclusiones de la primera versión

Quedan fuera del alcance inicial:

- Planificación de producción.
- Ensayos.
- Gestión de calidad.
- Compras y proveedores.
- Mantenimiento.
- Control del stock general.
- Gestión completa del depósito.
- Colocación de códigos QR individuales sobre los materiales.
- Importación masiva mediante archivos CSV o Excel.
- Funcionamiento fuera de la red local de la fábrica.


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