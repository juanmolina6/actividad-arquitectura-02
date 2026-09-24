# 6. Criterios de revisión

La decisión de utilizar un monolito modular no se considera permanente. Se revisará utilizando evidencia obtenida del funcionamiento y de las pruebas realizadas sobre el sistema.

## 6.1 Rendimiento

Se realizarán pruebas de carga para comprobar el comportamiento del sistema cuando aumente la cantidad de solicitudes de creación de pedidos.

### Criterio

La arquitectura se considera adecuada mientras el sistema pueda procesar la carga esperada sin presentar una cantidad significativa de errores ni tiempos de respuesta que afecten el funcionamiento de la aplicación.

### Revisión

Si las pruebas muestran que el procesamiento de pedidos necesita recursos de manera independiente al resto de la aplicación, se analizará la posibilidad de separar este componente.

---

## 6.2 Compatibilidad

Se probará la creación de pedidos utilizando una versión anterior de la aplicación móvil.

### Criterio

Los clientes que todavía no envían la información de la ventana de entrega deben poder crear pedidos correctamente.

### Revisión

Si la incorporación de nuevas versiones comienza a generar incompatibilidades frecuentes con los clientes existentes, se deberá revisar el contrato de comunicación y la estrategia utilizada para mantener la compatibilidad.

---

## 6.3 Disponibilidad

Durante las pruebas de carga se observará el comportamiento general de la aplicación ante aumentos de solicitudes.

### Criterio

El sistema debe continuar disponible y procesando pedidos durante los niveles de carga definidos para las campañas.

### Revisión

Si una campaña provoca interrupciones frecuentes o afecta varias funcionalidades al mismo tiempo, se deberá analizar si es necesario separar componentes para reducir el impacto de estas situaciones.

---

## 6.4 Facilidad de cambio

Se revisará el impacto de nuevas funcionalidades relacionadas con pedidos y entregas.

### Criterio

Los cambios deben poder realizarse principalmente dentro de los módulos relacionados sin modificar de manera innecesaria otras partes del sistema.

### Revisión

Si agregar nuevas funcionalidades requiere modificar constantemente diferentes módulos, se deberá evaluar nuevamente la estructura modular o la separación de algunos componentes.

---

## 6.5 Resumen de criterios

| Aspecto | Qué se revisa | Condición para reconsiderar la arquitectura |
|---|---|---|
| Rendimiento | Tiempo de respuesta y errores bajo carga | El sistema no soporta la carga esperada |
| Compatibilidad | Funcionamiento de clientes anteriores | Aparecen incompatibilidades frecuentes |
| Disponibilidad | Continuidad del servicio durante campañas | Las campañas provocan interrupciones importantes |
| Facilidad de cambio | Cantidad de módulos afectados por cambios | Los cambios afectan constantemente otras funcionalidades |

## 6.6 Evidencias

Para realizar estas revisiones se tendrán en cuenta:

- Resultados de pruebas de carga.
- Tiempos de respuesta.
- Porcentaje de solicitudes procesadas correctamente.
- Registro de errores.
- Pruebas con versiones anteriores de la aplicación.
- Cantidad de módulos afectados por cambios.

La arquitectura deberá revisarse cuando la evidencia obtenida muestre que alguno de los criterios definidos dejó de cumplirse.