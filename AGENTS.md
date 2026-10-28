# Instrucciones para agentes

## Inicio de cada sesión

Al comenzar cada sesión de trabajo en este monorepo, antes de analizar la tarea o editar archivos:

1. Lee todos los archivos Markdown de `memory-bank/`, incluidos `projectbrief.md`, `techContext.md` y `progress.md`.
2. Usa el contexto, las decisiones y el estado registrados allí como referencia; si contradicen el código o la petición actual, señala la discrepancia y aclárala antes de asumir.
3. Lee las instrucciones específicas aplicables a los archivos que vayas a modificar.

No des por leída la memoria por aparecer en el historial de otra sesión: vuelve a consultarla al inicio de cada sesión.

## Criterio técnico transversal

Antes de proponer o implementar cambios técnicos, consulta `.agents/skills/trackflow-technical-context/SKILL.md`. Distingue entre el stack observado en el repositorio, la arquitectura heredada de TrackFlow y las propuestas aún no aprobadas. No presentes una propuesta —como FastAPI— como decisión confirmada.

## Flujo obligatorio antes de cada commit

No crees commits salvo que el desarrollador lo solicite explícitamente. Cuando lo solicite, completa estos pasos en orden antes de ejecutar el commit:

1. **Comprobar autorización y alcance:** confirma que existe una petición explícita de commit y determina qué cambios pertenecen a la tarea. Revisa `git status` y conserva intactos los cambios preexistentes o ajenos.
2. **Validar los cambios:** ejecuta las pruebas, comprobaciones de tipos, lint o validaciones más específicas disponibles para los archivos modificados. Si no hay una comprobación aplicable, indícalo.
3. **Revisar el diff preparado:** inspecciona el diff staged y confirma que solo incluye los cambios autorizados, sin archivos ajenos, secretos, credenciales ni artefactos generados.
4. **Sincronizar el estado del proyecto:** si el trabajo cambia el estado o los próximos pasos, actualiza `memory-bank/progress.md` y revisa ese cambio junto con el resto del diff.
5. **Confirmar y crear el commit:** verifica una vez más los archivos staged, usa un mensaje breve que describa el cambio y ejecuta el commit solo después de superar los pasos anteriores.

Si algún paso falla o revela cambios inesperados, detente y consulta al desarrollador antes de continuar con el commit.

## Rutas protegidas

No modifiques, elimines, renombres ni sobrescribas estas rutas sin confirmación explícita del desarrollador en la conversación actual. Una solicitud que las mencione de forma directa cuenta como confirmación solo para el alcance solicitado; no autoriza cambios adicionales relacionados.

- `.git/`: metadatos y estado interno de Git.
- `.devcontainer/` y `.vscode/`: configuración del entorno de desarrollo y del editor.
- `infra/`: configuración de infraestructura, despliegue y recursos operativos.
- `data/`: datos fuente, conjuntos de datos y archivos de entrada del proyecto.
- `content/contexts/00-general-contexts/trackflow-BRIEFING.en.md`: briefing de negocio de referencia.
- Archivos de secretos o credenciales, incluidos `.env` y variantes, claves privadas, tokens y archivos equivalentes. No copies sus valores a respuestas, logs ni commits. Si una tarea parece requerir modificarlos, detente y pide confirmación sin revelar su contenido.
- Directorios y artefactos generados o instalados, como `node_modules/`, `dist/`, `build/`, `.venv/` y `__pycache__/`.

La confirmación para una ruta protegida no elimina la obligación de conservar los cambios ajenos, limitar el alcance y evitar exponer secretos.
