# 003 · Conectividad, borradores locales y copias de seguridad
- Fecha: 2026-10-31
- Estado: aceptada

## Contexto
En la zona de recolección hay señal móvil, por lo que se descartó construir un sistema offline distribuido de varios días (S21, RNF03). Sin embargo, el chofer no debe perder ningún dato cargado si se cierra el navegador o hay un microcorte de señal en el tambo (RF41, RNF17), y la familia necesita copias de seguridad automáticas y exportables para no quedar atrapada ni perder información (RF35, RNF06, RNF10).

## Opciones consideradas
1. **Sincronización offline completa con base de datos local replicada (CRDT / PouchDB / RxDB):**
   - Sobredimensionado para 5 camiones con señal en la zona; introduce conflictos de edición.
2. **Autoguardado de borrador en almacenamiento local (`localStorage` / `IndexedDB`) + estado `borrador` en servidor + backups automáticos:**
   - Simple, predecible y cubre tanto el cierre accidental de la app como cortes puntuales de red.

## Decisión
1. **Borrador local y en base de datos:** Cada cambio en el formulario del parte diario se guarda instantáneamente en el almacenamiento local del navegador del chofer y se sincroniza con la fila en estado `borrador` en `partes_diarios` cuando hay red. Si el envío falla por falta momentánea de señal, queda pendiente en el dispositivo y se reintenta al recuperar conexión.
2. **Backups de base de datos y libros Excel (RNF06, RF35):**
   - Durante el piloto (Supabase Free): tarea programada semanal (`pg_dump`) y **respaldo automático rotativo de 31 días en libro Excel multi-hoja (`.xlsx`)** desde la vista de Contaduría (`BackupExcelModal.tsx` + `excelBackupService.ts`), con pestañas separadas para Partes Diarios, Sueldos, Cheques, Gastos, Cuentas Corrientes y Auditoría, más un **importador inteligente de planillas Excel históricas** (`importadorExcelHistoricoService.ts`) para migrar los cuadernos y planillas previas de mamá sin tipeo manual.
   - En producción (Supabase Pro): backups diarios automáticos de Supabase (7 días de retención) más la exportación mensual y diaria descargable en `.xlsx` por Contaduría.

## Consecuencias
- El chofer nunca pierde lo tipeado en cabina.
- No hay conflictos de sincronización entre múltiples dispositivos porque cada chofer opera su propio parte del día (`unique (fecha, empleado_id)`).

