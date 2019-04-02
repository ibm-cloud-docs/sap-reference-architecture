---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Advanced Business Application Programming, ABAP, ABAP SAP Central Services, ASCS, SAP Central Services, SAP Software Provisioning Manager, SWPM, HANA System Replication, HSR, User Management Engine, UME, VLAN, SAP Web Dispatcher, SAP NetWeaver application servers, application servers, database, instance, load balancing, SAP logon groups, RFC server groups, high availability, highly available, HA, disaster recovery, DR, cluster software, Linux Pacemaker, virtual hostname

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Anleitung für die von SAP zertifizierte IBM Cloud-Infrastruktur
{: #recommendations}

Ihre Anforderungen können sich von den hier beschriebenen Gegebenheiten unterscheiden. Die folgende Anleitung dient jedoch als Ausgangspunkt für das Einrichten Ihres von SAP zertifizierten Servers in der {{site.data.keyword.cloud}}-Umgebung.

Abbildung 1. Beispielreferenzarchitektur

![Abbildung 1. Beispielreferenzarchitektur](/images/SAP-optimization-ref-architecture-20180527.png "Beispielreferenzarchitektur")

## VLANs
{: #vlans}

Die SAP-Richtlinien für das Design von Systemlandschaften empfehlen eine Aufteilung des Serverdatenverkehrs auf verschiedene Netzschnittstellencontroller (Network Interface Controller, NIC). Beispielsweise sollten Geschäftsdaten von Verwaltungs- und Sicherungsdaten getrennt werden. Die Zuordnung mehrerer NICs zu verschiedenen Teilnetzen ermöglicht diese Aufteilung der Daten. Weitere Informationen finden Sie im Abschnitt zu Netzumgebungen in der Veröffentlichung [Building High Availability for SAP NetWeaver and SAP HANA ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} (PDF).

Der NIC-Empfehlung entsprechend lässt {{site.data.keyword.cloud_notm}} die Konfiguration mehrerer VLANs auf den Servern zu. Die VLAN-Schnittstellen können über mehrere NICs hoch verfügbar gemacht werden, damit sie unter Bond-Schnittstellen (Linux) oder unter Teaming-Schnittstellen (Microsoft Windows) konfiguriert werden können. Für HA- und DR-Funktionen (High Availability, Disaster Recovery) auf dem {{site.data.keyword.baremetal_short}} ist es am besten, zusätzliche IP-Adressen zu reservieren und die Adressen den verschiedenen SAP-Services zuzuweisen, wenn die Services implementiert werden. Informationen zur Adressvergabe während der Installation mit dem SAP Software Provisioning Manager (SWPM) finden Sie in der SAP-Installationsdokumentation. Bei virtuellen Maschinen (VMs) genügt in der Regel die Adresse der Hauptschnittstelle der VM.

Standardmäßig haben {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} eine öffentliche und eine private Schnittstelle. Im Allgemeinen ist es nicht empfehlenswert, das öffentliche LAN für alle Server in Ihrer {{site.data.keyword.cloud_notm}}-Infrastruktur zu konfigurieren. Spezifische Instanzen des Vyatta Network Gateway sollten bereitgestellt werden, um bei Bedarf den öffentlichen Zugriff auf Ihre Umgebung zu ermöglichen. Weitere Informationen finden Sie unter [Vyatta Network Gateway](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta).

## {{site.data.keyword.cloud_notm}}-Speicher
{: #storage}

Für SAP NetWeaver zertifizierte {{site.data.keyword.cloud_notm}}-Server können mit einer unterschiedlichen Anzahl von internen Platten sowie mit unterschiedlichen Layouts für diese Platten zur RAID-Konfiguration konfiguriert werden. Beachten Sie, dass diese Layouts möglicherweise bestimmten Projektanforderungen nicht gerecht werden (z. B. bei unzureichender Größe oder bei gemeinsamem Speicherzugriff).

Die Speicheranforderungen sind so unterschiedlich, dass die Projekt-KPIs zunächst hinsichtlich Zeitfenster für Sicherung und Wiederherstellung, hoher Verfügbarkeit und Failover-Anforderungen genau definiert werden müssen, bevor über den zu verwendenden Speichertyp entschieden werden kann. Nicht alle Optionen können hier behandelt werden. Ein paar Hinweise sind aber möglich.

  * Verwenden Sie gemeinsam genutzte iSCSI-Geräte für HA-Konfigurationen mit einer Datenbank, die für den Failover-Betrieb zwischen verschiedenen Knoten zur Verfügung steht. Dabei müssen Sie die erforderlichen E/A-Operationen pro Sekunde beachten.

  * Verwenden Sie den internen Speicher bei HA-Konfigurationen mit einer Datenbank, die repliziert wird (z. B. SAP HANA-Systemreplikation). SAP NetWeaver-Anwendungsserver können sich entweder in internem Speicher oder in gemeinsam genutztem NAS-Speicher (Network Attached Storage) befinden.

  * Verwenden Sie gemeinsam genutzten Speicher, um Failover-Funktionen bei VMware-basierten Installationen zu ermöglichen. Weitere Informationen zur Auswahl des richtigen Speichertyps finden Sie unter [Speicher für die Verwendung mit VMware-Systemen](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems).

Alle Optionen können innerhalb der {{site.data.keyword.cloud_notm}}-Infrastruktur ausgewählt werden.

## Hohe Verfügbarkeit (High Availability)
{: #availability}

Bei einer verteilten Installation von SAP-Anwendungen mit einer zentralen Datenbank wird die Basisinstallation repliziert, um eine hohe Verfügbarkeit zu erreichen. Für jede Schicht der Architektur variiert das Hochverfügbarkeitsdesign.

  * **SAP Web Dispatcher**. Hohe Verfügbarkeit wird durch mehrere redundante SAP Web Dispatcher-Instanzen mit SAP-Anwendungsdatenverkehr erreicht. Der SAP Web Dispatcher dient als potenzieller Einstiegspunkt für eine Reihe von SAP-Systemen und andere `https`-basierte Services. Er liegt typischerweise zwischen dem Internet und den Back-End-Systemen und verarbeitet die webprotokollbasierten Anforderungen der "Außenwelt". Der SAP Web Dispatcher arbeitet wie ein Reverse Proxy und bietet eine Vielzahl von unterstützten Funktionen wie Lastausgleich und Single Sign-on. Weitere Informationen finden Sie in [SAP-Web-Dispatcher ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window}.

  * **ABAP SAP Central Services (ASCS)**. Für eine hohe Verfügbarkeit von ASCS in einer {{site.data.keyword.cloud_notm}}-Umgebung muss die Cluster-Software des Zielbetriebssystems installiert sein, z. B. Linux Pacemaker oder Microsoft Cluster. Der Single Point of Failure des ASCS (SAP Enqueue Service) muss so konfiguriert werden, dass seine Daten in einen Enqueue Replication Service (ERS) repliziert werden. Eine ERS-Instanz muss im Rahmen des SAP-Installationsprozesses installiert werden; sie wird vom SAP-SWPM unterstützt. Einzelheiten zur Installation und Konfiguration der Clusterkomponenten für ASCS und ERS finden Sie in der Dokumentation des Betriebssystemanbieters.

  * **SAP NetWeaver Application Server**. Hohe Verfügbarkeit wird durch Lastausgleichsverkehr innerhalb eines Pools von Anwendungsservern erreicht. Wenn nur eine begrenzte Anzahl von Ressourcen benötigt wird, kann ein einzelner Anwendungsserver als hoch verfügbar konfiguriert werden. Der Anwendungsserver muss mit einem Speicher installiert werden, auf den alle potenziellen Clusterknoten zugreifen können, die für die Failover-Funktionalität zur Verfügung stehen. Außerdem muss der SAP NetWeaver-Stack einen virtuellen Hostnamen verwenden. Einzelheiten zur erforderlichen Konfiguration können Sie der Betriebssystemdokumentation des entsprechenden Anbieters und der SAP-Dokumentation zur Hochverfügbarkeit entnehmen. Wenn Ihre Konfiguration mehrere Anwendungsserver erfordert, muss die Konfiguration der SAP-Anwendungsserver auch den Lastausgleich abdecken (z. B. in SAP-Anmeldegruppen und RFC-Servergruppen). Weitere Informationen finden Sie im Handbuch zur Systemverwaltung (Administration Guide) für Ihre SAP NetWeaver-Version.

  * **Datenbankschicht**. Die Beispielreferenzarchitektur stellt eine einzelne SAP HANA- oder andere Datenbankinstanz bereit. Für eine hohe Verfügbarkeit müssen Sie mehr als eine Instanz bereitstellen und HANA System Replication (HSR) verwenden, um die manuelle Failover-Funktionalität zu implementieren. Um einen automatischen Failover zu ermöglichen, ist eine Hochverfügbarkeitserweiterung für die jeweilige Linux-Distribution erforderlich. Für andere Datenbanken kann entweder ein Failover der Datenbankinstanz auf gemeinsam genutztem Speicher konfiguriert oder ein Replikationsverfahren ähnlich dem SAP-HANA-Szenario verwendet werden. In der Dokumentation des unterstützten Datenbanksystems erfahren Sie, welche Optionen für die Konfiguration hoher Verfügbarkeit oder der Replikation erforderlich sind.

  Zusätzliche Informationen finden Sie in [Hochverfügbarkeitsunterstützung in {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha).

## Wiederherstellung (Disaster Recovery)
{: #dr}

Jede Schicht wendet eine eigene Strategie für den Disaster-Recovery-Schutz an.

 * **SAP NetWeaver Application Server**. Die SAP-Anwendungsserver enthalten zwar keine Geschäftsdaten; die Installation und Konfiguration des Servers müssen jedoch so ausgelegt werden, dass der Betrieb nach einer Störung oder einem Katastrophenfall aufrechterhalten werden kann. Eine Disaster-Recovery-Strategie besteht zum Beispiel darin, auch über SAP-Anwendungsserver in einer anderen Region zu verfügen. Alle Konfigurationsänderungen oder Kernelaktualisierungen auf dem primären Anwendungsserver müssen auf die virtuellen Maschinen oder Server in der Disaster-Recovery-Region kopiert werden.

 * **SAP Central Services (SCS)**. Die SCS-Komponente des SAP-Anwendungsstacks enthält keine Geschäftsdaten. Sie können einen Server oder eine VM in der Disaster-Recovery-Region einrichten, um die SCS-Rolle auszuführen. Der einzige zu synchronisierende Inhalt vom primären SCS-Server ist der gemeinsam genutzte Inhalt von `/sapmnt`. Auch wenn Konfigurationsänderungen oder Kernelaktualisierungen auf den primären SCS-Servern stattfinden, müssen die Änderungen auf die Disaster-Recovery-SCS repliziert werden. Um die beiden Server zu synchronisieren, müssen Sie einen zeitgesteuerten Kopierjob verwenden, um `/sapmnt` auf die Disaster-Recovery-Server zu kopieren. Weitere Informationen zu SCS finden Sie in [Central Services Instance ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window}.

 * **Datenbankschicht**. Für SAP HANA-basierte Systeme verwenden Sie HANA-unterstützte Replikationslösungen, wie z. B. HANA System Replication oder {{site.data.keyword.cloud_notm}}-Speicherreplikationsfunktionen. Informationen zu anderen unterstützten Datenbanken finden Sie in der entsprechenden Datenbankdokumentation. Im Allgemeinen ist beim Auswählen aus den verfügbaren Optionen eine gute Kenntnis der Geschäftsanforderungen der zugrunde liegenden SAP-Anwendung erforderlich. Die Auswirkungen eines möglichen Verlustes einzelner Transaktionen oder sogar aller Daten in einem bestimmten Zeitfenster müssen ermittelt werden.

 * **Infrastruktur**. Je nachdem, wo sich die SAP-Clients in Ihrer {{site.data.keyword.cloud_notm}}-Infrastruktur befinden, müssen andere Komponenten für Disaster-Recovery-Szenarien vorbereitet werden. In der Beispielreferenzarchitektur greifen Clients von der On-Premises-Seite oder aus dem Unternehmensnetz des Kunden auf die SAP-Systeme zu.

## Sicherheit
{: #security}

### Benutzermanagement

SAP verfügt über eine eigene User Management Engine (UME) zur Steuerung des rollenbasierten Zugriffs und der Autorisierung für die SAP-Anwendung. Weitere Informationen finden Sie in [SAP HANA-Sicherheit - Übersicht ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://archive.sap.com/documents/docs/DOC-62943){: new_window}. Aus der Perspektive des Benutzermanagements ist es nicht relevant, ob Ihre SAP-Systeme bei Ihnen vor Ort ('on-premises') oder unter {{site.data.keyword.cloud_notm}} ausgeführt werden. Ausnahmen zu dieser Regel sind unter [Jump-Box-Server](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box) beschrieben.

### Netzsicherheit

Da es verschiedene Möglichkeiten gibt, auf eine {{site.data.keyword.cloud_notm}}-basierte Umgebung zuzugreifen, müssen die Sicherheitsmaßnahmen differenziert werden.

Die Verwendung einer öffentlichen Schnittstelle für den externen Zugriff sollte nur bei Bereitstellungen für den Konzeptnachweis (Proof-of-Concept) in Betracht gezogen werden. Bei Produktionsszenarien ist die Bereitstellung von Vyatta-Appliances möglich, da die Appliances über alle erforderlichen Funktionen verfügen (VPN-Firewall, etc.). Sollten die Latenz- und/oder Durchsatzanforderungen nicht durch die Vyatta-Appliances erfüllt werden, wenden Sie sich an den {{site.data.keyword.cloud_notm}} Support, um mehr über die Maßnahmen und Konfigurationen zu erfahren, die über die Vyatta-Appliances hinaus möglich sind.
