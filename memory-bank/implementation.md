# Plan de Implementación MVP — Sistema de Automatización para Cartas de Restaurante

## 1. Objetivo del MVP

Construir una aplicación web para bares y restaurantes que permita gestionar carta, comandas y estados de preparación entre camareros, cocina y gerencia.

El MVP debe validar si el restaurante puede coordinar pedidos de mesa de forma más clara y rápida que con procesos manuales.

## 2. Alcance del MVP

### Incluido

- Autenticación de usuarios.
- Roles: gerente, camarero y cocinero.
- Gestión básica de usuarios por parte del gerente.
- Gestión de categorías y platos de la carta.
- Creación de comandas asociadas a mesa.
- Gestión de estados por ítem de comanda.
- Vista diferenciada por rol.
- Marcado manual de comandas como pagadas y archivadas.

### Fuera del MVP inicial

- Pago online completo con Stripe.
- Reservas.
- Inventario.
- Analítica avanzada.
- Impresión de tickets.
- Notificaciones en tiempo real avanzadas.
- Diseño visual complejo.

Stripe puede prepararse como integración futura, pero para esta primera iteración el pago se validará con estado manual: “pagado”.

## 3. Stack Técnico

- Frontend: React con Vite.
- UI: ShadCN/ui y Tailwind CSS.
- Backend y base de datos: Supabase.
- Autenticación: Supabase Auth.
- Despliegue frontend: Vercel.
- Servicios backend: Supabase.

## 4. Fase 0 — Preparación del Proyecto

### Pasos

1. Crear repositorio del proyecto.
2. Inicializar aplicación React con Vite.
3. Instalar y configurar Tailwind CSS.
4. Instalar y configurar ShadCN/ui.
5. Crear estructura base de carpetas:
   - páginas o rutas
   - componentes
   - servicios
   - tipos
   - utilidades
6. Configurar variables de entorno para Supabase.
7. Crear proyecto en Supabase.
8. Crear proyecto en Vercel conectado al repositorio.
9. Configurar variables de entorno en Vercel.

### Entregable

Aplicación mínima funcionando localmente con layout base.

## 5. Despliegue 1 — Aplicación mínima en producción

### Pasos

1. Crear una pantalla inicial simple con nombre del producto.
2. Añadir navegación mínima:
   - Inicio
   - Login
   - Perfil o sesión
3. Confirmar que la aplicación compila correctamente.
4. Desplegar en Vercel.
5. Verificar que la URL pública carga correctamente.

### Criterios de aceptación

- La aplicación abre en producción.
- El diseño base responde en móvil y escritorio.
- Las variables de entorno están configuradas en Vercel.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 6. Fase 1 — Autenticación y Sesión

### Pasos

1. Configurar Supabase Auth.
2. Crear pantalla de inicio de sesión.
3. Crear pantalla de registro solo si se decide permitir alta inicial.
4. Crear cierre de sesión.
5. Crear control de sesión activa.
6. Crear redirección según estado de autenticación.
7. Crear tabla de perfiles de usuario con rol asociado:
   - gerente
   - camarero
   - cocinero
8. Crear un usuario gerente inicial.
9. Aplicar reglas básicas de seguridad para que cada usuario acceda solo a lo permitido.

### Criterios de aceptación

- Un usuario puede iniciar sesión.
- Un usuario puede cerrar sesión.
- La aplicación reconoce el rol del usuario.
- El gerente inicial puede acceder al panel de gerencia.

## 7. Despliegue 2 — Autenticación en producción

### Pasos

1. Subir cambios al repositorio.
2. Desplegar en Vercel.
3. Probar login y logout en producción.
4. Probar usuario gerente en producción.
5. Confirmar que la sesión persiste correctamente.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 8. Fase 2 — Navegación por Rol

### Pasos

1. Crear layout principal autenticado.
2. Crear navegación simple según rol.
3. Para gerente, mostrar accesos a:
   - usuarios
   - carta
   - comandas
4. Para camarero, mostrar accesos a:
   - carta
   - nueva comanda
   - comandas activas
5. Para cocinero, mostrar acceso a:
   - comandas de cocina
