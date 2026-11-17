Institución: Instituto Tecnológico Superior de San Pedro de las Colonias  
Carrera: Ingeniería en Sistemas Computacionales  
Asignatura: Fundamentos de Ingeniería de Software (SCC-1007)  
Grupo: 5° A  
Docente: Ruth Aivi Chávez Rodríguez  
Alumno: Jorge Luis Monsivais Rodriguez  
Proyecto: TecConnect  
Rol en Unidad 3: Project Coordinator / Lead Developer  
Fecha de elaboración: 17 de noviembre de 2026  

## 1. Fuentes de información, hallazgos y necesidades

Para el proceso **TO-BE: Gestión digital del préstamo de libros en ventanilla de Biblioteca**, mi aporte se enfoca en el inicio del flujo operativo (escaneo de credencial QR del estudiante en ventanilla), en la validación automática de estatus académico y adeudos en el SII, y en la coordinación técnica y diseño de la secuencia de wireframes de baja fidelidad.

| ID | Técnica o documento | Fecha | Hallazgo documentado | Estado |
| :--- | :--- | :--- | :--- | :--- |
| **F-01** | Revisión documental: acuerdo y descripción del proyecto | 08/10/2026 | TecConnect contempla la automatización de trámites estudiantiles mediante credencialización digital QR y control de préstamos entre estudiantes y personal de ventanilla. | Documentado |
| **F-02** | Revisión documental: proceso actual AS-IS (`trabajos.pdf`) | 08/10/2026 | El proceso actual de préstamo de libros depende de captura manual en bitácora, revisión lenta de credenciales y falta de consulta inmediata de préstamos activos. | Documentado |
| **F-03** | Entrevista semiestructurada: Encargada de biblioteca (ITSSPC) | 10/11/2026 | Se confirmó que solo alumnos con estatus activo en el SII pueden solicitar libros, que el sistema debe bloquear el préstamo ante multas o libros vencidos pendientes, y que el alumno confirma con su matrícula. | Validado (Acta 01) |

### Necesidades identificadas
* **N-01 (Identificación ágil del estudiante en ventanilla):** Sustituir la captura manual de datos de credencial por una lectura inmediata del código QR del estudiante al iniciar el trámite de préstamo de libro.
* **N-02 (Validación automática de estatus y bloqueo por adeudos):** Garantizar que el sistema consulte en el SII la vigencia académica y bloquee automáticamente el préstamo mediante un mensaje claro cuando existan multas o libros pendientes de devolución.

---

## 2. Requisitos individuales (RF-01 y RF-02)

### Requisito 1: RF-01 — Escaneo de credencial digital QR y recuperación de datos del alumno

| Atributo | Detalle |
| :--- | :--- |
| **ID** | RF-01 |
| **Tipo** | Requisito Funcional (RF) |
| **Prioridad y motivo** | **P1 - Alta:** Es el punto de partida indispensable del recorrido en ventanilla; sin la lectura del código QR no se puede identificar al estudiante para iniciar el préstamo del libro. |
| **Autor** | Jorge Luis Monsivais Rodriguez |
| **Estado** | Validado |
| **Tarjeta Trello** | `[TC-05]` / `[RF-01]`: Escaneo de credencial QR (Jorge) — Tablero TecConect 2.0 |

* **Enunciado verificable:**
  El sistema debe leer el código QR de la credencial digital del estudiante desde la interfaz de ventanilla y recuperar automáticamente su matrícula y nombre completo en el formulario de registro de préstamo.

* **Criterios de aceptación verificables (`RF-01`):**

| Escenario | Condición (Dado) | Acción (Cuando) | Resultado observable esperado (Entonces) |
| :--- | :--- | :--- | :--- |
| **RF-01.1 (Éxito — QR válido)** | El personal de ventanilla accede a la pantalla inicial (`01. Inicio`) y presiona *Iniciar préstamo / Escanear QR*. | Escanea el código QR vigente de la credencial digital del alumno en la vista `02. Capturar y confirmar`. | El sistema lee el código y despliega en pantalla la matrícula (`22100458`) y el nombre del estudiante en menos de 2 segundos. |
| **RF-01.2 (Error / Alternativa — QR ilegible)** | El personal de ventanilla intenta leer una credencial en la vista `02. Capturar y confirmar`. | El código QR presenta daños, baja resolución o no corresponde al formato institucional. | El sistema muestra un mensaje de error claro (*"Código QR no reconocido; intente nuevamente"*) y detiene el avance hacia la confirmación. |

