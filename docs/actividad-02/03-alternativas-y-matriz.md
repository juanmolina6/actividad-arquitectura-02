# 3. Alternativas arquitectónicas y matriz comparativa

Para resolver el problema se plantearon dos alternativas. Las dos permiten incorporar la ventana de entrega y buscan mantener el funcionamiento del sistema durante periodos de alta demanda.

## 3.1 Alternativa 1: Monolito modular

La primera alternativa consiste en mantener el sistema como una aplicación única, pero organizar internamente sus funcionalidades en módulos independientes.

Los principales módulos serían:

- Pedidos.
- Entregas.
- Inventario.
- Usuarios.

La nueva ventana de entrega se incorporaría principalmente en el módulo de entregas, manteniendo una comunicación clara con el módulo de pedidos.

### Ventajas

- Menor complejidad inicial.
- Menor costo de mantenimiento.
- Es más sencillo de desarrollar y probar en comparación con varios servicios independientes.
- Permite organizar mejor el código sin cambiar completamente la arquitectura existente.
- Los cambios pueden realizarse por módulos.

### Desventajas

- Un problema en la aplicación completa puede afectar diferentes funcionalidades.
- El escalamiento puede ser menos específico porque se escala la aplicación completa.
- Si el sistema aumenta mucho de tamaño, mantener los módulos separados puede requerir mayor disciplina.

---

## 3.2 Alternativa 2: Servicio independiente de pedidos

La segunda alternativa consiste en separar el procesamiento de pedidos como un servicio independiente.

La aplicación móvil se comunicaría con el sistema y el procesamiento de pedidos estaría separado de otras funcionalidades.

El servicio de pedidos sería responsable de:

- Recibir las solicitudes.
- Validar la información del pedido.
- Procesar la creación del pedido.
- Coordinar la información necesaria para la entrega.

### Ventajas

- El procesamiento de pedidos puede escalar de forma independiente.
- Permite aislar una de las funciones más importantes durante las campañas.
- Los cambios relacionados con pedidos pueden realizarse sin modificar directamente todo el sistema.
- Puede facilitar una futura separación de otros servicios.

### Desventajas

- Aumenta la complejidad del sistema.
- Requiere administrar la comunicación entre componentes.
- Puede aumentar los costos de infraestructura y mantenimiento.
- Los errores de comunicación entre servicios pueden generar problemas adicionales.

---

# 3.3 Matriz comparativa

Para comparar las alternativas se utilizaron cuatro criterios: costo, riesgo, calidad y facilidad de cambio.

| Criterio | Monolito modular | Servicio independiente de pedidos |
|---|---|---|
| Costo | Bajo a medio | Medio a alto |
| Riesgo de implementación | Bajo | Medio |
| Rendimiento en picos de demanda | Medio | Alto |
| Compatibilidad | Alta | Alta |
| Facilidad de cambio | Media-alta | Alta |
| Complejidad | Baja-media | Alta |
| Mantenimiento | Más sencillo | Requiere mayor coordinación |

## 3.4 Análisis de la matriz

### Costo

El monolito modular requiere menos infraestructura y menos componentes que administrar. El servicio independiente necesita recursos adicionales para desplegar y mantener el nuevo servicio.

### Riesgo

El monolito modular representa un cambio menor sobre el sistema existente. Separar el procesamiento de pedidos introduce nuevas comunicaciones y componentes que deben probarse.

### Calidad

El servicio independiente permite escalar específicamente el procesamiento de pedidos cuando aumenta la cantidad de solicitudes. El monolito modular también puede soportar aumentos de carga, pero el escalamiento se realiza sobre la aplicación completa.

### Facilidad de cambio

Las dos alternativas permiten incorporar la ventana de entrega. El servicio independiente proporciona una separación mayor del procesamiento de pedidos, pero también requiere mantener contratos de comunicación entre componentes.

## 3.5 Resultado de la comparación

Las dos alternativas pueden resolver el problema planteado. La primera presenta menor complejidad y costo inicial, mientras que la segunda permite un escalamiento más específico del procesamiento de pedidos.

La decisión final se documentará en el ADR de la actividad teniendo en cuenta las necesidades actuales del sistema y el costo de introducir una mayor complejidad.