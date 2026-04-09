# REALITY_CHECK.md

---

## Información General

| Campo | Detalle |
|---|---|
| **Proyecto** | PetTech: Matcher de Adopción y Cuidados |
| **QA** | Elian Condor |
| **DEV** | Alejandra Marin |
| **Fecha de cierre** | 09/04/2026 |
| **Sprints cubiertos** | Micro-Sprint 1 · Micro-Sprint 2 |
| **HUs ejecutadas** | HU-01 a HU-15 |

---

## 1. ¿Qué estimamos vs. qué costó realmente?

> Registra de forma honesta la diferencia entre los Story Points estimados y el esfuerzo real invertido. Incluye la causa raíz de cada desviación.

| HU | Story Points estimados | Tiempo real invertido | Desviación | Causa de la desviación |
|---|---|---|---|---|
| HU-01 | 5 SP | ~2.5h | Sin desviación | Formulario estándar, sin complejidades inesperadas |
| HU-02 | 3 SP | ~1.5h | Sin desviación | Validación de fechas resuelta con lógica directa |
| HU-03 | 3 SP | ~2.0h | Leve + | Manejo de tipos de archivo requirió ajuste adicional |
| HU-04 | 5 SP | ~5.0h | Leve + | Validación de cédula ecuatoriana requirió investigación |
| HU-05 | 3 SP | ~2.5h | Sin desviación | Campos de hogar bien definidos desde el inicio |
| HU-06 | 3 SP | ~2.5h | Sin desviación | Filtrado por estado fue directo en el ORM |
| HU-07 | 5 SP | ~2.5h | Sin desviación | Vista de detalle reutilizó lógica del listado |
| HU-08 | 3 SP | ~3.0h | Sin desviación | Validaciones de estado y duplicados bien cubiertos |
| HU-09 | 3 SP | ~2.0h | Sin desviación | Consulta de solicitud fue lectura directa de BD |
| HU-10 | 5 SP | ~4.0h | Sin desviación | Transiciones de estado implementadas con máquina de estados simple |
| HU-11 | 3 SP | ~1.0h | No priorizada | Descartada: no es criterio de negocio para el MVP actual |
| HU-12 | 3 SP | ~3.5h | Leve + | Registro de fecha de adopción y vinculación requirieron pruebas adicionales |
| HU-13 | 5 SP | ~2.5h | Sin desviación | Historial con filtros fue consulta directa sin lógica adicional |
| HU-14 | 8 SP | ~5.0h* | Parcial | En proceso de mejoras: lógica por especie/edad más compleja de lo estimado |
| HU-15 | 3 SP | ~2.5h* | Parcial | En proceso de mejoras: depende del estado de HU-14 |
| **Total** | **60 SP** | **~37h aprox.** | **Aceptable** | Sprint 1: 16h · Sprint 2: 21h |

> *Tiempo estimado parcial; trabajo en curso.

### Reflexión sobre las desviaciones

El Sprint 1 fue el más predecible: el uso de pipelines CI/CD desde el inicio permitió detectar regresiones de forma temprana y mantener el ritmo. Las 6 HUs se completaron en 16 horas sin incidentes bloqueantes. Las desviaciones más relevantes se concentraron en el Sprint 2, específicamente en HU-14 y HU-15, cuya lógica de generación de calendarios por especie y edad resultó más compleja de lo visualizado en la estimación inicial. El desarrollo asistido con IA híbrida (Claude Code / OpenCode) aceleró la generación de código base, pero la validación de las reglas de vacunación requirió iteraciones adicionales. HU-11 fue descartada por decisión de negocio, no por dificultad técnica.

---

## 2. ¿El MVP entregado es valioso para el negocio?

> Responde: A pesar de no haber terminado todo el backlog, ¿el incremento entregado resuelve el problema de negocio central?

### ¿Qué se logró entregar?

| Funcionalidad | Estado | Observaciones |
|---|---|---|
| Registro de mascotas (HU-01, HU-02, HU-03) | Completo | Todas las validaciones pasaron en Sprint 1. Pipeline verde. |
| Registro de familias adoptantes (HU-04, HU-05) | Completo | Cédula, mayoría de edad y duplicados validados. Sprint 1 cerrado sin bugs. |
| Visualización de mascotas (HU-06, HU-07) | Completo | Listado filtrado por estado y detalle completo entregados. |
| Solicitud y flujo de decisión (HU-08, HU-09, HU-10) | Completo | Flujo end-to-end: solicitud → pendiente → aprobada/rechazada funcional. |
| Sugerencia de adopción (HU-11) | No priorizada | Descartada del MVP: no es criterio crítico de negocio en esta iteración. |
| Confirmación de adopción (HU-12, HU-13) | Completo | Confirmación registra fecha automática y vincula mascota-familia. |
| Calendario de vacunación (HU-14, HU-15) | Parcial | Generación básica implementada; lógica por especie/edad en proceso de mejora. |

### Valoración del MVP

El incremento entregado cubre el flujo crítico de adopción de extremo a extremo: registro de mascota → exploración por familia → solicitud → decisión administrativa → confirmación. Este flujo reduce la dependencia del proceso manual y permite tomar decisiones más informadas sobre compatibilidad. La exclusión de HU-11 (sugerencias de adopción) no compromete el valor central del producto; puede incorporarse en el siguiente sprint. El calendario de vacunación (HU-14/15) está funcional en su forma básica, suficiente para el MVP, con mejoras en curso.

