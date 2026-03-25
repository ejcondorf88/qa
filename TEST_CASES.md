# TEST_CASES.md

---

## Información General

| Campo | Detalle |
|---|---|
| **Proyecto** | PetTech: Matcher de Adopción y Cuidados |
| **QA** | Elian Condor |
| **DEV** | Alejandra Marin |
| **Fecha** | 27/03/2026 |

---

# MICRO-SPRINT 1

**Período:** 27/03 – 01/04/2026
**HUs cubiertas:** HU-01 · HU-02 · HU-03 · HU-04 · HU-05 · HU-06

---

## HU-01 — Registrar información básica de la mascota

### TC-001

| Campo | Detalle |
|---|---|
| **ID** | TC-001 |
| **HU Asociada** | HU-01 — Registrar información básica de la mascota |
| **Prioridad** | Crítico |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que el administrador del refugio está autenticado en el sistema
Cuando ingresa los datos básicos de una mascota (nombre, especie, raza, edad, sexo)
Y hace clic en "Guardar"
Entonces el sistema registra la mascota exitosamente
Y muestra un mensaje de confirmación
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | El administrador debe estar autenticado. El formulario de registro debe estar disponible. |
| **Datos de entrada** | Nombre: "Luna", Especie: "Perro", Raza: "Labrador", Edad: 2, Sexo: "Hembra" |
| **Pasos de ejecución** | 1. Iniciar sesión como administrador. 2. Ir a "Registrar mascota". 3. Completar todos los campos obligatorios. 4. Hacer clic en "Guardar". |
| **Resultado esperado** | La mascota queda registrada en el sistema y aparece en el listado. |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-01 |

---

### TC-002

| Campo | Detalle |
|---|---|
| **ID** | TC-002 |
| **HU Asociada** | HU-01 — Registrar información básica de la mascota |
| **Prioridad** | Alto |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que el administrador del refugio está autenticado en el sistema
Cuando intenta guardar el formulario de registro de mascota con campos obligatorios vacíos
Entonces el sistema no registra la mascota
Y muestra mensajes de error en los campos requeridos
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | El administrador debe estar autenticado. El formulario de registro debe estar disponible. |
| **Datos de entrada** | Nombre: "" (vacío), Especie: "" (vacío), Raza: "" (vacío) |
| **Pasos de ejecución** | 1. Iniciar sesión como administrador. 2. Ir a "Registrar mascota". 3. Dejar campos obligatorios vacíos. 4. Hacer clic en "Guardar". |
| **Resultado esperado** | El sistema muestra errores de validación y no guarda el registro. |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-01 |

---

## HU-02 — Registrar información de salud de la mascota

### TC-003

| Campo | Detalle |
|---|---|
| **ID** | TC-003 |
| **HU Asociada** | HU-02 — Registrar información de salud de la mascota |
| **Prioridad** | Crítico |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que el administrador tiene una mascota ya registrada en el sistema
Cuando ingresa la información de salud (vacunas, esterilización, enfermedades)
Y hace clic en "Guardar"
Entonces el sistema asocia los datos de salud a la mascota correctamente
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | Mascota previamente registrada (HU-01 completada). Administrador autenticado. |
| **Datos de entrada** | Vacunada: Sí, Esterilizada: No, Enfermedades: "Ninguna" |
| **Pasos de ejecución** | 1. Acceder al perfil de la mascota registrada. 2. Ir a "Información de salud". 3. Completar los campos. 4. Guardar. |
| **Resultado esperado** | Los datos de salud quedan vinculados a la mascota. |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-02 |

---

## HU-03 — Subir fotos de la mascota

### TC-004

| Campo | Detalle |
|---|---|
| **ID** | TC-004 |
| **HU Asociada** | HU-03 — Subir fotos de la mascota |
| **Prioridad** | Alto |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que el administrador accede al perfil de una mascota registrada
Cuando sube una imagen en formato JPG o PNG menor a 5MB
Entonces el sistema guarda la foto y la muestra en el perfil de la mascota
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | Mascota registrada. Administrador autenticado. |
| **Datos de entrada** | Archivo: "foto_luna.jpg", Tamaño: 2MB, Formato: JPG |
| **Pasos de ejecución** | 1. Acceder al perfil de la mascota. 2. Ir a "Subir foto". 3. Seleccionar archivo válido. 4. Confirmar subida. |
| **Resultado esperado** | La foto se muestra en el perfil de la mascota. |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-03 |

---

### TC-005

