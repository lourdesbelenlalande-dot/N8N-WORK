# Especificaciones de los seis workflows

## 1. Captación y seguimiento de clientes

**Problema empresarial.** Los leads llegan desde distintos formularios y se pierden por falta de seguimiento.

**Flujo.** `Webhook → Code: validar lead → IF: datos completos → CRM/Google Sheets → correo de bienvenida → tarea de seguimiento`. La rama incompleta devuelve un error controlado y genera una alerta interna. El campo `event_id` evita duplicados.

**Demostración.** Enviar el payload `captacion_cliente` de `datos_prueba.json`, mostrar el registro creado y enseñar qué ocurre cuando falta el correo.

**Criterios de aceptación.** El lead válido se registra una sola vez, recibe confirmación, queda con una tarea de seguimiento y produce un log no sensible. El lead inválido no genera un registro incompleto.

## 2. Agenda automática

**Problema empresarial.** Las solicitudes de cita requieren comprobar disponibilidad y enviar confirmaciones manuales.

**Flujo.** `Webhook → Code: normalizar fecha y zona horaria → Google Calendar/Microsoft 365: consultar disponibilidad → IF: disponible → crear evento → correo/WhatsApp de confirmación`. Si el horario está ocupado, se ofrecen alternativas.

**Demostración.** Enviar `solicitud_cita` con una fecha disponible y otra ocupada. Explicar el tratamiento de zonas horarias y la prevención de reservas duplicadas mediante `request_id`.

**Criterios de aceptación.** No se crean dos eventos para la misma solicitud; el usuario recibe una respuesta clara con fecha, zona horaria y estado.

## 3. Procesamiento de facturas

**Problema empresarial.** Las facturas recibidas por correo o carpeta compartida deben registrarse y revisarse.

**Flujo.** `Google Drive/OneDrive Trigger → descargar PDF → OCR → extracción estructurada con IA → Code: validar totales → IF: confianza suficiente → registrar en Sheets/ERP`. Los documentos de baja confianza van a revisión humana.

**Demostración.** Usar la factura simulada `factura` y una segunda entrada con subtotal + impuesto diferente del total esperado.

**Criterios de aceptación.** El workflow detecta discrepancias, conserva el documento original, evita duplicados por hash o número de factura y no registra automáticamente información incoherente.

## 4. Informes y alertas

**Problema empresarial.** La dirección necesita un resumen periódico de ventas y alertas sobre cambios importantes.

**Flujo.** `Schedule Trigger → obtener ventas → Code Python/JavaScript: agregar por canal → calcular métricas → generar informe → enviar email/Slack/Teams`. Las reglas de alerta se parametrizan, por ejemplo, caída diaria superior al 20%.

**Demostración.** Procesar `ventas`, mostrar total, promedio y distribución por canal, y ejecutar un caso que active una alerta.

**Criterios de aceptación.** El informe contiene periodo, volumen, total y excepciones; los valores se calculan de forma reproducible y el workflow no envía alertas duplicadas.

## 5. Asistente empresarial con RAG

**Problema empresarial.** El equipo necesita respuestas rápidas basadas en políticas y documentos internos.

**Flujo.** `Webhook/Chat Trigger → recibir pregunta → recuperar fragmentos relevantes → construir contexto → agente o LLM → verificar que la respuesta tenga fuentes → responder`. La ingesta documental se muestra como workflow separado o subworkflow: `Drive → extracción de texto → división en fragmentos → embeddings → base vectorial`.

**Demostración.** Usar `pregunta_asistente`, devolver la respuesta de cuatro horas laborables y mostrar la fuente contextual. Probar una pregunta que no esté en los documentos y exigir una respuesta de “no encontrado”.

**Criterios de aceptación.** La respuesta no inventa políticas, incluye fuentes o fragmentos utilizados, limita el contexto y deja registro de la pregunta sin almacenar secretos.

## 6. Integración API/ERP

**Problema empresarial.** Un pedido externo debe transformarse y registrarse en un ERP o API interna.

**Flujo.** `Webhook autenticado → Code Python: validar y normalizar pedido → HTTP Request: crear pedido en ERP sandbox → IF: respuesta 2xx → Respond to Webhook`. Los errores 4xx/5xx se envían a una rama de reintento o cola de revisión.

**Demostración.** Enviar `pedido_erp`, calcular el total y llamar a un endpoint de prueba. Ejecutar también un pedido sin `order_id` y una respuesta simulada de error del ERP.

**Criterios de aceptación.** Solo pasan pedidos válidos; se conserva el `event_id`; las respuestas externas se clasifican por código; se evita duplicar el pedido al reintentar; la clave API o Bearer Token permanece en Credentials.

## Evidencias que debe mostrar cada proyecto

Cada carpeta debe terminar con una captura o exportación del workflow, un ejemplo de entrada, un ejemplo de salida, una prueba de error y una ficha de una página. La ficha debe explicar el problema, la solución, las integraciones, los supuestos, el tiempo de implementación, el mantenimiento mensual y los riesgos conocidos.
