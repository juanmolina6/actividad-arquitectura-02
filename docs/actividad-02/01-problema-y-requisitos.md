# 1. Problema y requisitos

## 1.1 Problema

La aplicación móvil permite a los usuarios crear pedidos, pero el sistema debe evolucionar para permitir que cada pedido pueda incluir una ventana de entrega.

El problema principal es incorporar esta nueva información sin afectar el funcionamiento actual de la aplicación ni generar interrupciones para los usuarios que todavía utilizan una versión anterior.

Además, durante campañas comerciales pueden aumentar considerablemente las solicitudes de creación de pedidos. Por esta razón, la solución debe permitir que el sistema continúe funcionando correctamente durante estos periodos de alta demanda.

La decisión arquitectónica debe buscar un equilibrio entre el funcionamiento actual, la incorporación de nuevas funcionalidades, el rendimiento y la facilidad de realizar cambios futuros.

## 1.2 Actores

| Actor | Necesidad |
|---|---|
| Cliente de la aplicación móvil | Crear pedidos y seleccionar una ventana de entrega cuando esté disponible. |
| Sistema de pedidos | Recibir y procesar los pedidos correctamente. |
| Área de operaciones | Gestionar los pedidos y sus horarios de entrega. |
| Administrador del sistema | Mantener y actualizar la aplicación sin afectar a los usuarios actuales. |
| Servicios externos | Proporcionar información necesaria para procesar los pedidos. |

## 1.3 Requisitos priorizados

### Prioridad alta

- El sistema debe permitir crear pedidos correctamente.
- La incorporación de la ventana de entrega no debe impedir que funcionen las versiones anteriores de la aplicación.
- El sistema debe continuar procesando pedidos durante periodos de alta demanda.

### Prioridad media

- La nueva ventana de entrega debe poder incorporarse sin modificar completamente el funcionamiento existente.
- Los errores del procesamiento de pedidos deben poder identificarse fácilmente.
- La solución debe permitir realizar cambios futuros con un impacto controlado.

### Prioridad baja

- Mejorar posteriormente la información mostrada al usuario sobre el estado de su pedido.
- Incorporar nuevas opciones relacionadas con los horarios de entrega.

## 1.4 Restricciones

- No se debe asumir que todos los usuarios actualizarán la aplicación al mismo tiempo.
- La solución debe considerar el sistema existente y evitar cambios innecesarios.
- Se debe controlar el costo y la complejidad de la solución.
- La arquitectura debe poder ser revisada si las condiciones del sistema cambian.

## 1.5 Alcance

### Dentro del alcance

- Creación de pedidos.
- Incorporación de la ventana de entrega.
- Compatibilidad con versiones anteriores de la aplicación.
- Comportamiento del sistema durante picos de demanda.
- Decisión sobre la alternativa arquitectónica.

### Fuera del alcance

- Diseño visual de la aplicación móvil.
- Implementación completa de un sistema de pagos.
- Desarrollo de nuevas funcionalidades que no estén relacionadas con los pedidos.
- Selección de proveedores específicos de infraestructura.