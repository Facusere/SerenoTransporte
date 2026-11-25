# 12 · Hallazgos y análisis (post-entrevistas)

Fecha: 2026-10-02 · Fuente: `assets/respuestas/Preguntas-respondidas-2026-10-02.pdf`

## 1. El problema real no es el cuaderno de papá, es el trabajo de mamá
- Papá: el cuaderno le lleva **15 min por día** y "es la costumbre". Su preocupación diaria es operativa (que no se rompa nada, cumplir).
- Mamá: recibe los sueldos los días 1-2, **tiene que re-controlar las sumas** (errores de suma, viajes sin sumar), dedica ~1 h a sueldos + ~2 h a preparar pagos y registrar en Excel, y **controla cheques todos los días**.

**Implicancia:** el valor del sistema está en (a) eliminar la planilla manual de sueldos y sus errores, (b) ordenar cheques y gastos para mamá. Para papá, el sistema tiene que ser **igual o más rápido que el cuaderno** o vuelve a él. Papá ya dijo que sería más ágil si **los choferes cargaran sus propios datos**: ese es el cambio de proceso clave (cada chofer carga su parte diario; papá revisa/aprueba).

## 2. Contradicciones y dudas a resolver
| # | Tema | Qué dijeron | Acción |
|---|---|---|---|
| H1 | Nombre de la 2.ª empresa | ✅ **Resuelto (2026-10-14):** La Paulina y Molfino son la misma empresa; La Paulina es la marca de los productos | Usar "Molfino" como empresa y "La Paulina" como marca |
| H2 | Gastos por camión | ✅ **Resuelto (2026-10-14):** papá acepta indicar el camión al cargar combustible y repuestos | Asignar camión al cargar; las facturas viejas quedan sin asignar |
| H3 | Qué ve el chofer | Papá: "les gusta ver todo". Mamá: "solo sus viajes", ingresos/egresos no | Definir: viajes, francos, adelantos y su propia liquidación propios; nada de ingresos/egresos de la empresa |
| H4 | Cobro por litros | Se cobra por litros **cargados** (no descargados como suponíamos) | Corregido; descargados sirve para controlar mermas |
| H5 | Sueldo "legal" vs sueldo "que se paga" | Mamá: el recibo legal se hace en Holistor (estudio); el sueldo que pagan "es otro" según la planilla | Preguntar a mamá qué diferencia hay y qué debería calcular el sistema (ver nota) |
| H6 | Empleados | ✅ **Resuelto (2026-10-14):** 5 empleados (1 larga, 4 corta), sin relevo fijo, salen 5 camiones por día | Rotación informal de camiones |
| H7 | Control de la facturación a fábricas | Hoy se controla "en la liquidación que ellos envían" | Oportunidad: cruzar con nuestros propios registros para detectar diferencias |

> **Nota H5 y comprobantes sin IVA:** el sistema registra lo que se paga y los comprobantes tal como son, con un campo "tipo de comprobante". **No genera recibos legales ni liquida impuestos** (mamá lo confirmó: eso lo hace el contador/estudio). Las decisiones fiscales son de mamá y su contador, no del sistema.

## 3. Reglas de negocio descubiertas
**Viajes y calidad**
- Hasta **2 recorridos por camión por día**; cada recorrido pasa por **1 a 6 tambos**.
- Los recorridos los arman las **empresas**, varían por **temporada** (más/menos producción). La recolección primaria es fija; el destino de descarga puede variar.
- Medición: **caudalímetro** del camión (emite ticket); si falla, **regla** del tambo (manual). La fábrica descarga con su caudalímetro.
- **Obligatorio por tambo:** temperatura y **prueba de acidez** (leche ácida **no se carga**; queda registrado el rechazo).
- Existe un **margen de error permitido** carga/descarga; si se supera, **el transporte responde**.
- Deseable: km, horarios y combustible por viaje.

**Tarifas**
- La Paulina: pago **por recorrido**. Manfrey: **por km y litros**.
- Los valores cambian con inflación/combustible (referencia: cámara de transporte). Manfrey avisa mes a mes; en La Paulina se ve en la facturación.
- Las fábricas **envían la liquidación mensual** (viajes, litros, km, montos); mamá factura en ARCA con eso. Cobro mensual por orden de pago/transferencia o e-cheqs; con **retenciones** (ganancias, ingresos brutos, seguridad social).

