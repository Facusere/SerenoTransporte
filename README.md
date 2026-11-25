# Transporte Sereno

Sistema de gestión para el transporte de leche de la familia Sereno: viajes, litros, precios, sueldos, adelantos, francos/vacaciones, gastos por camión y reportes contables.

> Repositorio **privado**. Contiene datos y procesos internos de la familia. No subir datos reales de empleados, sueldos ni fotos de comprobantes sin revisar.

## Estado del proyecto

**Fase actual: análisis cerrado y aplicación web implementada.** Hay lógica de negocio probada (`core/`), esquema de base de datos probado (`database/`) y pantallas web implementadas y probadas (`app/`).

1. [x] Armar estructura de documentación
2. [x] Completar supuestos propios (`docs/01-supuestos.md`)
3. [x] Entrevistar a papá (`docs/09-preguntas/papa.md`)
4. [x] Entrevistar a mamá (`docs/09-preguntas/mama.md`)
5. [ ] Fotografiar y analizar el cuaderno (`docs/03-proceso-actual.md`)
6. [x] Actualizar supuestos y requisitos con las respuestas (1.ª ronda)
6b. [x] Segunda ronda respondida (`docs/09-preguntas/seguimiento.md`)
6c. [x] Tercera ronda respondida e incorporada en [`docs/12-hallazgos-y-analisis.md`](docs/12-hallazgos-y-analisis.md#9-ronda-3-2026-10-30-respuestas-correcciones-y-decisión-de-avanzar). Desde acá se avanza con supuestos de trabajo (sección 9.3)
6d. [x] Cálculo de sueldos verificado con los recibos reales (`docs/14-calculo-de-sueldos.md`)
7. [x] Tecnologías confirmadas en ADR (`docs/10-decisiones/`)
7b. [x] `core/`: sueldos, margen mensual, semáforo de vencimientos, adelantos (30 pruebas)
7c. [x] `database/`: esquema PostgreSQL/Supabase con permisos por rol (64 pruebas)
8. [x] `app/`: Pantallas de Empleado, Empleador y Contaduría con modo offline, diagrama de 22 cubiertas por chasis con mm de dibujo y DOT, respaldos rotativos Excel e importador histórico

## Índice de documentación

| Doc | Contenido |
|---|---|
| [01 Supuestos](docs/01-supuestos.md) | Lo que creemos hoy; se marca confirmado/descartado |
| [02 Actores y roles](docs/02-actores-y-roles.md) | Quién usa el sistema y qué ve |
| [03 Proceso actual](docs/03-proceso-actual.md) | Cómo funciona el cuaderno hoy |
| [04 Glosario](docs/04-glosario.md) | Vocabulario común |
| [05 Requisitos funcionales](docs/05-requisitos-funcionales.md) | Qué debe hacer el sistema |
| [06 Requisitos no funcionales](docs/06-requisitos-no-funcionales.md) | Conectividad, seguridad, dispositivos, backups, etc. |
| [07 Reportes](docs/07-reportes.md) | Vistas y exportaciones para papá y mamá |
| [08 Modelo de datos](docs/08-modelo-de-datos.md) | Modelo conceptual e historial de ajustes |
| [09 Preguntas y respuestas](docs/09-preguntas/) | Entrevistas (papá, mamá) y seguimiento |
| [10 Decisiones](docs/10-decisiones/) | Registro de decisiones técnicas (ADR 001–007) |
| [11 Roadmap MVP](docs/11-roadmap-mvp.md) | Etapas de desarrollo |
| [12 Hallazgos y análisis](docs/12-hallazgos-y-analisis.md) | Conclusiones de las 3 rondas, reglas de negocio y supuestos vigentes (D1–D14) |
| [13 Vista del Empleado](docs/13-vista-empleado.md) | Especificación de la carga por choferes, flujos, validaciones y adopción |
| [14 Cálculo de sueldos](docs/14-calculo-de-sueldos.md) | Fórmulas verificadas de corta y larga distancia, escala mensual y pago real |
| [15 Sistema de trabajo IA](docs/15-sistema-de-trabajo-ia.md) | Reglas de orquestación, niveles N0–N3, skills, conexiones y costos |

## Cómo trabajar con esta documentación

- Cada doc tiene una sección **Estado** o **Pendiente** al final. Actualizarla al cambiar algo.
- Las respuestas de las entrevistas van en `09-preguntas/` y `12-hallazgos-y-analisis.md`; después se reflejan en supuestos y requisitos.
- Los supuestos nunca se borran: se marcan como ✅ Confirmado, ❌ Descartado o ✏️ Corregido, con fecha.
- Las fotos del cuaderno van en `assets/cuaderno/` (no se versionan en Git por contener datos sensibles; ver `.gitignore`).

## Código
| Carpeta | Contenido | Cómo probarlo |
|---|---|---|
| [`core/`](core/) | Lógica de negocio en TypeScript, sin dependencias | `cd core && npm test` (Node 22.18 o más) |
| [`database/`](database/) | Esquema PostgreSQL/Supabase y pruebas de permisos | `DATABASE_URL=... bash database/test/run.sh` |
| [`app/`](app/) | Aplicación web (React 19 + TypeScript + Vite + Tailwind v4) con las 3 vistas, cola offline, diagrama de 22 cubiertas (mm y DOT) y respaldos Excel | `cd app && npm test -- --run` |
