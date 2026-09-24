# 5. Trade-offs

Una decisión arquitectónica implica aceptar algunas desventajas para obtener determinados beneficios. En este caso se decidió utilizar inicialmente un monolito modular.

## 5.1 Complejidad vs. escalabilidad

Al utilizar un monolito modular se mantiene una arquitectura más sencilla de desarrollar y administrar.

El costo de esta decisión es que, cuando aumente considerablemente la cantidad de pedidos, no será posible escalar únicamente el módulo de pedidos de manera independiente. En caso de que esto se convierta en un problema, se deberá evaluar la separación de este módulo.

## 5.2 Costo vs. capacidad de crecimiento

El monolito modular permite reducir los costos iniciales porque se necesitan menos componentes de infraestructura.

A cambio, se acepta que la solución puede requerir cambios arquitectónicos adicionales si el crecimiento del sistema supera la capacidad de la arquitectura seleccionada.

## 5.3 Simplicidad vs. aislamiento

Mantener las funcionalidades dentro de una misma aplicación facilita el desarrollo y las pruebas.

Sin embargo, existe un menor aislamiento entre los módulos que en una arquitectura con servicios independientes. Por esta razón, será necesario mantener límites claros entre las responsabilidades de cada módulo.

## 5.4 Evolución gradual vs. cambio inmediato

Se decidió no separar el procesamiento de pedidos desde el inicio. Esto permite realizar primero los cambios necesarios y obtener información real sobre el comportamiento del sistema.

El costo de esta decisión es que, si las pruebas muestran problemas de rendimiento, posteriormente será necesario realizar un proceso de separación y adaptación.

## 5.5 Resumen del trade-off

La decisión prioriza una arquitectura con menor complejidad y menor costo inicial, aceptando que el escalamiento independiente de los pedidos podría requerir una modificación futura.

Esta decisión se considera válida mientras las pruebas demuestren que el sistema puede cumplir los escenarios de calidad definidos.

Si las condiciones cambian, la arquitectura deberá revisarse.