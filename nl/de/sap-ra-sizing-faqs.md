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

# Häufig gestellte Fragen zu Dimensionierung und Architektur
{: #faqs_sizing}

## Welches sind die SAPS-Messwerte (SAPS = SAP Application Performance Standard) für jeden SAP NetWeaver-zertifizierten IBM Cloud-Server (SAPS/Kern)?

Tabelle enthält die SAP-Messwerte für den SAP NetWeaver-zertifizierten {{site.data.keyword.cloud}}-{{site.data.keyword.baremetal_short}}.

Tabelle 1. SAPS-Messwerte für den SAP NetWeaver-zertifizierten {{site.data.keyword.cloud_notm}}-{{site.data.keyword.baremetal_short}}.

| **Servertyp** | **SAPS** | **RAM** | **Kerne** | **SAPS/Kern** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2688 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2293 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |

## Welche Datenbanken werden vom IBM Cloud SAP-Certified Infrastructure-Angebot unterstützt?

Bei SAP HANA-Konfigurationen sind SAP HANA 1.0 und SAP HANA 2.0 die unterstützten Datenbankplattformen. Umfassende Informationen zur Betriebssystem- und Datenbankunterstützung für SAP NetWeaver finden Sie unter [SAP-Hinweis 2414097](https://launchpad.support.sap.com/#/notes/2414097).

## Kann eine Tier-2-Konfiguration (Anwendungsserver plus SAP HANA-Datenbank) mit den SAP HANA-zertifizierten IBM Cloud-Bare-Metal-Servern eingerichtet werden?

Eine Tier-2-Konfiguration kann nicht auf derselben Hardwarekomponente eingerichtet werden. Sie kann aber unter Verwendung einer Kombination der SAP NetWeaver- und SAP HANA-Konfigurationen erfolgen.

## Wird die Virtualisierung (VMware) in der IBM Cloud SAP-zertifizierten Infrastruktur für SAP NetWeaver oder SAP HANA unterstützt?

Ja, die {{site.data.keyword.cloud_notm}} SAP-zertifizierte Infrastruktur unterstützt VMware ESXi für SAP NetWeaver und SAP HANA. Wenn Sie sich für die Bestellung und Implementierung eines Servers mit VMware entscheiden, ist es Ihre Aufgabe, alle virtuellen Maschinen auf dem Server so zu dimensionieren und zu konfigurieren, dass sie den Einschränkungen und Best Practices von SAP entsprechen. Zusätzliche Informationen finden Sie unter [SAP-Hinweis 2161991](https://launchpad.support.sap.com/#/notes/2161991).

## Kann die Konfiguration von IBM Cloud-Bare-Metal-Servern geändert werden, die von SAP zertifiziert wurden?

SAP HANA-zertifizierte {{site.data.keyword.baremetal_short}} haben eine feste Konfiguration für Prozessor, RAM und lokalen Speicher (abhängig vom gewählten Server) und können nicht geändert werden. Optionen für Netzbetrieb, Betriebssystem und Überwachungsservices können konfiguriert werden.

SAP NetWeaver-zertifizierte {{site.data.keyword.baremetal_short}} haben eine feste Konfiguration für Prozessor und RAM; der lokale Speicher kann nach Bedarf entsprechend Ihren Anforderungen konfiguriert werden. Optionen für Netzbetrieb, Betriebssystem und Überwachungsservices können konfiguriert werden.

## Gibt es empfohlene Methoden, um eine SAP-Lösung in der IBM Cloud SAP-zertifizierten Infrastruktur bereitzustellen?

Ja, [SAP Best Practices](https://help.sap.com/viewer/p/SAP_Best_Practices) bietet Optionen, die Sie bei der Bereitstellung verwenden können. {{site.data.keyword.IBM_notm}} bietet außerdem cloudbezogene Beratungsleistungen. Weitere Informationen finden Sie unter [{{site.data.keyword.cloud_notm}} Advisory Services](https://www.ibm.com/us-en/marketplace/cloud-consulting-services).

## Muss ich SAP Solutions Manager und SAProuter bereitstellen? Wenn ja, gibt es eine empfohlene Infrastruktur?

Nein, die Bereitstellung von SAP Solutions Manager und SAProuter ist nicht zwingend erforderlich, wenn Sie mit einer Trainings-, Sandbox- oder ähnlichen Umgebung arbeiten. Am besten ist es jedoch, wenn diese Komponenten in Ihrer Produktionsumgebung bereitgestellt werden.

