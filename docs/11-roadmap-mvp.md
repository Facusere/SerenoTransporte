# 11 · Roadmap y MVP (v2)

Criterio de orden: **ahorrar tiempo y errores a mamá** y **no pedirle a papá más trabajo que el cuaderno**.

## Etapa 0 · Validación (en curso)
Segunda ronda (`09-preguntas/seguimiento.md`), obtener documentos de ejemplo: planilla de sueldos, Excel de cheques, liquidaciones de fábrica, ticket de caudalímetro, fotos del cuaderno.

## Etapa 1 · Parte diario (MVP)
- Login, roles y vistas de papá/mamá/chofer
- Camiones, empleados, empresas, tambos, recorridos
- Parte diario del chofer (litros, temperatura, acidez, horas, km, domingos)
- Aprobación de papá
- Descarga y diferencia con margen configurable
- Francos básicos
**Éxito:** papá deja de anotar el día en el cuaderno y los partes del mes quedan completos.

## Etapa 2 · Sueldos y finanzas de mamá
- Cálculo del sueldo a pagar (corta y larga distancia) validado contra la planilla real
- Adelantos con tope, préstamos y cuotas
- Planilla de sueldos exportable
- **Cheques** con agenda diaria
- Gastos por rubro con foto
- Francos y vacaciones con calendario
- Tarifas por empresa e ingresos estimados
**Éxito:** mamá no recalcula sumas y maneja los cheques desde el sistema.

## Etapa 3 · Camiones y alertas
- Camión asignado a gastos (combustible, repuestos, gomas)
- Gastos fijos y cuotas con recordatorios
- Vencimientos (VTV, seguro, licencias, psicofísico, service)
- Ámbito empresa/personal

## Etapa 4 · Control y conciliación
- Liquidación de la fábrica vs. partes propios
- Cobros y retenciones; resumen anual para Ganancias
- Importar comprobantes de ARCA
- Rentabilidad por camión

## Etapa 5 · Mejoras
- Avisos por WhatsApp, estado del tiempo, notificaciones push
- Backups avanzados, historial de cambios completo

## Pendiente
Revisar etapas tras la segunda ronda de entrevistas.

## Ajuste ronda 2: detalle de la Etapa 1 con las tres vistas
1. Datos maestros y usuarios (Empleador): empresas, tambos, recorridos, camiones, empleados, PIN.
2. **Vista Empleado:** iniciar jornada, cargar tambos y descarga, cerrar y enviar parte, "Mis partes".
3. **Vista Empleador:** bandeja de partes por aprobar, devolver con comentario, resumen del día.
4. **Vista Contaduría (mínima):** partes aprobados del mes y exportación a Excel.
5. **Piloto** con 1-2 choferes, en paralelo con el cuaderno, 2 semanas.

## Ajuste ronda 3 (2026-10-14)
- **Etapa 1:** agregar la generación de la **hoja de ruta global** (mensaje por WhatsApp) y el registro de **remito** y **aviso por acidez**.
- **Etapa 2:** agregar **escala salarial mensual** (incluye valor de domingo y franco), préstamos de mutuales, descuento por margen 0,2 % **mensual** y cheques con estado.
- **Los documentos de ejemplo ya no son condición para empezar.** Se programa con supuestos de trabajo y se ajusta cuando lleguen la muestra de hoja de ruta, un remito y las liquidaciones de las plantas.

