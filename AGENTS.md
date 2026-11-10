# Instrucciones para Codex — proyecto actual `siplap-booked`

## Alcance y objetivo

Este repositorio es el **proyecto actual**, que sirve como fuente de referencia para una futura migración a otro repositorio. El equipo continúa trabajando aquí. El asesor externo administra las instrucciones y la arquitectura del repositorio de destino.

**No migres, reestructures ni adaptes automáticamente este repositorio a la arquitectura nueva.** Prioriza conservar el comportamiento actual y realizar únicamente los cambios que solicite el usuario.

Estas instrucciones se aplican a todo el repositorio. Los archivos `AGENTS.md` de subdirectorios, como `frontend/AGENTS.md`, añaden instrucciones específicas para esos directorios. Si hay conflictos, identifica el conflicto y pregunta antes de actuar. No sobrescribas instrucciones generadas por herramientas.

## Conocimiento del proyecto y verificación

- La estructura observada incluye `backend/`, `frontend/`, `packages/` y `docs/`. **No presupongas** el framework, los nombres de archivos, las rutas, la configuración de Prisma ni el funcionamiento de cada módulo sin inspeccionar el código.
- Antes de una tarea, revisa solo los archivos relevantes, `package.json` y la documentación existente. Verifica los scripts reales antes de ejecutarlos.
- Trata el código, las pruebas y los esquemas actuales como fuente de verdad sobre el comportamiento implementado. Si la documentación difiere, señala la diferencia en lugar de inventar una explicación.
- Si se solicita preparar información para la migración, describe el comportamiento actual, sus dependencias y sus riesgos; no implementes cambios en el repositorio de destino sin una petición explícita y acceso autorizado.

## Forma de trabajo

1. Resume en español qué entendiste de la solicitud y qué archivos o módulos parecen implicados.
2. Para tareas no triviales, presenta un plan corto antes de editar. Si faltan datos críticos, pregunta primero.
3. Realiza cambios mínimos, localizados y reversibles. Evita refactorizaciones ajenas al objetivo.
4. Conserva los contratos públicos, rutas, nombres de permisos, reglas de autorización, formatos de respuesta y comportamiento existente, salvo solicitud explícita.
5. Después del cambio, ejecuta únicamente las verificaciones pertinentes que estén disponibles. No afirmes haber probado algo que no ejecutaste.
6. Resume los archivos modificados, los motivos, las pruebas ejecutadas y cualquier limitación o riesgo pendiente.

## Backend, frontend y contratos compartidos

- Antes de cambiar una función, rastrea su flujo completo cuando corresponda: interfaz → petición HTTP → endpoint → validación → autorización → lógica → persistencia → respuesta.
- Antes de cambiar contratos, tipos, esquemas Zod, permisos o endpoints, localiza todos sus consumidores y revisa el impacto tanto en `frontend/` como en `backend/` y `packages/`.
- No elimines validaciones ni controles de autorización para hacer pasar una petición o prueba.
- No sustituyas reglas de negocio existentes por suposiciones. Si hay una inconsistencia, explícala y pide confirmación.
- Respeta las convenciones y herramientas que realmente estén configuradas en cada paquete; no agregues dependencias por preferencia personal.
- Al trabajar en `frontend/`, consulta y respeta también `frontend/AGENTS.md`, incluyendo sus instrucciones específicas de Next.js.

## Datos, configuración y seguridad

- Nunca imprimas, copies a respuestas, registres en logs ni incluyas en commits secretos de `.env`, `.env.local`, tokens, contraseñas o cadenas de conexión reales.
- Puedes inspeccionar los **nombres** de variables requeridas, sin divulgar sus valores. Usa `.env.example` con valores ficticios cuando se solicite documentar configuración.
- No edites archivos de secretos reales salvo petición explícita y justificada.
- No ejecutes `prisma migrate reset`, `db push` con pérdida de datos, borrados masivos, truncados, migraciones destructivas ni cambios de producción sin aprobación explícita.
- No borres archivos o carpetas, no sobrescribas cambios ajenos y no ejecutes comandos destructivos sin autorización.

## Git y colaboración

- Antes de editar, comprueba el estado de Git y respeta cambios existentes del equipo.
- No cambies de rama, hagas `commit`, `push`, `merge`, `rebase`, `reset`, `clean` ni abras PR sin solicitud explícita.
- No presupongas que las reglas de ramas del repositorio de destino se aplican al actual. Sigue las convenciones comprobadas en este repositorio.

## Preparación para la migración futura

Cuando se pida documentar un módulo para migración, entrega:

1. Propósito y funcionalidades que ya existen.
2. Archivos principales de backend y frontend y sus responsabilidades.
3. Endpoints, contratos, validaciones y permisos **verificados en el código**.
4. Modelos, relaciones y dependencias de datos relevantes.
5. Flujo de ejecución explicado de forma comprensible.
6. Pruebas disponibles, casos límite y riesgos conocidos.
7. Aspectos que deberán contrastarse con las reglas del nuevo repositorio.

Distingue siempre entre **verificado en código**, **inferido** y **pendiente de revisar**. No inventes permisos, endpoints, tablas ni pruebas.

## Comunicación

- Responde en español, con lenguaje técnico claro pero sin tecnicismos innecesarios.
- Mantén los identificadores de código en el idioma y formato que ya use el proyecto.
- Si la tarea es solo de análisis o documentación, no edites código.
- Ante instrucciones ambiguas, riesgos de pérdida de datos o conflictos entre reglas, detente y pide confirmación.

## Referencia para la futura migración

El proyecto actual será migrado a una nueva
plataforma institucional.

La arquitectura de destino está definida por:

1. README.md del repositorio nuevo.
2. CONTRIBUTING.md del repositorio nuevo.
3. docs/architecture/rules.md del repositorio nuevo.

Estos documentos establecen las reglas que
deberá cumplir el código migrado.

No asumir que estos archivos existen dentro
del repositorio actual.

No modificar la arquitectura existente para
adaptarla anticipadamente al repositorio nuevo.

Cuando se solicite preparar un módulo para
migración, identificar las diferencias entre
su implementación actual y las reglas de destino.

Si los documentos de destino no están
disponibles, solicitar acceso antes de
realizar una comparación.