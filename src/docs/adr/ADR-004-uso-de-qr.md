# ADR-004 — Uso de códigos QR en ubicaciones

## Estado

Aceptado

## Fecha

30/08/2026

## Contexto

Los materiales del sistema son principalmente componentes metálicos de transformadores.

Colocar códigos QR individuales sobre cada material podría ser poco práctico y generar una carga adicional de mantenimiento.

Sin embargo, las ubicaciones físicas son puntos fijos y fácilmente identificables.

## Alternativas consideradas

### QR en cada material

Ventajas:

- Identificación individual inmediata.

Desventajas:

- Gran cantidad de componentes.
- Dificultad para colocar identificadores sobre materiales metálicos.
- Mayor mantenimiento.
- Mayor complejidad operativa.

### QR únicamente en ubicaciones

Ventajas:

- Menor cantidad de QR.
- Fácil mantenimiento.
- Permite identificar rápidamente una ubicación.
- Facilita registrar un material en el lugar donde se deposita.
- Permite consultar qué materiales deberían estar allí.

## Decisión

Los códigos QR se utilizarán únicamente en ubicaciones físicas.

## Justificación

El objetivo principal del sistema es conocer dónde se encuentran los materiales cuando se separan del transformador.

Identificar las ubicaciones mediante QR permite simplificar el proceso sin necesidad de etiquetar individualmente todos los materiales.

## Consecuencias

Al escanear un QR se podrá:

- Consultar la ubicación.
- Ver materiales registrados.
- Registrar un nuevo material en esa ubicación.