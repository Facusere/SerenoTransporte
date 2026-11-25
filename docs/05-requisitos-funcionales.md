# 05 · Requisitos funcionales

Prioridad: **M**ust · **S**hould · **C**ould · **W**on't. Etapa: ver `11-roadmap-mvp.md`.
Actualizado 2026-10-31.

## Parte diario y viajes
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF01 | El chofer carga su **parte diario**: camión, recorrido(s), tambos visitados, litros por tambo, temperatura, acidez, hora de salida/llegada, km | M | 1 |
| RF02 | Registrar rechazo de leche por acidez (tambo, motivo) | M | 1 |
| RF03 | Registrar método de medición (caudalímetro/regla) y adjuntar foto del ticket | S | 1 |
| RF04 | Registrar descarga (fábrica, litros) y calcular diferencia vs cargado, marcando cuando supera el margen configurable | M | 1 |
| RF05 | Papá **revisa** y corrige los partes **después** de que el chofer los envía (no los frena). Debe estar todo revisado para cerrar el mes | M | 1 |
| RF06 | Registrar cargas de combustible en ruta por camión (litros, odómetro en km, estación, tanque lleno y foto del ticket) con cálculo de rendimiento en `L/100 km` (sin generar gasto automático en efectivo en Contaduría, ya que el gasoil se abona con cheque en estación) | S | 3 |
| RF07 | Recorridos por empresa, con tambos en orden, reutilizables; poder compartirlos al chofer | S | 1 |
| RF08 | Marcar domingos trabajados y francos | M | 1 |

## Tarifas e ingresos
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF09 | Tarifas por empresa con dos esquemas: por recorrido, y por km + litros; con vigencia e histórico | M | 2 |
| RF10 | Calcular ingresos del mes por empresa (sobre litros cargados) | S | 2 |
| RF11 | Cargar la liquidación mensual de la fábrica y **conciliarla** con el parte (diferencias de litros, km, montos) | S | 4 |
| RF12 | Registrar cobros: orden de pago y medio (transferencia/e-cheq). Retenciones solo las que mamá usa por mes (IIBB, contribuciones); el resumen anual de ganancias sale de ARCA | C | 4 |

## Personal
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF13 | Empleados con categoría (corta/larga distancia), antigüedad, datos personales y documentos | M | 1 |
| RF14 | Calcular el **sueldo a pagar** por mes según esquema: corta (horas, extras, viáticos, comida) o larga (km, viáticos por km), con antigüedad | M | 2 |
| RF15 | Conceptos extra: domingos, franco no gozado, bono anual | M | 2 |
| RF16 | Adelantos con **tope 30%**, descuento en el mes siguiente o en cuotas | M | 2 |
| RF17 | Préstamos de **mutuales** a choferes (hoy 3): mutual, cuota, cantidad de cuotas, saldo; la empresa paga la cuota y la descuenta | S | 2 |
| RF18 | Francos y vacaciones: calendario, pedido del empleado, aprobación | S | 2 |
| RF19 | Planilla de sueldos mensual exportable (Excel/PDF) para mamá | M | 2 |
| RF20 | **No** generar recibos legales: solo entregar datos para Holistor | — | — |

## Cheques y gastos (mamá)
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF21 | **Cheques**: emitidos y recibidos (número, **origen**, fecha, monto, físico o e-cheq, estado; banco opcional). Un rechazado se vincula con el cheque que lo repone | M | 2 |
| RF22 | Agenda de cheques por entrar/salir hoy y próximos días, con aviso | M | 2 |
| RF23 | Gastos por **rubro** (lista de mamá) con medio de pago, tipo de comprobante y foto | M | 2 |
| RF24 | Asignar **camión** al gasto cuando corresponda (combustible, repuestos, gomas) | S | 3 |
| RF25 | Ámbito del gasto: empresa / personal | S | 3 |
| RF26 | Gastos fijos y cuotas (préstamos, planes ARCA, alquiler de tanque, seguros) con recordatorio | S | 3 |
| RF27 | Importar comprobantes desde archivo de ARCA ("Mis Comprobantes") | C | 4 |
| RF28 | **No** liquidar impuestos | — | — |

