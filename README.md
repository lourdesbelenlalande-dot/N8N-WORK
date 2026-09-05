# Portafolio de automatización e IA empresarial con n8n

Este repositorio reúne seis demostraciones de automatización empresarial creadas con n8n, Webhooks, APIs, Python/JavaScript y servicios de inteligencia artificial. El objetivo es mostrar cómo convertir procesos manuales en soluciones seguras, medibles y mantenibles.

## Proyectos incluidos

| Proyecto | Problema que resuelve | Tecnologías y conceptos |
|---|---|---|
| [01 — Captación y seguimiento](01_clientes_seguimiento/) | Leads dispersos y seguimiento manual | Webhook, validación, CRM, idempotencia |
| [02 — Agenda automática](02_citas/) | Reservas y confirmaciones manuales | Calendario, zonas horarias, conflictos |
| [03 — Procesamiento de facturas](03_facturas_ocr/) | Registro manual y errores en documentos | OCR, extracción, validación, revisión humana |
| [04 — Informes y alertas](04_informes_alertas/) | Datos sin análisis operativo | ETL, métricas, alertas y reporting |
| [05 — Asistente empresarial](05_asistente_rag/) | Búsqueda lenta en documentación interna | RAG, contexto, fuentes y control de alucinaciones |
| [06 — Integración API/ERP](06_integracion_api_erp/) | Sistemas que no comparten el mismo formato | REST, API Key/Bearer, Python, reintentos |

## Cómo revisar una demostración

Importa el JSON del proyecto en una instancia local de n8n, pulsa **Listen for test event** en el nodo Webhook y envía el payload correspondiente desde `datos_prueba.json`. Cada workflow está desactivado y utiliza datos simulados; no se incluyen credenciales reales.

La versión inicial prioriza una demostración reproducible con el patrón `Webhook → Code → Respond to Webhook`. En una implementación real, los nodos de demostración se conectan al CRM, calendario, proveedor OCR, base vectorial, servicio de IA o ERP del cliente.

## Buenas prácticas demostradas

Los workflows incluyen validación de entradas, clasificación de errores, separación entre configuración y credenciales, pruebas del caso exitoso y del caso inválido, y documentación de ampliaciones. Para producción se recomienda añadir autenticación del Webhook, HTTPS, idempotencia persistente, control de reintentos y registro de eventos sin datos sensibles.

## Documentación

- [Mapa del portafolio](PORTAFOLIO.md)
- [Especificaciones técnicas](ESPECIFICACIONES.md)
- [Instrucciones de importación y pruebas](IMPORTAR_Y_PROBAR.md)
- [Ficha comercial y estimación de esfuerzo](FICHA_COMERCIAL.md)
- [Datos simulados](datos_prueba.json)

## Perfil profesional

Especialista freelance en automatización e IA empresarial. Diseño workflows con n8n para integrar formularios, APIs, Webhooks, CRM, ERP, correo, calendarios, documentos y asistentes de IA, con foco en validación, documentación, pruebas y mantenimiento.
