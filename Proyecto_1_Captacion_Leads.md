# 🚀 Proyecto 1: Sistema Inteligente de Captación y Clasificación de Leads con IA

## 📖 Descripción del Problema
El equipo de ventas perdía tiempo filtrando manualmente leads entrantes desde formularios. No había un sistema automatizado para descartar correos duplicados, calificar la calidad del lead en tiempo real y guardarlo en la base de datos de manera fiable.

## 🎯 Objetivo (Portfolio)
Construir un flujo automatizado que reciba datos de un formulario, utilice Inteligencia Artificial para clasificar la intención del cliente, evite la creación de registros duplicados y almacene la información estructurada, contando con una red de seguridad para errores.

## 🏗 Arquitectura y Tecnologías
* **Orquestador:** n8n
* **Trigger:** Webhook / Form Submission
* **Inteligencia Artificial:** Google Gemini (Clasificación de texto)
* **Base de Datos:** Google Sheets
* **Observabilidad / Alertas:** Slack (vía Error Trigger global)

## ⚙️ Decisiones Técnicas Destacadas
1. **Deduplicación e Idempotencia:** Antes de insertar un nuevo registro, el workflow consulta la base de datos de Google Sheets (`Get Row`). Si el email ya existe, el lead es bloqueado mediante un nodo `IF` (Filtro Anti-Duplicados) para mantener la integridad de los datos.
2. **LLM como Motor de Clasificación:** En lugar de usar IA para generar texto libre, se utiliza Gemini con un prompt estructurado para analizar la entrada del usuario y devolver una categorización estricta (ej. ALTO, MEDIO, BAJO), facilitando el enrutamiento posterior.
3. **Manejo de Errores y Enrutamiento (Routing):** El workflow está protegido por un flujo global de alertas (`Error Trigger`). Si la API de Google falla (ej. token caducado) o el LLM da error, los metadatos de la ejecución (`$json.workflow.name`, error message) se envían a un nodo `Switch` que enruta la alerta crítica al canal de Slack `#operations-team`.

## 🛡️ Seguridad
* Las credenciales (OAuth2 para Google, API Keys para IA y Slack) están aisladas en el gestor de credenciales de n8n. No hay secretos *hardcodeados* en los nodos.

## 🚧 Limitaciones y Posibles Mejoras (Next Steps)
* **Limitación Actual:** Google Sheets no es ideal para grandes volúmenes de datos transaccionales ni búsquedas indexadas de alta velocidad.
* **Mejora Propuesta:** Añadir un mecanismo de *Retry* (reintentos) en las llamadas al LLM por si la API de Gemini devuelve un error 500 temporal, y migrar la base de datos a PostgreSQL (implementado en el Proyecto 2).
