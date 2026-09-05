# Importar y probar los seis workflows

## Importación

En n8n, abre el menú de workflows y selecciona **Import from File**. Importa uno de los archivos `workflow_*.json` de las seis carpetas. Los workflows están desactivados y no contienen credenciales reales.

## Primera prueba

Abre el nodo Webhook y pulsa **Listen for test event**. Copia la Test URL y envía el ejemplo correspondiente de `datos_prueba.json` con `curl`. Revisa el resultado en el nodo **Respond to Webhook** y en la ejecución manual.

| Proyecto | Archivo |
|---|---|
| Captación de leads | `01_clientes_seguimiento/workflow_leads.json` |
| Agenda | `02_citas/workflow_appointment.json` |
| Facturas | `03_facturas_ocr/workflow_invoice.json` |
| Informes | `04_informes_alertas/workflow_report.json` |
| Asistente | `05_asistente_rag/workflow_question.json` |
| API/ERP | `06_integracion_api_erp/workflow_order.json` |

## Personalización para una demo profesional

Los archivos actuales son una base demostrativa sin conexiones externas. Sustituye o amplía el nodo Code con los nodos de CRM, calendario, OCR, correo, proveedor de IA o ERP que quieras enseñar. Selecciona las credenciales desde la interfaz de n8n; no escribas claves dentro de los JSON exportados.

Antes de activar un workflow, prueba el caso correcto, un campo obligatorio ausente, una solicitud duplicada y un error de la integración externa. Configura autenticación Header Auth en los Webhooks de producción y usa URLs HTTPS cuando el servicio quede accesible desde Internet.

## Nota sobre credenciales

No se incluyen credenciales porque dependen de tus cuentas y de los servicios que elijas. La ausencia de una credencial en el JSON es intencional: permite que el selector de n8n siga siendo editable y evita publicar secretos.
