# Table of contents <a name="table-of-contents"></a>
1. [Introduction](#introduction)
    1. [Identifying information](#identifying-information)
    2. [Supplementary information](#supplementary-information)
    3. [Other information](#other-information)
        1. [Architecture evaluations](#architecture-evaluations)
        2. [Rationale for key decisions](#rationale-for-key-decisions)
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
        2. [Component model correspondence rules](#component-model-correspondence-rules)
    9. [Package model](#package-model)
        1. [Package model conventions](#package-model-conventions)
        2. [Package model correspondence rules](#package-model-correspondence-rules)
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
    3. [Correspondence rules](#correspondence-rules-ad)
6. [Architecture decisions and rationale](#architecture-decisions-and-rationale)
    1. [Decisions](#decisions)

# Introduction <a name="introduction"></a>
## Identifying information <a name="identifying-information"></a>
## Supplementary information <a name="supplementary-information"></a>
## Other information <a name="other-information"></a>
### Architecture evaluations <a name="architecture-evaluations"></a>
### Rationale for key decisions <a name="rationale-for-key-decisions"></a>

[Table of contents](#table-of-contents)

# Stakeholders and concerns <a name="stakeholders-and-concerns"></a>
## Stakeholders <a name="stakeholders"></a>

La siguiente tabla presenta, el catálogo de Stakeholders identificados dentro del problema, los cuales son identificados con un valor único, han sido descritos y se han relacionado sus preocupaciones principales de acuerdo a la actividad así:

| ID | Stakeholder | Descripción |
|---|---|---|
| STK-001 | Equipo de Gerencia | Equipo responsable de la dirección de la Compañía |
| STK-002 | Clientes | Potenciales consumidores |
| STK-003 | Equipo comercial | Personal que apoya el proceso de ventas |
| STK-004 | Equipo de mercadeo | Personal encargado de definir estrategias de mercadeo y diseño de catálogos |
| STK-005 | Equipo técnico | Expertos en cosmetología, apoyan el proceso de definición de los catálogos |
| STK-006 | Equipo de arquitectura | Encargados de diseñar implementar la mejor solución arquitectónica |
| STK-007 | Coordinador de proyectos | Responsable de liderar y presentar el proyecto al nivel directivo de la organización |
| STK-008 | Arquitecto de Software | Líder técnico del Equipo de desarrollo |
| STK-009 | Desarrollador | Responsable de la codificación del Aplicativo (Backend - Frontend) |
| STK-010 | Tester | Personal encargado de llevar a cabo las pruebas antes de salir a producción |

Tabla No 1 Catálogo de Stakeholder, Elaboración de los investigadores basada en Togaf 9.2 Diagrams, Catalog, Matrix

## Concerns <a name="concerns"></a>

Las Preocupaciones fueron discutidas en grupo, de tal forma que pudieran identificarse cuáles eran apropiados para el ejercicio, de esta manera llevar a cabo un análisis de información que permitirá mapearlos hacia los viewpoints que serán definidos.

| ID | Concern | Descripción |
|---|---|---|
| CNR-001 | Usabilidad | Se busca contar con herramientas de vanguardia que ofrezca una buena experiencia de usuario |
| CNR-002 | Disponibilidad (Availability) | Que el sistema sea accesible dentro y fuera de las instalaciones de la compañía |
| CNR-003 | Reacción al cambio "Escalabilidad" | Dada su efectividad se espera ser implementada en los 85 países donde se tiene presencia comercial |
| CNR-004 | Costos | Disminuir los recursos invertidos en procesos que pueden ser automatizados |
| CNR-005 | Definición de requerimiento | Recibir requerimientos de Calidad a tiempo |
| CNR-006 | Modificabilidad | La modificabilidad se refiere al grado en que un sistema puede ser modificado efectiva o eficientemente sin introducir defectos o degradar la calidad del sistema existente. |
| CNR-007 | Rendimento | Desempeño del aplicativo |
| CNR-008 | Modernización | Actualizar sus recursos comerciales |
| CNR-009 | Efectividad | Aumentar la efectividad del equipo comercial |
| CNR-010 | Acceso a la información | Contar con la información necesaria en el momento adecuado |
| CNR-011 | Estructura de información | Administrar y presentar la información en los catálogos de acuerdo a la estrategia definida |
| CNR-012 | Estandarización del desarrollo | La metodología de desarrollo que se emplea debe ser Scrum, debe desarrollarse empleando lenguaje de programación Java Spring boot, vista en Angular última versión y base de datos Oracle 12c |
| CNR-013 | Estandarización del Código | No debería haber código sin optimizar, se debe versionar el mismo, empleando git y Gogs como repositorio del mismo, se manejara el estándar de Java para el desarrollo (Nombres de Clases, Métodos, Comentar el código) |
| CNR-014 | Estandarización de las Pruebas | Debe existir un claro proceso de pruebas, esto debe incluir, punto de partida, componentes a estudiar, recomendaciones para desarrolladores, así mismo el personal responsable de la pruebas debe ser personal técnico que cuente con la experiencia en pruebas y validación de componentes desarrollados. |
| CNR-015 | Estandarización del Diseño | Se emplearán y documentaran los patrones de diseño empleado para el desarrollo del aplicativo, no debe existir desarrollo que no tenga documentación, así mismo debe existir un repositorio para persistir la documentación del proyecto. |

Tabla No 2 Catálogo de Preocupaciones, Elaboración de los investigadores basada en Togaf 9.2 Diagrams, Catalog, Matrix

## Concern–Stakeholder Traceability <a name="concern–stakeholder-traceability"></a>

La matriz de trazabilidad de Stakeholders versus preocupaciones nos permite analizar sobre que interesado se identifica con qué preocupación además de ello cuales son común a varios interesados y cuales se presentan en menor cantidad entre los Stakeholders.

| Stakeholders vs 
Concerns
 | CNR-001 | CNR-002 | CNR-003 | CNR-004 | CNR-005 | CNR-006 | CNR-007 | CNR-008 | CNR-009 | CNR-010 | CNR-011 | CNR-012 | CNR-013 | CNR-014 | CNR-015 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|


[Table of contents](#table-of-contents)

# Viewpoints+ <a name="viewpoints"></a>
## Development viewpoint <a name="development-viewpoint"></a>
## Overview <a name="overview-development"></a>
## Framed concerns and typical stakeholders <a name="framed-concerns-and-typical-stakeholders-development"></a>
### Concerns <a name="concerns-development"></a>
### Typical stakeholders <a name="typical-stakeholders-development"></a>
## Model kinds+ <a name="model-kinds"></a>
## Component model <a name="component-model"></a>
### Component model conventions <a name="component-model-conventions"></a>
### Component model correspondence rules <a name="component-model-correspondence-rules"></a>
## Package model <a name="package-model"></a>
### Package model conventions <a name="package-model-conventions"></a>
### Package model correspondence rules <a name="package-model-correspondence-rules"></a>
## Operations on views+ <a name="operations-on-views-component"></a>
## Correspondence rules <a name="correspondence-rules-component"></a>
## Sources <a name="sources-development"></a>

[Table of contents](#table-of-contents)

# Views+ <a name="views"></a>
Some introduction text, formatted in heading 2 style

[Table of contents](#table-of-contents)

# Consistency and correspondences <a name="consistency-and-correspondences"></a>
Some introduction text, formatted in heading 2 style

[Table of contents](#table-of-contents)

# Architecture decisions and rationale <a name="architecture-decisions-and-rationale"></a>
Some introduction text, formatted in heading 2 style

[Table of contents](#table-of-contents)

## Decisions <a name="decisions"></a>
The second paragraph text 

[Table of contents](#table-of-contents)
