# ADR-007 — Modelo de ubicación actual e historial de movimientos

## Estado

Aceptado.

## Contexto

Uno de los objetivos principales del sistema es permitir consultar rápidamente dónde se encuentra un material y, al mismo tiempo, conservar el historial completo de los movimientos realizados.

Para resolver este requisito se analizaron distintas formas de representar la ubicación de los materiales.

## Alternativas consideradas

### Calcular siempre la ubicación actual desde el último movimiento

La ubicación actual podría obtenerse buscando el movimiento más reciente del material.

Ventajas:

- Evita almacenar la ubicación actual por separado.
- El historial funciona como única fuente para reconstruir la ubicación.

Desventajas:

- Cada consulta de ubicación requiere localizar el movimiento más reciente.
- Las consultas resultan más complejas.
- El modelo depende de que exista un movimiento previo.

### Guardar únicamente la ubicación actual

El material podría almacenar solamente una referencia a su ubicación actual.

Ventajas:

- Permite realizar consultas simples y rápidas.

Desventajas:

- No permite reconstruir el recorrido realizado por el material.
- No cumple con el requisito de conservar trazabilidad histórica.

### Guardar ubicación actual e historial de movimientos

Cada material podrá almacenar una referencia a su ubicación actual y, además, cada cambio de ubicación generará un movimiento independiente.

Ventajas:

- Permite consultar rápidamente la ubicación actual.
- Conserva el historial completo.
- Permite reconstruir el recorrido del material.
- Permite identificar quién realizó cada movimiento y cuándo.

Desventajas:

- La ubicación actual y el historial deben mantenerse consistentes.
- El registro del movimiento y la actualización de la ubicación deben ejecutarse conjuntamente.

## Decisión

Se utilizará la tercera alternativa.

Cada material podrá tener registrada su ubicación actual.

Un material recién registrado podrá no poseer una ubicación actual conocida hasta que se registre su primer movimiento.

Además, cada cambio de ubicación generará un registro independiente dentro del historial de movimientos.

Cuando se registre correctamente un movimiento:

1. Se almacenará el movimiento.
2. Se actualizará la ubicación actual del material con la ubicación de destino.

Ambas operaciones deberán ejecutarse dentro de una misma transacción.

## Consecuencias

La consulta de la ubicación actual será directa y no requerirá reconstruir el historial en cada solicitud.

Los movimientos anteriores se conservarán para mantener la trazabilidad.

La capa de servicios del backend será responsable de mantener la consistencia entre la ubicación actual y el historial.

Si una operación falla, no deberán aplicarse parcialmente los cambios.