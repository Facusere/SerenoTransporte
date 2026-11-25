# 02 · Actores y roles

| Actor | Quién | Dispositivo | Qué necesita |
|---|---|---|---|
| Dueño / administrador | Papá (también maneja; no cobra sueldo) | iPhone | Ver el día, revisar partes de los choferes, precios, adelantos, francos, vencimientos, gastos |
| Contadora | Mamá | Computadora (Chrome) | Cheques, gastos por rubro, planillas de sueldos, exportaciones |
| Chofer | 5 empleados (+ relevo) | Celular con internet | Ver recorrido, cargar parte diario, ver sus viajes/francos/adelantos |

## Vistas (idea del proyecto)
Son **tres vistas desde el inicio**: **Empleado** (carga los datos), **Empleador** (revisa y aprueba) y **Contaduría** (finanzas y reportes). Detalle de la vista del empleado en `13-vista-empleado.md`. Todas leen y escriben la misma base de datos: lo que cargue uno se ve al instante en las otras. Para proteger sueldos y cheques, se propone login + sesión recordada, y PIN corto para cambiar de vista (ver `12-hallazgos`, sección 5).

### Vista Empleador (papá) · pantalla de inicio
Resumen del día (camiones, recorridos, litros) · partes sin revisar · vencimientos con semáforo y alertas · francos/vacaciones · adelantos del mes · lluvia en la zona de recolección.

### Vista Contaduría (mamá) · pantalla de inicio
**Orden pedido por ella:** 1) vencimientos de valores (cheques por entrar/salir hoy y esta semana) · 2) ingresos por empresa · 3) resumen de erogaciones. Debajo: estado de sueldos, carga de cheques y comprobantes, exportaciones.

### Vista Empleado (chofer)
Su recorrido del día · cargar parte diario (ver `13-vista-empleado.md`) · sus viajes del mes · sus francos/vacaciones · sus adelantos (nivel B en el MVP, ver supuesto D8).

## Matriz de permisos (alineada con `database/schema.sql`)
| Función | Empleador (Papá) | Contaduría (Mamá) | Empleado (Chofer) |
|---|---|---|---|
| Ver maestros (empresas, tambos, camiones, recorridos) | ✅ | ✅ | ✅ |
| Editar maestros y administrar usuarios | ✅ | ❌ | ❌ |
| Cargar y editar parte diario | ✅ (todos, salvo bloqueados) | ❌ | ✅ (propio, en borrador o devuelto) |
| Aprobar / devolver partes (con motivo) | ✅ | ❌ | ❌ |
| Ver partes | ✅ todos | ✅ enviados, aprobados y bloqueados | ✅ solo propios |
| Cerrar y reabrir mes | ❌ | ✅ (exige partes revisados) | ❌ |
| Editar tarifas de empresas | ✅ | ✅ | ❌ |
| Cargar escala salarial mensual | ✅ | ✅ | ❌ |
| Ver sueldos y liquidaciones | ✅ todos | ✅ todos | ❌ (nivel B en MVP: solo partes, adelantos y francos propios) |
| Registrar adelantos y préstamos de mutuales | ✅ | ✅ | ❌ (solicitud en Etapa 2) |
| Gestionar francos y vacaciones | ✅ | ✅ | ❌ (solicitud en Etapa 2) |
| Cargar gastos | ✅ | ✅ | ✅ combustible con camión asignado (Etapa 3, D9) |
| Cargar y ver cheques | ✅ | ✅ | ❌ |
| Ver ingresos/egresos/reportes contables | ✅ | ✅ | ❌ |
| Ver registro de auditoría (`audit_log`) | ✅ | ✅ | ❌ |

## Estado al 2026-10-31
Permisos de la Etapa 1 implementados en PostgreSQL mediante RLS (`database/schema.sql`) y verificados con 64 pruebas automáticas (`database/test/rls_test.sql`).
