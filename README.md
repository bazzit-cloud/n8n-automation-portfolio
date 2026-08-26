# 🚀 Portfolio de Automatización e Integración con n8n

¡Hola! Soy Automation & Integration Engineer especializado en la construcción de flujos de datos resilientes, automatización de procesos empresariales (RevOps/Operations) y aplicación práctica de Inteligencia Artificial (IA) sin sobreingeniería.

Este repositorio documenta proyectos técnicos reales diseñados para resolver problemas de negocio, priorizando la fiabilidad, la idempotencia, el manejo de errores y la observabilidad.

## 📂 Proyectos

### 🔗 [Proyecto 1: Sistema Inteligente de Captación y Clasificación de Leads con IA](./Proyecto_1_Captacion_Leads.md)
* **Objetivo:** Automatizar la recepción, validación y clasificación de leads desde formularios mediante un LLM (Gemini), asegurando la deduplicación y derivando alertas críticas a Slack ante fallos del sistema.

### 🔄 [Proyecto 2: Sincronización Transaccional HubSpot ↔ PostgreSQL con Idempotencia](./Proyecto_2_HubSpot_Postgres.md)
* **Objetivo:** Diseñar un pipeline de sincronización de datos periódico (Pull/Cron) entre un CRM y una base de datos relacional, garantizando idempotencia mediante claves únicas y observabilidad de errores.

## 🛠️ Stack Tecnológico
* **Orquestador:** n8n (Self-hosted / Cloud)
* **Integraciones:** APIs REST, Webhooks, HubSpot API, Google Sheets
* **Bases de Datos:** PostgreSQL
* **Inteligencia Artificial:** Google Gemini (Structured Output & Classification)
* **Monitoreo y Alertas:** Slack (Error Triggers y enrutamiento inteligente por canales)
* **Prácticas:** Idempotencia, gestión de reintentos, manejo tipado de errores, control de versiones..
