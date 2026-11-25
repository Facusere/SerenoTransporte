# 14 · Cálculo de sueldos (recibo teórico y pago real)

Fecha: 2026-10-30 · Fuente: los dos recibos que pasó mamá (corta y larga distancia) y sus respuestas de la ronda 3.

> **Alcance.** El sistema calcula un **recibo teórico** para comparar con la planilla de mamá y obtener el **pago real**. **No emite recibos legales** (eso sigue en Holistor) **ni liquida impuestos**. Los importes de los recibos reales **no se guardan en el repo**; acá solo están la estructura y las reglas.

## 1. Conceptos del recibo
| Código | Concepto | Corta | Larga | Tipo |
|---|---|---|---|---|
| 001000 | Sueldo mensual | ✅ | ✅ | Remunerativo |
| 002000 | Horas extras 50 % | ✅ | – | Remunerativo |
| 002100 | Horas extras 100 % | ✅ | – | Remunerativo |
| 014104, 014106 | Km (ítem 4.2.3) | – | ✅ | Remunerativo |
| 018801 | Antigüedad (6.1.5) | ✅ | ✅ | Remunerativo |
| 014103, 014105 | Km (ítem 4.2.4) | – | ✅ | **No** remunerativo |
| 014400 | Comida (4.1.12) | ✅ | – | **No** remunerativo |
| 015000 | Viático especial (4.1.13) | ✅ | – | **No** remunerativo |
| 030000 | Jubilación | ✅ | ✅ | Descuento 11 % |
| 030200 | Ley 19032 | ✅ | ✅ | Descuento 3 % |
| 031000 | Obra social | ✅ | ✅ | Descuento 3 % |
| 032305 | Cuota sindical | ✅ | ✅ | Descuento 3 % |
| 032306 | Cuota de afiliación | ✅ | ✅ | Descuento, **importe fijo** |
| 034005 | Seguro de sepelio | ✅ | ✅ | Descuento 1,5 % |

## 2. Fórmulas (verificadas)
1. **Sueldo mensual** = valor de la escala del mes para la categoría. (La columna "unidad" del recibo muestra los días del mes, 30 o 31; es informativa.)
2. **Valor hora** = sueldo mensual ÷ **192**.
3. **Horas extras 50 %** = valor hora × 1,5 × horas. **Horas extras 100 %** = valor hora × 2 × horas.
4. **Km (larga)** = km de cada ítem × tarifa del ítem. Los ítems 4.2.3 son remunerativos; los 4.2.4, no remunerativos.
5. **Antigüedad** = % de antigüedad × **suma de los conceptos remunerativos, sin contar la antigüedad** (en corta: sueldo + extras; en larga: sueldo + km 4.2.3).
6. **Comida** y **viático especial** = unidades × valor por unidad de la escala.
7. **Remunerativo** = suma de conceptos remunerativos. **No remunerativo** = suma de conceptos no remunerativos.
8. **Descuentos** = 11 % + 3 % + 3 % + 3 % + 1,5 % **del remunerativo**, más la cuota de afiliación (importe fijo del mes).
9. **Bruto** = remunerativo + no remunerativo. **Neto** = bruto − descuentos.
10. **Redondeo:** cada concepto se redondea a centavos y después se suma.

## 3. Verificación
Con los datos de los dos recibos, la fórmula reproduce **al centavo** el remunerativo, el no remunerativo, los descuentos y el neto, tanto en corta como en larga distancia. En la muestra de larga, las cuatro líneas de km usan la **misma tarifa por km**. Antes de usarlo en producción se repite con 2 o 3 meses de la planilla de mamá.

## 4. Escala mensual (parámetros que carga Contaduría)
La escala cambia **todos los meses** (la publica FEDCAM antes de fin de mes). Cada mes se carga:
- Sueldo mensual por categoría (corta / larga).
- Divisor de horas (hoy 192) y recargos de extras (1,5 y 2).
- Tarifa por km de cada ítem de km y si es remunerativo.
- Valor por unidad de comida y de viático especial.
- Valor de **domingo trabajado** y **franco no gozado** (lo fija el sindicato).
- Porcentajes de descuentos y cuota de afiliación.
- Bono anual según convenio.

## 5. Del recibo teórico al pago real
`pago real = neto del recibo teórico + ajustes`

Los ajustes son líneas que carga Contaduría o el Empleador, cada una con concepto, monto (positivo o negativo) y nota:
- **Aguinaldo adicional** al del recibo (a algunos choferes se les paga más).
- **Adelantos** (tope **30 %** del sueldo; se descuentan el mes siguiente o en cuotas).
- **Cuotas de préstamos de mutual**: mamá transfiere cada mes la cuota y se descuenta al chofer.
- Otros.

El tratamiento fiscal de esas diferencias lo deciden mamá y su contador; el sistema solo las registra y las muestra.

## 6. Datos de entrada por chofer y mes
| Dato | Corta | Larga | De dónde sale |
|---|---|---|---|
| Horas extras 50 % y 100 % | ✅ | – | Partes aprobados (jornada de 8 h; lo que pasa es extra) |
| Unidades de comida y viático | ✅ | – | Partes aprobados |
| Km por ítem | – | ✅ | Partes aprobados |
| Antigüedad (%) | ✅ | ✅ | Ficha del empleado |
| Domingos y francos no gozados | ✅ | ✅ | Partes y francos |

## 7. Dudas abiertas (con supuesto de trabajo)
| # | Duda | Supuesto |
|---|---|---|
| D13 | ¿Qué horas extras son al **100 %** y cuáles al 50 %? | Las carga Contaduría o el Empleador al revisar el parte; el sistema no lo decide solo |
| D14 | ¿Cómo se determinan las **unidades de comida y viático** (días, salidas)? | Se cargan a mano por mes hasta confirmar la regla |
| D6 | Reparto de los km entre ítems 4.2.3 y 4.2.4 | Contaduría carga los km por ítem |
| D7 | Prorrateo por ingreso o baja a mitad de mes | No se prorratea en el MVP |

## 8. Implementación
La lógica está en `core/src/liquidacion.ts`, con pruebas en `core/test/`. Trabaja con **centavos enteros** para evitar errores de redondeo con decimales.