6. Bloquear vistas no permitidas según rol.

### Criterios de aceptación

- Cada rol ve solo las secciones necesarias.
- La navegación es simple y usable desde móvil.
- Los usuarios sin sesión no pueden acceder a paneles internos.

## 9. Despliegue 3 — Navegación por rol en producción

### Pasos

1. Desplegar en Vercel.
2. Probar acceso con gerente.
3. Probar acceso con camarero.
4. Probar acceso con cocinero.
5. Confirmar que cada rol ve únicamente sus vistas.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 10. Fase 3 — Gestión de Usuarios por Gerente

### Pasos

1. Crear vista de usuarios para gerente.
2. Listar usuarios existentes con nombre, email y rol.
3. Permitir crear usuarios camarero y cocinero.
4. Permitir borrar o desactivar usuarios camarero y cocinero.
5. Impedir que camareros o cocineros gestionen usuarios.
6. Evitar que el gerente se elimine accidentalmente a sí mismo.

### Criterios de aceptación

- El gerente puede crear camareros.
- El gerente puede crear cocineros.
- El gerente puede borrar o desactivar usuarios operativos.
- Los roles no autorizados no acceden a esta función.

## 11. Despliegue 4 — Gestión de usuarios en producción

### Pasos

1. Desplegar en Vercel.
2. Crear un camarero desde producción.
3. Crear un cocinero desde producción.
4. Iniciar sesión con ambos usuarios.
5. Verificar permisos por rol.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 12. Fase 4 — Gestión de Carta

### Pasos

1. Crear modelo de categorías.
2. Crear modelo de platos.
3. Cada plato debe tener:
   - nombre
   - categoría
   - precio
   - foto opcional
   - estado activo/inactivo
4. Crear vista de carta para gerente.
5. Permitir crear, editar y borrar categorías.
6. Permitir crear, editar y borrar platos.
7. Permitir modificar precio de platos.
8. Crear vista de carta en modo lectura para camareros.
9. Mantener la gestión de fotos simple: usar URL o almacenamiento básico de Supabase si es necesario.

### Criterios de aceptación

- El gerente puede mantener la carta.
- El camarero puede ver platos disponibles.
- Los platos tienen nombre y precio visibles.
- Los platos inactivos no aparecen para crear comandas.

## 13. Despliegue 5 — Carta en producción

### Pasos

1. Desplegar en Vercel.
2. Crear categorías reales de prueba.
3. Crear platos reales de prueba.
4. Modificar precios.
5. Validar que el camarero ve la carta actualizada.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 14. Fase 5 — Creación de Comandas

### Pasos

1. Crear modelo de comandas.
2. Crear modelo de ítems de comanda.
3. Una comanda debe incluir:
   - número de mesa
   - usuario creador
   - estado general
   - fecha de creación
4. Cada ítem debe incluir:
   - plato
   - cantidad
   - estado
   - precio registrado en el momento del pedido
5. Crear vista para que camarero o gerente creen una comanda.
6. Permitir seleccionar mesa.
7. Permitir añadir platos desde la carta.
8. Permitir confirmar comanda.
9. Al confirmar, los ítems deben iniciar en estado “en preparación”.

### Criterios de aceptación

- Camarero puede crear una comanda para una mesa.
- Gerente puede crear una comanda.
- Cocina puede ver ítems confirmados.
- El precio queda guardado aunque luego cambie la carta.

## 15. Despliegue 6 — Creación de comandas en producción

### Pasos

1. Desplegar en Vercel.
2. Crear una comanda desde usuario camarero.
3. Crear una comanda desde usuario gerente.
4. Validar que las comandas aparecen correctamente.
5. Validar que los ítems llegan con estado inicial correcto.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 16. Fase 6 — Vista de Cocina y Estados de Ítems

### Pasos

1. Crear vista de cocina para cocinero.
2. Mostrar ítems agrupados por comanda o mesa.
3. Mostrar solo ítems pendientes o en preparación.
4. Permitir al cocinero marcar ítems como “listo para servir”.
5. Crear vista de comandas activas para camarero.
6. Permitir al camarero marcar ítems como “servido”.
7. Permitir al gerente modificar cualquier estado.
8. Definir estados permitidos:
   - en preparación
   - listo para servir
   - servido

