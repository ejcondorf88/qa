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

| ID | HU | Escenario Gherkin | Tipo | Precondiciones | Datos de entrada | Pasos de ejecución | Resultado esperado | Resultado obtenido | Prioridad | Estado |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-001 | HU-01 | **Dado** que el administrador está autenticado **Cuando** registra una mascota con datos válidos **Entonces** el sistema confirma el registro y la muestra en el listado | Positivo | Administrador autenticado. Formulario de registro disponible. | Nombre: "Luna", Especie: "Perro", Raza: "Labrador", Edad: 2, Sexo: "Hembra" | 1. Iniciar sesión como administrador. 2. Ir a "Registrar mascota". 3. Completar todos los campos obligatorios. 4. Guardar. | La mascota queda registrada y aparece en el listado con estado "disponible". | — | Crítico | Sin ejecutar |
| TC-002 | HU-01 | **Dado** que el administrador está autenticado **Cuando** intenta registrar una mascota con campos obligatorios vacíos **Entonces** el sistema muestra errores de validación y no guarda el registro | Negativo | Administrador autenticado. Formulario de registro disponible. | Nombre: "" (vacío), Especie: "" (vacío), Raza: "" (vacío) | 1. Iniciar sesión como administrador. 2. Ir a "Registrar mascota". 3. Dejar campos obligatorios vacíos. 4. Guardar. | El sistema muestra mensajes de error en los campos requeridos y no crea el registro. | — | Alto | Sin ejecutar |
| TC-003 | HU-01 | **Dado** que el administrador está autenticado **Cuando** intenta registrar una mascota con una edad inválida **Entonces** el sistema muestra un error de validación en el campo edad | Negativo | Administrador autenticado. Formulario de registro disponible. | Nombre: "Max", Especie: "Gato", Edad: -3 (valor negativo) | 1. Iniciar sesión como administrador. 2. Ir a "Registrar mascota". 3. Ingresar edad negativa. 4. Guardar. | El sistema muestra error: "La edad debe ser un valor positivo." y no guarda el registro. | — | Alto | Sin ejecutar |

---

## HU-02 — Registrar información de salud de la mascota

| ID | HU | Escenario Gherkin | Tipo | Precondiciones | Datos de entrada | Pasos de ejecución | Resultado esperado | Resultado obtenido | Prioridad | Estado |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-004 | HU-02 | **Dado** que el administrador tiene una mascota registrada **Cuando** registra su información de salud con datos válidos **Entonces** el sistema asocia los datos de salud al perfil de la mascota | Positivo | Mascota previamente registrada (TC-001 ejecutado). Administrador autenticado. | Vacunada: Sí, Esterilizada: No, Enfermedades: "Ninguna" | 1. Acceder al perfil de la mascota registrada. 2. Ir a "Información de salud". 3. Completar los campos. 4. Guardar. | Los datos de salud quedan vinculados a la mascota y visibles en su perfil. | — | Crítico | Sin ejecutar |

---

## HU-03 — Subir fotos de la mascota

| ID | HU | Escenario Gherkin | Tipo | Precondiciones | Datos de entrada | Pasos de ejecución | Resultado esperado | Resultado obtenido | Prioridad | Estado |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-005 | HU-03 | **Dado** que el administrador accede al perfil de una mascota registrada **Cuando** sube una imagen en formato y tamaño válidos **Entonces** el sistema guarda la foto y la muestra en el perfil | Positivo | Mascota registrada. Administrador autenticado. | Archivo: "foto_luna.jpg", Tamaño: 2MB, Formato: JPG | 1. Acceder al perfil de la mascota. 2. Ir a "Subir foto". 3. Seleccionar archivo JPG de 2MB. 4. Confirmar subida. | La foto se muestra correctamente en el perfil de la mascota. | — | Alto | Sin ejecutar |
| TC-006 | HU-03 | **Dado** que el administrador accede al perfil de una mascota registrada **Cuando** intenta subir un archivo en formato no permitido **Entonces** el sistema rechaza el archivo y muestra los formatos válidos | Negativo | Mascota registrada. Administrador autenticado. | Archivo: "documento.pdf", Formato: PDF | 1. Acceder al perfil de la mascota. 2. Ir a "Subir foto". 3. Seleccionar archivo .pdf. 4. Confirmar subida. | El sistema muestra error: "Formato no permitido. Use JPG o PNG." y no guarda el archivo. | — | Medio | Sin ejecutar |
| TC-007 | HU-03 | **Dado** que el administrador accede al perfil de una mascota registrada **Cuando** intenta subir una imagen que supera el tamaño máximo permitido **Entonces** el sistema rechaza el archivo y notifica el límite de tamaño | Negativo | Mascota registrada. Administrador autenticado. | Archivo: "foto_grande.jpg", Tamaño: 8MB, Formato: JPG | 1. Acceder al perfil de la mascota. 2. Ir a "Subir foto". 3. Seleccionar archivo JPG de 8MB. 4. Confirmar subida. | El sistema muestra error: "El archivo supera el tamaño máximo de 5MB." y no guarda la imagen. | — | Medio | Sin ejecutar |

