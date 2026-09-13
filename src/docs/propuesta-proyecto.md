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

## Análisis de viabilidad

### Viabilidad técnica

El proyecto es técnicamente viable porque utilizará tecnologías conocidas por los integrantes: Java, Spring Boot, Spring Data JPA, PostgreSQL, HTML, CSS y JavaScript. La aplicación podrá ejecutarse en un equipo conectado a la red local y utilizarse desde los navegadores de las computadoras y dispositivos móviles autorizados.

Será necesario confirmar la disponibilidad del equipo que funcionará como servidor, la cobertura de la red interna y el acceso desde los dispositivos utilizados en el área.

### Viabilidad temporal

El proyecto se desarrollará durante doce semanas. La primera versión se limitará al área de Terminación y a las funciones esenciales de trazabilidad, lo que permite mantener un alcance compatible con el tiempo disponible.

### Viabilidad del dominio

Michael trabaja en la planta y posee acceso al área en la que se presenta el problema. Esto permite observar el proceso, consultar a los operarios y validar el funcionamiento del sistema mediante una prueba piloto.


## Alternativas consideradas

### Registros manuales

El uso de planillas en papel tiene un costo inicial bajo, pero dificulta la actualización de la información, la búsqueda de registros y la consulta del historial.

### Archivos Excel o CSV

Permiten registrar información de manera sencilla, pero pueden producir versiones duplicadas, modificaciones simultáneas y dificultades para conocer la ubicación actual de cada material. Los archivos CSV o Excel podrán considerarse en el futuro como mecanismo de importación o contingencia.

### Software comercial de gestión

Existen sistemas empresariales de inventario y trazabilidad, pero suelen estar orientados al control general de stock y pueden requerir costos de licencia, infraestructura adicional o una adaptación compleja al proceso específico de la fábrica.

### Aplicación móvil nativa

Podría facilitar el uso desde celulares, pero requeriría mantener una aplicación diferente para cada plataforma. Una aplicación web responsive permite utilizar el sistema desde computadoras y celulares mediante un navegador.

### Alternativa seleccionada

Se seleccionó el desarrollo de una aplicación web propia, ejecutada dentro de la red local, porque puede adaptarse al proceso de la fábrica y no requiere una conexión permanente a Internet.


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

## Relevamiento de infraestructura

Se realizó un relevamiento inicial de la infraestructura necesaria para determinar la viabilidad del despliegue local del sistema.

La empresa deberá proporcionar una computadora con componentes adecuados para ejecutar la aplicación. El equipo estará ubicado en el área de Terminación y podrá permanecer encendido durante todos los turnos de trabajo.

La computadora se conectará mediante Wi-Fi a la red interna. El área de Terminación cuenta con cobertura estable y los celulares de los operarios podrán conectarse a la misma red para acceder a la aplicación.

Se confirmó que la red interna continuará funcionando cuando la planta opere mediante generadores. También estará permitida la instalación de las tecnologías necesarias, incluyendo Java, PostgreSQL y la aplicación web.

Un administrador designado será responsable de mantener el equipo en funcionamiento, administrar la aplicación y verificar que las copias de seguridad se ejecuten correctamente.

Las copias de seguridad se realizarán automáticamente una vez por semana y podrán almacenarse en un servidor local destinado a respaldos. La configuración definitiva deberá garantizar que las copias no se almacenen únicamente en el mismo equipo donde se ejecuten la aplicación y la base de datos.

Las características técnicas del equipo, como el sistema operativo, la memoria RAM, el procesador y el espacio de almacenamiento, se definirán antes de instalar la aplicación.

## Integrantes

- Enzo Chavez
- Michael Chiappone

## Tutor

- Santiago Fonzo