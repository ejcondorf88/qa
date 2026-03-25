# TEST_PLAN.md

---

## 1. Identificación del Plan

| Campo | Detalle |
|---|---|
| **Nombre del Proyecto** | PetTech: Matcher de Adopción y Cuidados |
| **Sistema Bajo Prueba** | PetTech — MVP Web (Django + React) |
| **Versión** | v1.0 / MVP |
| **Fecha** | 27/03/2026 |
| **Equipo** | QA: Elian Condor  \|  DEV: Alejandra Marin |
| **Ciclo** | Micro-Sprint 1 y Micro-Sprint 2 — HU-01 a HU-15 |

---

## 2. Contexto

> PetTech es una plataforma web que facilita la adopción responsable de mascotas. El sistema permite que administradores de refugios registren animales disponibles y que familias adoptantes exploren opciones y envíen solicitudes. El motor de reglas de compatibilidad evalúa factores como el tamaño del hogar, la experiencia previa y la presencia de niños, con el objetivo de reducir el 20.7% de adopciones fallidas actuales.
>
> Este plan cubre dos Micro-Sprints: el Micro-Sprint 1 abarca las Épicas 1, 2 y el inicio de la Épica 3 (registro completo de mascotas y familias adoptantes, más la visualización del listado). El Micro-Sprint 2 cubre las HU restantes correspondientes a las Épicas 3 a 6.

---

## 3. Alcance de las Pruebas

### 3.1 Micro-Sprint 1 — Historias incluidas

| ID | Historia de Usuario | Prioridad / SP |
|---|---|---|
| HU-01 | Registrar información básica de la mascota | Alta / 5 SP |
| HU-02 | Registrar información de salud de la mascota | Alta / 3 SP |
| HU-03 | Subir fotos de la mascota | Media / 3 SP |
| HU-04 | Registrar información básica de familia adoptante | Alta / 5 SP |
| HU-05 | Registrar condiciones del hogar y experiencia | Alta / 3 SP |
| HU-06 | Ver listado de mascotas disponibles | Alta / 3 SP |

### 3.2 Micro-Sprint 2 — Historias incluidas

| ID | Historia de Usuario | Prioridad / SP |
|---|---|---|
| HU-07 | [Por definir] | [Por definir] |
| HU-08 | [Por definir] | [Por definir] |
| HU-09 | [Por definir] | [Por definir] |
| HU-10 | [Por definir] | [Por definir] |
| HU-11 | [Por definir] | [Por definir] |
| HU-12 | [Por definir] | [Por definir] |
| HU-13 | [Por definir] | [Por definir] |
| HU-14 | [Por definir] | [Por definir] |
| HU-15 | [Por definir] | [Por definir] |

### 3.3 Fuera del alcance (MVP)

| Funcionalidad excluida | Razón |
|---|---|
| Pasarela de pagos | Fuera del MVP |
| Matching con IA avanzado | Fuera del MVP |
| Notificaciones / correos automáticos | Fuera del MVP |
| Chat entre adoptante y refugio | Fuera del MVP |

---

## 4. Estrategia de Pruebas

| Tipo de Prueba | Herramienta | Propósito |
|---|---|---|
| Pruebas Funcionales | SerenityBDD + Cucumber | Validar flujos de negocio mediante escenarios Gherkin |
| Pruebas de API | Karate | Automatizar y validar endpoints REST (GET, POST, PUT, DELETE) |
| Pruebas de Rendimiento | k6 | Medir tiempos de respuesta y comportamiento bajo carga |
| Asistencia IA | Claude Code / OpenCode | Generación y revisión de casos de prueba, escenarios |

---

## 5. Criterios de Entrada y Salida

### 5.1 Micro-Sprint 1

#### Criterios de Entrada
- [ ] Las HU-01 a HU-06 están definidas y aceptadas por el equipo
- [ ] El entorno de pruebas local está disponible (Django levantado en :8080)
- [ ] La base de datos Postgres está configurada y migrada
- [ ] Los casos de prueba del Micro-Sprint 1 están documentados en TEST_CASES.md
- [ ] Los escenarios Gherkin (.feature) para cada HU están redactados

#### Criterios de Salida
- [ ] El 100% de los casos críticos (happy path) de HU-01 a HU-06 han pasado
- [ ] No existen bugs bloqueantes abiertos en el Micro-Sprint 1
- [ ] Todos los escenarios de validación de campos obligatorios pasan correctamente
- [ ] Las HU-01 a HU-06 cumplen los criterios de aceptación definidos en las USER_STORIES

### 5.2 Micro-Sprint 2

#### Criterios de Entrada
- [ ] Las HU-07 a HU-15 están definidas y aceptadas por el equipo
- [ ] El Micro-Sprint 1 ha cerrado sin bugs bloqueantes abiertos
- [ ] Los casos de prueba del Micro-Sprint 2 están documentados en TEST_CASES.md
- [ ] Los escenarios Gherkin (.feature) para cada HU están redactados

#### Criterios de Salida
- [ ] El 100% de los casos críticos (happy path) de HU-07 a HU-15 han pasado
- [ ] No existen bugs bloqueantes abiertos en el Micro-Sprint 2
- [ ] Todos los escenarios de validación de campos obligatorios pasan correctamente
- [ ] Las HU-07 a HU-15 cumplen los criterios de aceptación definidos en las USER_STORIES

---

## 6. Entorno de Pruebas

| Campo | Detalle |
|---|---|
| **URL / Entorno** | http://localhost:8080 (desarrollo local) |
| **Sistema Operativo** | Windows 11 / macOS / Linux Ubuntu |
| **Base de Datos** | PostgreSQL |
| **Navegador** | Google Chrome v123+ / Firefox v124+ |
| **Backend** | Django — Python 3.x |
| **Configuración especial** | Variables de entorno: DB_URL, DB_USER, DB_PASS — Puerto: 8080 |

