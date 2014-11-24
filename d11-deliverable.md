# Use cases and data specified, data modelled and prepared

Deliverable 1.1

## Document History


| Ver. | Name            | Date        | Remark                              |
|------|-----------------|-------------|-------------------------------------|
| v0.1 | Adrian Gschwend | 24.11.2014  | Created initial structure           |

## Documentation Information


* *Deliverable Nr Title*: D1.1 Use cases and data specified, data modelled and prepared
* *Lead*: Adrian Gschwend (BUAS)
* *Authors*: Adrian Gschwend (BUAS)
* *Publication Level*: Public

### Document Context Information

* *Project (Title/Number)*: Fusepool P3 (609696)
* *Work Package / Task*: WP1 / T1.1, T1,2, T1,3, T1.4
* *Responsible person and project partner*: Adrian Gschwend (BUAS)


### Quality Assurance / Review

* XXX
* YYY


### Official Citation

Fusepool-P3-D1.1

### Copyright

This document contains material, which is the copyright of certain
Fusepool P3 consortium parties.

This work is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/.

## Executive Summary

The goal of Fusepool P3 project is to make publishing and processing of public data as linked data easy. For this purpose Fusepool P3 develops a set of software components that integrate seamlessly by well defined APIs basing on Linked Data Best Practices and the Linked Data Platform standard.

TODO Anpassung an hier

The Fusepool P3 process is divided in the following four steps: exploration, extraction, enrichment and delivery. The software provides tools for the last 3 steps:

 * Extraction: Data from various sources and formats is transformed to RDF and thus made usable in the Linked Open Data (LOD) Cloud.
 * Enrichment: Entity recognition, Natural Language Processing (NLP), Interlinking as well as human processing such as by Crowdsourcing allow to enrich the available data increasing its value to its and to application builders.
 * Delivery: The actual delivery of the data can be separated into making it available via Linked Data standards and the actual presentation to the user with apps running on desktops and mobile devices.

This document describes the TODO.

## Acronyms and Abbreviations

| Acronym |                 Description                  |
|---------|----------------------------------------------|
| ACL     | Access Control List                          |
| API     | Application Programming Interface            |
| BUAS    | Bern University of Applied Sciences          |
| CKAN    | Comprehensive Knowledge Archive Network      |
| ETL     | Extract, Transform, Load                     |
| FP3     | Fusepool P3                                  |
| GIS     | Geographic information system                |
| HTTP    | Hypertext Transfer Protocol                  |
| HTTPS   | Secure Hypertext Transfer Protocol           |
| IRI     | Internationalized Resource Identifier        |
| LDP     | Linked Data Platform                         |
| LDP-BC  | Linked Data Platform Basic Container         |
| LDPC    | Linked Data Platform Container               |
| LDP-DC  | Linked Data Platform Direct Container        |
| LDP-IC  | Linked Data Platform Indirect Container      |
| LDP-NR  | Linked Data Platform Non-RDF Source          |
| LDPR    | Linked Data Platform Resource                |
| LDP-RS  | Linked Data Platform RDF Source              |
| PAT     | Provincia Autonoma di Trento                 |
| POI     | Point of interest                            |
| RDF     | Resource Description Framework               |
| RDFS    | RDF Schema                                   |
| REST    | Representational State Transfer              |
| RET     | Regione Toscana                              |
| SPARQL  | SPARQL Protocol and RDF Query Language       |
| SQL     | Structured Query Language                    |
| URI     | Uniform Resource Identifier                  |
| URL     | Uniform Resource Locator                     |
| W3C     | World Wide Web Consortium                    |
| WG      | Working Group                                |
| WP      | Work Package                                 |

## Normative namespaces

