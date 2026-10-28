# Contexto técnico

## Repositorio y stack observado

- El repositorio es un monorepo organizado por responsabilidades: `uis/`, `services/`, `data/`, `agents/`, `skills/`, `mcps/`, `workflows/`, `packages/`, `shared/`, `infra/`, `scripts/`, `internal/` y `docs/`.
- `packages/shared/` contiene el paquete privado `@repo/shared-types`, con tipos TypeScript en `index.ts`; el paquete no declara scripts.
- La estructura y la documentación describen la base del proyecto, pero no equivalen a servicios desplegables. Según la documentación existente, aún no hay aplicaciones ejecutables, scripts globales ni runner de workspace en la raíz.
- No se ha confirmado un stack ejecutable completo, base de datos, entorno de despliegue ni estrategia global de pruebas.

## Arquitectura actual de TrackFlow

El briefing describe una arquitectura heredada, distinta del stack que se construya en este proyecto:

- Los almacenes usan dos sistemas de gestión distintos; uno es software comercial y el otro una hoja de cálculo avanzada.
- Hay un ERP antiguo, integraciones punto a punto en Python sin documentación adecuada y bases de datos en dos proveedores cloud.
- No existe telemetría centralizada; los problemas operativos se comunican informalmente y una nueva funcionalidad tarda entre una y dos semanas en desplegarse.

Estos datos describen el estado actual de la empresa, no componentes ya integrados en este repositorio.

## Decisiones, propuestas y convenciones

- Usar el briefing de `content/contexts/00-general-contexts/trackflow-BRIEFING.en.md` como referencia de dominio, registrando explícitamente cualquier dato contradictorio.
- La guía propone FastAPI para una API central. Es una propuesta, no una decisión confirmada ni una aplicación ya implementada; confirmar su uso al definir el primer entregable.
- Evitar microservicios prematuros y extraer workers solo si una necesidad concreta lo justifica.
- Ubicar cada entregable en su carpeta de responsabilidad y documentar junto a su implementación las nuevas apps, servicios, agentes y pipelines.
- Compartir contratos entre aplicaciones mediante paquetes reutilizables cuando sea necesario.

## Restricciones y asuntos por confirmar

- El dominio abarca Estados Unidos y España, dos almacenes, varios transportistas y dos marcos laborales. Los procesos y datos deben permitir distinguir país y operación cuando corresponda.
- El negocio requiere servicios de seguimiento y experiencia de cliente disponibles fuera del horario de oficina; los objetivos de disponibilidad y recuperación aún no están definidos.
- La empresa usa dos proveedores cloud y sistemas heredados, pero no se ha decidido qué integrar, reemplazar o simular en el primer entregable.
- Las restricciones regulatorias, de privacidad, residencia de datos y seguridad aplicables deben confirmarse antes de diseñar el almacenamiento o los flujos transfronterizos.
- El CEO aparece con dos nombres distintos en el briefing; resolverlo antes de usar el dato en sistemas o informes.
