# 15 · Sistema de trabajo con IA (Antigravity)

Estado: v1 · 2026-10-31. Reglas siempre activas: `AGENTS.md`. Niveles y skills: `.agents/rules/activation-policy.md`.

## 1. Idea
Un agente por defecto. Más revisión solo cuando el riesgo lo pide: en este proyecto el riesgo está en **dinero (sueldos, cheques)**, **permisos (RLS, PIN, sesiones)** y **datos personales de empleados**. Lo demás es trabajo normal.

## 2. Qué existe
| Pieza | Para qué | Cuándo se usa |
|---|---|---|
| `AGENTS.md` | Contrato y reglas de negocio | Siempre |
| `activation-policy` | Clasifica la tarea en N0–N3 | Al planificar |
| Revisor independiente | Revisión crítica en sesión nueva, solo lectura | N2 y N3 |
| Skills: `project-intake`, `implementation-tdd`, `independent-review`, `security-review`, `qa-and-e2e`, `release-and-rollback`, `database-migrations`, `legal-issue-spotting`, `payroll-and-money` | Procedimientos | Solo si hay señal |
| CI (`.github/workflows/ci.yml`) | Corre las 30 pruebas de `core/` y las 64 de la base en cada push | Automático |

## 3. Conexiones
- **No hace falta conectar nada por MCP** para empezar. Git y GitHub los maneja el agente con `git`/`gh`.
- **Supabase:** crear el proyecto en el panel web y aplicar `schema.sql` a mano desde el editor SQL. No conectar un MCP de Supabase a un proyecto con datos reales. Si más adelante lo conectás, que sea a un proyecto de desarrollo y en solo lectura.
- **No conectar:** correo, WhatsApp, ARCA, Holistor, banca ni deploy automático. RNF14 ya dice que se vinculan por archivos.

## 4. Backups y costos (verificar antes de decidir)
RNF06 pide copias automáticas con restauración probada y RNF07 pide costo bajo. Según fuentes públicas de 2026, el plan gratuito de Supabase **no incluye backups automáticos** y **pausa el proyecto tras 7 días sin actividad**; los backups diarios con retención de 7 días llegan con el plan Pro (unos USD 25 por mes). Confirmar en supabase.com/pricing. Propuesta: gratis durante el piloto con datos de prueba, volcado semanal automático a un repositorio privado, y pasar a Pro antes de cargar sueldos y cheques reales. Esto se decide en el ADR 001.

## 5. Qué ya está hecho y qué sigue (Actualizado al 2026-11-03)
- **Hecho y verificado:**
  - `core/`: 30 pruebas unitarias pasando (sueldos, margen 0,2 %, préstamos, saldos, vencimientos).
  - `database/`: 64 pruebas de permisos RLS pasando sobre `schema.sql` (21 tablas, vistas y funciones `cerrar_mes` / `reabrir_mes` / `audit_log`).
  - `app/`: 205 pruebas automatizadas en 64 suites pasando (`tsc -b && vite build` limpio). Cubre las 3 vistas completas (**Empleado**, **Empleador**, **Contaduría**), cola offline con resolución de conflictos, integración bidireccional con WhatsApp (`wa.me` + parser predictivo de ruta), importación/exportación Excel con respaldo rotativo de 31 días, ARCA CSV, gastos fijos recurrentes, mantenimiento/cubiertas por odómetro y cierre mensual imprimible.
  - **Stitch MCP (`projects/12695472662582226327`):** conectado con el Design System oficial *"Transporte Sereno — Agro-Logistics Rugged Industrial"*.
- **Qué sigue:**
  1. Migrar los módulos auxiliares que hoy persisten en `localStorage` (checklist de salida, tambos salteados, averías, mantenimiento/cubiertas, gastos fijos recurrentes y solicitudes de corrección) a tablas en `database/schema.sql` con sus pruebas RLS (tarea N3 con aprobación humana).
  2. Realizar el piloto de campo con los choferes en paralelo con el cuaderno.

## 6. Antes del piloto con choferes
Un mes en paralelo con el cuaderno, 1 o 2 choferes, guía impresa de 1 página y una persona de la familia a cargo del soporte (RNF20). Revisar `legal-issue-spotting` antes de cargar datos personales reales.
