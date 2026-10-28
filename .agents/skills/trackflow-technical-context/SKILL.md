---
name: trackflow-technical-context
description: "Use before proposing or implementing technical architecture, stack, integration, or deployment changes for TrackFlow; distinguish repository facts, company legacy systems, and unapproved proposals."
user-invocable: false
---

# Contexto técnico de TrackFlow

## Procedimiento

1. Lee `memory-bank/techContext.md` y consulta el briefing de dominio cuando el cambio dependa de sistemas o procesos actuales de TrackFlow.
2. Verifica las afirmaciones sobre la implementación actual en el código y la documentación del repositorio. No infieras que algo está implementado solo porque aparece en una guía.
3. Clasifica cada tecnología o decisión relevante como:
   - **Observada en el repositorio:** existe en el código o configuración actual.
   - **Arquitectura heredada:** pertenece a los sistemas actuales de TrackFlow, como sus WMS, ERP, scripts Python o proveedores cloud.
   - **Propuesta:** recomendada, pero todavía no aprobada para el entregable.
   - **Decisión confirmada:** acordada explícitamente para el proyecto.
4. No presentes una propuesta —por ejemplo, usar FastAPI— como decisión confirmada ni como componente implementado.
5. Expón los supuestos, restricciones o decisiones faltantes que afecten la solución. Si una nueva decisión queda confirmada, actualiza `memory-bank/techContext.md` para mantener la fuente de verdad.
