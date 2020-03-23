# Table of contents <a name="table-of-contents-vp"></a>
1. [Development viewpoint](#development-viewpoint)
    1. [Overview](#overview-development)
    2. [Framed concerns and typical stakeholders](#framed-concerns-and-typical-stakeholders-development)
        1. [Concerns](#concerns-development)
        2. [Typical stakeholders](#typical-stakeholders-development)
    3. [Model kinds+](#model-kinds-development)
    4. [Component model](#component-model)
        1. [Component model conventions](#component-model-conventions)
    5. [Package model](#package-model)
        1. [Package model conventions](#package-model-conventions)
    6. [Operations on views+](#operations-on-views-development)
    7. [Correspondence rules](#correspondence-rules-development)
    8. [Sources](#sources-development)
2. [Physical viewpoint](#physical-viewpoint)
    1. [Overview](#overview-physical)
    2. [Framed concerns and typical stakeholders](#framed-concerns-and-typical-stakeholders-physical)
        1. [Concerns](#concerns-physical)
        2. [Typical stakeholders](#typical-stakeholders-physical)
    3. [Model kinds+](#model-kinds-physical)
    4. [Deployment model](#deployment-model)
        1. [Deployment model conventions](#deployment-model-conventions)
    6. [Operations on views+](#operations-on-views-physical)
    7. [Correspondence rules](#correspondence-rules-physical)
    8. [Sources](#sources-physical)
3. [Logical viewpoint](#logical-viewpoint)
    1. [Overview](#overview-logical)
    2. [Framed concerns and typical stakeholders](#framed-concerns-and-typical-stakeholders-logical)
        1. [Concerns](#concerns-logical)
        2. [Typical stakeholders](#typical-stakeholders-logical)
    3. [Model kinds+](#model-kinds-logical)
    4. [Class model](#class-model)
        1. [Class model conventions](#class-model-conventions)
    5. [Sequence model](#sequence-model)
        1. [Sequence model conventions](#sequence-model-conventions)
    6. [Operations on views+](#operations-on-views-logical)
    7. [Correspondence rules](#correspondence-rules-logical)
    8. [Sources](#sources-logical)
4. [Process viewpoint](#process-viewpoint)
    1. [Overview](#overview-process)
    2. [Framed concerns and typical stakeholders](#framed-concerns-and-typical-stakeholders-process)
        1. [Concerns](#concerns-process)
        2. [Typical stakeholders](#typical-stakeholders-process)
    3. [Model kinds+](#model-kinds-process)
    4. [Activities model](#activities-model)
        1. [Activities model conventions](#activities-model-conventions)
    5. [Operations on views+](#operations-on-views-process)
    6. [Correspondence rules](#correspondence-rules-process)
    7. [Sources](#sources-process)
5. [Scenarios viewpoint](#scenarios-viewpoint)
    1. [Overview](#overview-scenarios)
    2. [Framed concerns and typical stakeholders](#framed-concerns-and-typical-stakeholders-scenarios)
        1. [Concerns](#concerns-scenarios)
        2. [Typical stakeholders](#typical-stakeholders-scenarios)
    3. [Model kinds+](#model-kinds-scenarios)
    4. [Use cases model](#use-cases-model)
        1. [Use cases model conventions](#use-cases-model-conventions)
    5. [Operations on views+](#operations-on-views-scenarios)
    6. [Correspondence rules](#correspondence-rules-scenarios)
    7. [Sources](#sources-scenarios)

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

## Model kinds+ <a name="model-kinds-development"></a>

* [MOD-001](#MOD-001) - Modelo de componentes
* [MOD-002](#MOD-002) - Modelo de Paquetes

__Subset of metamodel elements__

* Componente
* Interfaz
* Relación de dependencia
* Paquetes
* Dependencia entre paquetes

## Component model <a name="component-model"></a>

En esta sección se describe el diagrama de componentes de software que será empleado para describir la solución propuesta para la empresa K.

### Component model conventions <a name="component-model-conventions"></a>

El diagrama de componentes empleado para describir la vista de desarrollo está formado por tres elementos: Componente, Interfaz y Relación de dependencia.

__Componente:__ Representa una unidad lógicas del sistema, se grafica como un rectángulo con un rectángulo más pequeño en la esquina superior derecha con pestañas o la palabra escrita encima del nombre del componente.

Puede representar dos tipos de elementos: componentes lógicos (componentes de negocio o proceso) o componentes físicos (como componentes .NET, EJB).

![alt text][fig1]

Figura 1: Componente

__La interfaz:__ Representa la zona del módulo que es utilizada para la comunicación con otro de los componentes está compuesta generalmente por una relación de Proveedor y consumidor de un servicio que es expuesto mediante un contrato.

![alt text][fig2]

Figura 2: Interfaz

__La relación de dependencia:__ representa que un componente requiere de otro para ejecutar su trabajo. Es diferente a la interfaz, pues esta identifica que un componente ofrece una serie de operaciones. En cualquier caso, en ocasiones para simplificar el diagrama no se usan las interfaces sino que solamente se utilizan relaciones de dependencia.

![alt text][fig3]

Figura 3: Relación de dependencia

## Package model <a name="package-model"></a>

Por medio de estos diagramas se pretende presentar una visión más clara del sistema de información de la empresa K,   organizado en subsistemas y agrupando elementos para su análisis y mejor entendimiento así mismo se construyen dependencias entre paquetes, siendo una extensión del diagrama de clases y de componentes.

### Package model conventions <a name="package-model-conventions"></a>

__Paquetes:__ Consiste en agrupar elementos de casos de uso,  clases o componentes. a menudo es posible encontrar paquetes que contienen otros paquetes, su representación es un artefacto con forma de carpeta, el cual es nombrado según su uso y responsabilidad dentro del diagrama.

![alt text][fig4]

Figura 4: Paquete

__Dependencias entre paquetes:__ Existe una dependencia cuando un elemento de un paquete requiere de otro que pertenece a un paquete distinto. Las dependencias se representan con una flecha discontinua con inicio en el paquete que depende del otro.

![alt text][fig5]

Figura 5: Dependencia entre paquetes

## Operations on views+ <a name="operations-on-views-development"></a>

Operations define the methods to be applied to views and their models. Types of operations include:

* __Construction method:__ Este tipo de modelos se construye implementando componentes, los cuales deben llevar un estereotipo que los identifique, cada componente dentro del diagrama puede contener clases e interfaces.

  Así mismo pueden ser implementados por otros paquetes mediante el uso de interfaces que permiten exponer servicios y su consumo. 

  Debe existir relación de dependencia para los casos en que un paquete requiera de la funcionalidad de otro paquete para su correcto empleo. 

* __Analysis method:__ Para el arquitecto el diagrama de componentes le permite conocer un plano general de la aplicación, la relación entre módulos y sus dependencias, de tal manera que sea posible identificar las tareas de desarrollo que debe asignar al equipo, los estilos de arquitectura, patrones de diseño y distribuir actividades de acuerdo a la experticia del equipo.

Para el caso de los desarrolladores, el diagrama de componentes presenta la relación que debe existir entre las tareas que se le asignan como miembro del equipo de desarrollo, y sus compañeros, esto permite distinguir las responsabilidades de cada individuo como miembro del todo, restricciones, dependencia entre componentes, datos que son compartidos entre las funcionalidades de cada componente entre otros.

## Correspondence rules <a name="correspondence-rules-development"></a>

* R1: Los módulos presentados en el diagrama de componentes serán desplegados en nodos del diagrama de despliegue.
por lo anterior debe existir 2 nodos, Pruebas y Producción, para el caso de desarrollo corresponde al ambiente local de los programadores, pruebas será desplegado de manera independiente a producción, y si y sólo si sera puesto en producción aquellos componentes y/o paquetes que han sido probados por desarrolladores, testers y usuarios finales.

* R2: Las bases de datos estarán en 2 nodos, manejando dos ambientes producción y para el caso de desarrollo y pruebas la base de datos sera compartida.

* R3: Debe existir un solo repositorio para el versionamiento del código el cual será  desplegado en un nodo descrito en el diagrama de despliegue.

## Sources <a name="sources-development"></a>

[Table of contents](#table-of-contents-vp)

<!-- Fin de viewpoint de desarrollo -->

<!-- Inicio de viewpoint Fisica -->

## Physical viewpoint <a name="physical-viewpoint"></a>

El viewpoint Fisico describe los requerimientos no funcionales del sistema, en este apartado encontrará los concerns que enmarcan el punto de Vista, los tipos de modelos incluidos y convenciones que permiten un mejor entendimiento de la información que se presenta asi mismo el despliegue de componentes de Software sobre el hardware propuesto para las actividades.

## Overview <a name="overview-physical"></a>

El viewpoint de desarrollo se utiliza para describir la correlación de los módulos de software identificados en los requisitos detectados para la digitalización de los catálogos de ventas de los módulo de software sobre y el entorno de desarrollo del software.

## Framed concerns and typical stakeholders <a name="framed-concerns-and-typical-stakeholders-physical"></a>

El equipo de arquitectura asume la importancia de identificar las preocupaciones de Stakeholders y sus preocupaciones, por cuanto esto hace parte del análisis que permitirá abordar sus intereses y presentar una solución adecuada desde el punto de vista de Desarrollo, de tal forma que fuese posible tomar las decisiones necesarias y de esta manera ofrecer la solución que cubra las expectativas de los interesados.

### Concerns <a name="concerns-physical"></a>

A continuación se describe cada preocupación de las partes interesadas relacionadas con el Viewpoint Fisico, las preocupaciones identificadas en esta sección son información esencial para que el arquitecto tome desiciones sobre la arquitectura fisica del sistema que favorezcan la disponibilidad, confiabilidad, rendimiento y escalabilidad.

* [CNR-002](#CNR-002) - Disponibilidad "Availability": Que el sistema sea accesible dentro y fuera de las instalaciones de la compañía, esta preocupación dentro del analisis permitirá que se construya un sistema que en adelante permitirá a los vendedores gestionar sus ventas desde diferentes ubiciaciones, ahora durante las visitas se llevará a cabo presentación de catálogos para que el cliente este en la capacidad de seleccionar productos y proceder con la compra.  

* [CNR-003](#CNR-003) - Reacción al cambio "Escalabilidad": Dada su efectividad se espera ser implementada en los 85 países donde se tiene presencia comercial, la intención para esta preocupación debe ser la implementación una arquitectura que permita implementar la solución en diferentes tipos de dispositivos, para la empresa es importante crecer, lo que significa que los componentes y paquetes desarrollados deben ser altamente cohesionados y su nivel  de acoplamiento debe ser mínimo. 

* [CNR-006](#CNR-006) - Rendimiento: Desempeño del aplicativo, para la empresa es importante ampliar sus posibilidades de consulta y procesamiento de datos, es por ello que para el arquitecto debe ser importante diseñar una arquitectura que cumpla con las expectativas de la empresa, definir los estilos, patrones de diseño y técnicas a emplear importante, ya que a futuro las implementaciones de arquitectura repercuten en el correcto funcionamiento de características y requerimientos funcionales. 

* [CNR-010](#CNR-010) - Estructura de información: Presentar la información en los catálogos de acuerdo a roles de usuarios, asi mismo niveles de accesos y privilegios de perfil, solo quien cuente con el nivel y perfil de acceso y edición de información deberia poder hacerlo, esto aporta en temas de seguridad y confianza de la información contenida en los repositorios.

### Typical stakeholders <a name="typical-stakeholders-physical"></a>

Las partes interesadas para esta vista incluyen a los integrantes del equipo de desarrollo responsables de la construcción de software y sus descripciones Una vez revisada la tabla No 1, se identifican 3 Stakeholders para el viewpoint de fisico.

* [STK-002](#STK-002) - Equipo comercial: Personal que apoya el proceso de ventas
* [STK-003](#STK-003) - Equipo de mercadeo: Personal encargado de definir estrategias de mercadeo y diseño de catálogos
* [STK-004](#STK-004) - Equipo técnico: Expertos en cosmetología, apoyan el proceso de definición de los catálogos

Tabla No 4 Catálogo de Stakeholder Viewpoint fisico

## Model kinds+ <a name="model-kinds-physical"></a>

* [MOD-001](#MOD-001) - Modelo de despliegue

__Subset of metamodel elements__

* Artefacto
* Asociación
* Componente
* Dependencia
* Interfaz
* Nodo
* Estereotipo

## Deployment model <a name="deployment-model"></a>

En esta sección se describe el diagrama de despliegue que será empleado para describir la solución propuesta para la empresa “K”.

### Deployment model conventions <a name="deployment-model-conventions"></a>

El diagrama de despliegue empleado para describir la vista fisica está formado por los siguients elementos: Artefacto, Asociación, Componente, Dependencia, Interfaz, Nodo, Estereotipo

__Artefacto:__ Un producto desarrollado por el software, representado por un rectángulo con el nombre y la palabra "artefacto" encerrado por flechas dobles.

![alt text][fig6]

Figura 6: Artefacto

__Asociación:__ Una línea que indica un mensaje u otro tipo de comunicación entre nodos.

![alt text][fig7]

Figura 7: Asociación

__Componente:__ Representa una unidad lógicas del sistema, se grafica como un rectángulo con un rectángulo más pequeño en la esquina superior derecha con pestañas o la palabra escrita encima del nombre del componente.

Puede representar dos tipos de elementos: componentes lógicos (componentes de negocio o proceso) o componentes físicos (como componentes .NET, EJB).

![alt text][fig8]

Figura 8: Componente


__Dependencia:__ Una línea discontinua que termina en una flecha, que indica que un nodo o componente depende de otro.

![alt text][fig9]

Figura 9: Dependencia

__Interfaz:__ Representa la zona del módulo que es utilizada para la comunicación con otro de los componentes está compuesta generalmente por una relación de Proveedor y consumidor de un servicio que es expuesto mediante un contrato.

![alt text][fig10]

Figura 10: Interfaz

__Nodo:__ Un objeto de hardware o software, mostrado por un cuadro tridimensional.

![alt text][fig11]

Figura 11: Nodo

__Estereotipo:__ Un dispositivo contenido dentro del nodo, presentado en la parte superior del nodo, con el nombre entre flechas dobles a manera de corchetes.

![alt text][fig12]

Figura 12: Estereotipo

## Operations on views+ <a name="operations-on-views-physical"></a>

Operations define the methods to be applied to views and their models. Types of operations include:

* __Construction method:__ Este tipo de modelos se construye implementando nodos relacionados entre si, en la mayoria de los casos existen nodos de aplicaciones, bases de datos, almacenamiento masivo, terminales de usuario final entre otros.

  Al interior de los Nodos existiran componentes que en algunos casos tendran relación de dependencia para los casos en que un paquete requiera de la funcionalidad de otro paquete para su correcto empleo.

* __Analysis method:__ Para el arquitecto el diagrama de despliegue le permite conocer un plano general de la distribucion de la aplicación, bases de datos y otros componentes en la infraestructura (Hardware), ahora bien existen tecnologías que permiten virtualizar el despliegue y para este caso el diagrama es el mismo, este tipo d diagramas hace posible que identificar las necesidades de hardware para el dspliegue, generar solicitudes de equipos, requerimientos de configuración, permisos de seguridad y configuraciones de red.

Para el caso del personal de infraestructura, el diagrama de componentes les permitirá tener claro el panorama de despliegue y uso de equipos, asi mismo le permite identificar la necesidad de asignacion de recursos, memoria, disco, equipos fisicos, servicios virtuales, responsables y despliegue de aplicaciones en la infraestructura de la organización.

## Correspondence rules <a name="correspondence-rules-physical"></a>

* R1: Los módulos presentados en el diagrama de componentes serán desplegados en nodos del diagrama de despliegue.
por lo anterior debe existir 2 nodos, Pruebas y Producción, para el caso de desarrollo corresponde al ambiente local de los programadores, pruebas será desplegado de manera independiente a producción, y si y sólo si sera puesto en producción aquellos componentes y/o paquetes que han sido probados por desarrolladores, testers y usuarios finales.

* R2: Las bases de datos estarán en 2 nodos, manejando dos ambientes producción y para el caso de desarrollo y pruebas la base de datos sera compartida.

* R3: Debe existir un solo repositorio para el versionamiento del código el cual será  desplegado en un nodo descrito en el diagrama de despliegue.

## Sources <a name="sources-physical"></a>

[Table of contents](#table-of-contents-vp)

<!-- Fin de viewpoint Fisica -->



<!-- Inicio de viewpoint Procesos -->

## Process viewpoint <a name="process-viewpoint"></a>

La arquitectura de procesos nos muestra los procesos que hay en el sistema de la empresa K, y la forma en la que se comunican estos procesos, el flujo de trabajo paso a paso del negocio de catálogos de productos, la forma de expresar este flujo de los componentes del sistema se muestran en un diagrama de actividades UML.

La arquitectura de procesos tiene en cuenta algunos requisitos no funcionales como el rendimiento y la disponibilidad, y tiene en cuenta las principales abstracciones de la vista lógica. Los procesos representan el nivel en el que la arquitectura del proceso puede controlarse tácticamente, es decir, iniciar,recuperarse, configurarse y cerrarse.


## Overview <a name="overview-process"></a>

El viewpoint de procesos nos muestra el detalle de comunicación y flujo de procesos de trabajo que se ejecutan en el sistema de catálogos de productos de la empresa K, en este viewpoint brindaremos las vistas y modelos que nos ayudan a entender cómo funciona cada proceso, que entradas y salidas se obtienen durante el flujo.

## Framed concerns and typical stakeholders <a name="framed-concerns-and-typical-stakeholders-process"></a>

Para el tema de procesos, los equipos de comercial, mercadeo y técnicos de cosméticos, son los responsables de que un proceso en gestión de catálogos y gestión de manuales se cumpla de manera correcta, por este motivo, en esta vista se ofrece buscar un flujo de la mejor manera dentro del sistema de ventas, para ayudar así a los equipos mencionados con sus responsabilidades.


### Concerns <a name="concerns-process"></a>

Aquí se describen las preocupaciones de los stakeholder relacionados con el viewpoint de procesos.

* [CNR-001](#CNR-001): Usabilidad: Se busca contar con una herramienta de vanguardia que ofrezca una buena experiencia de usuario, esta preocupación se encuentra asociada al equipo comercial ya que en su día a día utilizan la herramienta y un sistema fácil e intuitivo para mostrar los catálogos al usuario final.

* [CNR-006](#CNR-006): Desempeño del sistema, el aplicativo debe tener un desempeño rápido y óptimo, debido a que se necesita consultar y gestionar los catálogos para mostrar al usuario final, y debe ser una consulta rápida y óptima, esta preocupación está relacionada con equipo comercial, equipo de mercadeo y equipo tecnico.

* [CNR-007](#CNR-007): Actualizar sus recursos comerciales, se necesita actualizar los productos en los catálogos, el sistema debe tener la capacidad para modificar los catálogos de manera fácil, esta preocupación está relacionada con el área comercial y mercadeo.

* [CNR-008](#CNR-008):  Aumentar la efectividad del equipo comercial, teniendo un sistema que se pueda acceder desde cualquier dispositivo y que el mismo tenga agilidad y velocidad para gestionar los catálogos, el equipo comercial está relacionado a esta preocupación ya que busca aumentar su productividad con el nuevo sistema.



### Typical stakeholders <a name="typical-stakeholders-process"></a>

Las partes interesadas para esta vista incluyen a los integrantes del equipo de procesos responsables de la ejecucion de procesos y/o actividades del sistema de ventas.


* [STK-002](#STK-002) - Equipo comercial: Personal que apoya el proceso de ventas
* [STK-003](#STK-003) - Equipo de mercadeo: Personal encargado de definir estrategias de mercadeo y diseño de catálogos
* [STK-004](#STK-004) - Equipo técnico: Expertos en cosmetología, apoyan el proceso de definición de los catálogos

Tabla No 4 Catálogo de Stakeholder Viewpoint fisico

## Model kinds+ <a name="model-kinds-process"></a>

* [MOD-006](#MOD-006) - Modelo de actividades 

__Subset of metamodel elements__

* Actividad
* condición 
* Marcos de responsabilidad  


## Activities model <a name="Activities-model"></a>

En este viewpoint se realiza el diagrama de Actividades uml que es lo recomendada de acuerdo a lo que menciona Philippe Kruchten en la vista de procesos.

Un diagrama de actividades ilustra la naturaleza dinámica de un sistema mediante el modelado del flujo ocurrente de actividad en actividad. Una actividad representa una operación en alguna clase del sistema y que resulta en un cambio en el estado de un sistema.


### Activities model conventions <a name="activities-model-conventions"></a>


__Actividad:__ 

![alt text][fig13]

Figura 13: Actividad

__Estados:__ 

![alt text][fig14]

Figura 14: Estados

__Ramificacion:__ 

![alt text][fig15]

Figura 15: Ramificacion 

__Sincronizacion:__ 

![alt text][fig16]

Figura 16: Sincronizacion 

__Marcos de Responsabilidad:__ 

![alt text][fig17]

Figura 16: Marcos de Responsabilidad 



* __Construction Method:__ 

Este tipo de modelos se construye estableciendo marcos de responsabilidad, en estos marcos incluimos las tareas y relación entre ellas, incluimos rombos que significan ciclos de decisión en caso de que se necesiten y un inicio y fin del flujo de trabajo. 

* __Analysis method:__ 

En la arquitectura de procesos, es indispensable mostrar el flujo de cada proceso, estos los representamos en un diagrama de actividades, y se muestra el flujo y estados de estas actividades, las mismas siempre están asociadas a responsables. Con este diagrama el arquitecto puede encontrar qué procesos deben ejecutarse en el sistema y de qué manera deben realizar su flujo.

## Correspondence rules <a name="correspondence-rules-process"></a>

* R4: Los procesos presentados en el diagrama de actividades serán desplegados en 3 marcos de responsabilidad, estos son los stakeholder que intervienen con los procesos, cada actividad mostrada en el diagrama tiene interaccion con sus responsables y se muestra el flujo de cada actividad para asi entender que secuencia, entradas y salidad tiene en el sistema de ventas.

## Sources <a name="sources-procesos"></a>

referencias: 
Architectural Blueprints—The “4+1” View
Model of Software Architecture Philippe Kruchten
Rational Software Corp.


[Table of contents](#table-of-contents-vp)

<!-- Fin de viewpoint procesos -->

<!-- Inicio de viewpoint logico -->

## Logic viewpoint <a name="logical-viewpoint"></a>

El viewpoint logico describe la estructura y funcionalidad que el sistema proporciona a los usuarios finales,  los requerimientos y preocupaciones del equipo comercial (vendedores), el equipo de mercadeo(Profesional de mercadeo) y al cliente final, en esta apartado encontrará los concerns que enmarcan el punto de Vista, los tipos de modelos incluidos y convenciones que permiten un mejor entendimiento de la información que se presenta.

## Overview <a name="overview-logical"></a>

El viewpoint logico se utiliza para describir la relacion e interaccion entre los diferentes entes que intervienen en el proceso. 

## Framed concerns and typical stakeholders <a name="framed-concerns-and-typical-stakeholders-logical"></a>

El equipo de arquitectura asume la importancia de identificar las preocupaciones de Stakeholders y sus preocupaciones, por cuanto esto hace parte del análisis que permitirá abordar sus intereses y presentar una solución adecuada desde el punto de vista Logica, de tal forma que fuese posible tomar las decisiones necesarias y de esta manera ofrecer la solución que cubra las expectativas de los interesados.

### Concerns <a name="concerns-logical"></a>

A continuación se describe cada preocupación de las partes interesadas relacionadas con el Viewpoint Logico, las preocupaciones identificadas en esta sección son información esencial para el arquitecto ya que le ayudan a identificar las partes invlolucradas y su interaccion.

* [CNR-001](#CNR-001) - Usabilidad:  Se busca contar con herramientas de vanguardia que ofrezca una buena experiencia de usuario, se encuentra asociada al equipo comercial quienes buscan una herramienta que les brinde agilidad en sus procesos y que permitan capturar al cliente en una experiencia agil y sencialla.

* [CNR-002](#CNR-002) - Availability "Disponibilidad": Que el sistema sea accesible dentro y fuera de las instalaciones de la compañía, el equipo comercial busca una herramienta que le permita presentar su catalogo comercial en el momento en que el o su cliente lo requieran sin importar el tipo de dispositivo desde el que se quiera presentar.

* [CNR-005](#CNR-005) - Modificabilidad: La modificabilidad se refiere al grado en que un sistema puede ser modificado efectiva o eficientemente sin introducir defectos o degradar la calidad del sistema existente, la herramienta desarrollada debe ser entendible para el equipo de mercadeo, al momento de crear modificar o gestionar catalogos de productos permitiendole manejar variedad de atributos sin requerir mayor esfuerzo.

* [CNR-006](#CNR-006) - Rendimiento: Desempeño del aplicativo, para la empresa es importante ampliar sus posibilidades de consulta y procesamiento de datos, para la aplicacion el crecimiento exponencial de la data respecto a productos, pedidos o clientes no debe representar un riesgo en la agilidad ni en su renderizado.  

### Typical stakeholders <a name="typical-stakeholders-development"></a>

Las partes interesadas para esta vista incluye a los integrantes del equipo de desarrollo responsables de la construcción de software y sus descripciones Una vez revisada la tabla No 1, se identifican 3 Stakeholders para el viewpoint logico.

* [STK-002](#STK-002) - Equipo comercial: Personal que apoya el proceso de ventas
* [STK-003](#STK-003) - Equipo de mercadeo: Personal encargado de definir estrategias de mercadeo y diseño de catálogos

Tabla No 4 Catálogo de Stakeholder Viewpoint de Desarrollo

## Model kinds+ <a name="model-kinds-development"></a>

* [MOD-003](#MOD-003) - Modelo de Clases
* [MOD-005](#MOD-005) - Modelo de secuencia

__Subset of metamodel elements__

* Clases
* Relaciónes
* Objetos
* Casillas de activacion
* Actores
* Pauqetes
* Linea de vida
* Simbolos


## Class model <a name="class-model"></a>

En esta sección se describe el diagrama de clases que será empleado para describir la solución propuesta para la empresa K.

### Class model conventions <a name="class-model-conventions"></a>

El diagrama de clases empleado para describir la vista de desarrollo está formado por dos elementos: Clases y Relaciónes.

__Clases:__ Representa una entidad del sistema, se grafica como un rectángulo con un rectángulo dividido en tres partes, a superior contiene el nombre de la clase, la central contiene los atributos y la inferior las acciones.

![alt text][figNL1-vp]

Figura NL1: Clase

__Relaciones:__ Las relaciones representan algun tipo de dependencia o relacion entre clases, se diferencian pos la forma de sus flechas.

__Composicion:__ Es un tipo especial de agregación que denota una fuerte posesión de la Clase “Todo”, a la Clase “Parte”. Se grafica con un rombo diamante relleno contra la clase que representa el todo.

![alt text][figNL2-vp]

Figura NL2: Composicion

__Agregacion:__ Es una relación en la que la Clase “Todo” juega un rol más importante que la Clase "Parte", pero las dos clases no son dependientes una de otra. Se grafica con un rombo diamante vacío contra la Clase “Todo”.

![alt text][figNL3-vp]

Figura NL3: Agregacion

__Herencia:__ Se refiere a una relación entre dos clases en donde una Clase “Específica” es una versión especializada de la otra, o Clase “General”.

![alt text][figNL4-vp]

Figura NL4: Herencia

__Dependencia:__ Representa un tipo de relación en la que una clase es instanciada.

![alt text][figNL5-vp]

Figura NL5: Dependencia

## Sequence model <a name="sequence-model"></a>

Mediante el uso de estos diagramas se espera mostrar en una linea de vida el estado del proceso, la linea de vida y mensajes intercambiados entre ellos, pretende presentar una visión más clara del sistema de información de la empresa K,   organizado en subsistemas y agrupando elementos para su análisis y mejor entendimiento así mismo se construyen dependencias entre paquetes, siendo una extensión del diagrama de clases y de componentes, la idea principal del diagrama es poder planificar y comprender la funcion detallada de un escenario.

### Sequence model conventions <a name="sequence-model-conventions"></a>

__Objetos:__ Representa una clase u objeto en UML. El símbolo objeto demuestra cómo se comportará un objeto en el contexto del sistema. Los atributos de las clases no deben aparecer en esta figura.

![alt text][figNL6-vp]

Figura NL6: Objeto

__Casilla de activacion:__ Representa el tiempo necesario para que un objeto finalice una tarea. Cuanto más tiempo lleve la tarea, más larga será la casilla de activación.

![alt text][figNL7-vp]

Figura NL7: Casilla de activacion

__Actor:__ Muestra entidades que interactúan con el sistema o que son externas al sistema.

![alt text][figNL8-vp]

Figura NL8: Actor

__Linea de vida:__ Representa el paso del tiempo a medida que se extiende hacia abajo. Esta línea vertical discontinua representa eventos secuenciales que le ocurren a un objeto durante el proceso graficado. Las líneas de vida pueden comenzar con una figura rectangular etiquetada o un símbolo de actor.

![alt text][figNL9-vp]

Figura NL9: Linea de vida

__Simbolos:__ Usa los siguientes símbolos de mensaje y flechas para indicar cómo se transmite la información entre objetos. Estos símbolos pueden reflejar el inicio y la ejecución de una operación o el envío y la recepción de una señal.

__Sincrónico:__ Este símbolo se utiliza cuando un remitente debe esperar una respuesta a un mensaje antes de proseguir. El diagrama debe mostrar el mensaje y la respuesta.

![alt text][figNL10-vp]

Figura NL10: Símbolo de mensaje sincrónico



## Operations on views+ <a name="operations-on-views-logical"></a>

Operations define the methods to be applied to views and their models. Types of operations include:

* __Construction method:__ Este tipo de modelos se construye implementando clases relacionanda que representan entidades o stakeholders del proceso, los cuales tener caracteristicas basicas que los identifiquen junto con metodos u acciones que me permitar trasar una ruta interactiva entre las diferentes clases llevar un estereotipo que los identifique, cada componente dentro del diagrama puede contener clases e interfaces.

  De la misma manera pueden interactuar en el diagrama de seguencia ya identificando que clases u objetos intractuan con otros. 

  Existe una interaccion entre minimo dos clases u objetos donde un objeto hace una peticion y de alguna manera obtiene una respuesta de vuelta.. 

* __Analysis method:__ Para el arquitecto, el equipo y demas stakeholders que intervienen en este viewpoint el diagrama de clases y secuencias les permite visualizar de manera comprencible la forma en que los diferentes componentes, objetos u clases se comunicaran, ademas podran ver el flujo que trasa dichas interacciones.

Para el caso de los comerciales y profesionales de mercadeo, los diagramas les permiten ver la trasa de las actividades que tiene el proceso permitiendo identificar las responsabilidades de sus alternos.

## Correspondence rules <a name="correspondence-rules-logical"></a>

* R5: Las interacciones identificadas en el diagrama de clases representan las relaciones y acciones que se representan en el diagrama de secuencia.

* R6: Los actores del diagrama de casos de uso se identifican como clases en el diagrama de clases

* R7: Las clases del diagrama de clase se entiene como objetos de interaccion en el diagrama de secuencia


## Sources <a name="sources-logical"></a>

[Table of contents](#table-of-contents-vp)

<!-- Fin de viewpoint logico -->



<!-- Inicio de viewpoint Escenarios -->

## Escenarios viewpoint <a name="escenarios-viewpoint"></a>

El viewpoint de escenarios hace una abstracción de los requerimientos, mostrando cómo el sistema será operado con una descripción de las acciones y los procesos que se esperan del sistema, para las necesidades de los diferentes involucrados o stakeholders.


## Overview <a name="overview-escenarios"></a>

El viewpoint de escenarios se utiliza para tener un primer bosquejo general de lo que se espera del desarrollo en una solución, la primera interpretación que se le pueden dar a los requerimientos se logra mediante la identificación de cada una de sus partes, los diferentes procesos, sus interesados y funcionalidades.

al documentar los requerimientos desde la perspectiva del usuario tenemos la capacidad de identificar las necesidades individuales de cada uno.


## Framed concerns and typical stakeholders <a name="framed-concerns-and-typical-stakeholders-escenarios"></a>

Por medio del análisis de los requerimientos y mediante el viewpoint de escenarios el equipo de earquitectura espera enmarcar adecuadamente la arquitectura de la empresa K para ello se  identifican las preocupaciones de los stakeholders que tienen interés en el sistema y en el producto final. 


### Concerns <a name="concerns-escenarios"></a>

A continuación se describe cada preocupación de las partes interesadas relacionadas con el Viewpoint de Escenarios, las preocupaciones identificadas en esta sección son información esencial para el arquitecto ya que le ayudan a tener una perspectiva desde el punto de vista de cada uno de los diferentes stakeholders. s.

* [CNR-001]Usabilidad: Se busca contar con una herramienta de vanguardia que ofrezca una buena experiencia de usuario, dados los requerimientos iniciales se espera abarcar las necesidades de cada uno de los involucrado.

* [CNR-009](#CNR-009): Acceso a la información: Contar con la información necesaria en el momento adecuado, evitar complejidad en el flujo de la información haciendo procesos cortos y eficaces además de brindar la seguridad necesaria según sea la necesidad de los usuarios finales.


* [CNR-010](#CNR-010): Estructura de información: Administrar y presentar la información en los catálogos de acuerdo a la estrategia definida de manera que los diferentes usuarios finales disfruten de experiencia de usuario eficaz y entendibles.




### Typical stakeholders <a name="typical-stakeholders-process"></a>

Las partes interesadas para esta vista incluyen a los de actores responsables de la ejecucion de acciones o casos de uso del sistema de ventas.

* [STK-001](#STK-001) - Clientes
* [STK-002](#STK-002) - Equipo comercial: Personal que apoya el proceso de ventas
* [STK-003](#STK-003) - Equipo de mercadeo: Personal encargado de definir estrategias de mercadeo y diseño de catálogos
* [STK-004](#STK-004) - Equipo técnico: Expertos en cosmetología, apoyan el proceso de definición de los catálogos

Tabla No 4 Catálogo de Stakeholder Viewpoint fisico

## Model kinds+ <a name="model-kinds-process"></a>

* [MOD-007](#MOD-007) - Modelo de casos de uso 

__Subset of metamodel elements__

* Actores
* Casos de uso  
* Limite del sistema


## Casos de uso model <a name="casosdeuso-model"></a>

La vista de casos de uso captura la funcionalidad de un sistema, de un subsistema, o de una clase, tal como se muestra a un usuario exterior.

Aquí se especifican los requerimientos funcionales y damos una visión más clara de cada funcionalidad.


### Casos de uso model conventions <a name="casosdeuso-model-conventions"></a>


__Simbologia de Diagrama de casos de uso:__ 

![alt text][figES1-VP]

Caso de uso: Se representan con óvalos. La etiqueta en el óvalo indica la función del sistema.

Actor: Un diagrama de caso de uso contiene los símbolos del actor y del caso de uso, junto con líneas conectoras. Los actores son similares a las entidades externas; existen fuera del sistema. El término actor se refiere a un rol específico de un usuario del sistema.

Límite del sistema: Es el entorno en donde interactúan los casos de uso y acceso interno para los actores del sistema.

* __Construction Method:__ 

Este modelo lo realizamos estableciendo casos de uso y actores del sistema, entendiendo los requerimientos funcionales del sistema de ventas establecimos los casos de uso, e identificando los stakeholder pudimos relacionar los actores.  

* __Analysis method:__ 

Previamente se tuvieron que identificar los stakeholders, y como estos interactúan con los procesos del sistema de ventas, y analizando estos proceso y los requisitos de digitalizar catálogos, logramos establecer casos de uso que debe tener el sistema para funcionar de manera correcta, y esto unirlo en el diagrama de casos de uso.

## Correspondence rules <a name="correspondence-rules-process"></a>


## Sources <a name="sources-procesos"></a>

referencias: 
Architectural Blueprints—The “4+1” View
Model of Software Architecture Philippe Kruchten
Rational Software Corp.


[Table of contents](#table-of-contents-vp)

<!-- Fin de viewpoint Escenarios -->


[fig1]: /img/fig1-vp.png "Componente"
[fig2]: /img/fig2-vp.png "Interfaz"
[fig3]: /img/fig3-vp.png "Relación de dependencia"
[fig4]: /img/fig4-vp.png "Paquete"
[fig5]: /img/fig5-vp.png "Dependencia entre paquetes"
[fig6]: /img/fig6-vp.png "Diagrama de Componentes de aplicación"
[fig7]: /img/fig7-vp.png "Asociación"
[fig8]: /img/fig8-vp.png "Componente"
[fig9]: /img/fig9-vp.png "Dependencia"
[fig10]: /img/fig10-vp.png "Interfaz"
[fig11]: /img/fig11-vp.png "Nodo"
[fig12]: /img/fig12-vp.png "Estereotipo"
[fig13]: /img/fig13-proc-vp.png "Actividad"
[fig14]: /img/fig14-proc-vp.png "Estados"   
[fig15]: /img/fig15-proc-vp.png "Ramificacion"
[fig16]: /img/fig16-proc-vp.png "Sincronizacion"
[fig17]: /img/fig17-proc-vp.png "marcos de responsable"
[figNL1-vp]: /img/figLoN1-vp.png "Clase"
[figNL2-vp]: /img/figNoL2-vp.png "Composición"
[figNL3-vp]: /img/figNoL3-vp.png "Agregación"
[figNL4-vp]: /img/figNoL4-vp.png "Herencia"
[figNL5-vp]: /img/figNoL5-vp.png "Dependencia"
[figNL6-vp]: /img/figNoL6-vp.png "Objeto"
[figNL7-vp]: /img/figNoL7-vp.png "Casilla de activacion"
[figNL8-vp]: /img/figNoL8-vp.png "Actor"
[figNL9-vp]: /img/figNoL9-vp.png "Linea de vida"
[figNL10-vp]: /img/figNoL10-vp.png "Símbolo de mensaje sincrónico"
[figES1-VP]: /img/fig1ES-VP.png "Simbologia casos de uso"