### Criterios de aceptación

- Cocina ve los platos pendientes.
- Cocina puede marcar platos listos.
- Camarero ve platos listos para servir.
- Camarero puede marcar platos servidos.
- Gerente puede corregir estados.

## 17. Despliegue 7 — Flujo cocina-camarero en producción

### Pasos

1. Desplegar en Vercel.
2. Crear una comanda como camarero.
3. Marcar un plato como listo desde cocina.
4. Marcar el plato como servido desde camarero.
5. Confirmar que el gerente puede editar estados.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 18. Fase 7 — Pago Manual y Archivo de Comandas

### Pasos

1. Crear estado general de comanda:
   - activa
   - pagada
   - archivada
2. Crear vista de comandas para gerente.
3. Mostrar total de la comanda.
4. Permitir marcar comanda como pagada.
5. Permitir archivar comanda pagada.
6. Ocultar comandas archivadas de las vistas operativas.
7. Mantener acceso a comandas archivadas desde vista de gerente si es necesario.

### Criterios de aceptación

- Gerente ve comandas activas.
- Gerente puede marcar una comanda como pagada.
- Gerente puede archivar una comanda pagada.
- Las comandas archivadas no interfieren con cocina ni camareros.

## 19. Despliegue 8 — Pago manual y archivo en producción

### Pasos

1. Desplegar en Vercel.
2. Crear una comanda completa.
3. Marcar ítems como servidos.
4. Marcar la comanda como pagada.
5. Archivar la comanda.
6. Confirmar que desaparece de las vistas operativas.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 20. Fase 8 — Pulido MVP

### Pasos

1. Revisar experiencia mobile-first.
2. Mejorar textos vacíos:
   - sin comandas
   - sin platos
   - sin usuarios
3. Añadir estados de carga.
4. Añadir mensajes de error simples.
5. Añadir confirmaciones antes de borrar.
6. Revisar permisos de Supabase.
7. Revisar consistencia visual en modo oscuro.
8. Validar que el diseño sea adecuado para personal de bares y restaurantes, no para estudiantes universitarios.
9. Eliminar funciones no esenciales.
10. Revisar que no haya pantallas sin protección de sesión.

### Criterios de aceptación

- La aplicación puede usarse desde móvil en un entorno de restaurante.
- Los errores principales son comprensibles.
- Las acciones críticas tienen confirmación.
- El MVP no contiene funcionalidades innecesarias.

## 21. Despliegue 9 — Versión candidata MVP

### Pasos

1. Desplegar en Vercel.
2. Probar flujo completo:
   - gerente crea usuarios
   - gerente crea carta
   - camarero crea comanda
   - cocinero marca plato listo
   - camarero marca plato servido
   - gerente marca pagado
   - gerente archiva comanda
3. Probar en móvil.
4. Probar en escritorio.
5. Probar con datos reales de un restaurante piloto.

**Detente y espera a que implemente y pruebe la aplicación en producción antes de continuar.**

## 22. Validación del MVP

### Métrica principal de éxito

El MVP será exitoso si un restaurante piloto puede completar al menos 20 comandas reales o simuladas con menos de 10% de errores operativos reportados por el personal.

### Señales secundarias

- Camareros entienden cómo crear comandas sin formación extensa.
- Cocina identifica fácilmente qué platos preparar.
- Gerencia puede cerrar y archivar comandas sin asistencia técnica.
- El flujo completo tarda menos que el proceso manual actual o reduce confusiones.

## 23. Checklist Final

- La app está desplegada en Vercel.
- Supabase Auth funciona en producción.
- Existen roles diferenciados.
- Gerente puede crear camareros y cocineros.
- Gerente puede gestionar carta.
- Camarero puede crear comandas.
- Cocinero puede actualizar estado de platos.
- Camarero puede marcar platos servidos.
- Gerente puede marcar comandas como pagadas.
- Gerente puede archivar comandas.
- La app funciona correctamente en móvil.
- No hay funciones fuera del alcance MVP bloqueando el lanzamiento.
