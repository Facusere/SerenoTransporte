# 006 · Exportación, hoja de ruta global e integración por archivos
- Fecha: 2026-10-31
- Estado: aceptada

## Contexto
Mamá necesita exportar sueldos, cheques y reportes en **Excel y PDF** (RF19, RF32, RNF10), e importar mensualmente las planillas de compras y ventas descargadas de **ARCA** (RF27, RF70). Por su parte, a la planta láctea se le envía una **hoja de ruta global por mensaje** con los recorridos del día (S51, RF53). Holistor, ARCA y los bancos no se conectan de forma directa (RNF14).

## Opciones consideradas
1. **Integración directa por API / Webservices con ARCA (WSFE) y Holistor:**
   - Descartada por complejidad fiscal, certificados digitales y decisión explícita de negocio (RNF14, RF20, RF28).
2. **Generación de texto/archivos en la aplicación e importación de CSV/XLSX de ARCA:**
   - Mantiene al sistema simple, auditable y sin riesgo de emitir comprobantes fiscales por error.

## Decisión
- **Hoja de ruta global (RF53):** Se genera automáticamente a partir de los partes del día en dos formatos:
  1. **Texto formateado** con un botón "Copiar / Compartir por WhatsApp" desde el celular del Empleador.
  2. **Archivo descargable (Excel/PDF)**. La plantilla del mensaje se mantiene desacoplada para ajustarla apenas se reciba una muestra real (supuestos D2 y D3).
- **Exportaciones (RNF10):** Generación de planillas `.xlsx` y documentos `.pdf` (imprimibles como respaldo físico o "borrador", RF35) para sueldos, cheques y partes.
- **Importación de ARCA (RF70, Etapa 4):** Lector de archivos `.xlsx`/`.csv` para los dos formatos mensuales de "Mis Comprobantes" (ventas y compras por separado, S62), previsualizando antes de guardar.

## Consecuencias
- El sistema reemplaza el armado manual del mensaje de hoja de ruta desde la Etapa 1.
- Cero acoplamiento con sistemas externos de AFIP/ARCA o estudio contable.

