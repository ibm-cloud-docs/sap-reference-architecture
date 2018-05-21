---



copyright:
  years: 2018
lastupdated: "2018-03-15"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Preguntas frecuentes: Dimensionamiento y arquitectura
{: #faqs_sizing}

## ¿Cuáles son las medidas de SAPS (SAP Application Performance Standard) de cada servidor IBM Cloud certificado para SAP NetWeaver (tasa SAPS y núcleo)? 

La Tabla 1 contiene las medidas de SAP para los {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} certificados para SAP NetWeaver. 

Tabla 1. Medidas SAPS para {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} certificados para SAP NetWeaver. 

| **Tipo de servidor** | **SAPS** | **RAM** | **Núcleos** | **SAPS/Núcleo** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2688 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2293 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |

## ¿A qué bases de datos da soporte a la oferta IBM Cloud SAP-Certified Infrastructure?

Para configuraciones de SAP HANA, las plataformas de bases de datos soportadas son SAP HANA 1.0 y SAP HANA 2.0. Para conocer la información completa del soporte de base de datos y sistemas operativos para SAP NetWeaver, consulte la [Nota SAP 2414097](https://launchpad.support.sap.com/#/notes/2414097).

## ¿Se puede realizar una configuración de 2 niveles (servidor de aplicaciones más una base de datos SAP HANA) con los IBM Cloud Bare Metal Servers certificados para SAP HANA? 

No es posible realizar una configuración de 2 niveles en el mismo componente de hardware. Es posible, sin embargo, realizarlo utilizando una combinación de configuraciones de SAP NetWeaver y SAP HANA. 

## ¿Se da soporte a la virtualización (VMware) en la infraestructura certificada SAP de IBM Cloud para SAP NetWeaver o SAP HANA?

Sí, la infraestructura certificada para SAP de {{site.data.keyword.cloud_notm}} da soporte a VMware ESXi para SAP NetWeaver y SAP HANA. Es importante señalar que si solicita e implementa un servidor ejecutando VMware, es su responsabilidad dimensionar y configurar adecuadamente todas las máquinas virtuales en el servidor para satisfacer las restricciones y las prácticas recomendadas de SAP. Para obtener información adicional, consulte la [Nota SAP 2161991](https://launchpad.support.sap.com/#/notes/2161991). 

## ¿Es posible cambiar las configuraciones de los IBM Cloud Bare Metal Servers certificados para SAP? 

Los {{site.data.keyword.baremetal_short}} certificados para SAP HANA tienen configuraciones fijadas de procesador, RAM y almacenamiento local basadas en el servidor que elija, y no es posible modificarlas. Las opciones de red, sistema operativo y servicios de supervisión es posible configurarlas. 

Los {{site.data.keyword.baremetal_short}} certificados para SAP NetWeaver tienen configuraciones fijadas de procesador, RAM y almacenamiento local que es posible configurar según sea necesario para satisfacer sus necesidades. Las opciones de red, sistema operativo y servicios de supervisión es posible configurarlas. 

## ¿Hay algún método recomendado por el que desplegar una solución SAP en la infraestructura certificada para SAP de IBM Cloud? 

Sí, las [Prácticas recomendadas de SAP](https://help.sap.com/viewer/p/SAP_Best_Practices) proporcionan opciones que se pueden utilizar durante su despliegue. {{site.data.keyword.IBM_notm}} también ofrece servicios de consultoría en la nube. Para obtener más información, consulte [{{site.data.keyword.cloud_notm}}IBM Cloud Advisory Services](https://www.ibm.com/us-en/marketplace/cloud-consulting-services). 

## ¿Es necesario desplegar SAP Solutions Manager y SAProuter? Si es así, ¿existe una infraestructura recomendada?

No. El despliegue de SAP Solutions Manager y SAProuter no es obligatorio al trabajar en un entorno de pruebas, recintos de pruebas (sandbox) o similar. Sin embargo, es mejor desplegar estos componentes en los entornos de producción. 

