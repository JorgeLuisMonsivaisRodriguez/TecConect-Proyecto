# Aporte individual U3-E02 — TecConnect

**Alumno:** Ángel David Pérez Sánchez  
**Responsabilidad en la unidad:** Documentación  
**Parte del proceso propuesta para este aporte:** Registro de la operación y actualización de inventario.  
**Estado:** Validado institucionalmente.

## 1. Fuente y hallazgo
**Fuente documental (F-03):** Entrevista semiestructurada con la Encargada de biblioteca, realizada el 10/11/2026. 

**Hallazgo documentado:** El proceso manual mediante bitácoras de Excel provoca que en ocasiones se presten equipos que ya estaban apartados o que no se registre la hora exacta de salida. En la entrevista se confirmó que, una vez que el alumno digita su NIP, el sistema debe generar un registro inalterable y actualizar inmediatamente el estado del equipo para que ya no aparezca disponible.

**Necesidad identificada (N-04 y N-05):** Contar con un registro digital consultable de cada préstamo autorizado (vinculando alumno y equipo) y automatizar el bloqueo del equipo prestado para mantener la congruencia del inventario.

## 2. Requisitos propuestos y validados

### RF-05: Guardar el préstamo autorizado
*   **Tipo:** Requisito Funcional.
*   **Autor:** Ángel David Pérez Sánchez.
*   **Prioridad y motivo:** P1 - Alta. Sustituye la bitácora manual de Excel y es el objetivo central del proceso TO-BE.
*   **Enunciado verificable:** Después de recibir la confirmación digital del estudiante mediante NIP, el sistema debe guardar el préstamo autorizado relacionando el identificador del estudiante, el código del equipo y la fecha y hora exacta de la operación, y generar un folio visible.
*   **Criterio de aceptación (F RF-05):** 
    *   *Condición (Dado):* Las validaciones de alumno y equipo fueron exitosas y el estudiante ingresa su NIP correcto.
    *   *Acción (Cuando):* El sistema procesa y guarda la operación.
    *   *Resultado esperado (Entonces):* Se conserva un registro vinculado (estudiante, equipo, fecha/hora), se muestra en pantalla el mensaje "Préstamo confirmado" con su número de folio, y el personal puede proceder a entregar físicamente el equipo.

### RF-06: Actualización automática de disponibilidad del equipo
*   **Tipo:** Requisito Funcional.
*   **Autor:** Ángel David Pérez Sánchez.
*   **Prioridad y motivo:** P1 - Alta. Es crucial para evitar conflictos físicos donde se intente prestar un equipo que acaba de ser entregado a otra persona.
*   **Enunciado verificable:** Simultáneamente a la generación del préstamo, el sistema debe actualizar el estado del equipo escaneado en la base de datos de inventario, cambiándolo de "Disponible" a "En uso".
*   **Criterio de aceptación (F RF-06):** 
    *   *Condición (Dado):* Se acaba de generar y guardar el registro de un préstamo autorizado.
    *   *Acción (Cuando):* El sistema actualiza el registro interno del equipo.
    *   *Resultado esperado (Entonces):* El equipo cambia su estado a "En uso". Si otro usuario intenta escanear ese mismo código de equipo en la vista de acción, el sistema mostrará que ya no está disponible.

## 3. Ubicación y control de cambios
**Ruta en el repositorio:** `docs/U3/aportes/Angel_David_Perez_Aporte.md`  
**Commit descriptivo:** `docs(u3): añade aporte individual sobre registro de préstamo y actualización de inventario (RF-05, RF-06)`