---

## HU-04 — Registrar información básica de familia adoptante

| ID | HU | Escenario Gherkin | Tipo | Precondiciones | Datos de entrada | Pasos de ejecución | Resultado esperado | Resultado obtenido | Prioridad | Estado |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-008 | HU-04 | **Dado** que una familia accede al formulario de registro **Cuando** completa todos los campos obligatorios con datos válidos **Entonces** el sistema crea el perfil familiar exitosamente | Positivo | Formulario de registro de familias disponible. | Nombre: "Familia García", Cédula: "1234567890", Teléfono: "0991234567", Dirección: "Quito, Pichincha" | 1. Acceder al formulario de registro de familia. 2. Completar todos los campos. 3. Hacer clic en "Registrarse". | El perfil de la familia queda registrado y se muestra mensaje de bienvenida. | — | Crítico | Sin ejecutar |
| TC-009 | HU-04 | **Dado** que una familia accede al formulario de registro **Cuando** ingresa una cédula con formato inválido **Entonces** el sistema muestra un error de validación y no crea el registro | Negativo | Formulario de registro de familias disponible. | Cédula: "123" (menos de 10 dígitos), Nombre: "Familia López" | 1. Acceder al formulario de registro. 2. Ingresar cédula con formato inválido. 3. Completar resto de campos. 4. Hacer clic en "Registrarse". | El sistema muestra error: "La cédula debe tener 10 dígitos." y no crea el registro. | — | Alto | Sin ejecutar |
| TC-010 | HU-04 | **Dado** que una familia accede al formulario de registro **Cuando** el solicitante es menor de edad **Entonces** el sistema rechaza el registro e indica el requisito de mayoría de edad | Negativo | Formulario de registro de familias disponible. | Nombre: "Carlos Pérez", Fecha de nacimiento: que resulte en edad menor a 18 años | 1. Acceder al formulario de registro. 2. Ingresar fecha de nacimiento de menor de edad. 3. Completar resto de campos. 4. Hacer clic en "Registrarse". | El sistema muestra error: "Debes ser mayor de edad para registrarte." y no crea el registro. | — | Alto | Sin ejecutar |
| TC-011 | HU-04 | **Dado** que ya existe una familia registrada con una cédula en el sistema **Cuando** otra familia intenta registrarse con la misma cédula **Entonces** el sistema rechaza el registro y notifica la duplicidad | Negativo | Familia con cédula "1234567890" previamente registrada (TC-008 ejecutado). | Cédula: "1234567890" (duplicada), Nombre: "Familia Rodríguez" | 1. Acceder al formulario de registro. 2. Ingresar cédula ya existente. 3. Completar resto de campos. 4. Hacer clic en "Registrarse". | El sistema muestra: "Esta cédula ya está registrada." y no crea duplicado. | — | Alto | Sin ejecutar |

---

## HU-05 — Registrar condiciones del hogar y experiencia

| ID | HU | Escenario Gherkin | Tipo | Precondiciones | Datos de entrada | Pasos de ejecución | Resultado esperado | Resultado obtenido | Prioridad | Estado |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-012 | HU-05 | **Dado** que la familia adoptante tiene un perfil registrado **Cuando** completa las condiciones del hogar con datos válidos **Entonces** el sistema almacena la información vinculada al perfil familiar | Positivo | Familia registrada (TC-008 ejecutado). | Tamaño hogar: "Grande", Niños: "Sí", Experiencia previa: "Sí", Tipo vivienda: "Casa" | 1. Acceder al perfil familiar. 2. Ir a "Condiciones del hogar". 3. Completar campos. 4. Guardar. | Las condiciones del hogar quedan guardadas y vinculadas al perfil familiar. | — | Crítico | Sin ejecutar |

---

## HU-06 — Ver listado de mascotas disponibles

