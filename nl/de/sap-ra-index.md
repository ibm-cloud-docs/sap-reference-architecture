---



copyright:
  years: 2018
lastupdated: "2018-03-26"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Einführung in die IBM Cloud SAP-Referenzarchitektur
{: #getting-started}

Die {{site.data.keyword.cloud}}-Architektur bietet überlegene technische Funktionalität, wie z.B. eine für die Cloudinfrastruktur kritische, softwaredefinierbare Umgebung, programmierbare Schnittstellen und Hunderte von Hardware- und Netzkonfigurationen. Sie wurde entwickelt, um ein höheres Maß an Flexibilität (durch das Kombinieren von virtuellen und dedizierten Servern für eine Vielzahl von Workloads), Automatisierung von Schnittstellen und Hybridbereitstellungsoptionen zur Verfügung zu stellen. Das {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure-Angebot für SAP HANA und SAP NetWeaver bietet eine Lösung mit hoher Passgenauigkeit. Diese Auswahl umfasst Bare-Metal- und virtualisierungsbasierte Server, auf denen der SAP-Software-Stack ausgeführt wird.

## Referenzarchitektur
{: #ref-arch}

Abbildung 1 zeigt eine Referenzarchitektur (RA) für eine Systemlandschaft mit folgenden Bestandteilen:

  * Vyatta-Netzkomponenten
  * SAP Web Dispatcher
  * SAP NetWeaver Application Server
  * SAP HANA-Datenbanken
  * Andere Managementsysteme für relationale Datenbanken (RDBMS) 
  
Die Beispielreferenzarchitektur ist mit Hochverfügbarkeits- und Wiederherstellungsfunktionen konfiguriert (High Availability, Disaster-Recovery). Beachten Sie bei Abbildung 1, dass es sich bei den Datenbankservern um jedes von SAP NetWeaver unterstützte Datenbanksystem handeln kann, z. B. SAP HANA. 

Abbildung 1. Beispielreferenzarchitektur

![Abbildung 1. Beispielreferenzarchitektur](/images/ref_architecture.png "Beispielreferenzarchitektur")
