# 005 · Alertas de vencimientos y clima
- Fecha: 2026-10-31
- Estado: aceptada

## Contexto
Las empresas lácteas ya usan un sistema con semáforo para vencimientos (verde vigente, amarillo ≤ 7 días, rojo vencido), pero no envía avisos activos y obliga a entrar a mirar (S48, S64, RF64). Además, papá consulta todos los días la lluvia en la zona de recolección (Porteña y alrededores, Córdoba) para prever el uso del camión de días de barro (RF38, RF62, RF68).

## Opciones consideradas
1. **Integración inmediata con API de WhatsApp Business:**
   - Costo adicional, plantillas sujetas a aprobación de Meta y mantenimiento de webhooks. Se pospone a la Etapa 5 (RF37).
2. **Cálculo determinista en `core/` + bandeja de alertas en el inicio + consulta meteorológica liviana:**
   - Cero costo y resuelve la visibilidad diaria al abrir la app.

## Decisión
- **Semáforo y alertas (RF61, RF64):** Implementados y probados en `core/src/vencimientos.ts`. Semáforo: `verde` (> 7 días), `amarillo` (0 a 7 días), `rojo` (< 0 días). Alertas activas configurables por defecto a los **15, 7 y 0 días** antes del vencimiento (supuesto D10), destacadas en la pantalla de inicio del Empleador y de Contaduría.
- **Clima en el inicio del Empleador (RF68, Etapa 5):** Widget de lluvia para las coordenadas de Porteña, Córdoba, consultando una API pública sin clave (ej. Open-Meteo) solo al abrir la pantalla de inicio (sin consumo en segundo plano, RNF18).

## Consecuencias
- La regla del semáforo ya cuenta con cobertura de pruebas en `core/test/vencimientos.test.ts`.
- Los avisos por WhatsApp quedan desacoplados para la Etapa 5 sin frenar las Etapas 1 a 3.

