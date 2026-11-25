# 01 · Supuestos

Estados: ⏳ Sin validar · ✅ Confirmado · ❌ Descartado · ✏️ Corregido
Última revisión: 2026-10-31 (tras 3.ª ronda de entrevistas y verificación de recibos)

## Operación
| # | Supuesto original | Estado | Fecha | Resultado |
|---|---|---|---|---|
| S01 | Cada viaje tiene fecha, camión, chofer, tambo de origen, litros cargados y fábrica | ✏️ | 2026-10-02 | Se anota lo hecho por el chofer cada día. Además: temperatura, acidez, km, horarios, ticket de caudalímetro |
| S02 | Se registran litros cargados y descargados, puede haber merma | ✅ | 2026-10-02 | Hay margen permitido; si se supera, responde el transporte (% a confirmar) |
| S03 | Un camión levanta de varios tambos por viaje | ✅ | 2026-10-02 | De 1 a 6 tambos; hasta 2 recorridos por camión por día |
| S04 | Los recorridos son fijos y se pasan a choferes | ✏️ | 2026-10-02 | Los arman las empresas, varían por temporada, se pasan por WhatsApp. Recolección fija; el destino puede variar |
| S05 | Hay más de una fábrica | ✅ | 2026-10-14 | Dos empresas: **Manfrey** y **Molfino** (La Paulina es la marca de los productos elaborados de Molfino) |

## Precios
| # | Supuesto original | Estado | Fecha | Resultado |
|---|---|---|---|---|
| S06 | El precio varía por tambo, recorrido, fábrica o fecha | ✏️ | 2026-10-02 | La Paulina: por recorrido. Manfrey: por km y litros |
| S07 | El precio cambia y hay que guardar histórico | ✅ | 2026-10-02 | Cambia por inflación/combustible. Manfrey avisa; La Paulina se ve en la facturación |
| S08 | Ingresos = litros × precio | ✏️ | 2026-10-02 | Depende del esquema de cada empresa. Se cobra por litros **cargados**. Las fábricas mandan su liquidación mensual |

## Personal
| # | Supuesto original | Estado | Fecha | Resultado |
|---|---|---|---|---|
| S09 | Choferes cobran básico + variable | ✏️ | 2026-10-02 | Dos esquemas: corta distancia (horas) y larga (km/viajes), con antigüedad, viáticos, comida, domingos, francos no gozados y bono anual |
| S10 | Adelantos se descuentan del siguiente sueldo | ✅ | 2026-10-02 | Tope 30%; casos especiales en cuotas. También hay cuotas de créditos de choferes |
| S11 | Hay francos y vacaciones a registrar | ✅ | 2026-10-02 | Se acomodan por mes y por pedido del empleado |
| S12 | Papá maneja y cobra como empleado | ✏️ | 2026-10-02 | Maneja pero no cobra sueldo |
| S13 | Choferes con celular, señal irregular | ✏️ | 2026-10-02 | Todos tienen celular e internet; hay señal en toda la zona |

## Gastos
| # | Supuesto original | Estado | Fecha | Resultado |
|---|---|---|---|---|
| S14 | Gastos se asocian a un camión | ✏️ | 2026-10-02 | Hoy las facturas no indican camión. Se debe asignar al cargar el gasto |
| S15 | Se necesita foto del comprobante | ✅ | 2026-10-02 | Hoy todo está en papel; mamá quiere digital |

## Contabilidad
| # | Supuesto original | Estado | Fecha | Resultado |
|---|---|---|---|---|
| S16 | Mamá necesita exportar a Excel/CSV/PDF | ✅ | 2026-10-02 | Excel o PDF |
| S17 | Mamá liquida con datos manuales de papá | ✏️ | 2026-10-02 | Recibe planilla manual los días 1-2; recibos legales en Holistor; facturas en ARCA |
| S18 | Mamá necesita ingresos y egresos por período y camión | ✏️ | 2026-10-02 | Por período y rubro sí. Por camión no es viable con los datos actuales |

## Uso y tecnología
| # | Supuesto original | Estado | Fecha | Resultado |
|---|---|---|---|---|
| S19 | Papá usa celular; mamá computadora | ✅ | 2026-10-02 | Papá iPhone; mamá computadora con Chrome |
| S20 | Debe ser muy simple | ✅ | 2026-10-02 | Papá prefiere escribir y anota a la noche en casa |
| S21 | Hay que poder trabajar offline | ❌ | 2026-10-02 | Hay señal siempre. Sí quieren respaldo/borrador |
| S22 | Datos de sueldos confidenciales | ✅ | 2026-10-02 | Choferes ven solo sus viajes; no ven ingresos/egresos |