---

### Requisito 2: RF-02 — Validación de estatus en el SII y bloqueo por adeudos en Biblioteca

| Atributo | Detalle |
| :--- | :--- |
| **ID** | RF-02 |
| **Tipo** | Requisito Funcional (RF) |
| **Prioridad y motivo** | **P1 - Alta:** Asegura el cumplimiento directo de las reglas institucionales de Biblioteca (`RG-01` y `RG-02`), impidiendo prestar libros a alumnos inactivos o con adeudos vigentes. |
| **Autor** | Jorge Luis Monsivais Rodriguez |
| **Estado** | Validado |
| **Tarjeta Trello** | `[TC-06]` / `[RF-02]`: Validación SII y bloqueo por adeudos (Jorge) — Tablero TecConect 2.0 |

* **Enunciado verificable:**
  El sistema debe consultar automáticamente el estatus académico del estudiante en el SII y su historial en Biblioteca, bloqueando la operación y desplegando el motivo explícito en texto cuando detecte inactividad académica, multas vigentes o libros pendientes de devolución.

* **Criterios de aceptación y método de comprobación (`RF-02`):**

| Escenario | Condición (Dado) | Acción (Cuando) | Resultado observable esperado (Entonces) |
| :--- | :--- | :--- | :--- |
| **RF-02.1 (Éxito — Alumno elegible)** | El sistema identificó la matrícula de un estudiante inscrito activo y sin adeudos en Biblioteca (`Vista 02`). | Ejecuta la consulta automática al SII y registros de Biblioteca. | Muestra el indicador *"Estatus ACTIVO · Sin adeudos"* y habilita continuar con el escaneo del libro y la confirmación por matrícula. |
| **RF-02.2 (Error — Bloqueo por adeudo o baja)** | Se escanea la credencial de un alumno con multa vigente, libro vencido sin devolver o baja académica. | El sistema evalúa las condiciones de elegibilidad antes de confirmar el préstamo. | Bloquea el registro, transita a la vista `03B. Préstamo bloqueado` mostrando en texto claro el motivo del rechazo y habilita el botón *"Regresar y corregir"*. |

* **Comprobación desde el rol de Coordinación y Desarrollo en U3:**
  Se verifica mediante inspección directa de la secuencia de wireframes de baja fidelidad (`docs/U3/prototipo/`), comprobando que las pantallas de entrada (`01`), captura/validación (`02`) y respuesta de bloqueo (`03B`) muestren claramente el estado de validación y las transiciones mediante flechas de flujo.

---

## 3. Verificación técnica y trazabilidad individual

Como responsable de **Coordinación / Desarrollador**, comprobé que mis dos requisitos y el diseño del prototipo cumplan con los estándares de calidad de la especificación:
* **Unicidad y tipo:** Identificadores únicos (`RF-01` y `RF-02`), ambos funcionales, sin duplicar reglas del dominio ni traslaparse con los requisitos de los demás integrantes (`RF-03`, `RF-04`, `RF-05` y `RNF-01`).
* **Trazabilidad completa:** Ambos requisitos cuentan con origen documentado (`F-01`, `F-02` y `F-03`), necesidad asociada (`N-01` y `N-02`), prioridad justificada (`P1`) y criterios de aceptación observables de éxito y error.
* **Correspondencia con el prototipo:** `RF-01` se comprueba en las vistas `01. Inicio` y `02. Capturar y confirmar`; `RF-02` se comprueba en las vistas `02. Capturar y confirmar` y `03B. Préstamo bloqueado` (con mensaje textual de rechazo y flecha de retorno hacia `02`).

---

## 4. Control de versiones y referencias

* **Archivo en GitHub:** `docs/U3/aportes/Jorge_Luis_Monsivais_Rodriguez_Aporte.md`
* **Rama individual:** `docs/U3-jorge-monsivais`
* **Commit registrado:** `docs(u3): agrega aporte individual RF-01 y RF-02`
* **Tablero Trello:** Tablero *TecConect 2.0* (`[TC-05]` y `[TC-06]`)
* **Fuentes consultadas:** Entrevista semiestructurada con la Encargada de Biblioteca del ITSSPC (10/11/2026, Acta 01), documentación base del proyecto *TecConnect* (`trabajos.pdf`, Unidad 2) y guía de la asignatura *Fundamentos de Ingeniería de Software (SCC-1007)*.
