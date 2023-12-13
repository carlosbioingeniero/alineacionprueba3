[[_TOC_]]

# Modelo del sistema

## Los dominios
Relacionan entidades y sistemas con parte del negocio.

Si bien **los sistemas son el nivel básico de encapsulación para entidades relacionadas**, a menudo **es útil agrupar una colección de sistemas que comparten terminología, modelos de dominio, métricas, KPI, propósito comercial o documentación**, es decir, forman un contexto delimitado.

**Por ejemplo**, tendría sentido si los diferentes sistemas en el dominio "Pagos" vinieran con alguna documentación sobre cómo aceptar pagos por un nuevo producto o caso de uso, compartir los mismos tipos de entidad en sus API y integrarse bien con cada uno. Otros dominios podrían ser "Ingestión de contenido", "Anuncios" o "Búsqueda".

## Los sistemas
Son una colección de entidades que cooperan para realizar alguna función. Los sistemas son un concepto útil en el sentido de que nos permiten ignorar los detalles de implementación de una determinada funcionalidad para los consumidores, al tiempo que permiten que el equipo propietario realice los cambios que considere oportunos (lo que lleva a un acoplamiento bajo).

Un sistema, en este sentido, es una colección de recursos y componentes que expone una o varias API públicas. **El principal beneficio de modelar un sistema es que oculta sus recursos y API privadas entre los componentes para cualquier consumidor**. Esto significa que, como propietario, **puede evolucionar la implementación, en términos de componentes y recursos, sin que sus consumidores se den cuenta**. Por lo general, un sistema constará como máximo de un puñado de componentes.

**Por ejemplo**, **un sistema de gestión de listas de reproducción** podría encapsular un servicio de back-end para actualizar las listas de reproducción, un servicio de back-end para consultarlas y una base de datos para almacenarlas. Podría exponer una API RPC, un conjunto de datos de instantáneas diarias y un flujo de eventos de actualizaciones de listas de reproducción.

## Api
Las API se implementan mediante componentes y forman **límites entre los componentes**. Pueden definirse mediante un RPC IDL (p. ej., Protobuf, GraphQL, ...), un esquema de datos (p. ej., Avro, TFRecord, ...) o como interfaces de código. En cualquier caso, las API expuestas por los componentes deben estar en un formato legible por máquina conocido para que podamos construir más herramientas y análisis en la parte superior. 

Las API tienen una visibilidad: son **públicas** (haciendo que estén disponibles para que las consuma cualquier otro componente), **restringidas** (solo disponibles para un conjunto de consumidores incluidos en la lista de permitidos) o **privadas** (solo disponibles dentro de su sistema). Como las API públicas serán la forma principal de interacción entre los componentes, Backstage admite la documentación, la indexación y la búsqueda de todas las API para que podamos explorarlas como desarrolladores.

## Recursos
Son la **infraestructura** que necesita un componente para funcionar en tiempo de ejecución, como bases de datos de BigTable, temas de Pub/Sub, depósitos de S3 o CDN.

## Componentes
Es una **pieza de software**, por ejemplo, una función móvil, un sitio web, un servicio backend o una canalización de datos (la lista no es exhaustiva). **Un componente puede implementar API** para que otros componentes las consuman. A su vez, puede consumir las API implementadas por otros componentes o depender directamente de los componentes o recursos que se le adjuntan en tiempo de ejecución.

## Referencias

[System Model](https://backstage.io/docs/features/software-catalog/system-model)
