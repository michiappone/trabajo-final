# Matriz de Trazabilidad

## Índice

- [Objetivo](#objetivo)
- [Funcionalidades incluidas](#funcionalidades-incluidas)
- [Requisitos no funcionales relacionados](#requisitos-no-funcionales-relacionados)
- [Funcionalidades fuera del alcance inicial](#funcionalidades-fuera-del-alcance-inicial)

## Objetivo

Este documento relaciona las funcionalidades definidas dentro del alcance del proyecto con los requisitos funcionales, casos de uso y reglas de negocio asociadas.

La matriz permite verificar que las funcionalidades previstas cuenten con una definición consistente dentro de la documentación del sistema y facilita el seguimiento entre el problema planteado, los requisitos y las funcionalidades que posteriormente serán implementadas.

## Funcionalidades incluidas

| Funcionalidad | Requisitos funcionales | Casos de uso | Reglas de negocio |
|---|---|---|---|
| Identificación y gestión de usuarios | RF-01, RF-02, RF-03 | CU-01, CU-02 | — |
| Gestión de áreas y ubicaciones | RF-04, RF-05 | CU-03 | RN-06 |
| Gestión de transformadores | RF-06 | CU-04 | RN-01, RN-02 |
| Registro de materiales | RF-07, RF-08 | CU-05 | RN-03, RN-04 |
| Consulta de transformadores y sus materiales | RF-09 | CU-06 | RN-02, RN-03, RN-04 |
| Consulta de ubicación actual de materiales | RF-10 | CU-07 | RN-05 |
| Registro de movimientos | RF-11, RF-12, RF-13, RF-14 | CU-08 | RN-05, RN-08 |
| Consulta del historial de movimientos | RF-15 | CU-09 | RN-11 |
| Registro de observaciones | RF-16 | CU-10 | RN-10 |
| Advertencia por material de otro transformador | RF-17 | CU-12 | RN-09 |
| Uso de ubicaciones temporales | RF-18 | CU-03, CU-08 | RN-06 |
| Identificación de ubicaciones mediante códigos QR | RF-19 | CU-11 | RN-07 |
| Consulta de movimientos asociados a una ubicación | RF-20 | CU-09 | RN-11 |

## Requisitos no funcionales relacionados

Las funcionalidades anteriores también se encuentran condicionadas por los requisitos no funcionales definidos para la primera versión.

| Requisito | Incidencia principal |
|---|---|
| RNF-01 — Aplicación web | Define la forma general de acceso al sistema. |
| RNF-02 — Diseño responsive | Permite utilizar la aplicación desde PC y dispositivos móviles. |
| RNF-03 — Funcionamiento en red local | Define el entorno de funcionamiento de la primera versión. |
| RNF-04 — Compatibilidad | Define el acceso mediante navegadores web actuales. |
| RNF-05 — Usabilidad | Incide especialmente en consultas y registro de movimientos. |
| RNF-06 — Tiempo de operación | Incide en la consulta de materiales y movimientos. |
| RNF-07 — Persistencia | Define PostgreSQL como base de datos. |
| RNF-08 — Backend | Define Java y Spring Boot para la implementación del backend. |
| RNF-09 — Control de acceso | Incide en los módulos de usuarios y administración. |
| RNF-10 — Trazabilidad | Incide en movimientos, historial, ubicaciones y usuarios. |
| RNF-11 — Copias de seguridad | Incide en la protección y recuperación de los datos. |
| RNF-12 — Escalabilidad funcional | Permite incorporar otras áreas productivas en el futuro. |
| RNF-13 — Disponibilidad local | Define las condiciones necesarias para utilizar el sistema durante los turnos de trabajo. |

## Funcionalidades fuera del alcance inicial

Las siguientes funcionalidades fueron excluidas de la primera versión.

Al encontrarse fuera del alcance actual, no poseen requisitos funcionales ni casos de uso específicos de implementación dentro de esta etapa.

| Funcionalidad excluida | Estado |
|---|---|
| Planificación de producción | Fuera del alcance inicial |
| Ensayos | Fuera del alcance inicial |
| Gestión de calidad | Fuera del alcance inicial |
| Compras y proveedores | Fuera del alcance inicial |
| Mantenimiento | Fuera del alcance inicial |
| Control del stock general | Fuera del alcance inicial |
| Gestión completa del depósito | Fuera del alcance inicial |
| Códigos QR individuales sobre los materiales | Fuera del alcance inicial |
| Importación masiva mediante CSV o Excel | Fuera del alcance inicial |
| Funcionamiento fuera de la red interna de la fábrica | Fuera del alcance inicial |

Si alguna de estas funcionalidades se incorpora en una versión futura, deberán definirse los requisitos, casos de uso y reglas de negocio correspondientes y actualizarse esta matriz.