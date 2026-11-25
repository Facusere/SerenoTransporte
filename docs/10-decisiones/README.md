# 10 · Registro de decisiones (ADR)

Una decisión por archivo: `NNN-titulo.md`. Usar la plantilla de abajo.

## Decisiones (índice)
| Archivo | Tema | Estado |
|---|---|---|
| [001](001-stack-y-arquitectura.md) | Tipo de app, backend, base de datos, hosting y costos | Aceptada |
| [002](002-autenticacion-y-roles.md) | Autenticación, roles, empleados, administración y soporte | Aceptada |
| [003](003-offline-y-backups.md) | Conexión, borradores y copias de seguridad | Aceptada |
| [004](004-fotos-y-archivos.md) | Fotos: almacenamiento y compresión | Aceptada |
| [005](005-alertas-y-clima.md) | Alertas de vencimientos y clima | Aceptada |
| [006](006-exportacion-y-hoja-de-ruta.md) | Excel, PDF, hoja de ruta, ARCA | Aceptada |
| [007](007-reglas-de-negocio-configurables.md) | Asignación, cierre de mes, escala, margen, adelantos | Aceptadas con supuestos |

## Equivalencia con la lista anterior de pendientes
001, 002, 003 → ADR 001 · 004, 008, 013 → ADR 002 · 005, 006 → ADR 003 · 009 → ADR 004 · 007, 014 → ADR 006 · 010, 011, 012, 015, 016 → ADR 007.

## Plantilla
```
# NNN · Título
- Fecha:
- Estado: propuesta / aceptada / reemplazada
## Contexto
## Opciones consideradas
## Decisión
## Consecuencias
```