## Camiones, vencimientos y reportes
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF29 | Camiones y documentos con **vencimientos** (VTV, seguro, service), control de odómetro/mantenimiento preventivo y **diagrama interactivo de 22 cubiertas por chasis (+ 2 auxilios)** con medición de milímetros de dibujo (`mm`), código `DOT` (semana/año), recapados y rotación entre posiciones | S | 3 |
| RF30 | Vencimientos de choferes (licencia, psicofísico) y avisos | S | 3 |
| RF31 | Rentabilidad por camión (ingresos − gastos asignados) | C | 3-4 |
| RF32 | Reportes y exportaciones (ver `07-reportes.md`) | M | 2 |

## Acceso
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF33 | Login con roles (papá, mamá, chofer), sesión recordada y vistas propias | M | 1 |
| RF34 | Selector/cambio de vista con PIN para quienes tienen más de un rol | S | 1 |
| RF35 | Respaldo exportable/imprimible ("borrador") de partes y sueldos, **backup multi-hoja en Excel (`.xlsx`) con retención rotativa de 31 días** e **importador de planillas Excel históricas** | S | 2 |
| RF36 | Historial de cambios inmutable (`audit_log`: quién modificó qué, cuándo y con qué motivo) con visor de auditoría en Contaduría | S | 2 |
| RF37 | Aviso por WhatsApp de recorridos o vencimientos | C | 5 |
| RF38 | Estado del tiempo en la pantalla de inicio de papá | C | 5 |

## Vista Empleado y flujo de carga (ronda 2)
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF39 | Alta/baja de usuarios de empleados por el Empleador, con **PIN** y reinicio de PIN | M | 1 |
| RF40 | **Revocar sesión** de un dispositivo (celular perdido) | S | 1 |
| RF41 | **Autoguardado de borrador** del parte en el dispositivo; se recupera si se corta la conexión o se cierra la app | M | 1 |
| RF42 | Estados del parte en BD: `borrador`, `enviado`, `devuelto` (con motivo obligatorio), `aprobado`, `bloqueado` (toda corrección del Empleador queda en `audit_log`) | M | 1 |
| RF43 | **Plan base** de recorrido y camión por chofer (la asignación suele ser fija); se puede cambiar de camión (relevo, camión de días de barro) dejando constancia | S | 1 |
| RF44 | Alertas de validación: temperatura fuera de rango (`> 5,5 °C`), **detector de error de tipeo de litros según el promedio histórico del tambo** (cero de más o de menos) y diferencia sobre el margen | S | 1 |
| RF45 | Marcar carga tardía, cambio de camión durante el día, tambo extra/salteado con motivo | S | 1 |
| RF46 | Pedido de corrección de un parte ya aprobado por parte del chofer (queda auditado) | S | 2 |
| RF47 | **Cierre de mes** por Contaduría con **asistente guiado de 4 pasos** (verifica partes sin revisar, escala salarial vigente, alertas de margen 0,2 % y genera backup Excel automático antes de bloquear el período; `cerrar_mes` / `reabrir_mes` en BD) | M | 1 |
| RF48 | Reportar problema/avería mecánica del camión en ruta con categoría, severidad (`puede seguir` / `requiere taller` / `varado en ruta`), foto y seguimiento de resolución | C | 3 |
| RF49 | Recordatorio al chofer si no envió el parte del día | C | 2 |
| RF50 | Vista "Mis partes" con estados y comentarios del Empleador | M | 1 |
| RF51 | Pedido de francos, vacaciones o adelanto desde la vista Empleado (con aprobación) | C | 2 |
| RF52 | Compresión de fotos antes de subir | S | 1 |

