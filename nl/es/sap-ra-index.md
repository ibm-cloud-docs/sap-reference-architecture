---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, relational database management systems, RDBMS, SAP Web Dispatcher, SAP NetWeaver Application Servers, application servers, database, high availability, disaster recovery

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Iniciación a la arquitectura de referencia de IBM Cloud SAP
{: #getting-started}

La arquitectura de {{site.data.keyword.cloud}} proporciona capacidades técnicas superiores como, por ejemplo, software para entornos críticos para infraestructura en la nube, interfaces programables y cientos de configuraciones de red y hardware. Está diseñada para ofrecer un mayor nivel de flexibilidad (combinando servidores dedicados y virtuales para ajustarse a distintas cargas de trabajo) así como para permitir la automatización de interfaces y las opciones de despliegue híbrido. La oferta de la infraestructura certificada de SAP de {{site.data.keyword.cloud_notm}} para SAP HANA y SAP NetWeaver proporciona una selección óptima. En esta selección se incluyen servidores nativos y basados en la virtualización encima de los que se ejecuta la pila de software SAP.

## Arquitectura de referencia
{: #ref-arch}

En la Figura 1 se muestra la arquitectura de referencia (RA) para un entorno formado por

  * Componentes de red Vyatta
  * SAP Web Dispatcher
  * Servidores de aplicaciones SAP NetWeaver
  * Bases de datos SAP HANA
  * Otros RDBMS (Relational Database Management Systems)

El ejemplo de la arquitectura de referencia está configurado con alta disponibilidad y recuperación ante desastres. Tenga en cuenta que en la Figura 1, los servidores de bases de datos pueden ser cualesquiera a los que SAP NetWeaver dé soporte, por ejemplo, SAP HANA.

Figura 1. Arquitectura de referencia de ejemplo

![Figura 1. Arquitectura de referencia de ejemplo](/images/SAP-optimization-ref-architecture-20180527.png "Arquitectura de referencia de ejemplo")
