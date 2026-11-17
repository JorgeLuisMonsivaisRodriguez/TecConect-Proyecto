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

Para el proceso **TO-BE: Gestión digital del préstamo de equipo de cómputo y herramientas**, mi aporte se enfoca en el inicio del flujo operativo (acceso principal al sistema y punto de partida de la solicitud), en la claridad visual de la retroalimentación ante errores de operación, y en la coordinación técnica y diseño del recorrido del prototipo de baja fidelidad.

| ID | Técnica o documento | Fecha | Hallazgo documentado | Estado |
| **F-01** | Revisión documental: acuerdo y descripción del proyecto  | 08/10/2026 | TecConnect contempla la automatización mediante credencialización digital y control de préstamos entre estudiantes y personal de ventanilla. | Documentado |
| **F-02** | Revisión documental: proceso actual AS-IS  | 08/10/2026 | El proceso actual carece de un punto de entrada digital estandarizado y depende de registros manuales sin retroalimentación clara ni consulta inmediata. | Documentado |
| **F-03** | Entrevista semiestructurada: Encargada de biblioteca (ITSSPC) y análisis de guías U3 | 10/11/2026 | Se confirmó la necesidad de contar con una interfaz inicial ágil para iniciar la solicitud de préstamo y de notificar mediante texto claro cualquier rechazo o conflicto de disponibilidad. | Validado (Acta 01) |

### Necesidades identificadas
* **N-01 (Punto de entrada accesible al flujo de préstamo):** Sustituir la solicitud verbal o en bitácora manual por una pantalla principal digital con una acción visible e intuitiva para iniciar el préstamo de equipo.
* **N-02 (Retroalimentación clara y comprensible ante errores):** Garantizar que el sistema informe mediante mensajes de texto explícitos cuando una solicitud no pueda procesarse (por conflicto de horario o equipo ocupado) y ofrezca una ruta clara para corregir los datos.

---

## 2. Requisitos individuales (RF-01 y RNF-02)

Requisito 1: RF-01 — Pantalla de inicio y punto de entrada al sistema

| Atributo | Detalle |
| **ID** | RF-01 |
| **Tipo** | Requisito Funcional (RF) |
| **Prioridad y motivo** | P1 - Alta: Es el punto de partida indispensable del recorrido; sin una vista inicial con una acción principal visible, la persona usuaria no puede comenzar el proceso de solicitud de préstamo. |
| **Autor** | Jorge Luis Monsivais Rodriguez |
| **Estado** | Validado |
| **Tarjeta Trello** | [RF-01]: Pantalla de inicio y acceso principal (Jorge) — Tablero TecConect 2.0 |

* **Enunciado verificable:**
  El sistema debe proveer una pantalla de inicio accesible que muestre la bienvenida a la plataforma y un botón o enlace visible para iniciar de forma directa el proceso de solicitud de préstamo de equipo.

* **Criterios de aceptación verificables (F RF-01):**
| Escenario | Condición (Dado) | Acción (Cuando) | Resultado observable esperado (Entonces) |
| RF-01 (Éxito) | La persona usuaria accede a la pantalla principal de la aplicación (Vista 01). | Visualiza la interfaz de bienvenida y presiona el botón *"Agendar / Solicitar"*. | El sistema responde dirigiendo al usuario hacia el formulario de captura de datos de la solicitud (Vista 02). |
| **RF-01.2 (Alternativa / Navegación secundaria)** | La persona usuaria ya cuenta con un folio previo y se encuentra en la pantalla principal (Vista 01). | Selecciona la opción de consulta en la barra de navegación inferior (*"Consultar"*). | El sistema redirige directamente a la pantalla de búsqueda y consulta de estado (Vista 04) sin obligar a iniciar una nueva solicitud. |


### Requisito 2: RF-02 — Claridad de errores mediante texto explicativo en interfaz

| Atributo | Detalle |
| **ID** | RF-02 |
| **Tipo** | Requisito No Funcional (RF — Usabilidad / Interfaz) |
| **Prioridad y motivo** | **P2 - Media.** Asegura la usabilidad y comprensión del sistema; los mensajes de error textuales y descriptivos evitan confusiones cuando una solicitud es rechazada. |
| **Autor** | Jorge Luis Monsivais Rodriguez |
| **Estado** | Validado |
| **Tarjeta Trello** | [RF-02]: Claridad de errores en interfaz y prototipo (Jorge) — Tablero TecConect 2.0 |

* **Enunciado verificable:**
  Los avisos de error derivados de fallas o conflictos en la solicitud de préstamo (como un horario o equipo ya reservado) deben notificarse mediante mensajes de texto explicativos claros en la interfaz, sin depender exclusivamente de íconos o indicadores de color aislados.

* **Criterios de aceptación y método de comprobación (RF-02):**

| Escenario | Condición (Dado) | Acción (Cuando) | Resultado observable esperado (Entonces) |
| **RF-02.1 (Notificación textual de error)** | El usuario intenta confirmar una solicitud con un horario o equipo no disponible (Vista 02). | El sistema ejecuta la validación y detecta el conflicto de disponibilidad. | Se despliega la pantalla de error (Vista 03B) mostrando un texto explicativo claro que detalla el motivo del rechazo ("El horario seleccionado ya está reservado...") y un botón de retorno ("Regresar y corregir"). |

* **Comprobación desde el rol de Coordinación y Desarrollo en U3:**
  Se verifica mediante inspección visual directa del recorrido gráfico en el prototipo de baja fidelidad (`docs/U3/prototipo/`), comprobando que los estados de respuesta estén claramente diferenciados (`03A` Éxito y `03B` Error con texto explicativo) y conectados mediante flechas de flujo.

---

## 3. Verificación técnica y trazabilidad individual

Como responsable de **Coordinación / Desarrollador**, comprobé que mis dos requisitos y el diseño del prototipo cumplan con los estándares de calidad de la especificación:
* **Unicidad y tipo:** Identificadores únicos (`RF-01` funcional y `RF-02` no funcional), sin duplicar reglas del dominio ni traslaparse con los requisitos de los demás integrantes (`RF-05` y `RF-01`).
* **Trazabilidad completa:** Ambos requisitos cuentan con origen documentado (`F-01`, `F-02` y `F-03`), necesidad asociada (`N-01` y `N-02`), prioridad justificada y criterios de aceptación observables.
* **Correspondencia con el prototipo:** `RF-01` se comprueba en Vista 01 (pantalla de inicio con acceso visible hacia Vista 02); `RF-02` se comprueba en Vista 03 (mensaje de error explicativo en texto y flecha de retorno hacia Vista 02). 


## 4. Control de versiones y referencias

* **Archivo en GitHub:** `docs/U3/aportes/Jorge_Luis_Monsivais_Rodriguez_Aporte.md`
* **Rama individual:** `docs/U3-jorge-monsivais`
* **Commit registrado:** `docs(u3): agrega aporte individual RF-01 y RNF-02`
* **Tablero Trello:** Tablero TecConect 2.0


