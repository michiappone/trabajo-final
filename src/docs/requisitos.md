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
- Identificaciones de proveedor asociadas a transformadores.
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

El número real del transformador será utilizado como identificador único dentro del sistema.

Ejemplos:

- 6674.
- 6682.
- 6785.

No se utilizará un código adicional para identificar al transformador.

Cada transformador deberá registrar además la identificación proporcionada por el proveedor para sus materiales.

Esta identificación podrá contener letras y números, por ejemplo:

- UN20.
- UN46.
- K486.

### RF-07 — Registro de materiales

El administrador deberá poder registrar los materiales controlados mediante el sistema.

Para cada material se deberá registrar, como mínimo:

- Tipo o descripción.
- Transformador al cual pertenece.

La identificación del proveedor no deberá almacenarse de manera independiente en cada material, ya que corresponde al transformador y es compartida por todos sus materiales.

### RF-08 — Asociación entre materiales y transformadores

Cada material deberá estar asociado a un transformador.

A partir de esta asociación será posible conocer también la identificación del proveedor correspondiente al material.

### RF-09 — Consulta de transformadores y materiales

El sistema deberá permitir consultar los transformadores activos y visualizar los materiales asociados a cada uno.

La consulta deberá mostrar:

- Número del transformador.
- Identificación del proveedor.
- Materiales asociados.
- Ubicación actual conocida de cada material.

### RF-10 — Consulta de ubicación actual

El sistema deberá permitir consultar la ubicación actual de un material.

Si el material todavía no posee una ubicación registrada, el sistema deberá indicar que no existe una ubicación actual conocida.

### RF-11 — Registro de movimientos

El sistema deberá permitir registrar movimientos de materiales.

Como mínimo deberán contemplarse:

- Ingreso.
- Traslado interno.
- Devolución a depósito.
- Pase a despacho.

### RF-12 — Información del movimiento

Cada movimiento deberá registrar:

- Material involucrado.
- Transformador asociado.
- Ubicación de origen, cuando corresponda.
- Ubicación de destino.
- Usuario que realizó el registro.
- Fecha.
- Hora.
- Observación, cuando corresponda.

### RF-13 — Actualización de ubicación

Cuando se registre correctamente un movimiento, el sistema deberá actualizar la ubicación actual del material con la ubicación de destino.

### RF-14 — Registro entre diferentes turnos

El sistema no deberá exigir que el mismo operario que registró el movimiento anterior sea quien registre el siguiente.

Cualquier operario habilitado podrá continuar registrando movimientos sobre un material.

### RF-15 — Historial de movimientos

El sistema deberá conservar un historial de los movimientos realizados sobre cada material.

El historial deberá permitir consultar:

- Ubicación de origen.
- Ubicación de destino.
- Fecha.
- Hora.
- Usuario.
- Observaciones asociadas.

### RF-16 — Registro de observaciones

Los usuarios habilitados deberán poder agregar observaciones relacionadas con un material o movimiento.

Las observaciones serán de texto libre.

### RF-17 — Advertencia por material de otro transformador

Cuando se intente utilizar un material asociado a un transformador diferente del correspondiente, el sistema deberá mostrar una advertencia antes de confirmar la operación.

### RF-18 — Ubicaciones temporales

El sistema deberá permitir registrar materiales en ubicaciones temporales cuando se encuentren separados momentáneamente de la ubicación principal correspondiente a su transformador.

### RF-19 — Uso de códigos QR

El sistema deberá permitir utilizar códigos QR asociados a ubicaciones físicas.

Al escanear un código QR, el usuario deberá poder identificar la ubicación correspondiente y acceder a las funciones relacionadas con ella.

Los códigos QR no estarán asociados individualmente a los materiales.

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

La primera versión deberá funcionar dentro de la red interna de la fábrica.

El funcionamiento normal no deberá depender de una conexión permanente a Internet.

### RNF-04 — Compatibilidad

La aplicación deberá poder utilizarse mediante navegadores web actuales desde los dispositivos autorizados conectados a la red interna.

### RNF-05 — Usabilidad

Las operaciones habituales deberán diseñarse para requerir la menor cantidad razonable de pasos.

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

### RNF-10 — Trazabilidad

Los movimientos deberán conservar información suficiente para identificar qué material fue movido, desde dónde, hacia dónde, cuándo y por qué usuario.

### RNF-11 — Copias de seguridad

La base de datos deberá contar con copias de seguridad automáticas al menos una vez por semana.

Los respaldos deberán almacenarse en un equipo o servidor diferente del equipo principal.

### RNF-12 — Escalabilidad funcional

Aunque la primera versión se implemente en Terminación, la estructura deberá permitir incorporar posteriormente otras áreas productivas.

### RNF-13 — Disponibilidad local

El sistema deberá poder utilizarse durante los turnos de trabajo mientras se encuentren disponibles el equipo servidor y la red interna.

## Reglas de negocio

### RN-01 — Identificador del transformador

El número real del transformador será utilizado como su identificador único dentro del sistema.

No se utilizará un identificador técnico adicional para representar al transformador.

### RN-02 — Identificación del proveedor

Cada transformador tendrá asociada una única identificación proporcionada por el proveedor.

La identificación podrá ser alfanumérica y se almacenará como texto.

Ejemplos:

- UN20.
- UN46.
- K486.

### RN-03 — Identificación compartida por los materiales

Todos los materiales pertenecientes a un mismo transformador comparten la identificación del proveedor asociada a dicho transformador.

Por este motivo, la identificación no deberá almacenarse repetidamente en cada material.

### RN-04 — Asociación con transformadores

Cada material deberá estar asociado a un único transformador.

### RN-05 — Ubicación actual

Cada material podrá tener cero o una ubicación actual registrada.

Un material podrá no tener una ubicación conocida hasta que se registre su primer movimiento.

Cuando se registre un nuevo movimiento, la ubicación actual deberá actualizarse con el destino registrado.

### RN-06 — Ubicaciones temporales

Un material podrá permanecer temporalmente en una ubicación diferente de la ubicación principal correspondiente a su transformador.

### RN-07 — QR asociados a ubicaciones

Los códigos QR estarán asociados a ubicaciones físicas y no a materiales individuales.

### RN-08 — Operarios diferentes

Un movimiento podrá ser registrado por un operario diferente de quien realizó el movimiento anterior.

### RN-09 — Advertencias entre transformadores

Cuando exista una diferencia entre el transformador asociado al material y aquel sobre el cual se intenta utilizar, el sistema deberá advertir al usuario antes de confirmar la operación.

### RN-10 — Observaciones

Las observaciones serán opcionales y podrán escribirse como texto libre.

### RN-11 — Historial

Los movimientos registrados formarán parte del historial del material y deberán conservarse aunque posteriormente cambie su ubicación.