## Supuestos nuevos (surgidos de las entrevistas)
| # | Supuesto | Estado | Notas |
|---|---|---|---|
| S23 | El cuaderno no es el dolor de papá (15 min/día); el dolor está en mamá (sueldos, cheques) | ✅ | Define prioridades del MVP |
| S24 | Los choferes pueden cargar su propio parte diario | ✏️ | Papá (2026-10-14): ya cargan datos del recorrido. Papá (2026-10-30): la hoja de ruta que va a la planta es **una sola global, enviada por mensaje**; los remitos se hacen día a día por recorrido. Falta saber quién completa la hoja global |
| S25 | Mamá necesita un módulo de cheques con agenda diaria | ✅ | Confirmado el 2026-10-30: prioridad #1 en su pantalla de inicio (ver S44, S60 y S63) |
| S26 | Las finanzas personales conviven con las de la empresa | ✅ | Confirmado el 2026-10-30: se separan con campo "ámbito" empresa/personal (ver S58 y S59) |
| S27 | El sistema no liquida impuestos ni genera recibos legales | ✅ | Confirmado por mamá |
| S28 | Las facturas de ARCA se pueden importar por archivo | ✅ | Confirmado el 2026-10-30: se exportan mensualmente compras y ventas en planillas separadas (ver S49 y S62) |
| S29 | Las liquidaciones de las fábricas sirven para conciliar | ✅ | Confirmado como etapa 4 (RF11); pendiente recibir muestra física |
| S30 | La planilla manual de sueldos sirve como caso de prueba | ✅ | Fórmulas ya verificadas al centavo con 2 recibos reales (2026-10-30); se contrastará con 2-3 meses de planilla |

## Riesgos
- Papá vuelve al cuaderno por costumbre. *Mitigación:* que sea tan rápido como escribir; mantener un respaldo imprimible.
- Los choferes no cargan los datos. *Mitigación:* pantalla mínima de pocos campos; papá aprueba.
- Reglas de sueldo con excepciones (domingos, francos, cuotas). *Mitigación:* validar con la planilla real.
- No se puede asignar gastos a camiones hacia atrás. *Mitigación:* capturar el camión desde el inicio.
- Datos sensibles (sueldos, finanzas personales). *Mitigación:* login, roles y backups.

## Supuestos nuevos (ronda 2: vista del empleado)
| # | Supuesto | Estado | Notas |
|---|---|---|---|
| S31 | Habrá tres vistas desde el inicio: Empleado, Empleador, Contaduría | ✅ | Decisión del equipo (2026-10-02) |
| S32 | Los choferes cargan en cada tambo/recorrido o al terminar, **no manejando** | ✅ | Adoptado como regla de diseño (RNF15, 2026-10-30); se valida en piloto con choferes (D11) |
| S33 | Cada chofer maneja habitualmente el mismo camión y recorrido | ✅ | 2026-10-30: **la asignación suele ser fija**. Flota de 7: 5 regulares + 1 de relevo + 1 para días de barro. Se mantiene el plan base y se permite cambiar de camión |
| S34 | Los celulares de los choferes permiten usar la app web y la cámara | ⏳ | Se valida en el piloto con 1-2 choferes (supuesto D11) |
| S35 | Los choferes aceptan que sus horas y jornadas queden registradas | ⏳ | Se valida en el piloto con 1-2 choferes (supuesto D11) |
| S36 | Papá aprueba los partes antes de que entren a la liquidación | ✏️ | 2026-10-30: los remitos se hacen día a día y **no se pueden verificar antes de que se entreguen**. La revisión de papá es **posterior** y no frena al chofer; se exige revisar todo antes de cerrar el mes |
| S37 | El empleado ve nivel B de su dinero (partes, adelantos y francos) en el MVP | ✅ | 2026-10-30: adoptado como supuesto de trabajo vigente D8 (`13-vista-empleado.md`, sección 10) |