---

## 3. ¿Cómo garantizó el QA la calidad en tan poco tiempo?

> Describe la estrategia de calidad aplicada durante los micro-sprints bajo presión de tiempo.

### Estrategia aplicada

Se priorizaron los casos críticos (happy path) de cada HU antes de abordar los escenarios negativos. En el Sprint 1 se utilizaron pipelines CI/CD que ejecutaban validaciones automáticas en cada push, reduciendo el tiempo de detección de regresiones. Para el Sprint 2 se combinó la ejecución manual con Karate para los endpoints más críticos de la API. El desarrollo con IA híbrida (Claude Code / OpenCode) se utilizó para generación de casos de prueba y revisión de escenarios Gherkin, acelerando la documentación sin sacrificar cobertura.

### Cobertura alcanzada

| Sprint | Casos planificados | Casos ejecutados | Casos que pasaron | Casos que fallaron | Bugs encontrados |
|---|---|---|---|---|---|
| Micro-Sprint 1 | 20 | 20 | 20 | 0 | 0 |
| Micro-Sprint 2 | 32 | 28 | 26 | 2 | 2 |
| **Total** | **52** | **48** | **46** | **2** | **2** |

> Los 4 casos no ejecutados corresponden a los TCs de HU-14 y HU-15 que quedan pendientes por las mejoras en curso.

### Evidencias de calidad generadas

| Artefacto | Herramienta | Ubicación / Enlace |
|---|---|---|
| Reporte funcional automatizado | SerenityBDD + Cucumber | [Enlace al repositorio] |
| Reporte de pruebas de API | Karate | [Enlace al repositorio] |
| Reporte de rendimiento | k6 | [Enlace al repositorio] |
| Evidencias de ejecución manual | Pantallazos / Video | [Enlace o carpeta] |
| Reporte de bugs / incidencias | GitHub Issues | [Enlace] |

---

## 4. Bugs y defectos encontrados

> Lista los defectos detectados durante la ejecución de pruebas.

| ID Bug | HU afectada | Caso de prueba | Descripción del defecto | Severidad | Estado |
|---|---|---|---|---|---|
| BUG-001 | HU-14 | TC-047 | El calendario no excluye correctamente las vacunas ya aplicadas en gato adulto con historial parcial. | Alto | En progreso |
| BUG-002 | HU-15 | TC-051 | El sistema muestra el calendario de vacunación aunque la solicitud está en estado "pendiente". | Alto | En progreso |

---

## 5. ¿Qué haríamos diferente en el próximo sprint?

> Reflexión orientada a la mejora continua del proceso.

### Como equipo

Incluiríamos un refinamiento técnico más detallado para HUs con lógica condicional compleja (como el calendario de vacunación) antes de estimar Story Points. Esto evitaría subestimaciones en funcionalidades que dependen de múltiples combinaciones de datos de entrada. Además, estableceríamos criterios de done intermedios para HUs de más de 5 SP.

### Como QA

Comenzaría a escribir los escenarios Gherkin en paralelo al desarrollo desde el primer día del sprint, en lugar de esperar a que las funcionalidades estén listas. Esto aceleraría la detección temprana de ambigüedades en los criterios de aceptación y reduciría el tiempo de documentación al cierre.

### Como DEV

Dividiría las HUs más grandes como HU-14 en subtareas técnicas desde el inicio, con criterios de done intermedios, para tener mejor visibilidad del avance real y evitar que queden en estado "parcial" al cierre del sprint.

---

## 6. Estado del tablero GitHub Projects al cierre

> Describe el estado final del tablero ágil al cerrar los micro-sprints.

| Columna | Cantidad de HUs | Observaciones |
|---|---|---|
| Done | 12 HUs | HU-01 a HU-10, HU-12, HU-13 |
| In Progress | 2 HUs | HU-14 y HU-15: entregadas parcialmente, mejoras en curso |
| Not Prioritized | 1 HU | HU-11: descartada del MVP por criterio de negocio |



---

## 7. Conclusión del equipo

Este taller nos permitió vivir en carne propia la diferencia entre planear y ejecutar. El Sprint 1, apoyado en pipelines CI/CD y una correcta definición de las HUs, cerró limpio en 16 horas. El Sprint 2 evidenció que las funcionalidades con reglas de negocio múltiples requieren una descomposición técnica más granular antes de estimar.

El desarrollo con IA híbrida (Claude Code / OpenCode) fue un habilitador clave: redujo el tiempo de generación de código base y permitió dedicar más esfuerzo a la validación y refinamiento. La exclusión de HU-11 fue una decisión consciente que priorizó el valor de negocio sobre la cobertura completa del backlog.

El MVP entregado es funcional y demuestra el potencial de PetTech para transformar el proceso de adopción responsable: desde el registro de una mascota hasta su entrega oficial a una familia, el flujo completo opera correctamente. Las mejoras pendientes en el calendario de vacunación no bloquean el lanzamiento del producto.

---

*Documento elaborado por: Elian Condor (QA) y Alejandra Marin (DEV)
