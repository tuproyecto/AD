# Table of contents <a name="table-of-contents"></a>
1. [Introduction](#introduction)
    1. [Identifying information](#identifying-information)
    2. [Supplementary information](#supplementary-information)
    3. [Other information](#other-information)
        1. [Rationale for key decisions](#rationale-for-key-decisions)
2. [Stakeholders and concerns](#stakeholders-and-concerns)
    1. [Stakeholders](#stakeholders)
    2. [Concerns](#concerns)
    3. [Concern–Stakeholder Traceability](#concern–stakeholder-traceability)
3. [Viewpoints+](#viewpoints)
    1. [Development viewpoint](#development-viewpoint)
    2. [Overview](#overview-development)
    3. [Framed concerns and typical stakeholders](#framed-concerns-and-typical-stakeholders-development)
        1. [Concerns](#concerns-development)
        2. [Typical stakeholders](#typical-stakeholders-development)
    4. [Model kinds+](#model-kinds)
    5. [Component model](#component-model)
        1. [Component model conventions](#component-model-conventions)
    9. [Package model](#package-model)
        1. [Package model conventions](#package-model-conventions)
    6. [Operations on views+](#operations-on-views-component)
    7. [Correspondence rules](#correspondence-rules-component)
    8. [Sources](#sources-development)
4. [Views+](#views)
    1. [Development view](#development-view)
        1. [Models+](#models-development-view)
        2. [Components](#models-component-development-view)
        3. [Package](#models-package-development-view)
        4. [Known Issues with View](#issues-with-development-view)
5. [Consistency and correspondences](#consistency-and-correspondences)
    1. [Known inconsistencies](#known-inconsistencies)
    2. [Correspondences in the AD](#correspondences-in-the-ad)
    3. [Correspondence rules](#correspondence-rules-final)
6. [Architecture decisions and rationale](#architecture-decisions-and-rationale)
    1. [Decisions](#decisions)

# Introduction <a name="introduction"></a>

El presente trabajo desarrolla un ejercicio de descripción arquitectónica que atiende las especificaciones del proyecto de modernización del modelo de ventas por catalogo el cual se basa principalmente en catálogos físicos de productos de maquillaje los cuales son presentados a los clientes para su respectiva compra.

Desarrollaremos la documentación arquitectónica basados en el modelo 4+1, de estas formas utilizaremos cada uno de los componentes de este modelo como un viewpoint y los diagramas de UML como modelos dentro de cada vista descrita con anterioridad por el viewpoint.

El ejercicio parte desde la defección de los stakeholders y concers que se encuentran el planteamiento inicial y se busca establecerá unas reglas de correspondencia entre viewpoints y busca manejar un alto grado de consistencia en el desarrollo de los modelos, pero principalmente se busca evidenciar el manejo de la correspondencia, las inconsistencias que se presentan durante el desarrollo del ejercicio y la forma en la que se pueden justificar las decisiones de arquitectura.

![alt text][fig1]

Figura 1: Modelo conceptual 

## Identifying information <a name="identifying-information"></a>

A continuación se identifica la arquitectura sobre la cual se trata esta descripción de arquitectura junto a conceptos claves que se manejan a lo largo del documento.

* 4 + 1 : es un modelo diseñado por Philippe Kruchten para "describir la arquitectura de sistemas software, basados en el uso de múltiples vistas concurrentes"
* ISO42010 : Es un estándar para la descripción de la arquitectura de sistemas y productos de software
* Diagrama : es una representación gráfica por medio de diferentes convenciones y atributos para dar a entender una idea, solución a un problema o demostración de una idea.


## Supplementary information <a name="supplementary-information"></a>

* Fecha de emisión: Marzo 13 de 2020
* Estado: Documento para revisón
* Autores: 
** Johan
** Alejandro
** Dubier
** Diego
* Revisores
* Autoridad de aprobación
* Organización emisora
* Historial de cambios: 
* Resumen
* Alcance
* Contexto
* Glosario
* Información de control de versión
* Información de gestión de configuración y referencias
* ISO 42010 5.2
 
## Other information <a name="other-information"></a>

### Rationale for key decisions <a name="rationale-for-key-decisions"></a>

| Matriz de poder | Keep Satisfied | Key Subject | Minimal Effort | Keep Informed |
|---|:-:|:-:|:-:|:-:|
| Clientes |  |  | X |  |
| Equipo comercial |  | X |  |  |
| Equipo de mercadeo |  | X |  |  |
| Equipo técnico | X |  |  |  |

Tabla No 1 Matriz de poder

[Table of contents](#table-of-contents)

# Stakeholders and concerns <a name="stakeholders-and-concerns"></a>

## Stakeholders <a name="stakeholders"></a>

La siguiente tabla presenta, el catálogo de Stakeholders identificados dentro del problema, los cuales son identificados con un valor único, han sido descritos y se han relacionado sus preocupaciones principales de acuerdo a la actividad así:

| ID | Stakeholder | Descripción |
|---|---|---|
| STK-001 <a name="STK-001"></a> | Clientes | Potenciales consumidores |
| STK-002 <a name="STK-002"></a> | Equipo comercial | Personal que apoya el proceso de ventas |
| STK-003 <a name="STK-003"></a> | Equipo de mercadeo | Personal encargado de definir estrategias de mercadeo y diseño de catálogos |
| STK-004 <a name="STK-004"></a> | Equipo técnico | Expertos en cosmetología, apoyan el proceso de definición de los catálogos |

Tabla No 2 Catálogo de Stakeholder, Elaboración de los investigadores basada en Togaf 9.2 Diagrams, Catalog, Matrix

## Concerns <a name="concerns"></a>

Las Preocupaciones fueron discutidas en grupo, de tal forma que pudieran identificarse cuáles eran apropiados para el ejercicio, de esta manera llevar a cabo un análisis de información que permitirá mapearlos hacia los viewpoints que serán definidos.

| ID | Concern | Descripción |
|---|---|---|
| CNR-001 <a name="CNR-001"></a> | Usabilidad | Se busca contar con herramientas de vanguardia que ofrezca una buena experiencia de usuario |
| CNR-002 <a name="CNR-002"></a> | Disponibilidad (Availability) | Que el sistema sea accesible dentro y fuera de las instalaciones de la compañía |
| CNR-003 <a name="CNR-003"></a> | Reacción al cambio "Escalabilidad" | Dada su efectividad se espera ser implementada en los 85 países donde se tiene presencia comercial |
| CNR-004 <a name="CNR-004"></a> | Costos | Disminuir los recursos invertidos en procesos que pueden ser automatizados |
| CNR-005 <a name="CNR-005"></a> | Modificabilidad | La modificabilidad se refiere al grado en que un sistema puede ser modificado efectiva o eficientemente sin introducir defectos o degradar la calidad del sistema existente. |
| CNR-006 <a name="CNR-006"></a> | Rendimento | Desempeño del aplicativo |
| CNR-007 <a name="CNR-007"></a> | Modernización | Actualizar sus recursos comerciales |
| CNR-008 <a name="CNR-008"></a> | Efectividad | Aumentar la efectividad del equipo comercial |
| CNR-009 <a name="CNR-009"></a> | Acceso a la información | Contar con la información necesaria en el momento adecuado |
| CNR-010 <a name="CNR-010"></a> | Estructura de información | Administrar y presentar la información en los catálogos de acuerdo a la estrategia definida |

Tabla No 3 Catálogo de Preocupaciones, Elaboración de los investigadores basada en Togaf 9.2 Diagrams, Catalog, Matrix

## Concern–Stakeholder Traceability <a name="concern–stakeholder-traceability"></a>

La matriz de trazabilidad de Stakeholders versus preocupaciones nos permite analizar sobre que interesado se identifica con qué preocupación además de ello cuales son común a varios interesados y cuales se presentan en menor cantidad entre los Stakeholders.

| Stakeholders vs Concerns | [CNR-001](#CNR-001) | [CNR-002](#CNR-002) | [CNR-003](#CNR-003) | [CNR-004](#CNR-004) | [CNR-005](#CNR-005) | [CNR-006](#CNR-006) | [CNR-007](#CNR-007) | [CNR-008](#CNR-008) | [CNR-009](#CNR-009) | [CNR-010](#CNR-010) |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| [STK-001](#STK-001) | X | X |  | X |  |  |  |  | X |  |
| [STK-002](#STK-002) | X | X | X |  |  | X | X | X |  |  |
| [STK-003](#STK-003) |  |  |  |  | X |  |  | X |  | X | 
| [STK-004](#STK-004) |  |  |  |  | X |  |  |  |  | X |

Tabla No 4 Catálogo de Preocupaciones, Elaboración de los investigadores basada en Togaf 9.2 Diagrams, Catalog, Matrix

[Table of contents](#table-of-contents)

# Viewpoints+ <a name="viewpoints"></a>

La arquitectura de la empresa K será expresada usando la vista de componentes y de despliegue, en ella se presentan los principales componentes de aplicación adaptados como solución a la necesidad de la organización. 

Una vez revisada la actividad, en conjunto se establece que que se tomarán los puntos de vista Desarrollo, lógico, Físico y Procesos. consideramos que de esta manera se abarca más información sobre la construcción de arquitectura de Software como respuesta a la necesidad de la Empresa k

| ID | Viewpoints | Descripción |
|---|---|---|
| VWP-001 <a name="VWP-001"></a> | Viewpoint lógica | Establece convenciones para crear, interpretar y usar la vista lógica. |
| VWP-002 <a name="VWP-002"></a> | Viewpoint desarrollo | Establece convenciones para crear, interpretar y usar la vista de desarrollo. |
| VWP-003 <a name="VWP-003"></a> | Viewpoint proceso | Establece convenciones para crear, interpretar y usar la vista de proceso. |
| VWP-004 <a name="VWP-004"></a> | Viewpoint física | Establece convenciones para crear, interpretar y usar la vista física. |
| VWP-005 <a name="VWP-005"></a> | Viewpoint escenarios | Establece convenciones para crear, interpretar y usar la vista de escenarios. |

Tabla No 5 Viewpoints

| ID | Vistas | Descripción |
|---|---|---|
| VIEW-001 <a name="VIEW-001"></a> | Vista lógica | Principalmente los requerimientos funcionales. Como se descompone el sistema en un conjunto de abstracciones tomadas principalmente del dominio del problema en forma de objetos y clases. |
| VIEW-002 <a name="VIEW-002"></a> | Vista desarrollo | Descomposición de del subsistema. Se centra en la organización de los módulos de software. |
| VIEW-003 <a name="VIEW-003"></a> | Vista proceso | Algunos requerimientos no funcionales. Aborda problemas de concurrencia y distribución. |
| VIEW-004 <a name="VIEW-004"></a> | Vista física | Mapeo de software y hardware. Principalmente requisitos no funcionales. |
| VIEW-005 <a name="VIEW-005"></a> | Vista escenarios | Abstracción de requisitos importante. |

Tabla No 6 Vistas

| ID | Modelos | Descripción |
|---|---|---|
| MOD-001 <a name="MOD-001"></a> | Modelo de Componentes | Aquí modelamos los componentes que ayudan a gestionar las funcionalidades del sistema. |
| MOD-002 <a name="MOD-002"></a> | Modelo de Paquetes | Se definen distintos paquetes a nivel lógico que forman parte de la aplicación y la dependencia entre ellos. |
| MOD-003 <a name="MOD-003"></a> | Modelo de Clases | Descripción estática de un sistema, permite comunicar el diseño de un programa, así mismo permite presentar relaciones entre entidades. |
| MOD-004 <a name="MOD-004"></a> | Modelo de despliegue | Representación gráfica sobre la ubicación física de los artefactos de Software. |
| MOD-005 <a name="MOD-005"></a> | Modelo de Secuencia | Presenta gráficamente las interacciones del actor y las operaciones que realiza durante el tiempo de ejecución . |
| MOD-006 <a name="MOD-006"></a> | Modelo de Actividad | Describen procesos llevados a cabo dentro de un sistema, transacciones o procedimientos. |
| MOD-007 <a name="MOD-007"></a> | Modelo de casos de uso | Representan la comunicaciones entre usuarios de un sistema u otros sistemas. |

Tabla No 7 Modelos

| Stakeholders vs Concerns | [CNR-001](#CNR-001) | [CNR-002](#CNR-002) | [CNR-003](#CNR-003) | [CNR-004](#CNR-004) | [CNR-005](#CNR-005) | [CNR-006](#CNR-006) | [CNR-007](#CNR-007) | [CNR-008](#CNR-008) | [CNR-009](#CNR-009) | [CNR-010](#CNR-010) |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| [VWP-001](#VWP-001) | X | X |  |  | X | X |  |  |  |  |
| [VWP-002](#VWP-002) | X |  | X |  | X | X |  |  |  | X |
| [VWP-003](#VWP-003) |  |  |  |  |  | X | X | X |  |  | 
| [VWP-004](#VWP-004) |  | X | X |  | X | X |  |  |  |  |
| [VWP-005](#VWP-005) | X |  |  |  |  |  |  |  | X | X |

Tabla No 8 Concerns vs Viewpoints

| Stakeholders vs Viewpoints | [VWP-001](#VWP-001) | [VWP-002](#VWP-002) | [VWP-003](#VWP-003) | [VWP-004](#VWP-004) | [VWP-005](#VWP-005) |
|---|:-:|:-:|:-:|:-:|:-:|
| [STK-001](#STK-001) |  |  |  |  | X |
| [STK-002](#STK-002) | X | X | X | X | X |
| [STK-003](#STK-003) | X | X | X | X | X |
| [STK-004](#STK-004) | X | X |  | X | X |

Tabla No 9 Stakeholders vs Viewpoints

| Vistas vs Modelos | [MOD-001](#MOD-001) | [MOD-002](#MOD-002) | [MOD-003](#MOD-003) | [MOD-004](#MOD-004) | [MOD-005](#MOD-005) | [MOD-006](#MOD-006) | [MOD-007](#MOD-007) |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| [VIEW-001](#VIEW-001) |  |  | X |  | X |  |  |
| [VIEW-002](#VIEW-002) | X | X |  |  |  |  |  |
| [VIEW-003](#VIEW-003) |  |  |  |  |  | X |  |
| [VIEW-004](#VIEW-004) |  |  |  | X |  |  |  |
| [VIEW-005](#VIEW-005) |  |  |  |  |  |  | X |

Tabla No 10 Vistas vs Modelos

<!-- Inicio de viewpoint de desarrollo -->

## Development viewpoint <a name="development-viewpoint"></a>

El viewpoint de desarrollo describe los requerimientos, preocupaciones inicialmente del equipo de desarrollo (Arquitecto - Desarrolladores - Tester), en esta apartado encontrará los concerns que enmarcan el punto de Vista, los tipos de modelos incluidos y convenciones que permiten un mejor entendimiento de la información que se presenta.

## Overview <a name="overview-development"></a>

El viewpoint de desarrollo se utiliza para describir la correlación de los módulos de software identificados en los requisitos detectados para la digitalización de los catálogos de ventas de los módulo de software sobre y el entorno de desarrollo del software.

## Framed concerns and typical stakeholders <a name="framed-concerns-and-typical-stakeholders-development"></a>

El equipo de arquitectura asume la importancia de identificar las preocupaciones de Stakeholders y sus preocupaciones, por cuanto esto hace parte del análisis que permitirá abordar sus intereses y presentar una solución adecuada desde el punto de vista de Desarrollo, de tal forma que fuese posible tomar las decisiones necesarias y de esta manera ofrecer la solución que cubra las expectativas de los interesados.

### Concerns <a name="concerns-development"></a>

A continuación se describe cada preocupación de las partes interesadas relacionadas con el Viewpoint de Desarrollo, las preocupaciones identificadas en esta sección son información esencial para el arquitecto ya que le ayudan a decidir cuándo será útil este punto de vista.

* [CNR-001](#CNR-001) - Usabilidad:  Se busca contar con herramientas de vanguardia que ofrezca una buena experiencia de usuario, esta preocupación se encuentra asociada al arquitecto de Software  y  sera unos de los puntos a evaluar por parte del tester, para abordar esta preocupación, dentro del personal de desarrollo debe existir coordinación entre el equipo, así mismo debe garantizarse que al menos 1 desarrollador debe ubicarse del lado del Frontend y bajo la dirección del Arquitecto cumplira su tarea   

* [CNR-003](#CNR-003) - Reacción al cambio "Escalabilidad": Dada su efectividad se espera ser implementada en los 85 países donde se tiene presencia comercial, la intención para esta preocupación debe ser la implementación una arquitectura que permita implementar la solución en diferentes tipos de dispositivos, para la empresa es importante crecer, lo que significa que los componentes y paquetes desarrollados deben ser altamente cohesionados y su nivel  de acoplamiento debe ser mínimo.  

* [CNR-005](#CNR-005) - Modificabilidad: La modificabilidad se refiere al grado en que un sistema puede ser modificado efectiva o eficientemente sin introducir defectos o degradar la calidad del sistema existente, esta preocupación de stakeholder, es bastante importante, por cuanto en la mayoría de los casos, los aplicativos crecen, los usuarios solicitan nuevas características o requieren que se amplíe una funcionalidad, si la arquitectura no ha sido debidamente planteada, este tipo de cambios puede ser de criticidad alta a la hora de hacer modificaciones.

* [CNR-006](#CNR-006) - Rendimiento: Desempeño del aplicativo, para la empresa es importante ampliar sus posibilidades de consulta y procesamiento de datos, es por ello que para el arquitecto debe ser importante diseñar una arquitectura que cumpla con las expectativas de la empresa, definir los estilos, patrones de diseño y técnicas a emplear importante, ya que a futuro las implementaciones de arquitectura repercuten en el correcto funcionamiento de características y requerimientos funcionales.  

* [CNR-010](#CNR-010) - Estructura de información: Administrar y presentar la información en los catálogos de acuerdo a la estrategia definida.

### Typical stakeholders <a name="typical-stakeholders-development"></a>

Las partes interesadas para esta vista incluye a los integrantes del equipo de desarrollo responsables de la construcción de software y sus descripciones Una vez revisada la tabla No 1, se identifican 3 Stakeholders para el viewpoint de desarrollo.

* [STK-002](#STK-002) - Equipo comercial: Personal que apoya el proceso de ventas
* [STK-003](#STK-003) - Equipo de mercadeo: Personal encargado de definir estrategias de mercadeo y diseño de catálogos
* [STK-004](#STK-004) - Equipo técnico: Expertos en cosmetología, apoyan el proceso de definición de los catálogos

Tabla No 4 Catálogo de Stakeholder Viewpoint de Desarrollo

## Model kinds+ <a name="model-kinds"></a>

* [MOD-001](#MOD-001) - Modelo de componentes
* [MOD-002](#MOD-002) - Modelo de Paquetes

__Subset of metamodel elements__

* Componente
* Interfaz
* Relación de dependencia
* Paquetes
* Dependencia entre paquetes

## Component model <a name="component-model"></a>

En esta sección se describe el diagrama de componentes de software que será empleado para describir la solución propuesta para la empresa “K”.

### Component model conventions <a name="component-model-conventions"></a>

El diagrama de componentes empleado para describir la vista de desarrollo está formado por tres elementos: Componente, Interfaz y Relación de dependencia.

__Componente:__ Representa una unidad lógicas del sistema, se grafica como un rectángulo con un rectángulo más pequeño en la esquina superior derecha con pestañas o la palabra escrita encima del nombre del componente.

Puede representar dos tipos de elementos: componentes lógicos (componentes de negocio o proceso) o componentes físicos (como componentes .NET, EJB).

![alt text][fig2]

Figura 2: Componente

__La interfaz:__ Representa la zona del módulo que es utilizada para la comunicación con otro de los componentes está compuesta generalmente por una relación de Proveedor y consumidor de un servicio que es expuesto mediante un contrato.

![alt text][fig3]

Figura 3: Interfaz

__La relación de dependencia:__ representa que un componente requiere de otro para ejecutar su trabajo. Es diferente a la interfaz, pues esta identifica que un componente ofrece una serie de operaciones. En cualquier caso, en ocasiones para simplificar el diagrama no se usan las interfaces sino que solamente se utilizan relaciones de dependencia.

![alt text][fig4]

Figura 4: Relación de dependencia

## Package model <a name="package-model"></a>

Por medio de estos diagramas se pretende presentar una visión más clara del sistema de información de la empresa K,   organizado en subsistemas y agrupando elementos para su análisis y mejor entendimiento así mismo se construyen dependencias entre paquetes, siendo una extensión del diagrama de clases y de componentes.

### Package model conventions <a name="package-model-conventions"></a>

__Paquetes:__ Consiste en agrupar elementos de casos de uso,  clases o componentes. a menudo es posible encontrar paquetes que contienen otros paquetes, su representación es un artefacto con forma de carpeta, el cual es nombrado según su uso y responsabilidad dentro del diagrama.

![alt text][fig5]

Figira 5: Paquete

__Dependencias entre paquetes:__ Existe una dependencia cuando un elemento de un paquete requiere de otro que pertenece a un paquete distinto. Las dependencias se representan con una flecha discontinua con inicio en el paquete que depende del otro.

![alt text][fig6]

Figira 6: Dependencia entre paquetes

## Operations on views+ <a name="operations-on-views-component"></a>

Operations define the methods to be applied to views and their models. Types of operations include:

* __Construction method:__ Este tipo de modelos se construye implementando componentes, los cuales deben llevar un estereotipo que los identifique, cada componente dentro del diagrama puede contener clases e interfaces.

  Así mismo pueden ser implementados por otros paquetes mediante el uso de interfaces que permiten exponer servicios y su consumo. 

  Debe existir relación de dependencia para los casos en que un paquete requiera de la funcionalidad de otro paquete para su correcto empleo. 

* __Analysis method:__ Para el arquitecto el diagrama de componentes le permite conocer un plano general de la aplicación, la relación entre módulos y sus dependencias, de tal manera que sea posible identificar las tareas de desarrollo que debe asignar al equipo, los estilos de arquitectura, patrones de diseño y distribuir actividades de acuerdo a la experticia del equipo.

  Para el caso de los desarrolladores, el diagrama de componentes presenta la relación que debe existir entre las tareas que se le asignan como miembro del equipo de desarrollo, y sus compañeros, esto permite distinguir las responsabilidades de cada individuo como miembro del todo, restricciones, dependencia entre componentes, datos que son compartidos entre las funcionalidades de cada componente entre otros.

## Correspondence rules <a name="correspondence-rules-component"></a>

* R1: Los módulos presentados en el diagrama de componentes serán desplegados en nodos del diagrama de despliegue.
por lo anterior debe existir 3 nodos Desarrollo, Pruebas y Producción, desarrollo corresponde al nodo de desarrollo local de los programadores, mientras que pruebas será desplegado de manera independiente a producción, el nodo productivo será independiente y si y sólo si sera puesto en producción aquellos componentes y/o paquetes que han sido probadas por desarrolladores, testers y usuarios finales.

* R2: Las bases de datos estarán en nodos, manejando tres ambientes como es el caso de los componentes, desarrollo, pruebas y producción.

* R3: Debe existir un solo repositorio para el versionamiento del código el cual será  desplegado en un nodo descrito en el diagrama de despliegue.

## Sources <a name="sources-development"></a>

[Table of contents](#table-of-contents)

<!-- Fin de viewpoint de desarrollo -->

# Views+ <a name="views"></a>

## Development view <a name="development-view"></a>

Descripción de la vista de desarrollo usada. dos modelos uno de componentes y uno de paquetes

### Models+ <a name="models-development-view"></a>
### Components <a name="models-component-development-view"></a>

![alt text][fig7]

Figira 7: Diagrama de Componentes de aplicación

### Package <a name="models-package-development-view"></a>

El objetivo del diagrama es obtener una visión más clara del sistema de información orientado a objetos, organizándolo en subsistemas, agrupando los elementos de análisis, diseño y construcción detallando las relaciones de dependencia entre ellos.

El diagrama de paquetes y sus dependencias, son elementos de los diagramas de casos de uso y de componentes de nuestro sistema.

![alt text][fig8]

Figira 8: Diagrama de paquetes

### Known Issues with View <a name="issues-with-development-view"></a>

Documente cualquier discrepancia entre la vista y sus convenciones de puntos de vista. Cada vista de arquitectura debe cumplir con las convenciones de su punto de vista de arquitectura de gobierno. Los problemas conocidos pueden incluir: inconsistencias elementos a completar, problemas abiertos o no resueltos, excepciones y desviaciones de las convenciones establecidas por el punto de vista. Los asuntos abiertos pueden llevar a tomar decisiones. Las excepciones y desviaciones pueden documentarse como resultados de decisión y justificación.

[Table of contents](#table-of-contents)

# Consistency and correspondences <a name="consistency-and-correspondences"></a>

Este capítulo describe los requisitos de coherencia, el registro de inconsistencias conocidas en un AD y el uso y documentación de correspondencias y reglas de correspondencia.

## Known inconsistencies <a name="known-inconsistencies"></a>

Registre cualquier inconsistencia conocida en el AD. Aunque obviamente se prefieren los EA consistentes, a veces es inviable o poco práctico resolver todas las inconsistencias por razones de tiempo, esfuerzo o información insuficiente.

## Correspondences in the AD <a name="correspondences-in-the-ad"></a>

Identifique cada correspondencia en el AD y sus elementos de AD participantes. Identificar las reglas de correspondencia que rigen
Las correspondencias se utilizan para expresar, registrar, aplicar y analizar la coherencia entre modelos, vistas y otros elementos de AD dentro de una descripción de arquitectura, entre AD o entre un AD y otras formas de documentación.

Los elementos de AD incluyen instancias de partes interesadas, preocupaciones, puntos de vista y puntos de vista, tipos y modelos de modelos, decisiones y fundamentos. Las construcciones introducidas por los puntos de vista y los tipos de modelos también son elementos AD.

Las correspondencias son relaciones matemáticas n-arias. Las correspondencias pueden representarse mediante tablas, enlaces o mediante otras formas de asociación (como en UML).

[Table of contents](#table-of-contents)

## Correspondence rules <a name="correspondence-rules-final"></a>

Identifique cada regla de correspondencia que se aplica al AD.

Las reglas de correspondencia pueden ser introducidas por el AD, por uno de sus puntos de vista, o desde un marco de arquitectura o lenguaje de descripción de arquitectura que se esté utilizando.

Para cada regla de correspondencia identificada, registre si la regla cumple (se cumple) o, de lo contrario, registre todas las violaciones conocidas.

[Table of contents](#table-of-contents)

# Architecture decisions and rationale <a name="architecture-decisions-and-rationale"></a>
Some introduction text, formatted in heading 2 style

[Table of contents](#table-of-contents)

## Decisions <a name="decisions"></a>
The second paragraph text 

[Table of contents](#table-of-contents)

[fig1]: /img/fig1.png "Model Conceptual"
[fig2]: /img/fig2.png "Componente"
[fig3]: /img/fig3.png "Interfaz"
[fig4]: /img/fig4.png "Relación de dependencia"
[fig5]: /img/fig5.png "Paquete"
[fig6]: /img/fig6.png "Dependencia entre paquetes"
[fig7]: /img/fig7.png "Diagrama de Componentes de aplicación"
[fig8]: /img/fig8.png "Diagrama de paquetes"