| Campo | Detalle |
|---|---|
| **ID** | TC-005 |
| **HU Asociada** | HU-03 — Subir fotos de la mascota |
| **Prioridad** | Medio |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que el administrador accede al perfil de una mascota registrada
Cuando intenta subir un archivo en formato no permitido (PDF, DOCX, EXE)
Entonces el sistema rechaza el archivo
Y muestra un mensaje de error indicando los formatos permitidos
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | Mascota registrada. Administrador autenticado. |
| **Datos de entrada** | Archivo: "documento.pdf", Formato: PDF |
| **Pasos de ejecución** | 1. Acceder al perfil de la mascota. 2. Ir a "Subir foto". 3. Seleccionar archivo inválido (.pdf). 4. Confirmar subida. |
| **Resultado esperado** | El sistema muestra error: "Formato no permitido. Use JPG o PNG." |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-03 |

---

## HU-04 — Registrar información básica de familia adoptante

### TC-006

| Campo | Detalle |
|---|---|
| **ID** | TC-006 |
| **HU Asociada** | HU-04 — Registrar información básica de familia adoptante |
| **Prioridad** | Crítico |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que una familia adoptante accede al formulario de registro
Cuando completa todos los campos obligatorios (nombre, cédula, contacto, dirección)
Y hace clic en "Registrarse"
Entonces el sistema crea el perfil de la familia exitosamente
Y muestra un mensaje de bienvenida
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | El formulario de registro de familias debe estar disponible. |
| **Datos de entrada** | Nombre: "Familia García", Cédula: "1234567890", Teléfono: "0991234567", Dirección: "Quito, Pichincha" |
| **Pasos de ejecución** | 1. Acceder al formulario de registro de familia. 2. Completar todos los campos. 3. Hacer clic en "Registrarse". |
| **Resultado esperado** | El perfil de la familia queda registrado en el sistema. |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-04 |

---

## HU-05 — Registrar condiciones del hogar y experiencia

### TC-007

| Campo | Detalle |
|---|---|
| **ID** | TC-007 |
| **HU Asociada** | HU-05 — Registrar condiciones del hogar y experiencia |
| **Prioridad** | Crítico |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que la familia adoptante tiene un perfil registrado
Cuando completa las condiciones del hogar (tamaño, niños, experiencia previa)
Y hace clic en "Guardar"
Entonces el sistema almacena la información del hogar vinculada al perfil familiar
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | Familia registrada (HU-04 completada). |
| **Datos de entrada** | Tamaño hogar: "Grande", Niños: "Sí", Experiencia previa: "Sí", Tipo vivienda: "Casa" |
| **Pasos de ejecución** | 1. Acceder al perfil familiar. 2. Ir a "Condiciones del hogar". 3. Completar campos. 4. Guardar. |
| **Resultado esperado** | Las condiciones del hogar quedan guardadas y vinculadas al perfil. |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-05 |

---

### TC-008

| Campo | Detalle |
|---|---|
| **ID** | TC-008 |
| **HU Asociada** | HU-05 — Registrar condiciones del hogar y experiencia |
| **Prioridad** | Alto |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que una familia intenta registrarse con una cédula ya existente en el sistema
Cuando completa el formulario con el mismo número de cédula
Y hace clic en "Registrarse"
Entonces el sistema rechaza el registro
Y muestra un mensaje indicando que la cédula ya está registrada
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | Existe una familia registrada con cédula "1234567890". |
| **Datos de entrada** | Cédula: "1234567890" (duplicada) |
| **Pasos de ejecución** | 1. Acceder al formulario de registro. 2. Ingresar cédula ya existente. 3. Completar resto de campos. 4. Hacer clic en "Registrarse". |
| **Resultado esperado** | El sistema muestra: "Esta cédula ya está registrada." y no crea duplicado. |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-05 |

---

## HU-06 — Ver listado de mascotas disponibles

### TC-009

| Campo | Detalle |
|---|---|
| **ID** | TC-009 |
| **HU Asociada** | HU-06 — Ver listado de mascotas disponibles |
| **Prioridad** | Crítico |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que existe al menos una mascota con estado "disponible" en el sistema
Cuando la familia adoptante accede al listado de mascotas
Entonces el sistema muestra únicamente las mascotas con estado "disponible"
Y no muestra mascotas con estado "adoptada" o "no disponible"
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | Existen mascotas registradas con distintos estados. Usuario autenticado. |
| **Datos de entrada** | N/A (consulta de listado) |
| **Pasos de ejecución** | 1. Iniciar sesión como familia adoptante. 2. Acceder a "Ver mascotas". 3. Revisar el listado. |
| **Resultado esperado** | Solo aparecen mascotas con estado "disponible". |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-06 |

