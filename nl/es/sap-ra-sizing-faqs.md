---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

keywords: SAP Reference Architecture, SAP Application Performance Standard, SAPS, application servers, database, SAProuter

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Preguntas frecuentes: Dimensionamiento y arquitectura
{: #faqs_sizing}

## ¿Cuáles son las medidas de SAPS (SAP Application Performance Standard) de cada servidor IBM Cloud certificado para SAP NetWeaver (tasa SAPS y núcleo)?
{: faq}

La Tabla 1 contiene las medidas de SAP para los {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} certificados para SAP NetWeaver.

Tabla 1. Medidas SAPS para {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} certificados para SAP NetWeaver.

| **Tipo de servidor** | **SAPS** | **RAM** | **Núcleos** | **SAPS/Núcleo** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2745 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2292 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |
| BI.S3.NW32 | 11970 | 32 GB | 4 | 2992 |
| BI.S3.NW64 | 12750 | 64 GB | 4 | 3187 |
| BI.S3.NW192 | 78850 | 192 GB | 36 | 2190 |
| BI.S3.NW384 | 79430 | 384 GB | 36 | 2203 |
| BI.S3.NW768 | 79630 | 768 GB | 36 | 2211 |

## ¿A qué bases de datos da soporte a la oferta IBM Cloud SAP-Certified Infrastructure?
{: faq}

Para configuraciones de SAP HANA, las plataformas de bases de datos soportadas son SAP HANA 1.0 y SAP HANA 2.0. Para conocer la información completa del soporte de base de datos y sistemas operativos para SAP NetWeaver, consulte la [Nota de SAP 2414097 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}.

## ¿Se puede realizar una configuración de 2 niveles (servidor de aplicaciones más una base de datos SAP HANA) con los IBM Cloud Bare Metal Servers certificados para SAP HANA?
{: faq}

No es posible realizar una configuración de 2 niveles en el mismo componente de hardware. Es posible, sin embargo, realizarlo utilizando una combinación de configuraciones de SAP NetWeaver y SAP HANA.

## ¿Se da soporte a la virtualización (VMware) en la infraestructura certificada para SAP de IBM Cloud para SAP NetWeaver o SAP HANA?
{: faq}

Sí, la infraestructura certificada para SAP de {{site.data.keyword.cloud_notm}} da soporte a VMware ESXi para SAP NetWeaver y SAP HANA. Es importante señalar que si solicita e implementa un servidor ejecutando VMware, es su responsabilidad dimensionar y configurar adecuadamente todas las máquinas virtuales en el servidor para satisfacer las restricciones y las prácticas recomendadas de SAP. Para obtener información adicional, consulte la [Nota de SAP 2161991 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/notes/2161991){: new_window}.

## ¿Es posible cambiar las configuraciones de los {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} certificados para SAP?
{: faq}

Los {{site.data.keyword.baremetal_short}} certificados para SAP HANA tienen configuraciones fijadas de procesador, RAM y almacenamiento local basadas en el servidor que elija, y no es posible modificarlas. Las opciones de red, sistema operativo y servicios de supervisión es posible configurarlas.

Los {{site.data.keyword.baremetal_short}} certificados para SAP NetWeaver tienen configuraciones fijadas de procesador, RAM y almacenamiento local que es posible configurar según sea necesario para satisfacer sus necesidades. Las opciones de red, sistema operativo y servicios de supervisión es posible configurarlas.

## ¿Hay algún método recomendado por el que desplegar una solución SAP en la infraestructura certificada para SAP de {{site.data.keyword.cloud_notm}}?
{: faq}

Sí, las [Prácticas recomendadas de SAP ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.sap.com/viewer/p/SAP_Best_Practices){: new_window} proporcionan opciones que se pueden utilizar durante su despliegue. {{site.data.keyword.IBM_notm}} también ofrece servicios de consultoría en la nube. Para obtener más información, consulte [Infraestructura certificada para SAP ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/sap/certified-infrastructure){: new_window}.

## ¿Es necesario desplegar SAP Solutions Manager y SAProuter? Si es así, ¿existe una infraestructura recomendada?
{: faq}

No. El despliegue de SAP Solutions Manager y SAProuter no es obligatorio al trabajar en un entorno de pruebas, recintos de pruebas (sandbox) o similar. Sin embargo, es mejor desplegar estos componentes en los entornos de producción.