---

## 7. Herramientas

| Herramienta | Versión | Propósito |
|---|---|---|
| SerenityBDD + Cucumber | 3.x | Automatización de pruebas funcionales con Gherkin |
| Karate | 1.x | Automatización de pruebas de API REST |
| k6 | 0.50+ | Pruebas de rendimiento y carga |
| GitHub Projects | — | Gestión del backlog y seguimiento de casos de prueba |
| Claude Code / OpenCode | Latest | Asistencia IA para generación de casos |
| Postman | Latest | Exploración manual de endpoints antes de automatizar |

---

## 8. Roles y Responsabilidades

| Actividad | QA (Elian Condor) | DEV (Alejandra Marin) |
|---|---|---|
| Redacción del TEST_PLAN.md | Lidera | Revisa |
| Redacción del TEST_CASES.md | Lidera | Apoya |
| Implementación de Karate | Lidera | — |
| Desarrollo del MVP | — | Lidera |
| Registro de tiempos (time-tracking) | Apoya | Lidera |
| REALITY_CHECK.md | Co-redacta | Co-redacta |

---

## 9. Cronograma y Estimación

### Micro-Sprint 1

| Historia de Usuario | Story Points Estimados | Fechas |
|---|---|---|
| HU-01 — Reg. básico mascota | 5 SP | 24/03 – 25/03 |
| HU-02 — Info. de salud | 3 SP | 24/03 – 25/03 |
| HU-03 — Subir fotos | 3 SP | 24/03 |
| HU-04 — Reg. familia | 5 SP | 24/03 – 25/03 |
| HU-05 — Cond. del hogar | 3 SP | 24/03 – 25/03 |
| HU-06 — Ver listado mascotas | 3 SP | 25/03 |
| **Subtotal** | **22 SP** | **24/03 – 25/03/2026** |

### Micro-Sprint 2

| Historia de Usuario | Story Points Estimados | Fechas |
|---|---|---|
| HU-07 — [Por definir] | [X SP] | [Por definir] |
| HU-08 — [Por definir] | [X SP] | [Por definir] |
| HU-09 — [Por definir] | [X SP] | [Por definir] |
| HU-10 — [Por definir] | [X SP] | [Por definir] |
| HU-11 — [Por definir] | [X SP] | [Por definir] |
| HU-12 — [Por definir] | [X SP] | [Por definir] |
| HU-13 — [Por definir] | [X SP] | [Por definir] |
| HU-14 — [Por definir] | [X SP] | [Por definir] |
| HU-15 — [Por definir] | [X SP] | [Por definir] |
| **Subtotal** | **[X SP]** | **[Por definir]** |

### Total General

| | Story Points |
|---|---|
| Micro-Sprint 1 | 22 SP |
| Micro-Sprint 2 | [X SP] |
| **Total** | **[X SP]** |

---

## 10. Entregables de Prueba

| Artefacto | Micro-Sprint | Descripción | Responsable |
|---|---|---|---|
| TEST_PLAN.md | Sprint 1 | Plan formal de pruebas del micro-sprint | QA |
| TEST_CASES.md | Sprint 1 | Matriz completa de casos de prueba con datos de entrada | QA |
| Evidencias de ejecución | Sprint 1 y 2 | Capturas de pantalla o reportes generados por Serenity BDD, Cucumber o K6 | QA |
| Repositorio Serenity BDD | Sprint 1 y 2 | Repositorio independiente con escenarios funcionales automatizados | QA |
| Repositorio Karate | Sprint 1 y 2 | Repositorio independiente con pruebas de API REST automatizadas | QA |
| Repositorio K6 | Sprint 2 | Repositorio independiente con scripts de pruebas de rendimiento | QA |
| Reporte de bugs / defectos | Sprint 1 y 2 | Listado de defectos encontrados con pasos de reproducción incluidos | QA |
| REALITY_CHECK.md | Cierre | Documento retrospectivo del sprint | QA + DEV |
| GitHub Projects Board | Ambos | Tablero con HU y casos de prueba como sub-tareas | QA + DEV |

---

## 11. Riesgos y Contingencias

| Riesgo | Probabilidad | Impacto | Mitigación |
|---|---|---|---|
| Entorno de pruebas no disponible | Media | Alto | Usar entorno local o contenedor Docker |
| API no responde o endpoint inestable | Baja | Alto | Usar mocks o colección Postman como respaldo |
| Tiempo insuficiente en Sprint 1 | Media | Medio | Priorizar casos críticos; mover HU no críticas al Sprint 2 |
| Validación de datos incorrectos (edad, mayoría de edad) | Media | Alto | Definir datos de prueba y casos negativos explícitos en TEST_CASES |
| Formato de imagen no validado correctamente (HU-03) | Media | Medio | Probar con archivos .pdf, .docx, .exe en pruebas negativas |
| Registro duplicado de familia no detectado (HU-05) | Alta | Alto | Ejecutar escenario de duplicidad con mismo número de cédula |

---

## 12. Convención GitHub Projects

Por cada Historia de Usuario se creará una única sub-issue en GitHub Projects que contendrá la tabla completa de casos de prueba asociados, en lugar de crear sub-issues individuales por cada caso de prueba. Esto permite mantener el tablero organizado y trazable sin generar ruido en el backlog.

---

*Documento elaborado por: Elian Condor (QA) — Revisado por: Alejandra Marin (DEV) — Fecha: 27/03/2026*