| ID | HU | Escenario Gherkin | Tipo | Precondiciones | Datos de entrada | Pasos de ejecución | Resultado esperado | Resultado obtenido | Prioridad | Estado |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-013 | HU-06 | **Dado** que existen mascotas con distintos estados en el sistema **Cuando** la familia adoptante accede al listado de mascotas **Entonces** el sistema muestra únicamente las mascotas con estado "disponible" | Positivo | Mascotas registradas con estados variados. Usuario autenticado. | N/A (consulta de listado) | 1. Iniciar sesión como familia adoptante. 2. Acceder a "Ver mascotas". 3. Revisar el listado. | Solo aparecen mascotas con estado "disponible". No se muestran las adoptadas o no disponibles. | — | Crítico | Sin ejecutar |
| TC-014 | HU-06 | **Dado** que no existen mascotas con estado "disponible" en el sistema **Cuando** la familia adoptante accede al listado de mascotas **Entonces** el sistema muestra un mensaje informando que no hay mascotas disponibles | Negativo | No existen mascotas con estado "disponible". Usuario autenticado. | N/A (listado vacío) | 1. Iniciar sesión como familia adoptante. 2. Acceder a "Ver mascotas". 3. Revisar el listado. | El sistema muestra mensaje: "No hay mascotas disponibles en este momento." sin errores. | — | Medio | Sin ejecutar |

---

## Resumen Micro-Sprint 1

| ID | HU | Escenario | Tipo | Prioridad | Estado |
|---|---|---|---|---|---|
| TC-001 | HU-01 | Registro exitoso de mascota | Positivo | Crítico | Sin ejecutar |
| TC-002 | HU-01 | Campos obligatorios vacíos | Negativo | Alto | Sin ejecutar |
| TC-003 | HU-01 | Edad con valor inválido | Negativo | Alto | Sin ejecutar |
| TC-004 | HU-02 | Registro de salud exitoso | Positivo | Crítico | Sin ejecutar |
| TC-005 | HU-03 | Subida de foto válida | Positivo | Alto | Sin ejecutar |
| TC-006 | HU-03 | Subida de formato inválido | Negativo | Medio | Sin ejecutar |
| TC-007 | HU-03 | Imagen supera tamaño máximo | Negativo | Medio | Sin ejecutar |
| TC-008 | HU-04 | Registro de familia exitoso | Positivo | Crítico | Sin ejecutar |
| TC-009 | HU-04 | Cédula con formato inválido | Negativo | Alto | Sin ejecutar |
| TC-010 | HU-04 | Registro de menor de edad rechazado | Negativo | Alto | Sin ejecutar |
| TC-011 | HU-04 | Registro duplicado rechazado | Negativo | Alto | Sin ejecutar |
| TC-012 | HU-05 | Condiciones del hogar guardadas | Positivo | Crítico | Sin ejecutar |
| TC-013 | HU-06 | Listado solo muestra disponibles | Positivo | Crítico | Sin ejecutar |
| TC-014 | HU-06 | Listado vacío muestra mensaje | Negativo | Medio | Sin ejecutar |

---

# MICRO-SPRINT 2

**Período:** [DD/MM] – [DD/MM/2026]
**HUs cubiertas:** HU-07 · HU-08 · [completar según backlog]

> ⚠️ Los casos de prueba del Micro-Sprint 2 se documentarán al inicio de dicho sprint, una vez que las HUs estén definidas y aceptadas por el equipo.

## Plantilla para nuevos casos

| ID | HU | Escenario Gherkin | Tipo | Precondiciones | Datos de entrada | Pasos de ejecución | Resultado esperado | Resultado obtenido | Prioridad | Estado |
|---|---|---|---|---|---|---|---|---|---|---|
| TC-0XX | HU-0X | **Dado** que [contexto] **Cuando** [acción del usuario] **Entonces** [resultado esperado] | Positivo / Negativo | [Condiciones previas] | [Campo: "valor"] | 1. [Paso 1]. 2. [Paso 2]. 3. [Paso 3]. | [Resultado esperado] | — | [Crítico / Alto / Medio / Bajo] | Sin ejecutar |

---

## Resumen Micro-Sprint 2

| ID | HU | Escenario | Tipo | Prioridad | Estado |
|---|---|---|---|---|---|
| TC-0XX | HU-0X | [Nombre del escenario] | [Tipo] | [Prioridad] | Sin ejecutar |

---

# Resumen General — Ambos Sprints

| Sprint | Total Casos | Críticos | Altos | Medios | Bajos | Sin ejecutar |
|---|---|---|---|---|---|---|
| Sprint 1 | 14 | 5 | 6 | 3 | 0 | 14 |
| Sprint 2 | [X] | [X] | [X] | [X] | [X] | [X] |
| **Total** | **[X]** | **[X]** | **[X]** | **[X]** | **[X]** | **[X]** |

---

*Documento elaborado por: Elian Condor (QA) — Fecha: 27/03/2026*
