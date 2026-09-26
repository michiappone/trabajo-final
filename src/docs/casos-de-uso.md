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

Usuario responsable de administrar la información principal y la configuración del sistema.

### Operario

Usuario que consulta información y registra movimientos durante el proceso productivo.

## CU-01 — Iniciar sesión

**Actor principal:** Administrador u Operario.

**Objetivo:** Permitir que un usuario habilitado acceda al sistema.

**Precondición:**

El usuario debe encontrarse registrado y habilitado.

**Flujo principal:**

1. El usuario accede a la aplicación.
2. El sistema solicita sus credenciales.
3. El usuario ingresa los datos.
4. El sistema valida las credenciales.
5. El sistema identifica el rol.
6. El sistema permite el acceso.

### Criterios de aceptación

- Un usuario habilitado con credenciales válidas deberá poder ingresar.
- Las credenciales inválidas deberán ser rechazadas.
- Las funcionalidades disponibles dependerán del rol.

## CU-02 — Gestionar usuarios

**Actor principal:** Administrador.

**Objetivo:** Registrar y administrar usuarios.

### Criterios de aceptación

- Solo un administrador podrá gestionar usuarios.
- Todo usuario deberá poseer un rol.
- No se podrán guardar usuarios si faltan datos obligatorios.

## CU-03 — Gestionar ubicaciones

**Actor principal:** Administrador.

**Objetivo:** Registrar y administrar ubicaciones físicas.

**Flujo principal:**

1. El administrador accede a la gestión de ubicaciones.
2. Registra o modifica una ubicación.
3. El sistema valida los datos.
4. El sistema guarda la información.

### Criterios de aceptación

- Cada ubicación deberá poder identificarse dentro del sistema.
- Cada ubicación deberá pertenecer a un área.
- Solo el administrador podrá gestionar ubicaciones.

## CU-04 — Gestionar transformadores

**Actor principal:** Administrador.

**Objetivo:** Registrar y mantener actualizados los transformadores utilizados en el proceso.

**Precondición:**

El administrador debe haber iniciado sesión.

**Flujo principal:**

1. El administrador accede a la gestión de transformadores.
2. El sistema muestra los transformadores registrados.
3. El administrador selecciona registrar un nuevo transformador.
4. Ingresa el número real del transformador, por ejemplo 6682.
5. Ingresa la identificación proporcionada por el proveedor, por ejemplo UN20 o K486.
6. Selecciona la ubicación principal correspondiente.
7. El sistema valida los datos.
8. El sistema registra el transformador.

**Postcondición:**

El transformador queda disponible para asociar materiales.

### Criterios de aceptación

- El número real del transformador deberá utilizarse como identificador.
- No deberá existir más de un transformador con el mismo número.
- Cada transformador deberá tener una identificación de proveedor asociada.
- La identificación del proveedor deberá almacenarse como texto.
- La identificación del proveedor deberá ser única para cada transformador.
- No se deberá generar automáticamente dicha identificación.

## CU-05 — Registrar material

**Actor principal:** Administrador.

**Objetivo:** Registrar un material y asociarlo con el transformador al cual pertenece.

**Precondiciones:**

- El administrador debe haber iniciado sesión.
- El transformador debe estar registrado.

**Flujo principal:**

1. El administrador selecciona la opción para registrar un material.
2. El sistema solicita los datos del material.
3. El administrador ingresa el tipo o descripción.
4. El administrador selecciona el transformador correspondiente.
5. El sistema muestra la identificación del proveedor asociada a ese transformador.
6. El sistema valida los datos.
7. El sistema registra el material.

**Postcondición:**

El material queda asociado al transformador seleccionado.

### Criterios de aceptación

- Todo material deberá pertenecer a un transformador.
- La identificación del proveedor no deberá ingresarse nuevamente para cada material.
- La identificación deberá obtenerse a partir del transformador asociado.
- No deberá permitirse guardar un material cuando falten datos obligatorios.

## CU-06 — Consultar transformador y materiales

**Actor principal:** Administrador u Operario.

**Objetivo:** Consultar los materiales correspondientes a un transformador.

**Flujo principal:**

