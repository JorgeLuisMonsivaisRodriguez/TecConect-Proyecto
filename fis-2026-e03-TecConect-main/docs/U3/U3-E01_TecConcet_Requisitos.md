# U3:  requisitos de TecConect
Equipo y roles: 
[Angel David Perez Sánchez
Alfonso Herrera Diaz
Jorge Luis Monsivais Rodriguez

rol principal
-Analisis (Afonso)
-Documentación, calidad (Angel)
-Desarrollo , coordinación (Jorge)

## A. Identificación y alcance

* **Proceso TO-BE seleccionado:** Solicitud y préstamo de equipo físico en ventanilla mediante credencial digital.
* **Objetivo de esta especificación:** Definir y validar los requisitos para automatizar el proceso de verificación de identidad de alumnos, validación de estatus (vigencia y adeudos), comprobación de disponibilidad y registro digital de préstamos bajo un esquema de cero papel.
* **Dentro del alcance:**
  * Escaneo y lectura del código QR de la credencial digital desde el dispositivo del estudiante.
  * Consulta en base de datos para validación automática de matrícula, estatus de alumno activo y verificación de adeudos.
  * Escaneo e identificación del equipo/herramienta solicitado por código de barras o QR.
  * Comprobación automática de disponibilidad de equipo y generación del registro vinculando alumno, equipo y marca de tiempo.
  * Confirmación digital de recepción por parte del estudiante (mediante NIP o confirmación en pantalla).
  * Emisión de alertas por denegación en caso de inactividad, adeudos o falta de disponibilidad.
* **Fuera del alcance:**
  * Proceso de cobranza o pago de adeudos dentro de la plataforma (solo se notifica el bloqueo).
  * Registro físico o gestión en papel.
  * Mantenimiento físico o reparación del equipo dañado.

## B. Fuentes y necesidades

### B1. Plan de obtención

| Pregunta por resolver | Persona o documento a consultar | Técnica | Responsable | Estado |
| ¿Existe un límite de equipos o herramientas que un alumno activo puede solicitar al mismo tiempo? | Reglamento de Préstamos / Encargado de Ventanilla | Análisis documental / Entrevista | Jorge Luis Monsivais Rodriguez | Pendiente |
| ¿Qué tipo de NIP o método de autenticación se usará para la confirmación digital del alumno en pantalla? | Responsable de Seguridad / TI Institucional | Entrevista | Alfonso | Pendiente |
| ¿Cómo se procede cuando el código QR del equipo está dañado o no se lee correctamente? | Personal de ventanilla de laboratorio | Observación / Entrevista | Ángel | Pendiente |

### B2. Fuentes realmente consultada
Sin fuentes todavía.

## C. Organización del alcance

* **Ruta elegida:** Ruta A (con Épica)
* **Motivo:** El proceso seleccionado engloba múltiples capacidades interactuantes (validación de identidad, verificación de inventario de equipos y firma/confirmación digital de recepción).
* **Épica:** `EP-01: Gestión de Préstamos de Equipo en Ventanilla`
* **Capacidades incluidas:** 
  * Validar credencial y estatus del estudiante.
  * Registrar asignación de equipo mediante escaneo.
  * Autorización y confirmación digital del préstamo.
* **RF vinculados:** por definir
