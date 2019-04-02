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

# Häufig gestellte Fragen zu SAP HANA
{: #hana-faqs}

## In welchen Größen sind die IBM Cloud-Bare-Metal-Server für SAP HANA erhältlich?
{: faq}

Die von SAP zertifizierten {{site.data.keyword.baremetal_long}} sind mit folgenden RAM-Größen erhältlich:
* 512 GB
* 1024 GB (1 TB)
* 2048 GB (2 TB)
* 4096 GB (4 TB)
* 6144 GB (6 TB)
* 8192 GB (8 TB)
* 12288 GB (12 TB)

## Welche Optionen für die gemeinsame Nutzung von Hardware werden in der IBM Cloud-Infrastruktur unterstützt (z. B. Virtual HANA und Multitenant Database Containers (MDC))?
{: faq}

Bei dem {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure-Angebot handelt es sich um eine von SAP zertifizierte Bare-Metal-Server-Bereitstellung ohne Virtualisierung. Es liegt in Ihrer Verantwortlichkeit sicherzustellen, dass alle Änderungen an dieser Infrastruktur konform mit der SAP-Zertifizierung erfolgen.

## Wie kann ich SAP HANA unter IBM Cloud bereitstellen?
{: faq}

Die Implementierungsschritte finden Sie unter [SAP HANA unter {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started). Da es sich um ein selbstverwaltetes Angebot handelt, sind Sie für die Implementierung von SAP HANA in der {{site.data.keyword.cloud_notm}} verantwortlich. {{site.data.keyword.IBM_notm}} bietet Beratungsservices und verwaltete SAP-Services zu Ihrer Unterstützung. Weitere Informationen finden Sie in [Verwaltete Services für SAP-Anwendungen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## Wird Scale-out für SAP HANA unterstützt?
{: faq}

JA. Weitere Informationen finden Sie in [{{site.data.keyword.cloud_notm}}-Infrastruktur für die Unterstützung von SAP HANA-Systemen mit mehreren Knoten konfigurieren](/docs/infrastructure/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage). 

## Welche maximale Servergröße wird für SAP Business Suite auf HANA unterstützt?
{: faq}

8 TB ist die maximale Größe von Servern mit IaaS-Zertifizierung, die für SAP Business Suite on HANA unterstützt wird. Eine Größe von 12 TB wird unter HANA TDI v5 für genehmigte Workloads angeboten. 

##  Welche maximale Servergröße wird für SAP Business Warehouse auf HANA unterstützt?
{: faq}

4 TB ist die maximale Größe von Servern mit IaaS-Zertifizierung, die für SAP Business Warehouse on HANA unterstützt wird. 

## Wie sichere ich meine SAP HANA-zertifizierten Server?
{: faq}

Die Serversicherung ist nicht im selbstverwalteten Angebot enthalten. Hierfür können Sie unter verschiedenen Optionen wählen, während Sie den Server im Kundenportal für die {{site.data.keyword.cloud_notm}}-Infrastruktur bestellen. Außerdem haben Sie die Möglichkeit, eine Sicherungslösung von einem anderen Anbieter zu integrieren.

## Wie kann ich eine vorhandene SAP HANA-Datenbank oder eine relationale Datenbank auf einen SAP HANA-zertifizierten Server in IBM Cloud migrieren?
{: faq}

Im selbstverwalteten Service sind keine Migrationsservices enthalten; alle Migrationsaktivitäten liegen in Ihrer Verantwortlichkeit. {{site.data.keyword.IBM_notm}} bietet eine Reihe von Beratungsservices und verwalteten Services, die Sie bei der Planung und Ausführung der SAP-Migration unterstützen. Weitere Informationen finden Sie in [{{site.data.keyword.cloud_notm}} Advisory Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.com/us-en/marketplace/cloud-consulting-services){: new_window}. Wählen Sie *Services* > *Cloud-Services* aus.

## Wird SAP HANA 2.0 als Bestandteil des IBM Cloud SAP-Certified Infrastructure-Angebots unterstützt?
{: faq}

Ja, SAP HANA 2.0 wird unterstützt, wenn Sie einen von SAP zertifizierten Server mit einem Betriebssystem bestellen, das mit SAP HANA 2.0 konform ist. Weitere Informationen finden Sie im [SAP-Hinweis 2235581 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/2235581){: new_window}.
