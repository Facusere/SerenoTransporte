# 004 · Fotos y archivos: almacenamiento y compresión
- Fecha: 2026-10-31
- Estado: aceptada

## Contexto
El sistema almacena fotos de tickets de caudalímetro (RF03), remitos firmados por tambo (RF54, RF65) y comprobantes de gastos de mamá (RF23). Las cámaras actuales generan imágenes de 4 a 12 MB, lo que consumiría datos móviles del chofer (RNF18) y llenaría rápidamente la cuota de almacenamiento (RNF07, RNF12).

## Opciones consideradas
1. **Subir la foto original del teléfono y comprimir en servidor:**
   - Gasta datos móviles en cabina y tarda en subir con señal débil.
2. **Compresión en el navegador del cliente antes de subir + Supabase Storage privado:**
   - Reduce la imagen a ~150–300 KB en el propio celular en menos de un segundo antes de transmitirla por la red.

## Decisión
- **Compresión en el cliente (RF52, RNF18):** Redimensionar en el navegador (Canvas / WebP o JPEG, lado máximo 1600 px, calidad ~0.75) antes de subir, apuntando a ≤ 250 KB por imagen.
- **Almacenamiento (RNF12):** Bucket privado en **Supabase Storage** con rutas estructuradas por período y entidad (`partes/YYYY-MM/<parte_id>/<archivo>.webp`, `gastos/YYYY-MM/<gasto_id>.webp`).
- **Base de datos:** Las tablas guardan únicamente la ruta relativa (`foto_ticket_path`, `foto_remito_path`) y el acceso se controla con políticas RLS sobre `storage.objects` equivalentes a las de `partes_diarios` y `gastos`.

## Consecuencias
- Con ~250 KB por foto y ~300 cargas mensuales, el consumo es ~75 MB/mes (entra holgadamente en 1 GB del plan Free durante el piloto y en los 100 GB del plan Pro).
- Subida rápida incluso con señal móvil baja.