---

## Resumen Sprint 1

| ID | HU | Escenario | Prioridad | Estado |
|---|---|---|---|---|
| TC-001 | HU-01 | Registro exitoso de mascota | Crítico | Sin ejecutar |
| TC-002 | HU-01 | Campos obligatorios vacíos | Alto | Sin ejecutar |
| TC-003 | HU-02 | Registro de salud exitoso | Crítico | Sin ejecutar |
| TC-004 | HU-03 | Subida de foto válida | Alto | Sin ejecutar |
| TC-005 | HU-03 | Subida de formato inválido | Medio | Sin ejecutar |
| TC-006 | HU-04 | Registro de familia exitoso | Crítico | Sin ejecutar |
| TC-007 | HU-05 | Condiciones del hogar guardadas | Crítico | Sin ejecutar |
| TC-008 | HU-05 | Registro duplicado rechazado | Alto | Sin ejecutar |
| TC-009 | HU-06 | Listado solo muestra disponibles | Crítico | Sin ejecutar |

---

# MICRO-SPRINT 2

**Período:** [DD/MM] – [DD/MM/2026]
**HUs cubiertas:** HU-07 · HU-08 · [completar según backlog]

> ⚠️ Los casos de prueba del Sprint 2 se documentarán al inicio de dicho sprint, una vez que las HUs estén definidas y aceptadas por el equipo.

---

## HU-07 — [Nombre de la Historia]

### TC-010

| Campo | Detalle |
|---|---|
| **ID** | TC-010 |
| **HU Asociada** | HU-07 — [Nombre de la Historia] |
| **Prioridad** | [Crítico / Alto / Medio / Bajo] |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que [precondición del contexto]
Cuando [acción del usuario]
Y [acción adicional si aplica]
Entonces [resultado esperado principal]
Y [resultado esperado secundario si aplica]
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | [Condiciones previas necesarias para ejecutar el caso] |
| **Datos de entrada** | [Campo1: "valor1", Campo2: "valor2"] |
| **Pasos de ejecución** | 1. [Paso 1]. 2. [Paso 2]. 3. [Paso 3]. 4. [Paso 4]. |
| **Resultado esperado** | [Descripción del resultado esperado] |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-07 |

---

## HU-08 — [Nombre de la Historia]

### TC-011

| Campo | Detalle |
|---|---|
| **ID** | TC-011 |
| **HU Asociada** | HU-08 — [Nombre de la Historia] |
| **Prioridad** | [Crítico / Alto / Medio / Bajo] |
| **Estado** | Sin ejecutar |

**Escenario Gherkin:**
```gherkin
Dado que [precondición del contexto]
Cuando [acción del usuario]
Y [acción adicional si aplica]
Entonces [resultado esperado principal]
Y [resultado esperado secundario si aplica]
```

| Campo | Detalle |
|---|---|
| **Precondiciones** | [Condiciones previas necesarias para ejecutar el caso] |
| **Datos de entrada** | [Campo1: "valor1", Campo2: "valor2"] |
| **Pasos de ejecución** | 1. [Paso 1]. 2. [Paso 2]. 3. [Paso 3]. 4. [Paso 4]. |
| **Resultado esperado** | [Descripción del resultado esperado] |
| **Resultado obtenido** | — |
| **Estado** | Sin ejecutar |
| **GitHub Projects** | Sub-tarea de HU-08 |

---

## Resumen Sprint 2

| ID | HU | Escenario | Prioridad | Estado |
|---|---|---|---|---|
| TC-010 | HU-07 | [Nombre del escenario] | [Prioridad] | Sin ejecutar |
| TC-011 | HU-08 | [Nombre del escenario] | [Prioridad] | Sin ejecutar |

---

# Resumen General — Ambos Sprints

| Sprint | Total Casos | Críticos | Altos | Medios | Bajos | Sin ejecutar |
|---|---|---|---|---|---|---|
| Sprint 1 | 9 | 5 | 3 | 1 | 0 | 9 |
| Sprint 2 | [X] | [X] | [X] | [X] | [X] | [X] |
| **Total** | **[X]** | **[X]** | **[X]** | **[X]** | **[X]** | **[X]** |

---

*Documento elaborado por: Elian Condor (QA) — Fecha: 27/03/2026*
