# Preguntas de seguimiento (2.ª ronda)
> ✅ **Primera parte respondida el 2026-10-14.** Las respuestas de la 3.ª ronda (2026-10-30) y los supuestos de trabajo para la vista del Empleado quedaron consolidados en [`../12-hallazgos-y-analisis.md`](../12-hallazgos-y-analisis.md#9-ronda-3-2026-10-30-respuestas-correcciones-y-decisión-de-avanzar).


Surgieron de analizar las respuestas. Completar y luego actualizar supuestos y requisitos.

## Para papá
**1.** ¿La Paulina y Molfino son la misma empresa o son distintas?

> **Respuesta:** Es la misma empresa. La Paulina es la marca con la que se encuentran los productos elaborados (Molfino).

**2.** ¿Cuántos de los 5 empleados son de corta distancia y cuántos de larga? ¿Quién es el relevo? ¿Cuántos camiones salen por día?

> **Respuesta:** Un solo empleado es de larga distancia, el resto de corta. No hay relevo predeterminado: entre todos se acomodan. Salen 5 camiones por día.

**3.** ¿Cuál es el margen de error permitido en litros (porcentaje)? Cuando se supera, ¿cómo se calcula lo que se descuenta?

> **Respuesta:** El margen de error es 0,2 %. Si se supera, la fábrica lo descuenta a valor leche.

**4.** ¿Hay datos que se anoten por tambo además de litros, temperatura y acidez (por ejemplo, número de tambo, hora, remito)?

> **Respuesta:** En un remito se anota el número de tambo, fecha, hora y firma del chofer.

**5.** ¿Qué pasa con un tambo cuya leche se rechaza por ácida? ¿Hay que avisar a alguien o anotar el motivo?

> **Respuesta:** Se avisa a la fábrica y la leche no se retira.

**6.** ¿Los choferes cargarían ellos los datos al terminar el recorrido? ¿Vos revisarías y aprobarías después?

> **Respuesta:** Los choferes cargan los datos del recorrido en la plantilla que se entrega a la fábrica. (No respondió si él revisa y aprueba: queda pendiente.)

**7.** ¿Querés poder ver en el sistema la tarifa vigente de cada empresa (por recorrido, por km y litro) y su historial de cambios?

> **Respuesta:** Sí.

**8.** Al cargar combustible o un repuesto, ¿estarías dispuesto a que el chofer (o vos) indique de qué camión es?

> **Respuesta:** Sí.

**9.** ¿Qué vencimientos querés que avise (licencia, psicofísico, VTV, seguro, service, otros) y con cuánta anticipación?

> **Respuesta:** Todos.

**10.** ¿Querés ver el estado del tiempo en la pantalla de inicio? (Dijiste que lo mirás todos los días.)

> **Respuesta:** Estaría bueno.

## Para mamá
**1.** ¿Podés pasarme (sin datos sensibles si querés) una **planilla de sueldos de un mes**, el **Excel de cheques** y **una liquidación de cada fábrica**?

> **Respuesta:** Sí. Consulta por dónde pasarlo (¿WhatsApp?). Ver ronda-3.

**2.** En la planilla de sueldos: ¿cuál es la fórmula para cada chofer (corta y larga distancia)? ¿Qué valores cambian por mes (básico, valor por km, por recorrido, viáticos, comida)?

> **Respuesta:** Las escalas salariales cambian todos los meses.

**3.** Dijiste que el sueldo que se paga es "otro" respecto al recibo. ¿Qué querés que calcule el sistema: el monto a pagar según la planilla, y que el recibo siga en Holistor? ¿Hay conceptos que se pagan fuera del recibo que deban quedar registrados?

> **Respuesta:** El recibo de ley se hace en Holistor. El sistema puede calcular el sueldo real que se paga según la planilla.

**4.** ¿Cómo se calcula el pago por domingo trabajado y por franco no gozado? ¿Y el bono anual?

> **Respuesta:** El domingo y el franco son un valor del día que decide papá, de acuerdo al valor del día trabajado. El bono anual es el que establece el convenio colectivo.

**5.** Préstamos a choferes: ¿cómo funcionan (monto, cuotas, quién lo autoriza)? ¿Cuántos hay hoy?

> **Respuesta:** Los autoriza Gastón (firma de garantía en las mutuales). Hoy hay 3 choferes cuyos créditos paga la empresa.

**6.** Cheques: ¿qué datos anotás hoy de cada uno (número, banco, monto, fecha de emisión, fecha de pago, a quién, estado)? ¿Hay e-cheqs y cheques físicos?

> **Respuesta:** Hay cheques físicos y e-cheqs, en la misma planilla. Anota número de cheque, fecha, proveedor y monto.

**7.** ¿Querés que el sistema avise cuando un cheque vence ese día o los próximos días?

> **Respuesta:** Sí, puede ser.

**8.** Gastos personales: ¿querés llevarlos dentro del mismo sistema (separados de los de la empresa) o solo la parte de la empresa?

> **Respuesta:** Es lo mismo: con los ingresos de las empresas se pagan todos los gastos, pero podrían estar separados.

**9.** Facturas sin IVA o comprobantes informales: ¿cómo querés que figuren al cargarlos (tipo de comprobante, rubro, medio de pago)?

> **Respuesta:** Sí, pueden ser esos datos (tipo de comprobante, rubro, medio de pago).

**10.** Retenciones que hacen las fábricas: ¿querés registrarlas por cobro (ganancias, IIBB, seguridad social) para tener un resumen anual?

> **Respuesta:** Sí.

**11.** ¿Te sirve que se pueda importar el listado de comprobantes de ARCA ("Mis Comprobantes") en Excel/CSV?

> **Respuesta:** Sí. De ARCA se pueden exportar esos archivos para trabajar aparte.

**12.** ¿Qué te gustaría que cada pantalla de inicio de tu vista mostrara? (Ej.: cheques que entran hoy y esta semana, gastos del mes por rubro, alertas de sueldos.)

> **Respuesta:** Aceptó las opciones propuestas sin priorizar. Ver ronda-3.

---

# Parte 2 · Vista del Empleado y carga de datos

## Para papá (continuación)
**11.** Los choferes, ¿cargarían los datos en cada tambo (con el camión detenido), al terminar cada recorrido o al volver a casa? ¿Qué te parece más realista?

> **Respuesta:**

**12.** ¿Cada chofer maneja siempre el mismo camión y el mismo recorrido, o rotan? ¿Con qué frecuencia cambian?

> **Respuesta:**

**13.** ¿Preferís asignar vos cada día el recorrido y el camión, que quede un plan semanal fijo que ellos confirman, o que cada chofer elija el suyo?

> **Respuesta:**

**14.** Si un chofer se olvida de cargar o se equivoca, ¿quién lo corrige y hasta cuándo? ¿Querés aprobar cada parte o solo revisar los que tienen alertas?

> **Respuesta:**

**15.** ¿Qué celulares tienen los choferes (iPhone, Android, marca y antigüedad aproximada)? ¿Alguno con un celular viejo o con poco espacio?

> **Respuesta:**

**16.** En corta distancia, ¿cómo se registran hoy las horas de entrada y salida? ¿El chofer las anota o las anotás vos?

> **Respuesta:**

**17.** ¿Qué hacen cuando hay un cambio de última hora (otro camión, otro tambo, un recorrido extra)? ¿Se avisa por WhatsApp?

> **Respuesta:**

**18.** ¿Los choferes cargan combustible, peajes o gastos de viaje? ¿Cómo se reintegran los viáticos?

> **Respuesta:**

**19.** ¿Querés que el chofer pueda pedir franco, vacaciones o adelanto desde la app, y que vos lo apruebes?

> **Respuesta:**

**20.** ¿Querés que puedan reportar una avería o un problema del camión con foto y descripción?

> **Respuesta:**

**21.** ¿Cada mes los choferes firman o dan su conformidad a la liquidación? ¿Hay reclamos frecuentes sobre horas, km o viajes?

> **Respuesta:**

**22.** Cuando vos manejás, ¿cargás tu parte como un chofer más? ¿Alguien te lo aprueba?

> **Respuesta:**

**23.** ¿Quién va a dar de alta y baja a los choferes y resetear claves? ¿Quién les va a dar soporte si algo falla?

> **Respuesta:**

**24.** ¿Cómo imaginás la transición: probarlo un mes en paralelo con el cuaderno con uno o dos choferes, o pasar a todos juntos?

> **Respuesta:**

## Para mamá (continuación)
**13.** Los choferes, ¿deberían ver también sus horas/km acumulados, adelantos y francos? ¿Y su sueldo estimado o solo sus viajes?

> **Respuesta:**

**14.** ¿Cómo se controla hoy la planilla de horas o de viajes antes de liquidar? ¿Alguien la firma o confirma?

> **Respuesta:**

**15.** Cierre de mes: ¿hasta qué día pueden corregirse los partes? ¿Querés que el sistema **bloquee** el mes cuando liquidás?

> **Respuesta:**

**16.** ¿Qué datos de cada empleado necesitás para Holistor (CUIL, categoría, fecha de ingreso, etc.) para cargarlos una sola vez en el sistema?

> **Respuesta:**

**17.** ¿Querés ver los partes pendientes de aprobación o solo los aprobados?

> **Respuesta:**

**18.** Los gastos de combustible o repuestos sin camión asignado, ¿cómo querés tratarlos: dejarlos "sin asignar" y asignarlos después, o exigir el camión siempre?

> **Respuesta:**

**19.** ¿Querés poder ver quién modificó un sueldo, un cheque o un gasto y cuándo?

> **Respuesta:**

**20.** Copias de seguridad: ¿te serviría recibir cada mes un Excel/PDF completo para guardar vos?

> **Respuesta:**

## Para los choferes (entrevista corta, 5-10 min, a 2 o 3 de ellos)
**1.** ¿Qué celular tenés (marca y modelo) y tenés internet todo el día?

> **Respuesta:**

**2.** ¿Cómo anotás hoy lo que hacés en el día (papel, WhatsApp, de memoria)? ¿Cuánto tiempo te lleva?

> **Respuesta:**

**3.** ¿Cuándo te resultaría cómodo cargar los datos: en cada tambo, al terminar el recorrido o en tu casa?

> **Respuesta:**

**4.** ¿Qué datos te parecen más molestos o difíciles de cargar (temperatura, acidez, litros, km, fotos)?

> **Respuesta:**

**5.** ¿Te sirve ver tu recorrido del día en la app? ¿Qué información necesitás de cada tambo?

> **Respuesta:**

**6.** ¿Qué querrías ver de tus viajes, tus francos, tus adelantos y tu sueldo?

> **Respuesta:**

**7.** ¿Preferís entrar con un PIN, con huella o Face ID del celular?

> **Respuesta:**

**8.** ¿Alguna vez tuviste problemas con una app de trabajo? ¿Qué no querés que pase?

> **Respuesta:**

**9.** ¿Te molesta sacar una foto del ticket en cada carga?

> **Respuesta:**

**10.** ¿Qué te preocupa de cargar vos mismo tus datos (errores, que quede registrado, que te controlen)?

> **Respuesta:**
