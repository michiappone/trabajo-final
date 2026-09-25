# Propuesta de Proyecto

## Índice

- [Nombre del proyecto](#nombre-del-proyecto)
- [Problema](#problema)
- [Objetivos](#objetivos)
- [Solución propuesta](#solución-propuesta)
- [Caso principal](#caso-principal)
- [Usuarios](#usuarios)
- [Alcance](#alcance)
- [Análisis de viabilidad](#análisis-de-viabilidad)
- [Alternativas consideradas](#alternativas-consideradas)
- [Soluciones existentes en el mercado](#soluciones-existentes-en-el-mercado)
- [Comparación de alternativas](#comparación-de-alternativas)
- [Tecnologías](#tecnologías)
- [Plataforma y despliegue](#plataforma-y-despliegue)
- [Relevamiento de infraestructura](#relevamiento-de-infraestructura)
- [Riesgos y medidas de mitigación](#riesgos-y-medidas-de-mitigación)
- [Integrantes](#integrantes)
- [Tutor](#tutor)

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

La elección de una aplicación web se encuentra documentada en el [ADR-001 — Aplicación web](adr/ADR-001-arquitectura-web.md).

Cada transformador contará con:

- Código identificador.
- Materiales asociados.
- Ubicación principal asignada para sus materiales.

Cada material podrá registrar, entre otros datos:

- Tipo o descripción del material.
- Identificación UN.
- Transformador al que se encuentra asociado.
- Ubicación actual.
- Historial de movimientos.
- Observaciones.

La UN es una identificación que ya se encuentra grabada físicamente en el material según el estándar definido por el proveedor.

El sistema no generará ni asignará esta identificación, sino que registrará la UN existente para utilizarla como parte de la trazabilidad del material.

También existirán ubicaciones temporales para almacenar materiales que se encuentren separados momentáneamente de su transformador.

Las ubicaciones podrán identificarse mediante códigos QR para facilitar la consulta y el registro de movimientos.

La decisión de utilizar códigos QR en las ubicaciones y no individualmente sobre cada material se encuentra documentada en el [ADR-004 — Uso de códigos QR](adr/ADR-004-uso-de-qr.md).

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
- Materiales y registro de su identificación UN.
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
- Gestión de transformadores.
- Registro de materiales asociados a cada transformador.
- Registro de la identificación UN existente en cada material.
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

El proyecto es técnicamente viable porque utilizará tecnologías conocidas por los integrantes: Java, Spring Boot, Spring Data JPA, PostgreSQL, HTML, CSS y JavaScript.

La aplicación podrá ejecutarse en un equipo conectado a la red local y utilizarse desde los navegadores de las computadoras y dispositivos móviles autorizados.

El relevamiento de infraestructura confirmó que la empresa proporcionará un equipo para ejecutar el sistema, que el área posee cobertura Wi-Fi y que los dispositivos autorizados podrán acceder mediante la red interna.

Las principales decisiones técnicas se encuentran documentadas mediante ADR dentro del repositorio.

### Viabilidad temporal

El proyecto se desarrollará durante doce semanas.

La primera versión se limitará al área de Terminación y a las funciones esenciales de trazabilidad, lo que permite mantener un alcance compatible con el tiempo disponible.

La planificación y las fechas estimadas se encuentran detalladas en el [Roadmap del proyecto](roadmap.md).

### Viabilidad del dominio

Uno de los integrantes trabaja en la planta y posee acceso al área en la que se presenta el problema.

Esto permite observar el proceso productivo, consultar a los operarios y validar el funcionamiento del sistema mediante una prueba piloto.

## Alternativas consideradas

Durante el análisis inicial se evaluaron diferentes formas de resolver el problema.

### Registros manuales

El uso de planillas en papel tiene un costo inicial bajo, pero dificulta la actualización de la información, la búsqueda de registros y la consulta del historial.

### Archivos Excel o CSV

Permiten registrar información de manera sencilla, pero pueden producir versiones duplicadas, modificaciones simultáneas y dificultades para conocer la ubicación actual de cada material.

Los archivos CSV o Excel podrán considerarse en el futuro como mecanismo de importación o contingencia, pero no como solución principal de trazabilidad.

### Aplicación móvil nativa

Una aplicación móvil permitiría utilizar el sistema directamente desde los celulares de los operarios.

Sin embargo, implicaría desarrollar y mantener una aplicación específica para dispositivos móviles, mientras que también sería necesario disponer de acceso desde las computadoras del área.

Por este motivo se optó por una aplicación web responsive, decisión documentada en el [ADR-001 — Aplicación web](adr/ADR-001-arquitectura-web.md).

### Aplicación web propia

Permite disponer de una única aplicación accesible desde computadoras y celulares mediante un navegador.

Además, puede diseñarse específicamente para el proceso de la planta y ejecutarse dentro de la red local.

Esta fue la alternativa seleccionada.

## Soluciones existentes en el mercado

También se consideró la existencia de sistemas comerciales orientados a inventario, depósitos, gestión de activos y trazabilidad.

Estas herramientas pueden ofrecer funcionalidades como:

- Registro de productos o activos.
- Gestión de stock.
- Seguimiento de movimientos.
- Historial de operaciones.
- Identificación mediante códigos de barras o QR.
- Gestión de depósitos y ubicaciones.

Sin embargo, este tipo de soluciones suele estar diseñado para procesos generales de inventario o almacenamiento y puede requerir configuración, integración con otros sistemas, infraestructura adicional o adaptación al proceso específico de la planta.

El objetivo de este proyecto no es desarrollar un sistema general de gestión de stock, sino resolver específicamente el problema de conocer la ubicación y el historial de materiales asociados a cada transformador durante el proceso productivo.

## Comparación de alternativas

| Alternativa | Registro centralizado | Historial de movimientos | Acceso desde PC y celular | Adaptación al proceso de la planta | Dependencia de Internet |
|---|---|---|---|---|---|
| Registros manuales | No | Limitado | No | Alta | No |
| Excel / CSV | Parcial | Limitado | Parcial | Media | No necesariamente |
| Aplicación móvil nativa | Sí | Sí | Principalmente celular | Alta | Depende del despliegue |
| Software comercial de inventario o trazabilidad | Sí | Generalmente sí | Depende de la solución | Requiere configuración o adaptación | Depende de la solución |
| Aplicación web propuesta | Sí | Sí | Sí | Diseñada para el proceso | No |

### Conclusión

Se seleccionó el desarrollo de una aplicación web propia porque permite adaptar el sistema directamente al proceso de trabajo de la planta y utilizarlo tanto desde computadoras como desde dispositivos móviles.

Frente al procedimiento utilizado actualmente, permitirá centralizar la información, consultar la ubicación actual de los materiales y conservar un historial de movimientos.

En comparación con soluciones comerciales de inventario o trazabilidad, la propuesta tendrá un alcance específico, centrado en los materiales asociados a transformadores y en las necesidades concretas del área de Terminación.

Además, podrá ejecutarse dentro de la infraestructura existente de la fábrica sin depender de una conexión permanente a Internet.

## Tecnologías

### Backend

- Java.
- Spring Boot.
- Spring Web.
- Spring Data JPA.
- Hibernate.

La elección de Java y Spring Boot para el backend se encuentra documentada en el [ADR-003 — Stack backend](adr/ADR-003-stack-backend.md).

### Frontend

- HTML.
- CSS.
- JavaScript.

La decisión de utilizar una interfaz web responsive se encuentra documentada en el [ADR-001 — Aplicación web](adr/ADR-001-arquitectura-web.md).

### Base de datos

- PostgreSQL.

La elección de PostgreSQL se encuentra documentada en el [ADR-006 — PostgreSQL](adr/ADR-006-base-de-datos-postgresql.md), que reemplaza la decisión inicial de utilizar MySQL registrada en el [ADR-002 — MySQL](adr/ADR-002-base-de-datos-mysql.md).

### API

- REST.

### Documentación de la API

- Swagger / OpenAPI.

### Control de versiones

- Git.
- GitHub.

## Plataforma y despliegue

La aplicación será web y responsive, permitiendo su utilización desde computadoras y celulares mediante un navegador.

La elección de una aplicación web responsive se encuentra documentada en el [ADR-001 — Aplicación web](adr/ADR-001-arquitectura-web.md).

El sistema se desplegará en una computadora proporcionada por la empresa y ubicada en el área de Terminación.

Los dispositivos autorizados accederán a la aplicación mediante la red interna de la fábrica.

Este despliegue permitirá utilizar el sistema sin depender de una conexión permanente a Internet.

La red interna y el equipo continuarán funcionando cuando la planta opere mediante generadores.

Un administrador designado será responsable de mantener el equipo en funcionamiento y verificar las copias de seguridad automáticas semanales almacenadas en un servidor local diferente.

La decisión de despliegue se encuentra documentada en el [ADR-005 — Despliegue web local](adr/ADR-005-despliegue-web-local.md).

## Relevamiento de infraestructura

Se realizó un relevamiento inicial de la infraestructura necesaria para determinar la viabilidad del despliegue local del sistema.

La empresa deberá proporcionar una computadora con componentes adecuados para ejecutar la aplicación.

El equipo estará ubicado en el área de Terminación y podrá permanecer encendido durante todos los turnos de trabajo.

La computadora se conectará mediante Wi-Fi a la red interna.

El área de Terminación cuenta con cobertura estable y los celulares de los operarios podrán conectarse a la misma red para acceder a la aplicación.

Se confirmó que la red interna continuará funcionando cuando la planta opere mediante generadores.

También estará permitida la instalación de las tecnologías necesarias, incluyendo Java, PostgreSQL y la aplicación web.

Un administrador designado será responsable de mantener el equipo en funcionamiento, administrar la aplicación y verificar que las copias de seguridad se ejecuten correctamente.

Las copias de seguridad se realizarán automáticamente una vez por semana y se almacenarán en un servidor local destinado a respaldos.

La configuración deberá garantizar que las copias no se almacenen en el mismo equipo donde se ejecuten la aplicación y la base de datos.

Las características técnicas del equipo, como el sistema operativo, la memoria RAM, el procesador y el espacio de almacenamiento, se definirán antes de instalar la aplicación.

## Riesgos y medidas de mitigación

| Riesgo | Medida de mitigación |
|---|---|
| Interrupción de la conexión Wi-Fi | Controlar la estabilidad de la red y evaluar una conexión por cable si se producen interrupciones. |
| Falla del equipo donde se ejecuta la aplicación | Realizar copias de seguridad automáticas en un servidor local diferente. |
| Fallas no detectadas en las copias de seguridad | Designar un administrador responsable de verificar periódicamente los respaldos. |
| Movimientos no registrados | Diseñar un formulario sencillo que permita registrar el movimiento y agregar observaciones. |
| Operarios de diferentes turnos | Permitir que cualquier operario habilitado registre un movimiento, aunque no haya realizado el registro anterior. |
| Uso de materiales de otro transformador | Mostrar una advertencia antes de confirmar el movimiento. |
| Reubicación de tarimas | Identificar las ubicaciones mediante códigos QR. |
| Resistencia al uso del sistema | Diseñar pantallas sencillas y realizar una prueba piloto con operarios. |
| Ampliación excesiva del alcance | Limitar la primera versión al área de Terminación. |

Los movimientos no dependerán de que el mismo operario realice todos los registros.

Cualquier operario habilitado podrá registrar el ingreso, traslado interno, devolución a depósito o pase a despacho de un material.

El sistema almacenará el usuario que realizó cada registro, junto con la fecha, la hora, el origen, el destino y las observaciones correspondientes.

De esta manera, será posible mantener la trazabilidad aunque intervengan operarios de diferentes turnos.

## Integrantes

- Enzo Chavez.
- Michael Chiappone.

## Tutor

- Santiago Fonzo.