1. El usuario accede al listado de transformadores.
2. Selecciona un transformador.
3. El sistema muestra su número identificador.
4. El sistema muestra su identificación de proveedor.
5. El sistema muestra los materiales asociados.
6. Para cada material muestra su ubicación actual conocida.

### Criterios de aceptación

- Deberá mostrarse el número del transformador.
- Deberá mostrarse la identificación del proveedor.
- Deberán mostrarse los materiales asociados.
- Cada material deberá mostrar su ubicación actual conocida.

## CU-07 — Consultar ubicación de un material

**Actor principal:** Administrador u Operario.

**Objetivo:** Conocer la ubicación actual de un material.

**Flujo principal:**

1. El usuario selecciona o busca el material.
2. El sistema identifica el material.
3. El sistema consulta su ubicación actual.
4. El sistema muestra la ubicación.

### Criterios de aceptación

- Si el material posee una ubicación actual registrada, el sistema deberá mostrarla.
- Si todavía no posee una ubicación registrada, el sistema deberá informar que no existe una ubicación actual conocida.
- La consulta deberá poder realizarse desde PC o celular conectado a la red interna.
- La operación deberá poder completarse en menos de dos minutos en condiciones normales.

## CU-08 — Registrar movimiento

**Actor principal:** Operario.

**Objetivo:** Registrar el cambio de ubicación de un material.

**Precondiciones:**

- El operario debe estar identificado.
- El material debe estar registrado.
- La ubicación de destino debe existir.

**Flujo principal:**

1. El operario selecciona el material.
2. El sistema muestra el transformador al que pertenece.
3. El sistema muestra su ubicación actual.
4. El operario selecciona el tipo de movimiento.
5. Indica la ubicación de destino.
6. Puede agregar una observación.
7. El sistema valida la operación.
8. El operario confirma.
9. El sistema registra el movimiento.
10. El sistema actualiza la ubicación actual del material.
11. El movimiento queda incorporado al historial.

### Criterios de aceptación

- Cada movimiento deberá registrar material, origen cuando corresponda, destino, usuario, fecha y hora.
- La ubicación actual deberá actualizarse con el destino.
- El movimiento deberá conservarse en el historial.
- Un operario diferente podrá registrar el movimiento siguiente.

## CU-09 — Consultar historial de movimientos

**Actor principal:** Administrador u Operario.

**Objetivo:** Consultar los movimientos realizados sobre un material.

### Criterios de aceptación

- Cada movimiento deberá mostrar origen y destino.
- Deberá mostrar fecha y hora.
- Deberá identificar al usuario que realizó el registro.
- Deberá mostrar observaciones cuando existan.
- Los movimientos anteriores deberán conservarse.

## CU-10 — Registrar observación

**Actor principal:** Administrador u Operario.

**Objetivo:** Registrar información adicional relacionada con un material o movimiento.

### Criterios de aceptación

- La observación deberá aceptar texto libre.
- No será obligatorio seleccionar un motivo predefinido.
- La observación deberá conservar el usuario que realizó el registro.

## CU-11 — Escanear QR de ubicación

**Actor principal:** Operario.

**Objetivo:** Identificar una ubicación física mediante un código QR.

**Flujo principal:**

1. El operario escanea el código QR.
2. El sistema identifica la ubicación.
3. El sistema muestra la información correspondiente.
4. El operario puede consultar materiales o iniciar un movimiento.

### Criterios de aceptación

- Cada QR deberá identificar una ubicación.
- Los QR no deberán identificar materiales individuales.
- El sistema deberá mostrar la ubicación correspondiente.

## CU-12 — Advertir material de otro transformador

**Actor principal:** Operario.

**Objetivo:** Evitar el uso inadvertido de un material correspondiente a otro transformador.

**Flujo principal:**

1. El operario intenta registrar una operación para un transformador.
2. El sistema consulta a qué transformador pertenece el material.
3. El sistema compara ambos transformadores.
4. Si son diferentes, muestra una advertencia.
5. El operario revisa la información antes de continuar.

### Criterios de aceptación

- La comparación deberá utilizar el identificador real del transformador.
- La advertencia deberá mostrarse antes de confirmar la operación.
- El sistema no deberá modificar automáticamente la asociación original del material.