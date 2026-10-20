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

La solución propuesta busca mejorar la trazabilidad de los materiales asociados a transformadores durante su paso por el área de Terminación.

Actualmente, una vez que los materiales salen del depósito, pueden producirse cambios de ubicación, movimientos de tarimas, devoluciones incorrectas o utilización temporal en otros transformadores. Esto provoca que los operarios deban invertir tiempo buscando materiales y aumenta el riesgo de faltantes cruzados o montajes incorrectos.

Para abordar este problema, el sistema permitirá conocer la última ubicación registrada de cada material y conservar un historial de los movimientos realizados.

Cada transformador será identificado mediante su número real dentro del proceso productivo, por ejemplo 6674, 6682 o 6785. Además, tendrá asociada la identificación definida por el proveedor y grabada físicamente en sus materiales, que puede presentarse con formatos como UN20 o K486.

Todos los materiales correspondientes a un mismo transformador compartirán dicha identificación.

Cuando un material cambie de ubicación, el operario podrá registrar el movimiento indicando su origen, destino y cualquier observación necesaria. Como resultado, los demás operarios podrán consultar dónde se encuentra actualmente el material sin depender únicamente de información verbal o de conocer quién realizó el movimiento anterior.

También se utilizarán ubicaciones principales y temporales para representar los lugares donde pueden encontrarse los materiales durante el proceso.

Las ubicaciones podrán identificarse mediante códigos QR, permitiendo que un operario acceda rápidamente desde un dispositivo móvil a la información correspondiente y registre o consulte movimientos.

Cuando se intente utilizar un material asociado a otro transformador, el sistema mostrará una advertencia para reducir el riesgo de faltantes cruzados.

De esta manera, la solución busca:

- Reducir el tiempo empleado en localizar materiales.
- Mantener actualizada su ubicación.
- Conservar la trazabilidad de los movimientos.
- Evitar confusiones entre materiales pertenecientes a diferentes transformadores.
- Facilitar la continuidad del trabajo entre distintos operarios y turnos.

La solución será implementada mediante una aplicación web accesible desde los dispositivos autorizados conectados a la red interna.

La elección de una aplicación web se encuentra documentada en el [ADR-001 — Aplicación web](adr/ADR-001-arquitectura-web.md).

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
- Transformadores y sus identificaciones de proveedor.
- Materiales asociados a cada transformador.
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
- Registro de transformadores mediante su número identificador.
- Registro de la identificación del proveedor asociada a cada transformador.
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

La relación entre las funcionalidades incluidas en el alcance, los requisitos, los casos de uso y las reglas de negocio se encuentra documentada en la [Matriz de trazabilidad](trazabilidad.md).

## Análisis de viabilidad

### Viabilidad técnica

El proyecto es técnicamente viable porque utilizará tecnologías conocidas por los integrantes: Java, Spring Boot, Spring Data JPA, PostgreSQL, HTML, CSS y JavaScript.

La aplicación podrá ejecutarse dentro de la infraestructura interna de la empresa y utilizarse desde los navegadores de las computadoras y dispositivos móviles autorizados.

El relevamiento inicial confirmó que el área posee cobertura Wi-Fi y que los dispositivos autorizados podrán acceder mediante la red interna.

La infraestructura exacta donde se ejecutarán el backend y la base de datos deberá validarse con el área de Sistemas antes del despliegue definitivo.

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

Además, podrá ejecutarse dentro de la infraestructura interna disponible en la fábrica sin depender de una conexión permanente a Internet.

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

Los dispositivos autorizados accederán al sistema mediante la red interna de la fábrica, evitando que el funcionamiento habitual dependa de una conexión permanente a Internet.

Inicialmente se había considerado utilizar una computadora ubicada en el área de Terminación como equipo servidor. Sin embargo, al encontrarse dentro del área productiva, este equipo puede estar más expuesto a interrupciones, fallas físicas o condiciones propias del entorno industrial.

Por este motivo, se evaluará junto con el área de Sistemas la posibilidad de alojar la aplicación y la base de datos en un servidor interno dedicado, datacenter u otra infraestructura equivalente disponible dentro de la empresa.

Esta alternativa permitiría mantener el sistema dentro de la red interna y, al mismo tiempo, separar el servidor de los equipos utilizados directamente en planta.

