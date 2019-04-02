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

# Häufig gestellte Fragen zu SAP-Anwendungen
{: #application-faqs}

## Wo finde ich die SAP-Anwendungen, die in SAP NetWeaver zertifiziert sind?
{: faq}

Die SAP Business Suite, einschließlich SAP S/4HANA und SAP Business Warehouse on HANA, wird unterstützt. Informationen zu bestimmten Anwendungen finden Sie in der [SAP-Produktverfügbarkeitsmatrix ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://support.sap.com/en/release-upgrade-maintenance.html){: new_window} und in den [SAP-Hinweisen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://support.sap.com/en/index.html){: new_window}. In beiden Fällen ist für den Zugriff eine SAP S-Benutzer-ID erforderlich.

## Kann ich andere als SAP NetWeaver-Anwendungen ausführen - z. B. SAP Hybris und SAP BusinessObjects?
{: faq}

SAP BusinessObjects ist für die Ausführung auf virtuellen Servern in {{site.data.keyword.cloud}} zertifiziert. Weitere Informationen finden Sie im [SAP-Hinweis 2279688 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/2279688){: new_window}. SAP Hybris liegt außerhalb des Umfangs des {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure-Angebots. Für eine komplexe SAP-Implementierung bietet {{site.data.keyword.IBM_notm}} vollständig verwaltete Services für SAP. Weitere Informationen finden Sie in [Verwaltete Services für SAP-Anwendungen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## Wird SAP Business One auf den von SAP zertifizierten Bare-Metal-Servern unterstützt?
{: faq}

SAP Business One wird nicht auf dem von SAP zertifizierten {{site.data.keyword.baremetal_short}} unterstützt.

## Welche Version von SAP NetWeaver wird unterstützt?
{: faq}

Es werden Anwendungen unterstützt, die Anwendungsserver, SAP ABAP oder Java als Teil von SAP NetWeaver 7.0 oder höher ausführen und SAP-Kernel 7.21 EXT (mindestens PL #600), 7.22 EXT (mindestens PL #100), 7.45 (mindestens PL #100) und 7.49 (mindestens PL #100) oder höhere SAP-Kernelversionen verwenden.
