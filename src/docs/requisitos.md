# Requisitos del Sistema

## Índice

- [Introducción](#introducción)
- [Actores del sistema](#actores-del-sistema)
- [Requisitos funcionales](#requisitos-funcionales)
- [Requisitos no funcionales](#requisitos-no-funcionales)
- [Reglas de negocio](#reglas-de-negocio)

## Introducción

Este documento define los requisitos funcionales y no funcionales de la primera versión del sistema web de trazabilidad de materiales.

La primera versión estará orientada al área de Terminación y tendrá como objetivo registrar y consultar materiales asociados a transformadores, sus ubicaciones y los movimientos realizados durante el proceso productivo.

El sistema estará diseñado para poder extenderse posteriormente a otras áreas productivas.

## Actores del sistema

### Administrador

Usuario responsable de la configuración y administración general del sistema.

Podrá gestionar:

- Usuarios.
- Áreas.
- Ubicaciones.
- Transformadores.
- Materiales.

### Operario

Usuario que utilizará el sistema durante las tareas habituales del área productiva.

Podrá:

- Consultar transformadores.
- Consultar materiales.
- Consultar ubicaciones.
- Registrar movimientos.
- Registrar observaciones.
- Consultar historiales.
- Utilizar códigos QR asociados a ubicaciones.

## Requisitos funcionales

### RF-01 — Identificación de usuarios

El sistema deberá permitir identificar a los usuarios que realizan operaciones para registrar quién efectuó cada movimiento o modificación relevante.

### RF-02 — Gestión de usuarios

El administrador deberá poder registrar y gestionar los usuarios habilitados para utilizar el sistema.

### RF-03 — Roles de usuario

El sistema deberá distinguir al menos dos roles:

- Administrador.
- Operario.

Las acciones disponibles dependerán del rol asignado.

### RF-04 — Gestión de áreas

El administrador deberá poder registrar y gestionar las áreas productivas en las que podrá utilizarse el sistema.

La primera implementación utilizará el área de Terminación.

### RF-05 — Gestión de ubicaciones

El administrador deberá poder registrar y gestionar ubicaciones físicas dentro de las áreas productivas.

Las ubicaciones podrán utilizarse como ubicaciones principales o temporales para los materiales.

### RF-06 — Gestión de transformadores

El administrador deberá poder registrar y gestionar los transformadores que se encuentren activos dentro del proceso productivo.

Cada transformador deberá contar con un código identificador.

### RF-07 — Registro de materiales

El administrador deberá poder registrar los materiales que serán controlados mediante el sistema.

Para cada material se deberá poder registrar, como mínimo:

- Tipo o descripción.
- Identificación UN.
- Transformador asociado.

La identificación UN deberá corresponder a la identificación que el material ya posee físicamente según el estándar del proveedor.

El sistema no deberá generar ni asignar automáticamente números UN.

### RF-08 — Asociación entre materiales y transformadores

El sistema deberá permitir asociar cada material con el transformador al cual corresponde.

Esta asociación será utilizada para mantener la trazabilidad y detectar posibles usos de materiales correspondientes a otro transformador.

### RF-09 — Consulta de transformadores y materiales

El sistema deberá permitir consultar los transformadores activos y visualizar los materiales asociados a cada uno.

Para cada material deberá mostrarse su ubicación actual conocida.

### RF-10 — Consulta de ubicación actual

El sistema deberá permitir consultar la ubicación actual de un material.

### RF-11 — Registro de movimientos

El sistema deberá permitir registrar movimientos de materiales.

Como mínimo deberán contemplarse los siguientes tipos:

- Ingreso.
- Traslado interno.
- Devolución a depósito.
- Pase a despacho.

### RF-12 — Información del movimiento

Cada movimiento deberá registrar:

- Material involucrado.
- Transformador asociado.
- Ubicación de origen.
- Ubicación de destino.
- Usuario que realizó el registro.
- Fecha.
- Hora.
- Observación, cuando corresponda.

### RF-13 — Actualización de ubicación

Cuando se registre correctamente un movimiento, el sistema deberá actualizar la ubicación actual del material de acuerdo con el destino indicado.

### RF-14 — Registro entre diferentes turnos

El sistema no deberá exigir que el mismo operario que registró el movimiento anterior sea quien registre el siguiente.

Cualquier operario habilitado podrá continuar registrando movimientos sobre un material.

### RF-15 — Historial de movimientos

El sistema deberá conservar un historial de los movimientos realizados sobre cada material.

El historial deberá permitir consultar, como mínimo:

- Ubicación de origen.
- Ubicación de destino.
- Fecha.
- Hora.
- Usuario que realizó el registro.
- Observaciones asociadas.

### RF-16 — Registro de observaciones

Los usuarios habilitados deberán poder agregar observaciones relacionadas con un material o movimiento cuando resulte necesario.

Las observaciones serán de texto libre y no requerirán seleccionar un motivo predefinido.

### RF-17 — Advertencia por material de otro transformador

Cuando se intente utilizar o registrar un material asociado a un transformador diferente del correspondiente, el sistema deberá mostrar una advertencia antes de confirmar la operación.

### RF-18 — Ubicaciones temporales

El sistema deberá permitir registrar materiales en ubicaciones temporales cuando se encuentren separados momentáneamente de su ubicación principal.

### RF-19 — Uso de códigos QR

El sistema deberá permitir utilizar códigos QR asociados a las ubicaciones físicas.

Al escanear un código QR, el usuario deberá poder identificar la ubicación correspondiente y acceder a las funciones relacionadas con ella.

Los códigos QR no serán colocados individualmente sobre los materiales.

### RF-20 — Consulta del historial de una ubicación

El sistema deberá permitir consultar los movimientos asociados a una ubicación para conocer qué materiales fueron registrados en ella.

## Requisitos no funcionales

### RNF-01 — Aplicación web

El sistema deberá implementarse como una aplicación web.

Los dispositivos cliente no deberán requerir la instalación de una aplicación específica.

### RNF-02 — Diseño responsive

La interfaz deberá adaptarse al tamaño de pantalla del dispositivo utilizado.

Deberá poder utilizarse tanto desde computadoras como desde teléfonos celulares.

### RNF-03 — Funcionamiento en red local

La primera versión de la aplicación deberá funcionar dentro de la red interna de la fábrica.

El funcionamiento normal del sistema no deberá depender de una conexión permanente a Internet.

### RNF-04 — Compatibilidad

La aplicación deberá poder utilizarse mediante navegadores web actuales desde los dispositivos autorizados conectados a la red interna.

### RNF-05 — Usabilidad

Las operaciones habituales deberán diseñarse para requerir la menor cantidad razonable de pasos.

La interfaz deberá priorizar la simplicidad debido a que será utilizada durante el proceso productivo.

### RNF-06 — Tiempo de operación

La consulta de la ubicación de un material y el registro de un movimiento deberán poder realizarse en menos de dos minutos en condiciones normales de funcionamiento.

### RNF-07 — Persistencia

La información deberá almacenarse de forma persistente utilizando PostgreSQL.

La decisión se encuentra documentada en el [ADR-006 — PostgreSQL](adr/ADR-006-base-de-datos-postgresql.md).

### RNF-08 — Backend

El backend será desarrollado utilizando Java y Spring Boot.

La decisión se encuentra documentada en el [ADR-003 — Stack backend](adr/ADR-003-stack-backend.md).

### RNF-09 — Control de acceso

Las funcionalidades disponibles deberán limitarse según el rol del usuario.

Las operaciones administrativas deberán estar reservadas a usuarios con rol de administrador.

### RNF-10 — Trazabilidad

Los movimientos registrados deberán conservar información suficiente para identificar:

- Qué material fue movido.
- Desde qué ubicación.
- Hacia qué ubicación.
- Cuándo se realizó.
- Qué usuario realizó el registro.

### RNF-11 — Copias de seguridad

La base de datos deberá contar con copias de seguridad automáticas al menos una vez por semana.

Los respaldos deberán almacenarse en un servidor o equipo diferente de aquel donde se ejecuten la aplicación y la base de datos.

### RNF-12 — Escalabilidad funcional

Aunque la primera versión se implemente en Terminación, la estructura del sistema deberá permitir incorporar posteriormente otras áreas productivas sin requerir un rediseño completo de la aplicación.

### RNF-13 — Disponibilidad local

El sistema deberá poder utilizarse durante los turnos de trabajo mientras se encuentren disponibles el equipo servidor y la red interna.

## Reglas de negocio

### RN-01 — Identificación UN

La identificación UN es definida según el estándar del proveedor y se encuentra grabada físicamente en cada material.

El sistema únicamente registrará esa identificación.

No deberá generar ni asignar automáticamente una UN.

### RN-02 — Asociación con transformadores

Cada material deberá estar asociado al transformador al cual corresponde.

### RN-03 — Ubicación actual

Cada material tendrá una ubicación actual conocida.

Cuando se registre un nuevo movimiento, dicha ubicación deberá actualizarse con el destino registrado.

### RN-04 — Ubicaciones temporales

Un material podrá permanecer temporalmente en una ubicación diferente de la principal asignada para los materiales de su transformador.

### RN-05 — QR asociados a ubicaciones

Los códigos QR estarán asociados a ubicaciones físicas y no a materiales individuales.

### RN-06 — Operarios diferentes

Un movimiento podrá ser registrado por un operario diferente de quien realizó el movimiento anterior.

El sistema conservará el usuario correspondiente a cada registro.

### RN-07 — Advertencias entre transformadores

Cuando exista una diferencia entre el transformador asociado al material y aquel sobre el cual se intenta utilizar, el sistema deberá advertir al usuario antes de confirmar la operación.

### RN-08 — Observaciones

Las observaciones serán opcionales y podrán escribirse como texto libre.

### RN-09 — Historial

Los movimientos registrados formarán parte del historial del material y no deberán eliminarse al producirse movimientos posteriores.