# 002 · Autenticación, roles, empleados y soporte
- Fecha: 2026-10-31
- Estado: aceptada

## Contexto
Los choferes necesitan ingresar rápido desde su celular sin recordar contraseñas complejas ni depender de correo electrónico corporativo o SMS pagos (RF33, RF39). Al mismo tiempo, los datos de sueldos, cheques y finanzas personales deben estar estrictamente aislados por rol en la base de datos (RNF04), y el Empleador debe poder blanquear claves o revocar sesiones ante pérdida de un celular (RF40). Papá además cumple doble función: maneja un camión (Empleado) y administra la empresa (Empleador) (RF34).

## Opciones consideradas
1. **Supabase Auth con identificador sintético + PIN de 4 a 6 dígitos:**
   - Cada usuario tiene una cuenta en `auth.users` (ej. `usuario@sereno.local`) cuya credencial se valida mediante el PIN gestionado por el Empleador, y una fila en `public.perfiles` con su `rol` (`empleador`, `contaduria`, `empleado`) y su `empleado_id`.
2. **Login por SMS / OTP telefónico:**
   - Descartado por costo recurrente de SMS y demoras de entrega en zonas rurales.

## Decisión
Usar **Supabase Auth vinculado a `public.perfiles`** con ingreso por **usuario/alias + PIN numérico de 4 a 6 dígitos**:
- Sesión larga recordada en el dispositivo.
- La tabla `public.perfiles` asocia `auth.uid()` con el rol (`app.rol()`) y con la ficha del chofer (`app.empleado_id()`).
- El Empleador tiene su propio `empleado_id` asignado en `perfiles`, permitiéndole cargar partes cuando maneja y revisar/aprobar desde su rol de Empleador.
- Si se pierde un celular, el Empleador desactiva el perfil (`activo = false` en `perfiles`, lo que anula inmediatamente `app.rol()` en todas las políticas RLS) y reinicia el PIN.
- Una persona de la familia queda designada como responsable de soporte para altas y reinicios de PIN (RNF20).

## Consecuencias
- Cumple RNF04 y RF39/RF40 sin costos de mensajería externa.
- La revocación por `perfiles.activo = false` corta el acceso en tiempo real a nivel de base de datos sin esperar a que venza el token JWT.

