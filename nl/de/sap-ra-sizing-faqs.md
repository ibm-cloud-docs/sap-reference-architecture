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

# Häufig gestellte Fragen zu Dimensionierung und Architektur
{: #faqs_sizing}

## Welches sind die SAPS-Messwerte (SAPS = SAP Application Performance Standard) für jeden SAP NetWeaver-zertifizierten IBM Cloud-Server (SAPS/Kern)?
{: faq}

Tabelle enthält die SAP-Messwerte für den SAP NetWeaver-zertifizierten {{site.data.keyword.cloud}}-{{site.data.keyword.baremetal_short}}.

Tabelle 1. SAPS-Messwerte für den SAP NetWeaver-zertifizierten {{site.data.keyword.cloud_notm}}-{{site.data.keyword.baremetal_short}}.

| **Servertyp** | **SAPS** | **RAM** | **Kerne** | **SAPS/Kern** |
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

## Welche Datenbanken werden vom IBM Cloud SAP-Certified Infrastructure-Angebot unterstützt?
{: faq}

Bei SAP HANA-Konfigurationen sind SAP HANA 1.0 und SAP HANA 2.0 die unterstützten Datenbankplattformen. Umfassende Informationen zur Betriebssystem- und Datenbankunterstützung für SAP NetWeaver finden Sie im [SAP-Hinweis 2414097 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}.

## Kann eine Tier-2-Konfiguration (Anwendungsserver plus SAP HANA-Datenbank) mit den SAP HANA-zertifizierten IBM Cloud-Bare-Metal-Servern eingerichtet werden?
{: faq}

Eine Tier-2-Konfiguration kann nicht auf derselben Hardwarekomponente eingerichtet werden. Sie kann aber unter Verwendung einer Kombination der SAP NetWeaver- und SAP HANA-Konfigurationen erfolgen.

## Wird die Virtualisierung (VMware) in der IBM Cloud SAP-zertifizierten Infrastruktur für SAP NetWeaver oder SAP HANA unterstützt?
{: faq}

Ja, die {{site.data.keyword.cloud_notm}} SAP-zertifizierte Infrastruktur unterstützt VMware ESXi für SAP NetWeaver und SAP HANA. Wenn Sie sich für die Bestellung und Implementierung eines Servers mit VMware entscheiden, ist es Ihre Aufgabe, alle virtuellen Maschinen auf dem Server so zu dimensionieren und zu konfigurieren, dass sie den Einschränkungen und Best Practices von SAP entsprechen. Zusätzliche Informationen finden Sie im [SAP-Hinweis 2161991 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/2161991){: new_window}.

## Können die Konfigurationen der von SAP zertifizierten {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} geändert werden?
{: faq}

SAP HANA-zertifizierte {{site.data.keyword.baremetal_short}} haben eine feste Konfiguration für Prozessor, RAM und lokalen Speicher (abhängig vom gewählten Server) und können nicht geändert werden. Optionen für Netzbetrieb, Betriebssystem und Überwachungsservices können konfiguriert werden.

SAP NetWeaver-zertifizierte {{site.data.keyword.baremetal_short}} haben eine feste Konfiguration für Prozessor und RAM; der lokale Speicher kann nach Bedarf entsprechend Ihren Anforderungen konfiguriert werden. Optionen für Netzbetrieb, Betriebssystem und Überwachungsservices können konfiguriert werden.

## Gibt es empfohlene Methoden zur Bereitstellung einer SAP-Lösung in der von SAP zertifizierten {{site.data.keyword.cloud_notm}}-Infrastruktur?
{: faq}

Ja, in den [bewährten Verfahren von SAP ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.sap.com/viewer/p/SAP_Best_Practices){: new_window} finden Sie Optionen, die Sie bei der Bereitstellung verwenden können. {{site.data.keyword.IBM_notm}} bietet außerdem cloudbezogene Beratungsleistungen. Weitere Informtionen finden Sie in [Von SAP zertifizierte Infrastruktur ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/sap/certified-infrastructure){: new_window}.

## Muss ich SAP Solutions Manager und SAProuter bereitstellen? Wenn ja, gibt es eine empfohlene Infrastruktur?
{: faq}

Nein, die Bereitstellung von SAP Solutions Manager und SAProuter ist nicht zwingend erforderlich, wenn Sie mit einer Trainings-, Sandbox- oder ähnlichen Umgebung arbeiten. Am besten ist es jedoch, wenn diese Komponenten in Ihrer Produktionsumgebung bereitgestellt werden.