**Sueldos**
- Convenio 40/89 (Camioneros Córdoba). Dos esquemas:
  - **Corta distancia:** básico, antigüedad, horas extras, viáticos, comida → **planilla de horas**.
  - **Larga distancia:** básico, antigüedad, km recorridos, viáticos por km → **planilla de viajes**.
- Extras aparte: **trabajo en domingo**, **franco no gozado** (si no toman los 6 francos), **bono anual**.
- Adelantos: **tope 30% del sueldo**, se descuentan el mes siguiente; excepcionalmente en **cuotas**. También hay **cuotas de créditos de choferes** que paga la empresa y luego descuenta.
- Pago mensual dentro de los **primeros 5 días hábiles**, por transferencia. Mamá recibe datos el día 1-2.
- Vacaciones y aguinaldo: según recibo de ley (Holistor). Francos/vacaciones: se acomodan por mes y por pedido.

**Gastos y contabilidad**
- Rubros de mamá: combustibles, repuestos y reparaciones, seguros, sueldos, aportes, cuotas préstamos, cuotas planes de pago ARCA, gomas, alquiler tanque, impuestos. Patentes: pago anual.
- Combustible: 2 estaciones locales, **pago con cheque**.
- Facturas: **todo en papel** (carpetas); quiere foto digital.
- Contabilidad: Holistor (sueldos), ARCA (facturas compra/venta), Excel (cheques), planilla mensual propia de ingresos/egresos que **incluye gastos personales** para prever que alcance el dinero.
- Responsable Inscripto unipersonal (IVA y Ganancias).
- Papá **no cobra sueldo** (retira lo necesario).

## 4. Qué cambia respecto a lo que habíamos supuesto
1. Nuevo módulo central: **Cheques** (emitidos y recibidos, e-cheqs, agenda diaria de cobros). No estaba previsto y es lo que mamá más quiere ver.
2. La unidad de trabajo es el **parte diario del chofer** (recorridos, horas, km, litros, temperatura, acidez), no el "viaje" suelto.
3. **Offline pasa a baja prioridad**: hay señal en toda la zona. Sí hace falta **respaldo**/exportación imprimible ("siempre es ideal un borrador").
4. Hay **dos esquemas de tarifa** y **dos esquemas de sueldo** que el modelo debe soportar.
5. Hay **finanzas personales mezcladas** con las de la empresa: hace falta un campo "ámbito" (empresa/personal) para poder separarlas.
6. **Rentabilidad por camión** es posible solo si se captura el camión al cargar cada gasto; no se puede reconstruir de las facturas actuales.
7. **Conciliación con las liquidaciones de las fábricas** es un valor agregado no pedido pero muy útil.

## 5. Implicancias técnicas (para decidir luego, en `10-decisiones/`)
- Papá usa **iPhone** y Chrome en la computadora de mamá → una **app web instalable (PWA)** cubre ambos sin tiendas de apps; en iPhone requiere "agregar a pantalla de inicio" y las notificaciones push funcionan en iOS 16.4+.
- Papá vive en **WhatsApp**: evaluar avisos por WhatsApp (vencimientos, recorridos) como fase posterior.
- **Importar desde ARCA**: ARCA permite descargar listados de "Mis Comprobantes" en archivo; conviene importar por CSV/Excel, no por integración directa.
- **Selector de vista al inicio** (idea de ustedes): conviene implementarlo con **login + roles**. Si se elige "papá/mamá" sin clave, cualquiera que abra la app vería sueldos y cheques. Alternativa cómoda: sesión recordada en el dispositivo + PIN corto para cambiar de vista. Los datos son los mismos para todos y se actualizan al instante.
- Módulo de sueldos: capturar datos y calcular el monto interno; **el recibo legal sigue en Holistor**.

