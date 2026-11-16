# Aporte individual U3-E02 — TecConnect

**Institución:** Instituto Tecnológico Superior de San Pedro de las Colonias  
**Carrera:** Ingeniería en Sistemas Computacionales  
**Asignatura:** Fundamentos de Ingeniería de Software (SCC-1007)  
**Grupo:** 5° A  
**Docente:** Ruth Aivi Chávez Rodríguez  
**Alumno:** Ángel David Pérez Sánchez  
**Proyecto:** TecConnect  
**Rol en Unidad 3:** QA / Revisión  
**Fecha de elaboración:** 16 de noviembre de 2026  
**Estado:** Validado  

---

## 1. Fuentes de información, hallazgos y necesidades

Para el proceso **TO-BE: Gestión digital del préstamo de equipo de cómputo y herramientas**, mi aporte individual se enfoca en el cierre de la operación (confirmación del estudiante mediante su matrícula y registro autorizado del préstamo) y en la seguridad de acceso a los datos personales del estudiante.

| ID | Técnica o documento | Fecha | Hallazgo documentado | Estado |
|---|---|---|---|---|
| **F-01** | Revisión documental: acuerdo y descripción del proyecto (`trabajos.pdf`, pp. 1–5) | 08/10/2026 | TecConnect contempla credencialización digital y control de préstamos entre estudiantes y personal de ventanilla. | Documentado |
| **F-02** | Revisión documental: proceso actual AS-IS (`trabajos.pdf`, pp. 6–9) | 08/10/2026 | El proceso actual depende de bitácoras manuales y hojas de Excel sin folio automático ni control estricto sobre quién consulta la información académica del alumno. | Documentado |
| **F-03** | Entrevista semiestructurada: **Encargada de biblioteca** (ITSSPC) | 10/11/2026 | Se confirmó que en biblioteca se solicita la **matrícula del estudiante** para validar y confirmar el préstamo antes de entregar físicamente el equipo; el sistema debe guardar el préstamo generando un folio consultable y restringir el acceso a los datos del SII exclusivamente a personal autenticado. | Validado (Acta 01) |

### Necesidades identificadas
* **N-04 (Confirmación por matrícula y registro trazable del préstamo):** Sustituir la captura manual en bitácora/Excel por un registro digital autorizado que solicite la confirmación mediante la matrícula del estudiante y vincule alumno, equipo, folio único y fecha/hora.
* **N-05 (Seguridad y control de acceso):** Restringir la consulta de matrícula, estatus y adeudos del estudiante únicamente al personal de ventanilla autenticado.

---

## 2. Requisitos individuales (`RF-05` y `RNF-01`)

### Requisito 1: `RF-05` — Confirmación por matrícula y registro del préstamo autorizado