## Supuestos nuevos y resultados (ronda 3, 2026-10-14)
| # | Supuesto / dato | Estado | Notas |
|---|---|---|---|
| S38 | Existe una **plantilla de recorrido** que se entrega a la fábrica | ✏️ | 2026-10-30: es una **hoja de ruta global, enviada por mensaje**. El sistema debe **generar ese mensaje/planilla** desde los partes. Sin muestra todavía |
| S39 | Cada tambo emite un **remito** con nº de tambo, fecha, hora y firma del chofer | ✅ | Se conserva en papel; el sistema guarda nº y foto |
| S40 | Margen permitido carga/descarga: **0,2 %**; si se supera, la fábrica **descuenta a valor leche** | ✏️ | 2026-10-30: se calcula **sobre el total del mes, a precio actual**. Se evalúa por mes, no por viaje. El alerta por viaje es solo preventivo. Falta confirmar si se descuenta toda la diferencia o solo el exceso (hoy: toda la diferencia) |
| S41 | Las **escalas salariales cambian todos los meses** | ✅ | Parámetro con vigencia mensual; Contaduría lo carga |
| S42 | Domingo y franco no gozado = **valor del día** que fija papá (según el día trabajado) | ✏️ | 2026-10-30: **el precio lo determina el sindicato**, no papá. Es un valor de la escala mensual. Bono anual: según convenio |
| S43 | Préstamos a choferes: créditos en **mutuales** con garantía de papá; hoy hay 3 | ✅ | 2026-10-30: mamá tiene el detalle de cuotas de la mutual y **transfiere todos los meses**. Si el chofer se va con saldo: se descuenta lo posible del último mes y el resto lo cubre la empresa si el chofer no paga |
| S44 | Cheques: se anota número, fecha, proveedor y monto; físicos y e-cheqs en la misma planilla | ✅ | 2026-10-30: lo relevante es **origen, fecha y monto**. Un cheque rechazado **se repone en pocos días**: registrar el rechazo y el cheque de reemplazo |
| S45 | Con leche ácida se **avisa a la fábrica** y no se retira | ✅ | 2026-10-30: se avisa al **área de producción primaria** de la empresa |
| S46 | 1 chofer de larga distancia y 4 de corta | ✅ | Salen 5 camiones por día |
| S47 | Papá acepta indicar el camión al cargar combustible/repuestos | ✅ | Resuelve la contradicción H2 |
| S48 | Se quieren avisos para **todos** los vencimientos y el clima en el inicio | ✅ | 2026-10-30: las empresas ya tienen un sistema con semáforo (verde vigente, amarillo a 7 días, rojo vencido) pero **no manda alertas**: hay que entrar a mirar. Clima: **lluvia**, zona de recolección (Porteña y alrededores) |
| S49 | Mamá exporta de ARCA los comprobantes para trabajar aparte | ✅ | Importación por archivo viable |
| S50 | Papá aprueba los partes antes de liquidar | ✏️ | Ver S36: revisión posterior, obligatoria antes del cierre de mes |

## Resultados de la ronda 3 (2026-10-30)
| # | Supuesto / dato | Estado | Notas |
|---|---|---|---|
| S51 | La hoja de ruta se entrega a la planta **por mensaje** y es **una global**, no una por chofer | ✅ | El sistema genera el texto/planilla para compartir. Falta: frecuencia (¿diaria o semanal?) y quién la completa |
| S52 | Los **remitos los entregan las empresas, vienen numerados** y se confeccionan día a día por recorrido | ✅ | Se guarda número (único por empresa) y foto |
| S53 | El margen del 0,2 % y su descuento se calculan sobre el **total mensual** a precio actual de la leche | ✅ | Ver S40. Reporte mensual por empresa (R18) |
| S54 | Escala salarial: la publica **FEDCAM (cámara de transporte)** y el ente fiscalizador **antes de fin de mes**; km, viáticos y comida salen de la escala | ✅ | Contaduría carga la escala del mes; el sistema no inventa valores |
| S55 | Horas: la jornada es de **8 h**; lo que pasa es extra. Se puede seguir con el **navegador del camión** | ✅ | Fuente posible para validar horas; a investigar si exporta datos |
| S56 | Licencia: se paga proporcional según recibo. **Aguinaldo: a algunos choferes se les da más que el recibo** | ✅ | Hay diferencia entre recibo legal y pago real. El sistema guarda ambos y **no emite recibos** |
| S57 | Cuotas de mutual: mamá **transfiere todos los meses** según el detalle de la mutual | ✅ | Cuota mensual por préstamo; saldo de cuotas |
| S58 | Gastos personales: servicios públicos, tarjetas, préstamos, alquiler, cuotas colegio/universidad, deporte y gimnasio, mutual, celulares, cuotas auto, matrícula contador | ✅ | Rubros con ámbito = personal |
| S59 | Rubros de empresa actuales **se mantienen** | ✅ | Combustibles, repuestos y reparaciones, seguros, sueldos, aportes, cuotas préstamos, cuotas planes ARCA, gomas, alquiler tanque, impuestos |
| S60 | Pantalla de inicio de mamá: **1) vencimientos de valores, 2) ingresos por empresa, 3) resumen de erogaciones** | ✅ | Orden de prioridad |
| S61 | Retenciones: **IIBB y contribuciones patronales se usan por mes**; ganancias una vez al año. **ARCA ya da el resumen** de todas | ✅ | No duplicar el resumen de ARCA. Registrar solo lo que mamá use cada mes |
| S62 | ARCA se exporta **mensual**, con **ventas y compras en planillas separadas** | ✅ | Importación por archivo, dos formatos |
| S63 | Un cheque rechazado se **repone en unos días** | ✅ | Vincular el cheque rechazado con su reemplazo |
| S64 | Aviso de vencimientos: semáforo **verde / amarillo (≤ 7 días) / rojo (vencido)** como en el sistema de las empresas, más **alertas** (lo que ese sistema no hace) | ✅ | 2026-10-30: semáforo confirmado; anticipaciones de alerta por defecto: 15, 7 y 0 días (supuesto D10, configurable) |
| S65 | Papá no tiene lista de estaciones ni talleres para cargar de antemano (respuesta poco clara) | ✅ | 2026-10-30: los proveedores se van dando de alta al usarlos |