In this document the prefixes used in [CURIEs](http://www.w3.org/TR/curie/) shall refer the following
IRI prefixed:


| Prefix | Namespace|
|--------|----------|
| rdf    | [http://www.w3.org/1999/02/22-rdf-syntax-ns\#](http://www.w3.org/1999/02/22-rdf-syntax-ns) |
| rdfs   | [http://www.w3.org/2000/01/rdf-schema\#](http://www.w3.org/2000/01/rdf-schema) |
| xsd    | [http://www.w3.org/2001/XMLSchema\#](http://www.w3.org/2001/XMLSchema)  |
| dct    | [http://purl.org/dc/terms/](http://purl.org/dc/terms/) |
| oa     | [http://www.w3.org/ns/oa\#](http://www.w3.org/ns/oa#) |
| ldp    | [http://www.w3.org/ns/ldp\#](http://www.w3.org/ns/ldp#) |
| fp3    | [http://vocab.fusepool.info/fp3\#](http://vocab.fusepool.info/fp3#) |
| eldp   | [http://vocab.fusepool.info/eldp\#](http://vocab.fusepool.info/eldp#) |
| trans  | [http://vocab.fusepool.info/transformer\#](http://vocab.fusepool.info/transformer#) |
| fam    | [http://vocab.fusepool.info/fam\#](http://vocab.fusepool.info/fam#) |
| schema    | [http://schema.org/](http://schema.org/) |



## Introduction

This document describes the TODO

The main goal of the Fusepool P3 architecture is to provide interaction protocols and pattern so that the components can be used in concert to form the Fusepool P3 Platform.

### Use case summary

The Fusepool P3 project partners Provincia Autonoma di Trento and Regione Toscana have been publishing Open Data and develop apps in the domain of tourism for several years. During this time both partners gained valuable experience in data creation, maintenance and publication. 

Many of the published Open Data sets are used in Android or iOS apps aimed at tourists and/or inhabitants of the region. Some of them are written by the project partners, other apps by 3rd party developers which integrate parts of the published Open Data into their own apps.

As of today the data is mainly available in particular data formats like CSV, KML, XML and JSON. App developers need to download the raw data and process it using their own ETL (Extract, Transform, Load) processes. With every update of the raw data this process has to be triggered for every single application where it is used. If the format of the raw data changed, the process has to be adjusted and cannot be automated. With every new data source, maintenance complexity of these Open Data sets and its apps increases.

Linked Data can help to solve these problems: Data is made available in a standard format (RDF) which provides among others the following benefits[[1]](#ftnt1):

-   Every piece of information (data) has its own identifier (URI/IRI).
-   Those identifiers can be resolved via the web (HTTP),
-   which acts as a generalized API for developers.
-   Standardized vocabularies describe the meaning of the data,
-   and allow to relate information with each other.

The Linked Data technology stack [Bizer2009] provides many ways to interact with data in RDF format [Cyganiak2014]. This greatly reduces the overhead needed to integrate data sets into apps and thus increases the value of Open Data. However, one needs new ETL processes to transform raw data to Linked Data. While it facilitates data usage for app developers, Linked Data requires initially more work by the data owner and publisher.

In the past years many powerful tools got developed or extended to support creation and maintenance of Linked Data. Also new W3C standards and vocabularies are developed for turning legacy data into Linked Data. Many of these tools and standards are developed, extended or implemented by Fusepool P3 project partners. The emerging Linked Data Platform Standard (LDP)[[7]](#ftnt7) provide standardized means for making collections of linked data resources accessible.

What is lacking is an integration framework that combines the data transformation to RDF, possible enhancement steps and the publishing of the Linked Data. Fusepool P3 will provide such an integration framework along with User Interface tools that serve both to model the data publication process as well as to coordinate the human interactions that might be required while the data is processed.

This framework will integrate state-of-the-art tools like OpenRefine, OpenLink Virtuoso, Apache Stanbol, and Pundit. The framework is developed and tested based on the requirements by our project partners Provincia Autonoma di Trento (PAT) and Regione Toscana (RET). Both partners have started working with the platform in an early stage and feedback gets directly integrated into the agile development process of Fusepool P3.

## User Requirements

T1.1 - User requirements: identify key stakeholders, conduct in-depth interviews in the toursim related field; map requirements and expectations to functionality and develop use scenarios based on these requirements to form the basis of conceptual and functional test models.

To assure that Fusepool P3 creates a real value for the involved project partners and new stakeholders, it is essential to understand their motivation and needs. The Fusepool P3 project partners Provincia Autonoma di Trento (PAT) and Regione Toscana (RET) have been publishing Open Data and developing apps in the domain of tourism for several years. During this time both partners gained valuable experience in data creation, maintenance and publication. 

As of today both partners publish there data into a public CKAN[^ckan] repository. CKAN is a data management system aimed at data publishers wanting to make their data open and available. It provides tools to faciliate this publishing step and helps finding and using data. The data quality completely depends on the data provider. There is no additional work done on the data sets except adding some meta information. The data which gets pushed into the system is the data which is made available to the user.

Currently available open data by PAT and RET is available in particular data formats like CSV, KML, XML and JSON. App developers need to download the raw data and process it using their own ETL (Extract, Transform, Load) processes. With every update of the raw data this process has to be triggered for every single application where it is used. If the format of the raw data changed, the process has to be adjusted and cannot be automated. With every new data source, maintenance complexity of these Open Data sets and its apps increases.

In interviews with PAT and RET it became clear, that this is one of the big obstacles of the current approach. There is far more knowledge in these data sets available than what is visible and accessible to the open data developer.
This is best explained by the example of Via Francigena[^viafrancigena], an ancient road and pilgrim route running from France to Rome. In their geographic information system (GIS) RET collects many point of interest (POI) around this ancient road. This dataset is made available to the public but the data alone does not tell the full story of the POI. 



 tourism that enhances the cultural, environmental and historical heritage of the historic path, creating opportunities for small enterprises and for a conscious development of the territory. 



Linked Data can help to solve these problems: Data is made available in a standard format (RDF) which provides among others the following benefits:

-   Every piece of information (data) has its own identifier (URI/IRI).
-   Those identifiers can be resolved via the web (HTTP),
-   which acts as a generalized API for developers.
-   Standardized vocabularies describe the meaning of the data,
-   and allow to relate information with each other.

## Data Identification

T1.2 - Identify the data. Select potentially value-adding data sources based on application scenarios and use cases that a) provide a concrete benefit for the public agencies and SMEs, b) are likely to be re-used by others and c) integrate well into the existing Linked Data cloud.

## Data Modeling

T1.3 - Model the data: Identify existing ontologies/vocabularies to model the data, agree on standard structural and descriptive metadata, and define data models that reuse existing approaches and schemas to model relational and other data sources. 

## Data Preparation

T1.4 - Prepare the data: Adopt and implement consistent representations of data resources along with their human and machine readable descriptions, evaluate and specify approprate data publication licenses as well as appropriate hosting solutions and regular maintenance intervals.

## References

| Ref.             | Description |
|------------------|-------------|
| <a name="BernersLee2006"></a>BernersLee2006 | Berners-Lee, T. (2006). Design issues: Linked Data. W3C. |
| Bizer2009        | Bizer, C., Heath, T., & Berners-Lee,T. (2009). Linked data-the story so far. International journal on semantic web and information systems, 5(3), 1-22.                                                      |
| Brooks1995       | Brooks Jr, F. P. (1995). The Mythical Man-Month: Essays on Software Engineering, Anniversary Edition (2nd Edition)                                      |

Copyright Fusepool P3 Consortium

* * * * *

[^ckan]: Open Source Software, available at http://ckan.org/
[^viafrancigena]: Via Francigena in [Wikipedia](http://en.wikipedia.org/wiki/Via_Francigena)

