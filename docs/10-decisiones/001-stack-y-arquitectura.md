# 001 · Stack y arquitectura
- Fecha: 2026-10-31
- Estado: aceptada

## Contexto
El sistema requiere tres vistas (Empleado en celular iPhone/Android, Empleador en iPhone y Contaduría en Chrome de escritorio) conectadas en tiempo real sobre una misma base de datos (RNF01, RNF02, RNF15, RNF16). La lógica de negocio (`core/`) ya está escrita en TypeScript puro y el esquema con permisos (`database/schema.sql`) está escrito y probado para PostgreSQL 15+ con Row Level Security (RLS) de Supabase.

## Opciones consideradas
1. **PWA SPA (React + Vite + Tailwind CSS) + Supabase Cloud directo (`@supabase/supabase-js`):**
   - Cliente estático liviano e instalable en pantalla de inicio; llamadas directas a PostgREST protegidas por RLS; autoguardado inmediato en almacenamiento local del navegador (`localStorage`/`IndexedDB`).
2. **Next.js (App Router / Full-Stack) en Vercel + Supabase Cloud:**
   - Capa intermedia de servidor (Server Components / Server Actions). Agrega latencia de round-trip en conexiones móviles rurales y mayor peso de hidratación en celulares antiguos.

## Decisión
Adoptar la **Opción 1: PWA SPA (React + Vite + TypeScript + Tailwind CSS)** conectada directamente a **Supabase (PostgreSQL + Auth + Storage)**, compartiendo el paquete `core/` sin duplicar reglas de negocio.
- **Costos y plan (verificado en supabase.com/pricing el 2026-10-31):**
  - *Desarrollo y piloto:* Plan Free (USD 0/mes; 500 MB DB, 1 GB Storage; se pausa tras 7 días sin actividad en BD y no incluye backups automáticos).
  - *Producción (antes de cargar sueldos y cheques reales):* Plan Pro (USD 25/mes; sin pausa por inactividad y con backups automáticos diarios de 7 días de retención).

## Consecuencias
- Cero servidores intermedios que mantener; toda la seguridad de datos descansa en las políticas RLS probadas en `database/test/`.
- Excelente respuesta táctil en cabina y soporte directo para autoguardado local (RNF17).
- En Plan Free se requiere un volcado periódico (`pg_dump`) para cumplir RNF06 (ver ADR 003).

