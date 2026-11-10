**Proyecto:** TecConnect  
**Sección del proceso asignada:** Validación de estatus de alumnos y gestión técnica del escaneo de credenciales QR  
**Rol principal de la U3:** Desarrollo y Coordinación  

## 1. Información que necesito obtener
* **Pregunta 1:** ¿Existe algún límite o restricción en la base de datos sobre la cantidad de equipos activos que un alumno puede tener prestados simultáneamente?  
* **Pregunta 2:** ¿Qué formato o estructura técnica contiene exactamente el código QR de la credencial digital para asegurar que el lector lo procese sin errores?  
* **Técnica elegida y motivo:** Análisis documental (revisión de manuales técnicos o esquemas de base de datos) y entrevista breve al responsable de sistemas o encargados de ventanilla.  
* **Fuente a consultar:** Documentación interna del sistema y personal de operación en ventanilla.  
* **Estado:** Pendiente de consulta.  

## 2. Información que ya tengo
* **Fuente real:** Aún no disponible(Pendiente) 
* **Hallazgo comprobable:** Se ha delimitado el flujo técnico preliminar del TO-BE donde el sistema valida matrícula, estatus activo y adeudos mediante consulta a base de datos tras el escaneo del QR.  
* **Dudas:** Falta confirmar los tiempos de respuesta estimados de la base de datos al momento de hacer la validación masiva en horas pico.  

## 3. Necesidad identificada
* **Necesidad preliminar:** El sistema debe consultar de manera automatizada la base de datos para extraer la matrícula del estudiante, verificar su estatus vigente y bloquear el préstamo en caso de adeudos pendientes, garantizando la integridad del proceso de cero papel.