## 6. Datos para validar el diseño
- Usar la **planilla manual de sueldos** de 2-3 meses de mamá como caso de prueba: el sistema debe reproducir sus resultados.
- Pedir **una liquidación mensual de cada fábrica** y **el listado de cheques en Excel**: definen los formatos de importación/exportación.
- Pedir **fotos del cuaderno** y de un **ticket del caudalímetro**.

## 7. Ronda 2: tres vistas y carga por los empleados (2026-10-02)
- Como los choferes cargarán sus datos, las **tres vistas son parte del MVP**: Empleado (carga), Empleador (aprueba), Contaduría (finanzas). Ver `13-vista-empleado.md`.
- Aparece un **ciclo de aprobación** del parte (borrador → enviado → aprobado → bloqueado por mes) que protege a mamá de los errores de suma.
- La clave del éxito es la **adopción por los choferes**: formulario mínimo, uso con el camión detenido, autoguardado y un mes en paralelo con el cuaderno.
- Quedan decisiones abiertas: cómo se asigna el recorrido del día (se propone plan semanal base), qué ve el empleado de su plata (se propone nivel B) y quién da soporte.

## 8. Ronda 3 (2026-10-14): hallazgos de la segunda ronda de preguntas
**Lo más importante**
1. **Los choferes ya cargan una plantilla que se entrega a la fábrica** *(precisado el 2026-10-30: es una hoja de ruta global enviada por mensaje; ver sección 9)*. Es la oportunidad más grande: el parte diario de la app debe **cubrir esa plantilla y generarla** (PDF/Excel) para enviarla. Así el sistema reemplaza una tarea en vez de agregar otra. Hay que conseguir una copia del formato de cada empresa.
2. **El remito de cada tambo** (nº de tambo, fecha, hora, firma) sigue en papel; el sistema guarda su número y una foto.
3. **Margen de error 0,2 %** *(corregido el 2026-10-30: se mide sobre el total del mes)*: si se supera, la fábrica descuenta a valor leche. El sistema puede calcular el descuento esperado y compararlo con lo que descuenta la liquidación.
4. **Escalas salariales mensuales:** hay que modelarlas como parámetros con vigencia por mes, cargados por Contaduría. El domingo y el franco no gozado usan un valor del día *(corregido el 2026-10-30: lo fija el sindicato, está en la escala)*.
5. **Préstamos:** créditos de **mutuales** con garantía de papá; la empresa paga la cuota y la descuenta (hoy 3 choferes).
6. **Cheques:** hoy se anota número, fecha, proveedor y monto. Se agregan banco, estado y concepto.
7. **Contradicción resuelta:** papá acepta indicar el camión al cargar combustible o repuestos.
8. **Mamá confirmó** que el sistema puede calcular el **sueldo real a pagar**, que el recibo legal sigue en Holistor y que no se liquidan impuestos.

**Sigue sin respuesta**
- ~~Si papá aprueba los partes antes de que pasen a mamá~~ (resuelto el 2026-10-30: revisión posterior).
- La fórmula exacta de sueldo (mamá respondió que las escalas cambian mensualmente, no la fórmula).
- Qué prioriza mamá para su pantalla de inicio (aceptó las opciones sin ordenarlas).
- La entrevista corta a los choferes.

**Archivos a conseguir:** plantilla de la fábrica (Manfrey y Molfino), un remito, planilla de sueldos, Excel de cheques y una liquidación de cada fábrica. Mamá consultó por dónde pasarlos y envió dos recibos de sueldo que se analizaron en la sección 9 y en `14-calculo-de-sueldos.md`.

## 9. Ronda 3 (2026-10-30): respuestas, correcciones y decisión de avanzar

