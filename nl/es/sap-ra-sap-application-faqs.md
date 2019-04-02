---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, application servers

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Preguntas frecuentes: Aplicaciones SAP
{: #application-faqs}

## ¿Dónde puedo encontrar las aplicaciones SAP que están certificadas con SAP NetWeaver?
{: faq}

Se da soporte a SAP Business Suite, incluido SAP S/4HANA y SAP Business Warehouse en HANA. Para otras aplicaciones específicas, consulte la [Matriz de disponibilidad de productos SAP ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://support.sap.com/en/release-upgrade-maintenance.html){: new_window} y las [Notas de SAP ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://support.sap.com/en/index.html){: new_window}. Para acceder a ambos contenidos se necesita un ID de S-user de SAP.

## ¿Puedo ejecutar aplicaciones que no SAP NetWeaver como, por ejemplo, SAP Hybris y SAP BusinessObjects?
{: faq}

SAP BusinessObjects está certificado para ejecutarse en servidores virtuales en {{site.data.keyword.cloud}}. Para obtener más información, consulte la [Nota de SAP 2279688 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/notes/2279688){: new_window}. SAP Hybris está fuera del ámbito de la oferta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure. Para implementaciones de SAP complejas, {{site.data.keyword.IBM_notm}} ofrece servicios gestionados completos. Para obtener más información, consulte [Servicios gestionados para aplicaciones SAP ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## ¿Se da soporte a SAP Business One en los servidores nativos certificados para SAP?
{: faq}

No se da soporte a SAP Business One en los {{site.data.keyword.baremetal_short}} certificados para SAP.

## ¿Qué versión de SAP NetWeaver está soportada?
{: faq}

Se da soporte a las aplicaciones que se ejecutan en servidores de aplicaciones, SAP ABAP o Java como parte de SAP NetWeaver 7.0 o superior, utilizando SAP kernel 7.21 EXT (mínimo PL #600), 7.22 EXT (mínimo PL #100), 7.45 (mínimo PL #100) y 7.49 (mínimo PL #100) o versiones superiores del kernel SAP.
