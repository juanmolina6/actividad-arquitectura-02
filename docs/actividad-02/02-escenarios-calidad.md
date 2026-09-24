# 2. Escenarios de calidad

Los escenarios de calidad permiten definir cómo debe comportarse el sistema ante situaciones importantes para el negocio. En este caso se tienen en cuenta principalmente el rendimiento, la compatibilidad, la disponibilidad y la facilidad de cambio.

## 2.1 Rendimiento

### Escenario

Durante una campaña comercial aumenta considerablemente la cantidad de usuarios que realizan pedidos al mismo tiempo.

### Estímulo

Se presenta un aumento de solicitudes para crear pedidos.

### Respuesta esperada

El sistema debe continuar procesando los pedidos sin presentar errores generalizados y manteniendo tiempos de respuesta aceptables.

### Medición

Se revisará el tiempo de respuesta de las solicitudes y el porcentaje de solicitudes que terminan correctamente durante las pruebas de carga.

---

## 2.2 Compatibilidad

### Escenario

Un usuario utiliza una versión anterior de la aplicación móvil que todavía no conoce la nueva ventana de entrega.

### Estímulo

El usuario crea un pedido sin enviar información sobre la ventana de entrega.

### Respuesta esperada

El sistema debe aceptar el pedido y procesarlo correctamente sin exigir que el usuario actualice inmediatamente la aplicación.

### Medición

Se realizará una prueba utilizando una versión anterior del cliente y se comprobará que la creación del pedido continúe funcionando.

---

## 2.3 Disponibilidad

### Escenario

Durante una campaña comercial se presenta un incremento en las solicitudes de creación de pedidos.

### Estímulo

La cantidad de solicitudes aumenta por encima del comportamiento normal del sistema.

### Respuesta esperada

El sistema debe continuar disponible para los usuarios y evitar que el aumento de solicitudes provoque una caída completa del servicio.

### Medición

Se realizará una prueba de carga y se observará la cantidad de solicitudes procesadas correctamente, los errores y el comportamiento del sistema durante el periodo de mayor demanda.

---

## 2.4 Facilidad de cambio

### Escenario

Después de implementar la ventana de entrega, el negocio necesita agregar otra información relacionada con la entrega de los pedidos.

### Estímulo

Se solicita agregar una nueva característica relacionada con el proceso de entrega.

### Respuesta esperada

El cambio debe poder realizarse sin modificar de manera importante las funcionalidades que ya funcionan correctamente.

### Medición

Se revisará la cantidad de componentes afectados por el cambio y las pruebas que deben modificarse para incorporar la nueva funcionalidad.

---

## 2.5 Resumen de escenarios

| Calidad | Situación | Resultado esperado | Forma de comprobarlo |
|---|---|---|---|
| Rendimiento | Aumento de pedidos durante una campaña | El sistema continúa procesando solicitudes correctamente | Pruebas de carga y medición de tiempos |
| Compatibilidad | Cliente antiguo crea un pedido | El pedido se procesa sin exigir actualización | Prueba con versión anterior del cliente |
| Disponibilidad | Aumento considerable de solicitudes | El servicio continúa disponible | Prueba de carga y revisión de errores |
| Facilidad de cambio | Se agrega una nueva característica de entrega | El cambio afecta pocos componentes | Revisión de componentes y pruebas afectadas |