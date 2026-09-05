# Portafolio profesional de automatización e IA empresarial

## Objetivo

Este portafolio está diseñado para demostrar las competencias solicitadas en puestos freelance de automatización: análisis de viabilidad, diseño de soluciones, integración de APIs y webhooks, procesamiento de documentos, CRM/ERP, IA aplicada, pruebas, documentación, estimación de costes y mantenimiento.

Cada proyecto debe incluir un workflow importable, datos simulados, instrucciones de instalación, diagrama lógico, casos de éxito y error, y una ficha comercial con alcance, supuestos, plazo estimado y mantenimiento.

## Proyectos

| Nº | Proyecto | Flujo principal | Competencias demostradas | Integraciones sugeridas |
|---|---|---|---|---|
| 1 | Captación y seguimiento de clientes | Formulario → validación → CRM → correo/WhatsApp → tarea de seguimiento | Webhooks, CRM, API, reglas de negocio, idempotencia | Webhook, Google Sheets/Airtable, HubSpot/Pipedrive, Gmail, WhatsApp Cloud API |
| 2 | Agenda automática | Solicitud → disponibilidad → reserva → confirmación → recordatorio | Calendarios, zonas horarias, validación, manejo de conflictos | Google Calendar/Microsoft 365, Gmail, WhatsApp o Telegram |
| 3 | Procesamiento de facturas | PDF → OCR → extracción → validación → registro → alerta | Documentos, OCR, extracción estructurada, revisión humana | Drive/OneDrive, OCR, OpenAI/Claude/Gemini, Sheets/ERP |
| 4 | Informes y alertas | Datos → agregación → análisis → informe → alerta | ETL, métricas, programación, reporting y observabilidad | Sheets/ERP, Code Python, Gmail/Slack/Teams |
| 5 | Asistente empresarial | Pregunta → recuperación documental → contexto → respuesta con fuentes | IA, RAG, control de contexto, evaluación de respuestas | Drive/Notion, base vectorial, OpenAI/Claude/Gemini |
| 6 | Integración API/ERP | Webhook → autenticación → transformación Python → ERP → respuesta | APIs, Bearer/API Key, webhooks, Python, reintentos y errores | API REST, ERP de prueba, base de datos, Respond to Webhook |

## Orden de construcción

Se comenzará con los proyectos 1 y 6 porque muestran rápidamente el núcleo profesional de n8n: recepción de eventos, autenticación, transformación y comunicación con sistemas externos. Después se implementarán los proyectos 2 y 4 para mostrar automatizaciones operativas recurrentes. Finalmente se desarrollarán los proyectos 3 y 5, que incorporan documentos e inteligencia artificial y aportan diferenciación comercial.

## Criterio de calidad

Un workflow no se considerará terminado solo porque funcione con el caso feliz. Debe incluir entradas de prueba, validación, manejo de errores, logs no sensibles, documentación de credenciales, explicación del coste de servicios externos y una descripción de cómo modificarlo o mantenerlo.

> El objetivo no es mostrar muchos nodos, sino demostrar que puedes convertir una necesidad empresarial en una solución segura, medible y mantenible.
