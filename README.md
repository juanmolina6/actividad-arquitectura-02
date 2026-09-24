# Actividad 2 - Decisión arquitectónica

## Propósito

Esta actividad presenta el análisis y la decisión arquitectónica para una aplicación móvil que necesita incorporar ventanas de entrega en los pedidos y continuar funcionando correctamente durante periodos de alta demanda.

El objetivo es analizar el problema desde las necesidades del sistema y del negocio antes de seleccionar una alternativa arquitectónica.

---

## Problema

La aplicación móvil permite crear pedidos, pero se necesita incorporar una nueva información relacionada con la ventana de entrega.

El cambio debe realizarse sin afectar a los usuarios que utilizan versiones anteriores de la aplicación.

Además, durante campañas comerciales pueden aumentar considerablemente las solicitudes de creación de pedidos, por lo que la solución debe mantener un comportamiento adecuado durante estos periodos.

---

## Alternativas analizadas

Se analizaron dos alternativas:

### 1. Monolito modular

Mantener la aplicación como un sistema único, pero organizar sus funcionalidades en módulos separados para pedidos, entregas, inventario y usuarios.

### 2. Servicio independiente de pedidos

Separar el procesamiento de pedidos como un servicio independiente que pueda escalar de manera independiente al resto de funcionalidades.

---

## Decisión

Se decidió utilizar inicialmente un **monolito modular**.

Esta alternativa permite mantener una solución con menor complejidad y costo inicial, mientras se organizan las funcionalidades por módulos.

La decisión no se considera permanente. Si las pruebas muestran que el procesamiento de pedidos necesita escalar de manera independiente o que la arquitectura no soporta la carga esperada, se revisará la posibilidad de separar este componente.

---

## Trade-off principal

Al utilizar un monolito modular se acepta que el procesamiento de pedidos no podrá escalar de manera independiente desde el inicio.

A cambio, se obtiene una arquitectura con menor complejidad inicial, menor costo de infraestructura y un proceso de desarrollo más sencillo.

---

## Evidencia y revisión

La decisión será evaluada mediante:

- Pruebas de carga.
- Medición de tiempos de respuesta.
- Pruebas con versiones anteriores de la aplicación.
- Registro de errores.
- Revisión de los módulos afectados por nuevos cambios.

La arquitectura deberá revisarse si la evidencia demuestra que alguno de los escenarios de calidad definidos deja de cumplirse.

---

## Documentación

Los documentos completos de la actividad se encuentran en la carpeta [`docs/actividad-02`](docs/actividad-02/).

| Documento | Descripción |
|---|---|
| [Problema y requisitos](docs/actividad-02/01-problema-y-requisitos.md) | Problema, actores, requisitos, restricciones y alcance. |
| [Escenarios de calidad](docs/actividad-02/02-escenarios-calidad.md) | Rendimiento, compatibilidad, disponibilidad y facilidad de cambio. |
| [Alternativas y matriz](docs/actividad-02/03-alternativas-y-matriz.md) | Alternativas arquitectónicas y comparación. |
| [ADR](docs/actividad-02/04-ADR-decision-arquitectonica.md) | Registro de la decisión arquitectónica. |
| [Trade-offs](docs/actividad-02/05-trade-offs.md) | Costos y beneficios aceptados con la decisión. |
| [Criterios de revisión](docs/actividad-02/06-criterios-de-revision.md) | Condiciones y evidencias para revisar la decisión. |

---

## Conclusión

La propuesta busca resolver las necesidades actuales sin agregar complejidad innecesaria. La arquitectura podrá evolucionar posteriormente si las pruebas y el comportamiento real del sistema muestran que se necesita una solución diferente.