En caso de que la empresa no disponga de dicha infraestructura para la etapa inicial, podrá utilizarse una computadora dedicada como alternativa para realizar el piloto, manteniendo las copias de seguridad en un equipo o servidor diferente.

La decisión definitiva dependerá de la infraestructura que confirme el área de Sistemas.

El despliegue local originalmente considerado se encuentra documentado en el [ADR-005 — Despliegue web local](adr/ADR-005-despliegue-web-local.md). En caso de modificarse la decisión definitiva de infraestructura, se registrará mediante un nuevo ADR.

## Relevamiento de infraestructura

Se realizó un relevamiento inicial de la infraestructura necesaria para determinar la viabilidad del despliegue local del sistema.

El área de Terminación cuenta con cobertura Wi-Fi y los celulares de los operarios podrán conectarse a la red interna para acceder a la aplicación.

Se confirmó que la red interna continuará funcionando cuando la planta opere mediante generadores.

También estará permitida la utilización de las tecnologías necesarias para el proyecto, incluyendo Java, PostgreSQL y la aplicación web.

Para el despliegue definitivo se deberá validar con el área de Sistemas si existe un servidor interno, datacenter u otra infraestructura dedicada donde puedan alojarse el backend y la base de datos.

El orden de preferencia para el despliegue será:

1. Servidor interno o infraestructura dedicada administrada por Sistemas.
2. En caso de no encontrarse disponible, equipo dedicado para el piloto dentro de la red local.

Los dispositivos de los operarios no almacenarán directamente la información del sistema, sino que accederán a ella mediante la aplicación web.

Las copias de seguridad deberán ejecutarse automáticamente y almacenarse en un equipo o servidor diferente del que aloje la aplicación y la base de datos.

Un administrador designado será responsable de verificar el funcionamiento de la aplicación y la correcta ejecución de las copias de seguridad.

Las características técnicas definitivas del servidor o equipo utilizado se establecerán una vez confirmada la infraestructura disponible por parte de Sistemas.

## Riesgos y medidas de mitigación

| Riesgo | Tipo | Medida de mitigación |
|---|---|---|
| Interrupción de la conexión Wi-Fi | Implementación de la solución | Controlar la estabilidad de la red y evaluar una conexión por cable en los puntos necesarios. |
| Falla del equipo o servidor donde se ejecuta la aplicación | Implementación de la solución | Utilizar infraestructura interna protegida cuando esté disponible y mantener copias de seguridad en un equipo diferente. |
| Fallas no detectadas en las copias de seguridad | Implementación de la solución | Designar un responsable y verificar periódicamente la correcta generación y recuperación de los respaldos. |
| Movimientos no registrados por los operarios | Implementación de la solución | Diseñar un proceso de registro simple y rápido, con formularios que requieran la menor cantidad posible de pasos. |
| Intervención de operarios de diferentes turnos | Implementación de la solución | Permitir que cualquier operario habilitado pueda continuar registrando movimientos y conservar quién realizó cada operación. |
| Uso de materiales correspondientes a otro transformador | Implementación de la solución | Mostrar una advertencia antes de confirmar la utilización o movimiento del material. |
| Reubicación de tarimas o ubicaciones temporales | Implementación de la solución | Identificar las ubicaciones y permitir registrar los traslados realizados. |
| Resistencia de los usuarios al uso del sistema | Proyecto | Diseñar interfaces simples, realizar una prueba piloto y considerar la devolución de los operarios. |
| Demoras en la validación de infraestructura con Sistemas | Proyecto | Realizar la consulta con anticipación y mantener una alternativa de despliegue para el piloto. |
| Ampliación excesiva del alcance durante el desarrollo | Proyecto | Mantener la primera versión enfocada en Terminación y registrar nuevas funcionalidades como trabajo futuro. |

Los movimientos no dependerán de que el mismo operario realice todos los registros.

Cualquier operario habilitado podrá registrar el ingreso, traslado interno, devolución a depósito o pase a despacho de un material.

El sistema almacenará el usuario que realizó cada registro, junto con la fecha, la hora, el origen, el destino y las observaciones correspondientes.

De esta manera, será posible mantener la trazabilidad aunque intervengan operarios de diferentes turnos.

## Integrantes

- Enzo Chavez.
- Michael Chiappone.

## Tutor

- Santiago Fonzo.