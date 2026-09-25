# Casos de Uso

## Índice

- [Actores](#actores)
- [CU-01 — Iniciar sesión](#cu-01--iniciar-sesión)
- [CU-02 — Gestionar usuarios](#cu-02--gestionar-usuarios)
- [CU-03 — Gestionar ubicaciones](#cu-03--gestionar-ubicaciones)
- [CU-04 — Gestionar transformadores](#cu-04--gestionar-transformadores)
- [CU-05 — Registrar material](#cu-05--registrar-material)
- [CU-06 — Consultar transformador y materiales](#cu-06--consultar-transformador-y-materiales)
- [CU-07 — Consultar ubicación de un material](#cu-07--consultar-ubicación-de-un-material)
- [CU-08 — Registrar movimiento](#cu-08--registrar-movimiento)
- [CU-09 — Consultar historial de movimientos](#cu-09--consultar-historial-de-movimientos)
- [CU-10 — Registrar observación](#cu-10--registrar-observación)
- [CU-11 — Escanear QR de ubicación](#cu-11--escanear-qr-de-ubicación)
- [CU-12 — Advertir material de otro transformador](#cu-12--advertir-material-de-otro-transformador)

## Actores

### Administrador

Usuario responsable de administrar la información principal y configuración del sistema.

### Operario

Usuario que consulta información y registra movimientos durante el proceso productivo.

## CU-01 — Iniciar sesión

**Actor principal:** Administrador u Operario.

**Objetivo:** Permitir que un usuario habilitado acceda al sistema con su identidad y rol correspondiente.

**Precondiciones:**

- El usuario debe encontrarse registrado y habilitado.

**Flujo principal:**

1. El usuario accede a la aplicación.
2. El sistema solicita sus credenciales.
3. El usuario ingresa los datos requeridos.
4. El sistema valida las credenciales.
5. El sistema identifica el rol del usuario.
6. El sistema permite el acceso a las funciones correspondientes.

**Flujo alternativo:**

- Si las credenciales son incorrectas, el sistema informa que no fue posible iniciar sesión.

**Postcondición:**

- El usuario queda identificado dentro del sistema.

### Criterios de aceptación

- Dado un usuario registrado y habilitado, cuando ingresa credenciales válidas, entonces el sistema permite el acceso.
- Dadas credenciales inválidas, cuando se intenta iniciar sesión, entonces el sistema rechaza el acceso.
- Dado un usuario autenticado, el sistema deberá aplicar los permisos correspondientes a su rol.

## CU-02 — Gestionar usuarios

**Actor principal:** Administrador.

**Objetivo:** Registrar y administrar los usuarios habilitados para utilizar el sistema.

**Precondiciones:**

- El administrador debe haber iniciado sesión.

**Flujo principal:**

1. El administrador accede a la gestión de usuarios.
2. El sistema muestra los usuarios registrados.
3. El administrador selecciona la operación que desea realizar.
4. El administrador completa o modifica los datos.
5. El sistema valida la información.
6. El sistema guarda los cambios.

**Postcondición:**

- La información del usuario queda actualizada.

### Criterios de aceptación

- Solo los usuarios con rol de administrador podrán acceder a la gestión de usuarios.
- Los usuarios creados deberán quedar asociados a un rol.
- El sistema deberá impedir guardar un usuario cuando falten datos obligatorios.

## CU-03 — Gestionar ubicaciones

**Actor principal:** Administrador.

**Objetivo:** Registrar y administrar las ubicaciones físicas utilizadas para la trazabilidad.

**Precondiciones:**

- El administrador debe haber iniciado sesión.

**Flujo principal:**

1. El administrador accede a la gestión de ubicaciones.
2. El sistema muestra las ubicaciones registradas.
3. El administrador registra o modifica una ubicación.
4. El sistema valida la información.
5. El sistema guarda los cambios.

**Postcondición:**

- La ubicación queda disponible para ser utilizada en los movimientos de materiales.

### Criterios de aceptación

- Cada ubicación deberá poder identificarse de forma inequívoca dentro del sistema.
- Las ubicaciones deberán poder asociarse al área correspondiente.
- Solo un administrador podrá gestionar ubicaciones.

## CU-04 — Gestionar transformadores

**Actor principal:** Administrador.

**Objetivo:** Registrar y mantener actualizados los transformadores utilizados en el proceso.

**Precondiciones:**

- El administrador debe haber iniciado sesión.

**Flujo principal:**

1. El administrador accede a la gestión de transformadores.
2. El sistema muestra los transformadores registrados.
3. El administrador registra o modifica un transformador.
4. El sistema valida su código identificador.
5. El sistema guarda los cambios.

**Postcondición:**

- El transformador queda disponible para asociar materiales.

### Criterios de aceptación

- Cada transformador deberá contar con un código identificador.
- El sistema deberá permitir consultar sus materiales asociados.
- Solo un administrador podrá registrar o modificar transformadores.

## CU-05 — Registrar material

**Actor principal:** Administrador.

**Objetivo:** Registrar un material y asociarlo con el transformador al cual corresponde.

**Precondiciones:**

- El administrador debe haber iniciado sesión.
- El transformador debe encontrarse registrado.

**Flujo principal:**

1. El administrador selecciona la opción para registrar un material.
2. El sistema solicita los datos del material.
3. El administrador ingresa su descripción o tipo.
4. El administrador registra la identificación UN grabada físicamente en el material.
5. El administrador selecciona el transformador correspondiente.
6. El sistema valida los datos.
7. El sistema registra el material.

**Postcondición:**

- El material queda registrado y asociado al transformador seleccionado.

### Criterios de aceptación

- El sistema no deberá generar automáticamente la identificación UN.
- La UN registrada deberá corresponder al dato ingresado por el administrador.
- El material deberá quedar asociado a un transformador.
- No deberá permitirse guardar el material cuando falten datos obligatorios.

## CU-06 — Consultar transformador y materiales

**Actor principal:** Administrador u Operario.

**Objetivo:** Consultar los materiales correspondientes a un transformador.

**Precondiciones:**

- El usuario debe encontrarse identificado en el sistema.
- El transformador debe estar registrado.

**Flujo principal:**

1. El usuario accede al listado de transformadores.
2. El sistema muestra los transformadores disponibles.
3. El usuario selecciona un transformador.
4. El sistema muestra los materiales asociados.
5. El sistema muestra la ubicación actual conocida de cada material.

**Postcondición:**

- No se modifica información.

### Criterios de aceptación

- El sistema deberá mostrar los materiales asociados al transformador seleccionado.
- Para cada material deberá mostrarse su ubicación actual conocida.
- La consulta deberá estar disponible para administradores y operarios.

## CU-07 — Consultar ubicación de un material

**Actor principal:** Administrador u Operario.

**Objetivo:** Conocer rápidamente la ubicación actual de un material.

**Precondiciones:**

- El material debe encontrarse registrado.

**Flujo principal:**

1. El usuario busca o selecciona el material.
2. El sistema identifica el material.
3. El sistema consulta su ubicación actual.
4. El sistema muestra la ubicación al usuario.

**Postcondición:**

- No se modifica información.

### Criterios de aceptación

- El sistema deberá mostrar la última ubicación registrada del material.
- La consulta deberá poder realizarse desde una computadora o dispositivo móvil conectado a la red interna.
- La operación deberá poder completarse en menos de dos minutos en condiciones normales de funcionamiento.

## CU-08 — Registrar movimiento

**Actor principal:** Operario.

**Objetivo:** Registrar el cambio de ubicación de un material.

**Precondiciones:**

- El operario debe estar identificado.
- El material debe estar registrado.
- La ubicación de destino debe existir en el sistema.

**Flujo principal:**

1. El operario selecciona el material.
2. El sistema muestra su ubicación actual.
3. El operario selecciona el tipo de movimiento.
4. El operario indica la ubicación de destino.
5. El operario puede agregar una observación.
6. El sistema muestra los datos del movimiento.
7. El operario confirma la operación.
8. El sistema registra el movimiento.
9. El sistema actualiza la ubicación actual del material.
10. El movimiento queda incorporado al historial.

**Flujos alternativos:**

- Si falta información obligatoria, el sistema no registra el movimiento e informa qué dato debe completarse.
- Si el material corresponde a otro transformador, se ejecuta el caso de uso CU-12.

**Postcondiciones:**

- El movimiento queda registrado.
- La ubicación actual del material queda actualizada.
- El historial conserva el movimiento realizado.

### Criterios de aceptación

- Cada movimiento deberá registrar material, origen, destino, usuario, fecha y hora.
- Al confirmar un movimiento válido, la ubicación actual deberá coincidir con el destino.
- El movimiento deberá aparecer en el historial.
- Un operario diferente al que realizó el movimiento anterior deberá poder registrar el siguiente.
- Una observación podrá incluirse de forma opcional.

## CU-09 — Consultar historial de movimientos

**Actor principal:** Administrador u Operario.

**Objetivo:** Consultar los movimientos registrados de un material.

**Precondiciones:**

- El material debe encontrarse registrado.

**Flujo principal:**

1. El usuario selecciona un material.
2. El usuario solicita consultar su historial.
3. El sistema recupera los movimientos registrados.
4. El sistema muestra la información ordenada cronológicamente.

**Postcondición:**

- No se modifica información.

### Criterios de aceptación

- Cada registro deberá mostrar origen y destino.
- Deberá mostrar fecha y hora.
- Deberá identificar al usuario que registró el movimiento.
- Deberá mostrar la observación cuando exista.
- Los movimientos anteriores deberán conservarse aunque el material cambie nuevamente de ubicación.

## CU-10 — Registrar observación

**Actor principal:** Administrador u Operario.

**Objetivo:** Agregar información adicional relacionada con un material o movimiento.

**Precondiciones:**

- El usuario debe estar identificado.
- El material debe estar registrado.

**Flujo principal:**

1. El usuario selecciona el material o movimiento correspondiente.
2. El usuario escribe una observación.
3. El sistema registra la observación.
4. La observación queda disponible para futuras consultas.

**Postcondición:**

- La observación queda almacenada.

### Criterios de aceptación

- La observación deberá permitir texto libre.
- No será obligatorio seleccionar un motivo predefinido.
- El sistema deberá conservar el usuario relacionado con el registro cuando corresponda.

## CU-11 — Escanear QR de ubicación

**Actor principal:** Operario.

**Objetivo:** Identificar rápidamente una ubicación física mediante un código QR.

**Precondiciones:**

- La ubicación debe estar registrada.
- Debe existir un código QR asociado a la ubicación.
- El dispositivo debe tener acceso a la aplicación mediante la red interna.

**Flujo principal:**

1. El operario escanea el código QR.
2. El sistema identifica la ubicación asociada.
3. El sistema muestra la información de la ubicación.
4. El operario puede consultar los materiales relacionados o iniciar el registro de un movimiento.

**Postcondición:**

- No se modifica información hasta que el usuario confirme alguna operación posterior.

### Criterios de aceptación

- Cada QR deberá identificar una ubicación y no un material individual.
- El sistema deberá mostrar la ubicación correspondiente al código escaneado.
- El usuario deberá poder continuar desde esa ubicación hacia las funciones disponibles.

## CU-12 — Advertir material de otro transformador

**Actor principal:** Operario.

**Objetivo:** Evitar que un material correspondiente a un transformador sea utilizado inadvertidamente en otro.

**Precondiciones:**

- El material debe estar registrado.
- El material debe estar asociado a un transformador.

**Flujo principal:**

1. El operario intenta registrar una operación relacionada con un transformador.
2. El sistema verifica el transformador asociado al material.
3. El sistema detecta que no coincide con el transformador indicado.
4. El sistema muestra una advertencia al operario.
5. El operario revisa la información antes de continuar.

**Postcondición:**

- El usuario recibe información sobre la inconsistencia antes de confirmar la operación.

### Criterios de aceptación

- La verificación deberá realizarse antes de confirmar la operación.
- La advertencia deberá identificar que el material corresponde a otro transformador.
- El sistema no deberá modificar automáticamente la asociación original del material.