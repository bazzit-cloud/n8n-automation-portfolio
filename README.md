# 🚀 Proyecto 2: Sincronización Transaccional HubSpot ↔ PostgreSQL con Idempotencia y Observabilidad

## 📖 Descripción del Problema
El equipo de operaciones necesitaba sincronizar de forma desatendida los contactos generados en HubSpot con una base de datos relacional (PostgreSQL) para su posterior análisis y tratamiento interno, evitando la intervención manual y garantizando la integridad de los registros.

## 🎯 Objetivo (Portfolio)
Diseñar un pipeline de datos basado en *Polling* (Pull) que consulte periódicamente un CRM, valide la unicidad de cada registro para garantizar idempotencia, persista la información en PostgreSQL de forma resiliente y cuente con un sistema inteligente de enrutamiento de errores hacia Slack.

## 🏗 Arquitectura y Tecnologías
* **Orquestador:** n8n
* **Trigger:** Schedule Trigger (Cron job a intervalos regulares)
* **Origen de Datos (CRM):** HubSpot API (HTTP Request)
* **Base de Datos:** PostgreSQL (Upsert / Inserción segura)
* **Observabilidad / Alertas:** Slack (vía Error Trigger global y nodo Switch)

## ⚙️ Decisiones Técnicas Destacadas
1. **Arquitectura Pull vs Push:** A diferencia del Proyecto 1 basado en Webhooks (eventos en tiempo real), este sistema utiliza un *Schedule Trigger* para consultar periódicamente la API de HubSpot, adaptándose a escenarios donde los webhooks del CRM no están disponibles o requieren sincronización programada.
2. **Idempotencia y Prevención de Duplicados:** Para evitar que ejecuciones concurrentes o reintentos dupliquen filas en PostgreSQL, se utiliza el identificador único del contacto en HubSpot (`hubspot_id`) como clave de restricción (*upsert* o validación previa).
3. **Resiliencia ante Fallos de Red:** Los nodos de integración con bases de datos están configurados con una política de reintentos controlados (*retries*) para absorber intermitencias temporales en la red o caídas breves del servidor de base de datos.
4. **Enrutamiento Inteligente de Errores (Routing):** Un sistema centralizado de captura de errores analiza el nombre del workflow afectado mediante un nodo `Switch` y deriva la alerta específica al canal de Slack correspondiente (`#crm-hubspot`), evitando notificaciones genéricas.

## 🛡️ Seguridad
* Aislamiento estricto de credenciales de HubSpot, conexión a base de datos (PostgreSQL) y tokens de Slack mediante el gestor seguro de n8n.

## 🚧 Limitaciones y Posibles Mejoras (Next Steps)
* **Limitación Actual:** Consultar todos los registros en cada intervalo puede saturar la API si el volumen de contactos crece exponencialmente.
* **Mejora Propuesta:** Implementar paginación y filtrado por marcas de tiempo (*timestamp delta*) para sincronizar únicamente los registros modificados desde la última ejecución exitosa.

## 📸 Capturas de Pantalla
*(Añade aquí una captura de tu workflow HubSpot-Postgres y otra del canal de Slack #crm-hubspot recibiendo la alerta)*
