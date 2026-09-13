# ADR-005 — Despliegue web en red local

## Estado

Aceptado

## Fecha

13/09/2026

## Contexto

El sistema de trazabilidad debe utilizarse desde computadoras y celulares dentro del área de Terminación.

La conexión a Internet de la planta puede ser inestable, por lo que depender de un servicio online podría impedir el acceso al sistema durante la jornada laboral.

El relevamiento de infraestructura confirmó que el área de Terminación cuenta con cobertura Wi-Fi estable, que los celulares pueden conectarse a la red interna y que esta continúa funcionando cuando la planta opera mediante generadores.

La empresa deberá proporcionar una computadora con componentes adecuados para ejecutar la aplicación. El equipo estará ubicado en Terminación, podrá permanecer encendido durante todos los turnos y será administrado por una persona designada.

Esta decisión complementa al ADR-001, en el cual se estableció que el sistema será una aplicación web responsive.

## Alternativas consideradas

### Opción 1 — Despliegue en un servicio online

Ventajas:

- Permite acceder desde cualquier ubicación con conexión a Internet.
- El proveedor puede encargarse de parte de la infraestructura.
- Facilita el acceso remoto para mantenimiento.

Desventajas:

- Depende de una conexión estable a Internet.
- Una interrupción de Internet impediría utilizar el sistema.
- Puede generar costos de alojamiento.
- Requiere evaluar restricciones de seguridad y acceso a información interna.

### Opción 2 — Despliegue en la red local de la fábrica

Ventajas:

- No requiere una conexión permanente a Internet.
- Permite acceder desde computadoras y celulares conectados a la red interna.
- La red continúa funcionando cuando la planta utiliza generadores.
- La información permanece dentro de la infraestructura de la empresa.

Desventajas:

- La empresa debe proporcionar y mantener el equipo.
- El funcionamiento depende de que la computadora permanezca encendida.
- La conexión Wi-Fi debe mantenerse estable.
- Se debe designar una persona responsable de administrar el equipo y controlar las copias de seguridad.

## Decisión

La aplicación web se desplegará en una computadora proporcionada por la empresa y ubicada en el área de Terminación.

Los usuarios accederán mediante un navegador desde computadoras y celulares conectados a la red interna por Wi-Fi.

La computadora permanecerá encendida durante los turnos de trabajo. Un administrador designado será responsable de mantenerla en funcionamiento y verificar la ejecución de las copias de seguridad.

Los respaldos se realizarán automáticamente una vez por semana y se almacenarán en un servidor local diferente del equipo principal.

## Justificación

El despliegue en la red local permite utilizar el sistema sin depender de la conexión a Internet y aprovecha la infraestructura disponible en el área de Terminación.

Esta alternativa ofrece acceso desde diferentes dispositivos, mantiene la información dentro de la empresa y reduce el riesgo de interrupciones causadas por problemas con servicios externos.

## Consecuencias

- La aplicación solamente estará disponible para los dispositivos autorizados conectados a la red interna.
- La empresa deberá proporcionar una computadora con características adecuadas.
- El equipo deberá permanecer encendido durante los turnos.
- Se deberá controlar la estabilidad de la conexión Wi-Fi.
- Se designará un administrador responsable del equipo.
- Se configurarán copias de seguridad automáticas semanales.
- Los respaldos se almacenarán en un servidor local diferente.
- Si se requiere acceso desde fuera de la fábrica, deberá evaluarse una nueva decisión de arquitectura y seguridad.