### 9.1 Lo que cambió respecto a lo que suponíamos
| Tema | Antes | Ahora |
|---|---|---|
| Margen 0,2 % | Se evaluaba por viaje | Se evalúa **por mes y por empresa**, sobre el total, a precio actual de la leche. El alerta por viaje es solo preventivo |
| Valor de domingo y franco | Lo fijaba papá | Lo fija el **sindicato** (va en la escala mensual) |
| Aprobación de partes | Papá aprobaba antes de liquidar | Papá **revisa después**, porque los remitos no se pueden verificar antes de entregarse. Se exige todo revisado para **cerrar el mes** |
| Asignación de camiones | Rotación informal | **Suele ser fija**: 5 regulares + 1 relevo + 1 de días de barro |
| Hoja para la fábrica | Una plantilla por empresa | **Una hoja de ruta global enviada por mensaje** |
| Vencimientos | Había que inventar un sistema | Las empresas ya usan **semáforo** (verde / amarillo a 7 días / rojo). Lo que falta son **alertas** |
| Retenciones | Registrarlas por cobro | ARCA ya da el resumen: solo se registra lo que mamá usa por mes |
| Cheques | Banco, estado, concepto | Lo relevante es **origen, fecha y monto**; un rechazado se **repone en pocos días** |

### 9.2 Hallazgo principal: el cálculo de sueldos ya se puede construir
Con los dos recibos (corta y larga distancia) se dedujo la fórmula completa y **reproduce ambos recibos al centavo**. Detalle en `14-calculo-de-sueldos.md`. El monto que se paga no coincide siempre con el recibo (aguinaldo adicional, cuotas de mutual, adelantos), por eso el modelo separa **recibo teórico** y **pago real**.

### 9.3 Dudas abiertas y supuesto de trabajo
Se decidió **no frenar el proyecto** por estas dudas. Cada una tiene un supuesto de trabajo y un lugar del sistema donde es configurable.

| # | Duda | Supuesto de trabajo | Dónde se ajusta |
|---|---|---|---|
| D1 | ¿Con margen superado se descuenta toda la diferencia o solo el exceso? | **Toda la diferencia del mes** (lo que dijo papá: "sobre el total") | Parámetro `modo` del cálculo del margen |
| D2 | ¿Quién completa la hoja de ruta global y cada cuánto se manda? | Se genera sola a partir de los partes y se manda **por día** | Pantalla del Empleador |
| D3 | Formato exacto de la hoja de ruta, remito y liquidaciones de las plantas | Formato propio razonable; se ajusta al recibir la muestra | Plantilla del mensaje |
| D4 | Base del **tope de adelantos del 30 %**: ¿sueldo neto o bruto? | **Neto del recibo teórico** del mes | Parámetro |
| D5 | Fórmula de **domingo trabajado y franco no gozado** en la escala | Valor fijo por día cargado por Contaduría en la escala del mes | Escala mensual |
| D6 | Significado de los códigos de km (`4.2.3`, `4.2.4`, "100 % M", "MP LAC") | Se tratan como **ítems de la escala**, cada uno con su tarifa y su marca remunerativo / no remunerativo | Escala mensual |
| D7 | Prorrateo del sueldo por ingreso o egreso a mitad de mes | **No se prorratea** en el MVP; se ajusta a mano | Ajustes del pago real |
| D8 | Qué ve el empleado de su dinero | **Nivel B** (partes, adelantos y francos) | `13-vista-empleado.md`, sección 10 |
| D9 | ¿Los choferes cargan combustible? | Sí, con el camión asignado automáticamente | Permisos |
| D10 | Anticipación de alertas | **15, 7 y 0 días**, configurable | Parámetro |
| D11 | Entrevista a choferes (celulares, aceptación) | Se prueba con **1 o 2 choferes en piloto**, en paralelo con el cuaderno | Plan de adopción |
| D12 | ¿El navegador del camión exporta horas? | No se depende de él; el chofer carga hora de inicio y fin | Investigación posterior |
| D13 | ¿Qué horas extras van al 100 % y cuáles al 50 %? | Las define quien revisa el parte (ver `14-calculo-de-sueldos.md`) | Carga manual |
| D14 | Regla de las unidades de comida y viático | Se cargan a mano por mes hasta confirmar | Carga manual |

### 9.4 Cómo seguir
Las preguntas dejan de ser el camino crítico. Si hace falta, se agregan en `09-preguntas/` cuando algo bloquee de verdad. Lo que sí ayudaría, sin frenar el desarrollo: una muestra de la hoja de ruta, un remito, una liquidación de cada planta y la planilla de sueldos de 2 o 3 meses (sin datos personales).