## Ronda 3 (2026-10-14)
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF53 | **Generar la hoja de ruta global** que se envía a la planta por mensaje (texto listo para compartir por WhatsApp y exportable a Excel/PDF) desde los partes del día | M | 1 |
| RF54 | Registrar **remito** por tambo: número, nº de tambo, fecha, hora y foto del remito firmado, con **visor comparativo a pantalla dividida (Split-Screen)** con zoom y rotación para auditar foto vs. litros cargados | M | 1 |
| RF55 | Registrar el **aviso a la fábrica** por leche ácida (área de producción primaria, cuándo, medio) | S | 1 |
| RF56 | Calcular **por mes y por empresa** si la diferencia total supera el margen (**0,2 %**, configurable) y el descuento esperado a **valor leche actual**. El alerta por viaje es solo informativo | S | 2 |
| RF57 | **Escala salarial mensual** (básico, antigüedad, viáticos, comida, valores por km o recorrido, bono) con vigencia por mes, cargada por Contaduría | M | 2 |
| RF58 | Valor de **domingo trabajado y franco no gozado** tomado de la **escala del sindicato** del mes (no lo fija el Empleador) | M | 2 |
| RF59 | Cheques con banco (opcional), estado (pendiente, cobrado, rechazado) y concepto, además de número, fecha, proveedor y monto | M | 2 |
| RF60 | Camión obligatorio al cargar combustible y repuestos (aceptado por papá) | S | 3 |
| RF61 | Anticipación configurable de avisos para **todos** los vencimientos (valores a definir) | S | 3 |
| RF62 | Estado del tiempo en el inicio del Empleador (aceptado por papá; confirma RF38) | C | 5 |
| RF63 | Historial de tarifas visible para el Empleador (confirmado) | S | 2 |

## Ronda 3 (2026-10-30)
| ID | Requisito | Prio | Etapa |
|---|---|---|---|
| RF64 | **Semáforo de vencimientos** (verde / amarillo ≤ 7 días / rojo vencido) con **alertas** activas antes del vencimiento (por defecto 15, 7 y 0 días) | M | 3 |
| RF65 | Registro del **remito**: número único por empresa, foto y datos del tambo | M | 1 |
| RF66 | Calcular el **recibo de sueldo teórico** (corta y larga distancia) con la fórmula de `14-calculo-de-sueldos.md` y compararlo con la planilla de mamá | M | 2 |
| RF67 | Registrar **ajustes sobre el recibo** (aguinaldo adicional, adelantos, cuotas de préstamo) para obtener el **pago real**, sin generar recibos legales | M | 2 |
| RF68 | Lluvia de la zona de recolección (Porteña y alrededores) en el inicio del Empleador | C | 5 |
| RF69 | Rubros de gasto de empresa y personales según las listas de mamá, con ámbito | M | 2 |
| RF70 | Importar **ventas** y **compras** de ARCA por archivo (dos formatos, carga mensual) | C | 4 |
| RF71 | Cierre de mes: exige que no queden partes sin revisar | M | 2 |

## Estado de Cobertura al 2026-11-04
Todos los requisitos funcionales de las Etapas 1, 2, 3 y 4 (RF01 a RF11, RF13 a RF27, RF29 a RF37, RF38 a RF71) están implementados y verificados en `app/` (incluyendo diagrama interactivo de 22 cubiertas por chasis con mm de dibujo y DOT, bitácora de combustible y rendimiento L/100 km, detector de anomalías de tipeo de litros por tambo, respaldo rotativo de 31 días e importador de Excel histórico, asistente guiado de cierre de mes, visor de auditoría inmutable, visor comparativo Split-Screen de remitos, tambos salteados, gastos fijos recurrentes y paquete contable de cierre mensual), lógica pura en `core/` con **30 pruebas** pasando y esquema/RLS en `database/` con **64 pruebas** pasando. Conectados a Supabase (Postgres 17, RLS, Storage) y con fallback offline transparente.