| Atributo | Detalle |
|---|---|
| **ID** | `RF-05` |
| **Tipo** | Requisito Funcional (RF) |
| **Origen** | `F-03 -> N-04` |
| **Prioridad y motivo** | **P1 - Alta.** Es indispensable para sustituir la bitácora manual; sin la confirmación de la matrícula del alumno y el registro vinculado no puede autorizarse la entrega física del equipo. |
| **Autor** | Ángel David Pérez Sánchez |
| **Estado** | `Validado` |
| **Tarjeta Trello** | `[RF-05]: (Angel)` — [Tablero TecConect 2.0](https://trello.com/b/EZI199d4) |

* **Enunciado verificable:**  
  Una vez validados el estudiante y la disponibilidad del equipo, el sistema debe solicitar la confirmación mediante la matrícula del estudiante y guardar el préstamo autorizado relacionando la matrícula del estudiante, el código del equipo, un folio único y la fecha y hora exacta de la operación antes de habilitar la entrega física.

* **Criterios de aceptación verificables (`F RF-05`):**

| Escenario | Condición (Dado) | Acción (Cuando) | Resultado observable esperado (Entonces) |
|---|---|---|---|
| **RF-05.1 (Éxito)** | El estudiante es elegible y el equipo solicitado está disponible. | Se ingresa y confirma la matrícula válida del estudiante en la pantalla de confirmación (`Vista 02`). | El sistema guarda el registro vinculado (matrícula del alumno, ID equipo, fecha/hora), muestra el comprobante con folio único (`Vista 03A`), refleja el registro en el listado de préstamos activos (`Vista 04`) y habilita la entrega del equipo. |
| **RF-05.2 (Alternativa / Error)** | El sistema solicita la matrícula para confirmar el préstamo. | Se ingresa una matrícula que no coincide con la credencial escaneada o se cancela la operación. | El sistema rechaza la autorización (`Vista 03B`), muestra un aviso de error de validación, no guarda ningún registro de préstamo y mantiene el equipo disponible sin permitir su entrega. |

---

### Requisito 2: `RNF-01` — Restricción de acceso a datos personales

| Atributo | Detalle |
|---|---|
| **ID** | `RNF-01` |
| **Tipo** | Requisito No Funcional (RNF — Seguridad / Control de acceso) |
| **Origen** | `F-02, F-03 -> N-05` |
| **Prioridad y motivo** | **P1 - Alta.** El sistema consulta datos personales, matrícula y estatus de adeudos del estudiante en el SII; permitir el acceso sin autenticación compromete la privacidad de la información y la integridad de los registros. |
| **Autor** | Ángel David Pérez Sánchez |
| **Estado** | `Validado` |
| **Tarjeta Trello** | `[RNF-01]: Seguridad y Acceso (Angel)` — [Tablero TecConect 2.0](https://trello.com/b/EZI199d4) |

* **Enunciado verificable:**  
  El sistema debe restringir la consulta de datos personales del estudiante en el SII y el registro de préstamos exclusivamente al personal de ventanilla autenticado con sesión activa y permisos autorizados.

* **Criterios de aceptación y método de comprobación (`F RNF-01`):**

| Escenario | Condición (Dado) | Acción (Cuando) | Resultado observable esperado (Entonces) |
|---|---|---|---|
| **RNF-01.1 (Acceso autorizado)** | Un operador de ventanilla ha iniciado sesión con credenciales válidas y perfil autorizado. | Escanea la credencial QR de un estudiante en la vista inicial (`Vista 01`). | El sistema realiza la consulta al SII y muestra únicamente los datos necesarios para validar el préstamo. |
| **RNF-01.2 (Acceso denegado)** | Un usuario sin sesión activa o sin permisos de ventanilla intenta acceder al módulo de préstamos o consultar datos de un estudiante. | Intenta abrir la vista o ejecutar la consulta. | El sistema deniega el acceso, bloquea la visualización de datos personales y redirige a la pantalla de inicio de sesión. |

* **Comprobación desde el rol de QA / Revisión en U3:**  
  Se verifica mediante revisión visual de control de sesión en el recorrido del prototipo (identificador de operador activo en pantalla) y mediante definición de casos de prueba de control de acceso en la matriz de trazabilidad (Apartado H de `U3-E01`).

---

## 3. Verificación de calidad (QA) y trazabilidad individual

Como responsable de **QA / Revisión**, comprobé que mis dos requisitos cumplan con los criterios de calidad de la especificación:

* [x] **Unicidad y tipo:** Identificadores únicos (`RF-05` funcional y `RNF-01` no funcional), sin duplicar reglas del dominio ni comportamientos previos.
* [x] **Trazabilidad completa:** Ambos requisitos cuentan con origen documentado (`F-02` y `F-03`), necesidad asociada (`N-04` y `N-05`), prioridad `P1` justificada y criterios de aceptación observables.
* [x] **Correspondencia con el prototipo:** `RF-05` se comprueba en `Vista 02` (solicitud/confirmación de matrícula), `Vista 03A` (folio generado), `Vista 03B` (error de matrícula/cancelación) y `Vista 04` (consulta de préstamos activos); `RNF-01` se comprueba transversalmente mediante control de sesión activa.

---

## 4. Control de versiones y referencias

* **Archivo en GitHub:** `docs/U3/aportes/Angel_David_Perez_Aporte.md`
* **Rama individual:** `docs/u3-angel-perez-aporte`
* **Commit registrado:** `docs(u3): agrega aporte individual RF-05 y RNF-01`
* **Tablero Trello:** [Tablero TecConect 2.0](https://trello.com/b/EZI199d4)


### Referencias
1. Instituto Tecnológico Superior de San Pedro de las Colonias. *Trabajos de Fundamentos de Ingeniería de Software - TecConnect*. Documento base del equipo, 08 de octubre de 2026, pp. 1–15 (`trabajos.pdf`).
2. Entrevista semiestructurada a **Encargada de biblioteca**, Instituto Tecnológico Superior de San Pedro de las Colonias. Realizada el 10 de noviembre de 2026 (Acta de entrevista 01).
3. Chávez Rodríguez, R. A. *FIS · U3 · Semana 2 · Especificación A–I, prototipo y cierre*. Material de la asignatura Fundamentos de Ingeniería de Software (SCC-1007), noviembre de 2026.
