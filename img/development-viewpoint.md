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

En esta sección se describe el diagrama de componentes de software que será empleado para describir la solución propuesta para la empresa K.

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

Figura 5: Paquete

__Dependencias entre paquetes:__ Existe una dependencia cuando un elemento de un paquete requiere de otro que pertenece a un paquete distinto. Las dependencias se representan con una flecha discontinua con inicio en el paquete que depende del otro.

![alt text][fig6]

Figura 6: Dependencia entre paquetes

## Operations on views+ <a name="operations-on-views-component"></a>

Operations define the methods to be applied to views and their models. Types of operations include:

* __Construction method:__ Este tipo de modelos se construye implementando componentes, los cuales deben llevar un estereotipo que los identifique, cada componente dentro del diagrama puede contener clases e interfaces.

  Así mismo pueden ser implementados por otros paquetes mediante el uso de interfaces que permiten exponer servicios y su consumo. 

  Debe existir relación de dependencia para los casos en que un paquete requiera de la funcionalidad de otro paquete para su correcto empleo. 

* __Analysis method:__ Para el arquitecto el diagrama de componentes le permite conocer un plano general de la aplicación, la relación entre módulos y sus dependencias, de tal manera que sea posible identificar las tareas de desarrollo que debe asignar al equipo, los estilos de arquitectura, patrones de diseño y distribuir actividades de acuerdo a la experticia del equipo.

  Para el caso de los desarrolladores, el diagrama de componentes presenta la relación que debe existir entre las tareas que se le asignan como miembro del equipo de desarrollo, y sus compañeros, esto permite distinguir las responsabilidades de cada individuo como miembro del todo, restricciones, dependencia entre componentes, datos que son compartidos entre las funcionalidades de cada componente entre otros.

## Correspondence rules <a name="correspondence-rules-component"></a>

* R1: Los módulos presentados en el diagrama de componentes serán desplegados en nodos del diagrama de despliegue.
por lo anterior debe existir 2 nodos, Pruebas y Producción, para el caso de desarrollo corresponde al ambiente local de los programadores, pruebas será desplegado de manera independiente a producción, y si y sólo si sera puesto en producción aquellos componentes y/o paquetes que han sido probados por desarrolladores, testers y usuarios finales.

* R2: Las bases de datos estarán en 2 nodos, manejando dos ambientes producción y para el caso de desarrollo y pruebas la base de datos sera compartida.

* R3: Debe existir un solo repositorio para el versionamiento del código el cual será  desplegado en un nodo descrito en el diagrama de despliegue.

## Sources <a name="sources-development"></a>

[Table of contents](#table-of-contents)

<!-- Fin de viewpoint de desarrollo -->

<!-- Inicio de viewpoint Fisica -->

## Physical viewpoint <a name="development-physical"></a>

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

## Model kinds+ <a name="model-kinds"></a>

* [MOD-001](#MOD-001) - Modelo de despliegue

__Subset of metamodel elements__

* Artefacto
* Asociación
* Componente
* Dependencia
* Interfaz
* Nodo
* Estereotipo

## Component model <a name="component-model"></a>

En esta sección se describe el diagrama de despliegue que será empleado para describir la solución propuesta para la empresa “K”.

### Component model conventions <a name="component-model-conventions"></a>

El diagrama de despliegue empleado para describir la vista fisica está formado por los siguients elementos: Artefacto, Asociación, Componente, Dependencia, Interfaz, Nodo, Estereotipo

__Artefacto:__ Un producto desarrollado por el software, representado por un rectángulo con el nombre y la palabra "artefacto" encerrado por flechas dobles.

__Asociación:__ Una línea que indica un mensaje u otro tipo de comunicación entre nodos.

__Componente:__ Representa una unidad lógicas del sistema, se grafica como un rectángulo con un rectángulo más pequeño en la esquina superior derecha con pestañas o la palabra escrita encima del nombre del componente.

Puede representar dos tipos de elementos: componentes lógicos (componentes de negocio o proceso) o componentes físicos (como componentes .NET, EJB).

![alt text][fig2]

Figura 2: Componente


__Dependencia:__ Una línea discontinua que termina en una flecha, que indica que un nodo o componente depende de otro.


__La interfaz:__ Representa la zona del módulo que es utilizada para la comunicación con otro de los componentes está compuesta generalmente por una relación de Proveedor y consumidor de un servicio que es expuesto mediante un contrato.

![alt text][fig3]

Figura 3: Interfaz

__Nodo:__ Un objeto de hardware o software, mostrado por un cuadro tridimensional.


__Estereotipo:__ Un dispositivo contenido dentro del nodo, presentado en la parte superior del nodo, con el nombre entre flechas dobles a manera de corchetes.


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

[Table of contents](#table-of-contents)

<!-- Fin de viewpoint Fisica -->

# Views+ <a name="views"></a>

<!-- Inicio de view development -->
## Development  view <a name="development -view"></a>

A continuación se describe la vista de desarrollo los modelos de componentes y paquetes.

### Models+ <a name="models-development -view"></a>
### Components <a name="models-component-development-view"></a>

![alt text][fig7]

Figura 7: Diagrama de Componentes de aplicación

### Package <a name="models-package-development-view"></a>

El objetivo del diagrama es obtener una visión más clara del sistema de información orientado a objetos, organizándolo en subsistemas, agrupando los elementos de análisis, diseño y construcción detallando las relaciones de dependencia entre ellos.

El diagrama de paquetes y sus dependencias, son elementos de los diagramas de casos de uso y de componentes de nuestro sistema.

![alt text][fig8]

Figura 8: Diagrama de paquetes

### Known Issues with View <a name="issues-with-development-view"></a>

Documente cualquier discrepancia entre la vista y sus convenciones de puntos de vista. Cada vista de arquitectura debe cumplir con las convenciones de su punto de vista de arquitectura de gobierno. Los problemas conocidos pueden incluir: inconsistencias elementos a completar, problemas abiertos o no resueltos, excepciones y desviaciones de las convenciones establecidas por el punto de vista. Los asuntos abiertos pueden llevar a tomar decisiones. Las excepciones y desviaciones pueden documentarse como resultados de decisión y justificación.

[Table of contents](#table-of-contents)

<!-- Fin de view development -->

<!-- Inicio de view Fisica -->
## Physical  view <a name="physical-view"></a>

Descripción de la vista de fisica empleada, presentando el modelo de despliegue

### Models+ <a name="models-physical-view"></a>

### Components <a name="models-component-physical-view"></a>

El diagrama de despliegue describe la implementación física de la información generada por el programa de software en los componentes de hardware. La arquitectura presentada en capas, es la que ofrece mayor rendimiento en cumplimiento con las preocupaciones de stakeholders, respecto CNR-002 Disponibilidad "Availability", CNR-003 - Reacción al cambio "Escalabilidad", CNR-006 - Rendimiento: Desempeño del aplicativo, CNR-010 - Estructura de información.

Como se evidencia en la Figura 10, los se especifican 3 ambientes Desarrollo, Pruebas y Producción, este último es independiente mientra desarrollo y pruebas comparten base de datos lo cual optimiza recursos. 

![alt text][fig10]

Figura 10: Diagrama de Despliegue de aplicación en ambiente productivo

![alt text][fig10]

Figura 11: Diagrama de Despliegue de aplicación desarrollo y pruebas 

### Known Issues with View <a name="issues-with-physical-view"></a>

La empresa no cuenta con equipos de seguridad que permitan implementar medidas de seguridad de los servicios que se exponen y los equipos donde se encuntran desplegados. 


[Table of contents](#table-of-contents)

<!-- Fin de view Fisica -->