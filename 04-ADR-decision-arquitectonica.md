# 4. ADR - Decisión arquitectónica

## ADR-001: Arquitectura para pedidos y ventanas de entrega

### Estado

Aceptada

### Contexto

La aplicación móvil actualmente permite crear pedidos y se necesita incorporar una nueva ventana de entrega.

El cambio debe realizarse sin afectar a los usuarios que todavía utilizan versiones anteriores de la aplicación. Además, durante campañas comerciales se pueden presentar aumentos importantes en la cantidad de pedidos.

Por esta razón, la arquitectura debe permitir incorporar la nueva funcionalidad, mantener la compatibilidad y soportar incrementos de carga sin agregar una complejidad innecesaria.

### Problema

Se necesita seleccionar una arquitectura que permita evolucionar el sistema de pedidos y responder a los picos de demanda.

Se analizaron dos alternativas:

1. Monolito modular.
2. Servicio independiente de pedidos.

### Decisión

Se decide utilizar inicialmente un **monolito modular**, organizando las funcionalidades de pedidos, entregas, inventario y usuarios en módulos separados.

La incorporación de la ventana de entrega se realizará principalmente en el módulo de entregas, manteniendo una comunicación clara con el módulo de pedidos.

La decisión busca mantener una arquitectura sencilla en la etapa actual y evitar introducir componentes adicionales antes de contar con evidencia que demuestre que son necesarios.

### Razones de la decisión

- Tiene menor complejidad inicial.
- Requiere menos infraestructura.
- Reduce el riesgo de introducir problemas de comunicación entre servicios.
- Permite organizar las funcionalidades por módulos.
- Facilita mantener el sistema existente mientras se incorpora la nueva funcionalidad.
- Permite evaluar posteriormente si alguna parte del sistema necesita separarse.

### Consecuencias positivas

- Se mantiene una arquitectura relativamente sencilla.
- El desarrollo y las pruebas pueden realizarse dentro de una aplicación.
- Se reducen los costos iniciales de infraestructura.
- La ventana de entrega puede incorporarse sin dividir todo el sistema.
- La arquitectura puede evolucionar posteriormente si aparecen nuevas necesidades.

### Consecuencias negativas

- El escalamiento se realiza sobre la aplicación completa.
- Una falla general de la aplicación puede afectar varios módulos.
- Será necesario mantener una separación clara entre los módulos para evitar que se mezclen sus responsabilidades.
- Si la cantidad de pedidos aumenta considerablemente, podría ser necesario separar posteriormente el procesamiento de pedidos.

### Alternativas descartadas

#### Servicio independiente de pedidos

No se selecciona inicialmente porque introduce mayor complejidad de infraestructura y comunicación entre componentes.

Esta alternativa puede ser revisada posteriormente si las pruebas demuestran que el procesamiento de pedidos necesita escalar de forma independiente.

### Condición para revisar la decisión

La decisión deberá revisarse si las pruebas de carga muestran que el monolito no puede soportar los niveles de demanda establecidos para las campañas comerciales.

También se revisará si el procesamiento de pedidos necesita escalar de manera independiente al resto de funcionalidades o si los cambios relacionados con pedidos comienzan a afectar constantemente otros módulos.

### Evidencia necesaria

Para comprobar que la decisión continúa siendo válida se utilizarán:

- Pruebas de carga.
- Medición de tiempos de respuesta.
- Pruebas con versiones anteriores del cliente.
- Registro de errores durante periodos de alta demanda.
- Revisión de los componentes afectados por nuevos cambios.