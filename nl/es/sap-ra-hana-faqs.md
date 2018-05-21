---



copyright:
  years: 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Preguntas frecuentes: SAP HANA
{: #hana-faqs}

## ¿Cuáles son los tamaños de los servidores nativos de IBM Cloud disponibles para SAP HANA?

Los {{site.data.keyword.baremetal_long}} certificados para SAP están disponibles con los siguientes tamaños de RAM: 
  * 512 GB
  * 1 TB
  * 2 TB
  * 4 TB
  * 8 TB
  
## ¿Qué opciones de compartición de hardware hay soportadas en la infraestructura IBM Cloud? Por ejemplo, Virtual HANA y Multitenant Database Containers (MDC).

La oferta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure es para el despliegue de servidores nativos certificados para SAP y no incluye virtualización. Es responsabilidad del usuario asegurarse de que los cambios realizados por encima de esta infraestructura no alteran la certificación SAP. 

## ¿Cómo se despliega SAP HANA en IBM Cloud?

Los pasos de implementación se describen en [SAP HANA en {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started). Como se trata de una oferta autogestionada, es responsabilidad del usuario implementar SAP HANA en {{site.data.keyword.cloud_notm}}. {{site.data.keyword.IBM_notm}} ofrece asesoramiento y servicios SAP gestionados para ayudarle. Para obtener más información, consulte [{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed).

## ¿Se da soporte al escalado horizontal (scale-out) para SAP HANA?

Actualmente, no se da soporte al escalado horizontal (scale-out) para SAP-HANA. 

## ¿Cuál es el tamaño máximo de servidor soportado para SAP Business Suite en HANA?

El tamaño de servidor máximo soportado para SAP Business Suite en HANA es de 8 TB. 

##  ¿Cuál es el tamaño máximo de servidor soportado para SAP Business Warehouse en HANA?

El tamaño de servidor máximo soportado para SAP Business Warehouse en HANA es de 4 TB. 

## ¿Cómo puedo realizar copia de seguridad de mis servidores certificados para SAP HANA? 

En la oferta autogestionada no se incluye la copia de seguridad del servidor. Existen opciones que se pueden seleccionar en el proceso del pedido del servidor en el portal de cliente de la infraestructura {{site.data.keyword.cloud_notm}}.  También tiene la opción de integrar una solución de copia de seguridad de terceros. 

## ¿Cómo puedo migrar una base de datos SAP HANA existente o una base de datos relacional a un servidor certificado para SAP HANA en IBM Cloud?

En el servicio autogestionado no se incluyen servicios de migración. Todas las actividades de migración son responsabilidad del usuario. {{site.data.keyword.IBM_notm}} ofrece una serie de servicios de asesoramiento y gestionados que puede ayudarle en la planificación y la ejecución de la migración SAP. Para obtener más información, consulte [{{site.data.keyword.cloud_notm}}IBM Cloud Advisory Services](https://ibm.com/us-en/marketplace/cloud-consulting-services). 

## ¿Se da soporte a SAP HANA 2.0 como parte de la oferta IBM Cloud SAP-Certified Infrastructure? 

Sí, se da soporte a SAP HANA 2.0 si solicita un servidor certificado para SAP con un sistema operativo compatible con SAP HANA 2.0. Para obtener más información, consulte la [Nota SAP 2235581](https://launchpad.support.sap.com/#/notes/2235581). 
