# agente-turnos-odontologia
Agente autónomo de gestión de turnos para consultorio odontológico - n8n + Claude + Airtable
# Agente Autónomo de Gestión de Turnos - Consultorio Odontológico

Sistema de automatización que interpreta mensajes de pacientes en lenguaje natural (WhatsApp/Email), identifica el tipo de consulta y el horario solicitado usando Claude (Anthropic API), y gestiona el turno a través de un flujo con aprobación humana antes de confirmar cualquier cita.

## Stack
- **Orquestador:** n8n
- **Motor de IA:** Claude Sonnet 4.6 (Anthropic API)
- **Base de datos:** Airtable
- **Notificaciones:** Gmail

## Estructura del repositorio
- `diagrama_arquitectura.pdf` — Mapa completo del flujo (triggers, nodos de IA, destino de datos)
- `manual_tecnico.docx` — Estructuras de datos, matriz de costos y documentación de seguridad/resiliencia
- `AGENTE DE TURNOS.json` — Workflow principal exportado de n8n
- `MANEJO DE ERRORES.json` — Workflow de manejo de errores exportado de n8n
- `enlaces.md` — Links a la base de datos, Dashboard público y video demo
- Capturas de pantalla — Evidencia de ejecución del flujo, dashboard, notificaciones y manejo de errores

## Funcionamiento resumido
1. Llega un mensaje del paciente (simulado vía Webhook)
2. Claude interpreta tipo de consulta, horario solicitado y genera un resumen
3. El turno se guarda en Airtable con estado "Interpretado por IA"
4. Se notifica por Gmail a la recepcionista (Human-in-the-loop)
5. La recepcionista confirma o rechaza el turno directamente en Airtable
6. Un workflow separado captura y registra cualquier error del proceso
