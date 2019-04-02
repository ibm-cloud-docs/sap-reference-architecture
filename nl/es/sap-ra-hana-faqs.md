---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Multitenant Database Containers, MDC, database, SAP HANA

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Preguntas frecuentes: SAP HANA
{: #hana-faqs}

## ¿Cuáles son los tamaños de los servidores nativos de IBM Cloud disponibles para SAP HANA?
{: faq}

Los {{site.data.keyword.baremetal_long}} certificados para SAP están disponibles con los siguientes tamaños de RAM:
* 512 GB
* 1024 GB (1 TB)
* 2048 GB (2 TB)
* 4096 GB (4 TB)
* 6144 GB (6 TB)
* 8192 GB (8 TB)
* 12288 GB (12 TB)

## ¿Qué opciones de compartición de hardware hay soportadas en la infraestructura IBM Cloud? Por ejemplo, Virtual HANA y Multitenant Database Containers (MDC).
{: faq}

La oferta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure es para el despliegue de servidores nativos certificados para SAP y no incluye virtualización. Es responsabilidad del usuario asegurarse de que los cambios realizados por encima de esta infraestructura no alteran la certificación SAP.

## ¿Cómo se despliega SAP HANA en IBM Cloud?
{: faq}

Los pasos de implementación se describen en [SAP HANA en {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started). Como se trata de una oferta autogestionada, es responsabilidad del usuario implementar SAP HANA en {{site.data.keyword.cloud_notm}}. {{site.data.keyword.IBM_notm}} ofrece asesoramiento y servicios SAP gestionados para ayudarle. Para obtener más información, consulte [Servicios gestionados para aplicaciones SAP ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## ¿Se da soporte al escalado horizontal (scale-out) para SAP HANA?
{: faq}

Sí. Consulte [Configuración de la infraestructura de {{site.data.keyword.cloud_notm}} para que de soporte a SAP HANA multinodo](/docs/infrastructure/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage) para obtener más información.

## ¿Cuál es el tamaño máximo de servidor soportado para SAP Business Suite en HANA?
{: faq}

El tamaño máximo de servidor certificado para IaaS soportado para SAP Business Suite en HANA es de 8 TB.  Se ofrecen 12 TB bajo HANA TDI v5 para cargas de trabajo aprobadas.

##  ¿Cuál es el tamaño máximo de servidor soportado para SAP Business Warehouse en HANA?
{: faq}

El tamaño máximo de servidor certificado para IaaS soportado para SAP Business Warehouse en HANA es de 4 TB.

## ¿Cómo puedo realizar copia de seguridad de mis servidores certificados para SAP HANA?
{: faq}

En la oferta autogestionada no se incluye la copia de seguridad del servidor. Existen opciones que se pueden seleccionar en el proceso del pedido del servidor en el portal de clientes de la infraestructura {{site.data.keyword.cloud_notm}}. También tiene la opción de integrar una solución de copia de seguridad de terceros.

## ¿Cómo puedo migrar una base de datos SAP HANA existente o una base de datos relacional a un servidor certificado para SAP HANA en IBM Cloud?
{: faq}

En el servicio autogestionado no se incluyen servicios de migración. Todas las actividades de migración son responsabilidad del usuario. {{site.data.keyword.IBM_notm}} ofrece una serie de servicios de asesoramiento y gestionados que puede ayudarle en la planificación y la ejecución de la migración SAP. Para obtener más información, consulte [{{site.data.keyword.cloud_notm}} Advisory Services ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.com/us-en/marketplace/cloud-consulting-services){: new_window}. Seleccione *Servicios* > *Servicios de nube*.

## ¿Se da soporte a SAP HANA 2.0 como parte de la oferta IBM Cloud SAP-Certified Infrastructure?
{: faq}

Sí, se da soporte a SAP HANA 2.0 si solicita un servidor certificado para SAP con un sistema operativo compatible con SAP HANA 2.0. Para obtener más información, consulte la [Nota de SAP 2235581 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/notes/2235581){: new_window}.
