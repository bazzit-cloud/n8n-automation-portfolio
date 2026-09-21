# 🚀 Portfolio de Automatización e Integración con n8n

"¡Hola! Construyo automatizaciones que funcionan, conectan herramientas (APIs, bases de datos, CRMs) y no se rompen a la mínima.

En este repositorio no vas a encontrar workflows inflados de 80 nodos ni IA metida con calzador para que quede bonito. Aquí documento proyectos estructurados para resolver cuellos de botella reales en operaciones y ventas. Mi foco está en lo que importa: que los datos lleguen a su sitio sin duplicados, que el código sea mantenible y que el sistema avise por Slack si algo falla."

## 📂 Proyectos

### 🔗 [Proyecto 1: Sistema Inteligente de Captación y Clasificación de Leads con IA](./Proyecto_1_Captacion_Leads.md)
* **Objetivo:** Automatizar la recepción, validación y clasificación de leads desde formularios mediante un LLM (Gemini), asegurando la deduplicación y derivando alertas críticas a Slack ante fallos del sistema.

### 🔄 [Proyecto 2: Sincronización Transaccional HubSpot ↔ PostgreSQL con Idempotencia](./Proyecto_2_HubSpot_Postgres.md)
* **Objetivo:** Diseñar un pipeline de sincronización de datos periódico (Pull/Cron) entre un CRM y una base de datos relacional, garantizando idempotencia mediante claves únicas y observabilidad de errores.

### 🔀 [Proyecto 3: Enrutamiento Inteligente de Leads y Alertas Multicanal](./Proyecto_3_Routing_Alertas.md)
* **Objetivo:** Construir un pipeline tolerante a fallos que normaliza payloads de un CRM, enruta alertas VIP a Telegram y estándar a Slack, e incluye una vía de escape (fallback) para auditar datos incompletos sin detener la ejecución.

## 🛠️ Stack Tecnológico
* **Orquestador:** n8n (Self-hosted / Cloud)
* **Integraciones:** APIs REST, Webhooks, HubSpot API, Google Sheets
* **Bases de Datos:** PostgreSQL
* **Inteligencia Artificial:** Google Gemini (Structured Output & Classification)
* **Monitoreo y Alertas:** Slack (Error Triggers y enrutamiento inteligente por canales)
* **Prácticas:** Idempotencia, gestión de reintentos, manejo tipado de errores, control de versiones..
