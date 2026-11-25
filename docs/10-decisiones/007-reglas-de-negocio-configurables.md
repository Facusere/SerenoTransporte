# 007 · Reglas de negocio configurables y supuestos vigentes
- Fecha: 2026-10-31
- Estado: aceptada con supuestos

## Contexto
Las escalas salariales de FEDCAM, las tarifas de las fábricas (Manfrey y Molfino/La Paulina), el precio de la leche para evaluar el margen del 0,2 % y ciertos criterios operativos cambian mes a mes o tienen matices que no deben frenar el desarrollo (RNF13, `docs/12-hallazgos-y-analisis.md` sección 9).

## Opciones consideradas
1. **Codificar valores fijos o frenar la construcción hasta recibir cada documento histórico:**
   - Rompe RNF13 y demora innecesariamente la entrega del MVP.
2. **Parametrizar por vigencia mensual y aislar cada supuesto de trabajo (D1–D14) en funciones puras y tablas de configuración:**
   - Permite avanzar de inmediato y cambiar un parámetro sin redesplegar código.

## Decisión
Adoptar como reglas de diseño obligatorias (implementadas en `core/` y `database/schema.sql`):
1. **Dinero en centavos enteros (`core/src/dinero.ts`):** Ningún cálculo monetario usa coma flotante.
2. **Escala salarial mensual con vigencia (`core/src/liquidacion.ts`):** Contaduría carga cada mes los valores publicados por FEDCAM (básico por categoría, divisor 192, tarifas de km remunerativos 4.2.3 y no remunerativos 4.2.4, comida, viático especial, valor de domingo y franco no gozado fijado por el sindicato, porcentajes de descuento y cuota fija de afiliación).
3. **Separación de recibo teórico y pago real:** El sistema calcula el `recibo teórico` (que reproduce al centavo los recibos reales) y le aplica `ajustes` (aguinaldo adicional, adelantos, cuotas de mutuales) para obtener el `pago real`. Nunca emite recibos legales.
4. **Margen del 0,2 % mensual por empresa (`core/src/margen.ts`):** Se evalúa sobre la suma mensual de litros cargados vs. descargados por empresa (`v_litros_mensuales_por_empresa`), con `modo` configurable (`'total'` por defecto según supuesto D1, o `'exceso'`). El aviso por viaje es solo informativo.
5. **Tope de adelantos (`core/src/adelantos.ts`):** 30 % configurable sobre el sueldo neto del recibo teórico (supuesto D4), descontable en el mes siguiente o en cuotas cuya suma da siempre el monto exacto en centavos.
6. **Revisión posterior y cierre de mes (`database/schema.sql`):** El envío del parte no bloquea al chofer; el Empleador revisa después. Contaduría cierra el mes con `cerrar_mes(mes)`, función que exige cero partes sin revisar (RF71).
7. **Asignación habitual con cambio de camión:** Cada empleado tiene `camion_habitual_id` y `recorrido_habitual_id` en su ficha, pudiendo cambiar el camión en el parte del día (`regular`, `relevo`, `barro`).

## Consecuencias
- Los 14 supuestos de trabajo (D1–D14) tienen un único punto de configuración identificado.
- Cualquier ajuste futuro se resuelve cambiando un parámetro o una plantilla sin reescribir la lógica ni migrar datos históricos.

