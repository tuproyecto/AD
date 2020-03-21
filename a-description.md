# Table of contents <a name="table-of-contents"></a>
1. [Introduction](#introduction)
    1. [Identifying information](#identifying-information)
    2. [Supplementary information](#supplementary-information)
    3. [Other information](#other-information)
        1. [Rationale for key decisions](#rationale-for-key-decisions)
2. [Stakeholders and concerns](#stakeholders-and-concerns)
    1. [Stakeholders](#stakeholders)
    2. [Concerns](#concerns)
    3. [Concern–Stakeholder Taceability](#concern–stakeholder-traceability)
3. [Viewpoints+](#viewpoints)    
    1. [Viewpoints descriptions](#viewpoint-description)
4. [Views+](#views)    
    1. [Development view](#development-view)
        1. [Models+](#models-development-view)
        2. [Components](#models-component-development-view)
        3. [Package](#models-package-development-view)
        4. [Known Issues with View](#issues-with-development-view)
    2. [Physical view](#physical-view)
        1. [Models+](#models-physical-view)
        2. [Deployment](#models-deployment-physical-view)
        3. [Known Issues with View](#issues-with-physical-view)
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
* Estado: Documento en revisión
* Autores: 
  * Castiblanco Soler David Alejandro
  * Céspedes Ortega Johan Miguel
  * Espitia Aristizábal Dubier Esneider
  * Gómez Cuervo Diego Armando
* Revisores: Ing. Miguel Torres
* Historial de cambios: Primera versión del documento
* Resumen: Se realizará la descripción de arquitectura para la digitalización del catálogo de cosméticos utilizado por el equipo comercial para el proceso de ventas y que actualmente se encuentra en medio físico.
* Alcance: Definir una primera versión del documento de descripción de arquitectura para el proyecto de catálogo virtual.
* Contexto: Con el objetivo modernizar la operación y construir escenarios para una mayor expansión de su mercado, la empresa K busca digitalizar su catálogo físico a un catálogo digital que sirva como herramienta para que el equipo comercial optimice su eficiencia con una herramienta fácil de usar e intuitiva.
 
## Other information <a name="other-information"></a>

__Descripción general del sistema__ <a name="descripcion-general-sistema"></a>

La empresa K, lleva 5 años en el mercado ofreciendo a sus clientes productos cosméticos, para lo cual ha generado como apoyo a las ventas catálogos y manuales de producto.
Para bajar costos, los manuales se quieren manejar de manera electrónica y los catálogos se quieren manejar a través de tecnología Web.

La empresa cuenta con un equipo comercial, al cual se le asignan diferentes tipos de tecnologías para apoyar el proceso de ventas. Entre los equipos asignados están portátiles, tabletas, celulares, entre otros.

Se busca que el sistema permita a los comerciales presentar el catálogo durante sus visitas, independientemente de la tecnología. De modo que el comercial pueda ofrecer los productos y realizar el pedido de los mismos durante la visita. 

Al realizar el pedido se le debe indicar al cliente cuando se le realizará la entrega del producto. Adicional a los vendedores se cuenta con un equipo de mercadeo que define la estrategia, diseño, forma y contenido de los catálogos. Este equipo de mercadeo debe contar con las herramientas para poder ingresar, manipular y gestionar los catálogos.

El equipo de mercadeo, junto con un equipo técnico de expertos en cosmetología definen los manuales, el diseño de estos y su contenido. Estos equipos deben estar en la capacidad de crear nuevos manuales, gestionarlos y administrar su contenido.
Se espera que el sistema pueda ser usado tanto en las oficinas como fuera de estas.

Se busca un sistema fácil de usar, que permita una curva acelerada de aprendizaje al ser intuitivo. Los tiempos de respuesta deben ser acordes al mercado, de modo que los diferentes usuarios del sistema no deban esperar por la respuesta del sistema.

El sistema inicialmente se usará en Colombia, pero una vez se pruebe su efectividad, este se llevará a los 85 países donde se tiene ventas de los productos.

__Papel clave de las partes interesadas__

* Clientes: No jugaran un papel clave en esta descripción de arquitectura ya que según lo estipula la descripción general del sistema nos enfocaremos en el equipo comercial y de mercadeo como principales beneficiarios tanto a nivel de estrategia como de ejecución.
* Equipo comercial: Se busca que beneficie principalmente a este stakeholder ya que uno de los principales objetivos en mejorar la efectividad en cada visita.
* Equipo de mercadeo: Se busca que este stakeholder tenga la capacidad de diseñar estrategias más eficientes y oportunas al contar con las herramientas digitales para cerrar las brechas que generan los catálogos impresos.
* Equipo técnico: Tendrá la capacidad de ajustar de forma más oportuna los diseños y manuales de cosmetología de acuerdo con las estrategias que mercadeo dicte.

### Rationale for key decisions <a name="rationale-for-key-decisions"></a>

Conociendo los stakeholders vinculados al desarrollo de la descripción de arquitectura procedemos a realizar la matriz de porder [tabla 1](#tabla1) para determinar las prioridades y contar con un primer elemento de juicio para tomar las decisiones arquitectónicas relevantes.

| Matriz de poder<a name="tabla1"></a> | Keep Satisfied | Key Subject | Minimal Effort | Keep Informed |
|---|:-:|:-:|:-:|:-:|
| Clientes |  |  | X |  |
| Equipo comercial |  | X |  |  |
| Equipo de mercadeo |  | X |  |  |
| Equipo técnico | X |  |  |  |

Tabla 1:  Matriz de poder de stakeholders involucrados en la descripción de arquitectura.

Los stakeholders con mayor poder en para el ejercicio de descripción de arquitectura son el equipo de mercadeo y el equipo comercial ya que estos se encargaran de la estrategia y la ejecución respectivamente. Por tal motivo muchas de las decisiones tomadas se basaran en la prioridad que se les otorgará en las decisiones.

[Table of contents](#table-of-contents)

# Stakeholders and concerns <a name="stakeholders-and-concerns"></a>

## Stakeholders <a name="stakeholders"></a>

La [tabla 2](#tabla2) presenta el catálogo de Stakeholders identificados dentro del problema, los cuales son identificados con un id único, el cual será usado de aquí en adelante cada vez que se haga referencia a estos.

| ID | Stakeholder<a name="tabla2"></a> | Descripción |
|---|---|---|
| STK-001 <a name="STK-001"></a> | Clientes | Potenciales consumidores |
| STK-002 <a name="STK-002"></a> | Equipo comercial | Personal que apoya el proceso de ventas |
| STK-003 <a name="STK-003"></a> | Equipo de mercadeo | Personal encargado de definir estrategias de mercadeo y diseño de catálogos |
| STK-004 <a name="STK-004"></a> | Equipo técnico | Expertos en cosmetología, apoyan el proceso de definición de los catálogos |

Tabla 2: Catálogo de Stakeholder detectados con interés sobre el desarrollo del documento de descripción de arquitectura.

## Concerns <a name="concerns"></a>

Las Preocupaciones descritas en la [tabla 3](#tabla3) fueron discutidas basados en la revisión de la [descripción general del sistema](#descripcion-general-sistema), de tal forma que pudieran identificarse cuáles eran apropiados para el ejercicio, de esta manera llevar a cabo un análisis de información que permitirá mapearlos para poder establecer las relaciones asociaciones necesarias para definir de forma adecuada los viewpoints.

| ID | Concerns <a name="tabla3"></a> | Descripción |
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

Tabla 3: Catálogo de Preocupaciones definidas con base en la [descripción general del sistema](#descripcion-general-sistema)

## Concern–Stakeholder Traceability <a name="concern–stakeholder-traceability"></a>

La matriz de trazabilidad entre Stakeholders y preocupaciones presentada en la [tabla 4](#tabla4) nos permite analizar sobre ¿Qué stakeholder se identifica con cuáles preocupación? Además de ¿Cuáles son común a varios interesados? ¿Cuáles no tienen relevancia entre entre los Stakeholders identificados?.

| Stakeholders vs Concerns <a name="tabla4"></a> | [CNR-001](#CNR-001) | [CNR-002](#CNR-002) | [CNR-003](#CNR-003) | [CNR-004](#CNR-004) | [CNR-005](#CNR-005) | [CNR-006](#CNR-006) | [CNR-007](#CNR-007) | [CNR-008](#CNR-008) | [CNR-009](#CNR-009) | [CNR-010](#CNR-010) |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| [STK-001](#STK-001) | X | X |  | X |  |  |  |  | X |  |
| [STK-002](#STK-002) | X | X | X |  |  | X | X | X |  |  |
| [STK-003](#STK-003) |  |  |  |  | X |  |  | X |  | X | 
| [STK-004](#STK-004) |  |  |  |  | X |  |  |  |  | X |

Tabla 4: Matriz de stakeholders vs concerns, se muestra la asociación existente entre los stakeholders identificados y las preocupaciones.

[Table of contents](#table-of-contents)

# Viewpoints+ <a name="viewpoints"></a>

La arquitectura definida de acuerdo a la [descripción general del sistema](#descripcion-general-sistema) para la empresa K será expresada usando el modelo 4 + 1, de esta forma definiremos 4 viewpoints para el desarrollo de la actividad y enmarcamos las preocupaciones y los stakeholders dentro de estas 4 perspectivas del la arquitectura.

En conjunto se establece que se tomarán los puntos de vista descritos en la [tabla 5](#tabla5) los cuales corresponden a: desarrollo, lógico, físico, procesos y escenarios. Consideramos que de esta manera se abarca el total de la información sobre la construcción de arquitectura de software como respuesta a la necesidad de la Empresa K.

| ID | Viewpoints <a name="tabla5"> | Descripción |
|---|---|---|
| VWP-001 <a name="VWP-001"></a> | Viewpoint lógica | Establece convenciones para crear, interpretar y usar la vista lógica. |
| VWP-002 <a name="VWP-002"></a> | Viewpoint desarrollo | Establece convenciones para crear, interpretar y usar la vista de desarrollo. |
| VWP-003 <a name="VWP-003"></a> | Viewpoint proceso | Establece convenciones para crear, interpretar y usar la vista de proceso. |
| VWP-004 <a name="VWP-004"></a> | Viewpoint física | Establece convenciones para crear, interpretar y usar la vista física. |
| VWP-005 <a name="VWP-005"></a> | Viewpoint escenarios | Establece convenciones para crear, interpretar y usar la vista de escenarios. |

Tabla 5: Catálogo de viewpoints, se definen los viewpoint que se considerarán para el desarrollo de la descripción de arquitectura.

Ya teniendo definidos los viewpoints con los que trabajaremos para la descripción de arquitectura, procedemos a construir la [tabla 6](#tabla6) en la cual se describen las vistas con las que trabajaremos.

| ID | Vistas <a name="tabla6"> | Descripción |
|---|---|---|
| VIEW-001 <a name="VIEW-001"></a> | Vista lógica | Principalmente los requerimientos funcionales. Como se descompone el sistema en un conjunto de abstracciones tomadas principalmente del dominio del problema en forma de objetos y clases. |
| VIEW-002 <a name="VIEW-002"></a> | Vista desarrollo | Descomposición de del subsistema. Se centra en la organización de los módulos de software. |
| VIEW-003 <a name="VIEW-003"></a> | Vista proceso | Algunos requerimientos no funcionales. Aborda problemas de concurrencia y distribución. |
| VIEW-004 <a name="VIEW-004"></a> | Vista física | Mapeo de software y hardware. Principalmente requisitos no funcionales. |
| VIEW-005 <a name="VIEW-005"></a> | Vista escenarios | Abstracción de requisitos importante. |

Tabla 6: Catálogo de vistas basado en los viewpoints definidos por el modelo 4 + 1.

Teniendo definidas las vistas por el modelo 4 + 1, procedemos a definir en la [tabla 7](#tabla7) los modelos asociados a cada vista y los cuales definirán los viewpoints para el desarrollo de la descripción de arquitectura.

| ID | Modelos <a name="tabla7"> | Descripción |
|---|---|---|
| MOD-001 <a name="MOD-001"></a> | Modelo de Componentes | Aquí modelamos los componentes que ayudan a gestionar las funcionalidades del sistema. |
| MOD-002 <a name="MOD-002"></a> | Modelo de Paquetes | Se definen distintos paquetes a nivel lógico que forman parte de la aplicación y la dependencia entre ellos. |
| MOD-003 <a name="MOD-003"></a> | Modelo de Clases | Descripción estática de un sistema, permite comunicar el diseño de un programa, así mismo permite presentar relaciones entre entidades. |
| MOD-004 <a name="MOD-004"></a> | Modelo de despliegue | Representación gráfica sobre la ubicación física de los artefactos de Software. |
| MOD-005 <a name="MOD-005"></a> | Modelo de Secuencia | Presenta gráficamente las interacciones del actor y las operaciones que realiza durante el tiempo de ejecución . |
| MOD-006 <a name="MOD-006"></a> | Modelo de Actividad | Describen procesos llevados a cabo dentro de un sistema, transacciones o procedimientos. |
| MOD-007 <a name="MOD-007"></a> | Modelo de casos de uso | Representan la comunicaciones entre usuarios de un sistema u otros sistemas. |

Tabla 7: Descripción de los modelos definidos de acuerdo al modelo 4 + 1.

Contando con las tablas anteriormente descritas podemos establecer relaciones que nos ayudan a definir cada uno de los viewpoints. En la [tabla 8](#tabla8) se presenta la relación entre los viewpoints y los concerns relacionados a cada uno.

| Viewpoints vs Concerns <a name="tabla8"> | [CNR-001](#CNR-001) | [CNR-002](#CNR-002) | [CNR-003](#CNR-003) | [CNR-004](#CNR-004) | [CNR-005](#CNR-005) | [CNR-006](#CNR-006) | [CNR-007](#CNR-007) | [CNR-008](#CNR-008) | [CNR-009](#CNR-009) | [CNR-010](#CNR-010) |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| [VWP-001](#VWP-001) | X | X |  |  | X | X |  |  |  |  |
| [VWP-002](#VWP-002) | X |  | X |  | X | X |  |  |  | X |
| [VWP-003](#VWP-003) |  |  |  |  |  | X | X | X |  |  | 
| [VWP-004](#VWP-004) |  | X | X |  | X | X |  |  |  |  |
| [VWP-005](#VWP-005) | X |  |  |  |  |  |  |  | X | X |

Tabla 8: Matriz de relación enrte Viewpoints y Concerns para la elaboración de viewpoints.

Así mismo realizamos la [tabla 9](#tabla9) para relacionar los stakeholders identificados con los viewpoints definidos anteriormente.

| Stakeholders vs Viewpoints <a name="tabla9"> | [VWP-001](#VWP-001) | [VWP-002](#VWP-002) | [VWP-003](#VWP-003) | [VWP-004](#VWP-004) | [VWP-005](#VWP-005) |
|---|:-:|:-:|:-:|:-:|:-:|
| [STK-001](#STK-001) |  |  |  |  | X |
| [STK-002](#STK-002) | X | X | X | X | X |
| [STK-003](#STK-003) | X | X | X | X | X |
| [STK-004](#STK-004) | X | X |  | X | X |

Tabla 9: Matriz de relación entre stakeholders y viewpoints.

Para complementar las definiciones de cada viewpoint en la [tabla 10](#tabla10) realizamos la matriz de relación entre las vistas y los modelos con los que se representará cada una. 

| Vistas vs Modelos <a name="tabla10"> | [MOD-001](#MOD-001) | [MOD-002](#MOD-002) | [MOD-003](#MOD-003) | [MOD-004](#MOD-004) | [MOD-005](#MOD-005) | [MOD-006](#MOD-006) | [MOD-007](#MOD-007) |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| [VIEW-001](#VIEW-001) |  |  | X |  | X |  |  |
| [VIEW-002](#VIEW-002) | X | X |  |  |  |  |  |
| [VIEW-003](#VIEW-003) |  |  |  |  |  | X |  |
| [VIEW-004](#VIEW-004) |  |  |  | X |  |  |  |
| [VIEW-005](#VIEW-005) |  |  |  |  |  |  | X |

Tabla 10: Matriz de relación entre las vistas y los modelos con los que se representa cada vista.

## Viewpoint description <a name="viewpoint-description"></a>

A continuación se presentan los [viewpoints descriptions][vp-description]:

* [Development viewpoint][development-viewpoint-description]
* [Physical viewpoint][physical-viewpoint-description]
* [Logical viewpoint][logical-viewpoint-description]
* [Process viewpoint][process-viewpoint-description]
* [Scenarios viewpoint][scenarios-viewpoint-description]

# Views+ <a name="views"></a>

<!-- Inicio de view development -->
## Development  view <a name="development -view"></a>

A continuación se describe la vista de desarrollo los modelos de componentes y paquetes.

### Models+ <a name="models-development -view"></a>
### Components <a name="models-component-development-view"></a>

![alt text][fig14]

Figura 14: Diagrama de Componentes de aplicación

### Package <a name="models-package-development-view"></a>

El objetivo del diagrama es obtener una visión más clara del sistema de información orientado a objetos, organizándolo en subsistemas, agrupando los elementos de análisis, diseño y construcción detallando las relaciones de dependencia entre ellos.

El diagrama de paquetes y sus dependencias, son elementos de los diagramas de casos de uso y de componentes de nuestro sistema.

![alt text][fig15]

Figura 15: Diagrama de paquetes

### Known Issues with View <a name="issues-with-development-view"></a>

Documente cualquier discrepancia entre la vista y sus convenciones de puntos de vista. Cada vista de arquitectura debe cumplir con las convenciones de su punto de vista de arquitectura de gobierno. Los problemas conocidos pueden incluir: inconsistencias elementos a completar, problemas abiertos o no resueltos, excepciones y desviaciones de las convenciones establecidas por el punto de vista. Los asuntos abiertos pueden llevar a tomar decisiones. Las excepciones y desviaciones pueden documentarse como resultados de decisión y justificación.

[Table of contents](#table-of-contents-vp)

<!-- Fin de view development -->

<!-- Inicio de view Fisica -->
## Physical  view <a name="physical-view"></a>

Descripción de la vista de fisica empleada, presentando el modelo de despliegue.

### Models+ <a name="models-physical-view"></a>

### Components <a name="models-component-physical-view"></a>

El diagrama de despliegue describe la implementación física de la información generada por el programa de software en los componentes de hardware. La arquitectura presentada en capas, es la que ofrece mayor rendimiento en cumplimiento con las preocupaciones de stakeholders, respecto CNR-002 Disponibilidad "Availability", CNR-003 - Reacción al cambio "Escalabilidad", CNR-006 - Rendimiento: Desempeño del aplicativo, CNR-010 - Estructura de información.

Como se evidencia en la Figura 10, se especifica el ambiente de Producción y en la figura, los ambientes de Desarrollo y Pruebas, producción es independiente mientra desarrollo y pruebas comparten base de datos lo cual optimiza recursos.

El sistema de la empresa ”K” está diseñado para que se ejecute en un servidor de aplicaciones, este cuenta con un componente encargado de gestionar la vista, un servidor de aplicaciones con el backend de la aplicación y una base de datos en un nodo independiente.

El objetivo de separar los componentes por su responsabilidad, se plantea minimizando el acoplamiento, ademas de esto la lógica de negocio no se vera afectada en casos de requerir cambios, las transacciones y seguridad de la aplicación será aumentada por la distribución de capas y su consumo desde la capa superior únicamente.

La separación por capas permite que la aplicación sea fácilmente escalable.

La aplicación interactúa con una base de datos a través de una capa de persistencia, para lo cual emplea repositorio y es persistida por medio del motor de base de datos de la empresa.

![alt text][fig16]

Figura 16: Diagrama de Despliegue de aplicación en ambiente productivo

![alt text][fig17]

Figura 17: Diagrama de Despliegue de aplicación desarrollo y pruebas 

### Known Issues with View <a name="issues-with-physical-view"></a>

La empresa no cuenta con equipos de seguridad que permitan implementar medidas de seguridad de los servicios que se exponen y los equipos donde se encuntran desplegados. 

[Table of contents](#table-of-contents-vp)

<!-- Fin de view Fisica -->

# Consistency and correspondences <a name="consistency-and-correspondences"></a>

> Este capítulo describe los requisitos de coherencia, el registro de inconsistencias conocidas en un AD y el uso y documentación de correspondencias y reglas de correspondencia.

## Known inconsistencies <a name="known-inconsistencies"></a>

> Registre cualquier inconsistencia conocida en el AD. Aunque obviamente se prefieren los EA consistentes, a veces es inviable o poco práctico resolver todas las inconsistencias por razones de tiempo, esfuerzo o información insuficiente.

## Correspondences in the AD <a name="correspondences-in-the-ad"></a>

> Identifique cada correspondencia en el AD y sus elementos de AD participantes. Identificar las reglas de correspondencia que rigen

> Las correspondencias se utilizan para expresar, registrar, aplicar y analizar la coherencia entre modelos, vistas y otros elementos de AD dentro de una descripción de arquitectura, entre AD o entre un AD y otras formas de documentación.

> Los elementos de AD incluyen instancias de partes interesadas, preocupaciones, puntos de vista y puntos de vista, tipos y modelos de modelos, decisiones y fundamentos. Las construcciones introducidas por los puntos de vista y los tipos de modelos también son elementos AD.

> Las correspondencias son relaciones matemáticas n-arias. Las correspondencias pueden representarse mediante tablas, enlaces o mediante otras formas de asociación (como en UML).

[Table of contents](#table-of-contents)

## Correspondence rules <a name="correspondence-rules-final"></a>

> Identifique cada regla de correspondencia que se aplica al AD.

> Las reglas de correspondencia pueden ser introducidas por el AD, por uno de sus puntos de vista, o desde un marco de arquitectura o lenguaje de descripción de arquitectura que se esté utilizando.

> Para cada regla de correspondencia identificada, registre si la regla cumple (se cumple) o, de lo contrario, registre todas las violaciones conocidas.

[Table of contents](#table-of-contents)

# Architecture decisions and rationale <a name="architecture-decisions-and-rationale"></a>
Some introduction text, formatted in heading 2 style

[Table of contents](#table-of-contents)

## Decisions <a name="decisions"></a>
The second paragraph text 

[Table of contents](#table-of-contents)

[fig1]: /img/fig1.png "Model Conceptual"
[fig14]: /img/fig14.png "Diagrama de Componentes de aplicación"
[fig15]: /img/fig15.png "Diagrama de paquetes"
[fig16]: /img/fig16.png "Diagrama de Despliegue de aplicación en ambiente productivo"
[fig17]: /img/fig17.png "Diagrama de Despliegue de aplicación desarrollo y pruebas"

[vp-description]: /vp-description.md
[development-viewpoint-description]: /vp-description.md#development-viewpoint
[physical-viewpoint-description]: /vp-description.md#physical-viewpoint
[logical-viewpoint-description]: /vp-description.md#logical-viewpoint
[process-viewpoint-description]: /vp-description.md#process-viewpoint
[scenarios-viewpoint-description]: /vp-description.md#scenarios-viewpoint