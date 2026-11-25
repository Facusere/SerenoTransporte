# 07 · Reportes

Formatos: **Excel o PDF** (pedido de mamá).

## Pantallas de inicio
| ID | Vista | Contenido |
|---|---|---|
| R00a | Papá | Resumen del día, partes sin revisar, vencimientos con semáforo, francos, adelantos, **lluvia en la zona** |
| R00b | Mamá | **Prioridad definida por ella:** 1) vencimientos de valores (cheques), 2) ingresos por empresa, 3) resumen de erogaciones |

## Para papá
| ID | Reporte | Contenido |
|---|---|---|
| R01 | Resumen del día | Camiones, recorridos, litros, partes sin aprobar |
| R02 | Resumen mensual por empresa | Litros, km, recorridos, ingresos estimados |
| R03 | Diferencias carga/descarga | Por viaje, chofer, tambo; marca los que superan el margen |
| R04 | Rechazos por acidez | Por tambo y fecha |
| R05 | Adelantos y préstamos | Pendientes por empleado |
| R06 | Calendario de francos y vacaciones | Quién falta y cuándo |
| R07 | Vencimientos | Licencias, psicofísico, VTV, seguro, service |
| R08 | Gastos por camión | Cuando haya camión asignado |
| R09 | Conciliación con la liquidación de la fábrica | Diferencias de litros, km y montos |

## Para mamá
| ID | Reporte | Contenido |
|---|---|---|
| R10 | **Planilla de sueldos mensual** | Por chofer: días/horas o km/viajes, conceptos, domingos, francos, adelantos, cuotas, neto a pagar |
| R11 | **Listado de cheques** | Emitidos/recibidos, estado, fecha de pago; agenda diaria |
| R12 | **Gastos mensuales por rubro** | Rubros de mamá; empresa y personal separados |
| R13 | Gastos fijos y cuotas | Seguros, préstamos, planes ARCA, alquiler de tanque, aportes |
| R14 | Ingresos del mes | Por fábrica: facturado, retenciones, cobrado |
| R15 | Resumen anual para Ganancias | Ingresos, retenciones y gastos por rubro |
| R16 | Detalle de comprobantes | Con foto, para IVA y respaldo |

## Pendiente
Pedir la planilla de sueldos, el Excel de cheques y las liquidaciones de fábrica para fijar las columnas exactas.

## Ronda 3 (2026-10-14 y 2026-10-30)
| ID | Reporte | Contenido |
|---|---|---|
| R17 | **Hoja de ruta global para la planta** | Planilla única generada desde los partes del día, lista como texto para enviar por mensaje (WhatsApp) y exportable a Excel/PDF |
| R18 | Descuentos por superar el margen | **Por mes y empresa** (`v_litros_mensuales_por_empresa`): diferencia total, % sobre lo cargado y descuento esperado (a valor leche actual) vs. el de la liquidación |
| R19 | Retenciones mensuales | Las que mamá usa por mes (IIBB y contribuciones); el resumen anual sale de ARCA |
| R20 | Cuotas de préstamos | Por chofer: mutual, cuota mensual, cuotas restantes y saldo |
| R21 | Cheques por vencer | Hoy y próximos días, más seguimiento de cheques rechazados y su reposición |
| R22 | Recibo teórico vs. pago real | Por chofer y mes: neto del recibo teórico, ajustes (aguinaldo adicional, adelantos, cuotas de mutual) y pago real |

## Estado al 2026-11-04
- La vista `v_litros_mensuales_por_empresa` (base de R18) está creada en `database/schema.sql`.
- La lógica de cálculo para R10/R22, R18 y R07 está implementada y probada en `core/`.
- Los paneles e informes exportables/imprimibles están implementados en `app/`:
  - **Para Papá:** Resumen operativo diario (`EmpleadorDashboard`), generador y despachador de Hoja de Ruta Global y mensaje de recorrido por WhatsApp (R17 / RF37 / RF53), semáforo de vencimientos y odómetro de flota (R07 / RF29), **diagrama interactivo de 22 cubiertas por chasis (+ 2 auxilios) con medición de mm de dibujo, DOT y rotaciones (`ChasisCubiertasEsquema.tsx` / `CubiertasModal.tsx`)**, telemetría de rendimiento de combustible en `L/100 km` por camión (`ConsumoCombustibleFlotaModal.tsx`), visor comparativo a pantalla dividida (`SplitScreenComprobanteModal.tsx`) para auditar fotos de remitos contra litros cargados, calendario y aprobación de francos (R06), widget de lluvia en Porteña en tiempo real (R00a).
  - **Para Mamá:** Centro de comando con 4 paneles ejecutivos (R00b), planilla de sueldos con comparativa Recibo Teórico vs. Pago Real e impresión de ficha (R10, R20, R22), cartera de cheques con alertas de vencimiento y reposición (R11, R21), gastos por rubro y gastos fijos recurrentes (R12, R13), conciliación mensual de margen 0,2 % con fábrica (R03, R09, R14, R18), rentabilidad por camión (R08), **asistente guiado de cierre de mes (`AsistenteCierreMesModal.tsx`)**, paquete contable de cierre mensual imprimible (RF71), **visor de historial de auditoría inmutable (`AuditLogModal.tsx`)** y **exportación/importación multi-hoja en Excel `.xlsx` con respaldo automático rotativo de 31 días (`BackupExcelModal.tsx` / `importadorExcelHistoricoService.ts`)**.
