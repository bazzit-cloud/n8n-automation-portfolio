# Workflows exportados

Los cinco workflows en formato JSON, listos para importar en n8n (abre un workflow vacío y pega el contenido con Ctrl+V).

| Archivo | Proyecto |
|---|---|
| `01-captacion-leads.json` | Captación y clasificación de leads con IA |
| `02-hubspot-postgres.json` | Sincronización de contactos HubSpot → PostgreSQL |
| `03-aviso-deals.json` | Aviso de deals por importe (Slack / Telegram) |
| `04-alertas-de-error.json` | Alertas de error comunes a todos los flujos |
| `05-auditor-seo.json` | Auditor SEO técnico por sitemap (bajo demanda y vigilancia semanal) |

He quitado las credenciales y he sustituido los datos de mi cuenta por marcadores: `TU_GOOGLE_SHEET_ID`, `TU_CANAL_COMERCIAL`, `TU_CANAL_OPERACIONES`, `TU_CANAL_CRM`, `TU_CANAL_REVISION`, `TU_CHAT_ID_TELEGRAM`, `ID_WORKFLOW_LEADS`, `ID_WORKFLOW_HUBSPOT` y, en el auditor SEO, `TU_CANAL_CLIENTE` y la web de ejemplo del nodo «Webs vigiladas». Al importarlos, cambia esos valores y asigna tus credenciales.