## Estado al 2026-11-04
- **Construcción completada e integrada (Etapas 1, 2, 3, 4 y Automatización):**
  - **Vista Empleado (Móvil Chofer):** Carga de parte diario con paradas de carga y descarga, modo alto contraste solar para cabina (`modoSol`), deslizador antivibración (`SlideToConfirm.tsx`) para evitar cierres accidentales en caminos de tierra, feedback háptico, sugerencia de próximo tambo en 1 toque y detector de anomalías de tipeo de litros según promedio histórico del tambo (`asistenteRecorridoService.ts`), precarga automática de litros acumulados al abrir descarga, registro de tambos salteados con motivo (RF45), bitácora de carga de combustible en ruta con odómetro, rendimiento en `L/100 km` y foto de ticket (`CargaCombustibleModal.tsx`), reporte de averías mecánicas en ruta con semáforo de gravedad (`ReportarAveriaModal.tsx`), solicitud de corrección de partes enviados, selector rápido de temperatura con alertas (> 5,5 °C), soporte de segundo viaje diario, autoguardado y cola offline resiliente con sincronización automática al recuperar red, compresión client-side de fotos, bandeja "Mis Partes" y módulo "Mi Cuenta" (Nivel B).
  - **Vista Empleador (iPhone de Papá):** Bandeja de revisión ágil con botón de aprobación rápida en 1 toque (RF05) y aprobación en lote para partes limpios, visor comparativo a pantalla dividida (`SplitScreenComprobanteModal.tsx`) con zoom y rotación para contrastar fotos de remitos contra litros declarados, alertas visuales para partes con anomalías, modal de devolución con motivo obligatorio, generador de mensaje de recorrido para WhatsApp (RF37) y Hoja de Ruta Global diaria (RF53) con descarga CSV y enlace `wa.me`, widget de clima en tiempo real (Open-Meteo) en Porteña y zona rural, semáforo de vencimientos (15/7/0 días), control de odómetro/mantenimiento preventivo, **diagrama interactivo de 22 cubiertas por chasis (+ 2 auxilios) con milímetros de dibujo (`mm`), código `DOT`, recapados y rotación entre posiciones (`ChasisCubiertasEsquema.tsx` / `CubiertasModal.tsx`)**, telemetría de combustible de la flota (`ConsumoCombustibleFlotaModal.tsx`), bandeja de averías y solicitudes de corrección, y gestión de nómina, flota y tambos.
  - **Vista Contaduría (Desktop de Mamá):** Centro de comando con 4 paneles en Resumen Ejecutivo, agenda y gestión de cheques (cartera, cobrados, rechazados con reposición y endoso directo a gastos), gastos por rubro con asignación de camión y comprobante, gastos fijos y recurrentes con generación en 1 clic (RF26), importador masivo de compras desde "Mis Comprobantes" de ARCA (RF27, RF70), **importador inteligente de planillas Excel históricas (`importadorExcelHistoricoService.ts`)**, **respaldo automático rotativo en Excel multi-hoja de 31 días (`BackupExcelModal.tsx`)**, módulo de conciliación de liquidación de fábrica (RF11, RF56), liquidación de sueldos corta y larga distancia con comparación de recibo teórico vs. pago real, **asistente guiado de cierre de mes (`AsistenteCierreMesModal.tsx`)**, **visor de historial de auditoría inmutable (`AuditLogModal.tsx`)**, y paquete de cierre mensual imprimible para el contador (RF71).
  - **Funcionalidades Especializadas Destacadas (Cerradas e Integradas):**
    1. *Diagrama Interactivo de 22 Cubiertas por Chasis con mm de dibujo y DOT:* Esquema 2D superior de tractor (10 ruedas) + cisterna láctea de 3 ejes duales (12 ruedas) + 2 auxilios, con medición de milímetros de dibujo (`mm`), decodificación de semana/año `DOT`, alerta de seguridad si se coloca recapada en eje direccional, e intercambio de posiciones (`ChasisCubiertasEsquema.tsx`, `CubiertasModal.tsx`, `cubiertasService.ts`).
    2. *Calendario Visual de Francos y Chofer de Relevo:* Matriz mensual con detección de solapamientos críticos y asignación inteligente del chofer comodín (`calendarioFrancosService.ts`, `CalendarioFrancosModal.tsx`).
    3. *Conciliación Automática por Archivo:* Parser multiformato (CSV/TXT/Excel clipboard) con detector de discrepancias y nota formal de reclamo (`conciliacionService.ts`, `ConciliacionFabricaView.tsx`).
    4. *Respaldo Multi-Hoja Excel (31 días) e Importador Histórico:* Exportación e importación nativa `.xlsx` y checklist guiado de cierre mensual (`excelBackupService.ts`, `importadorExcelHistoricoService.ts`, `AsistenteCierreMesModal.tsx`).
- **Base de Datos y Supabase:**
  - Esquema Postgres 17 con permisos RLS por rol y funciones de auditoría, Storage bucket privado `partes` con políticas de seguridad, y datos semilla ejecutados con la flota completa de 7 camiones (5 regulares, 1 relevo, 1 barro), tambos, recorridos, 5 choferes, Empleador y Contaduría, más parte de prueba.
  - Migración modular formalizada en `database/migrations/002_servicios_operativos.sql` con su script inverso `002_rollback.sql`.
  - Persistencia dual offline-first en frontend: guardado inmediato local en `localStorage` + sincronización asíncrona no bloqueante con Supabase (`averiasService`, `tamboSalteadoService`, `cubiertasService`, `combustibleService`, `solicitudCorreccionService`, `gestionService`).
- **Evidencia de Calidad:**
  - 30/30 tests unitarios en `core/` pasan (Node 22+).
  - 64+ tests de permisos RLS en `database/` pasan.
  - Suite completa de pruebas en `app/` pasando en Vitest.
  - Compilación de producción (`tsc -b && vite build`) limpia y sin errores de tipos.
