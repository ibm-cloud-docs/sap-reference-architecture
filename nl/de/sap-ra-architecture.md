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

# Wissenswertes über die Architektur hinter der SAP-Referenzarchitektur
{: #architecture}

Das Architekturbeispiel in Abbildung 1 kann von Ihrer Architektur abweichen; es zeigt die allgemeinen Konzepte einer SAP {{site.data.keyword.cloud}}-basierten Bereitstellung. Ihre On-Premises-Systeme sind über das Internet mit Ihrer {{site.data.keyword.cloud_notm}}-Infrastruktur verbunden.

Wenn Sie Ihre Umgebung bestellt und bereitgestellt haben, stellen Sie über eine Verwaltungs-VPN eine Verbindung zu Ihrer {{site.data.keyword.cloud_notm}}-Infrastruktur her. Das VPN reicht möglicherweise nicht aus, um Ihre On-Premises-Systeme mit Cloud-basierten Systemen zu verbinden. Sie haben aber die Möglichkeit, eine Vyatta Network-Appliance in der {{site.data.keyword.cloud_notm}}-Umgebung bereitzustellen. Für höhere Bandbreitenanforderungen und niedrigere Latenzzeiten wird außerdem ein Ethernet-Circuit-Handover in die Cloud-Umgebung unterstützt.

Abbildung 1 zeigt zwei unterschiedliche Rechenzentren, die mehrere SAP-IaaS-zertifizierte Server für SAP NetWeaver und SAP HANA enthalten (IaaS = Infrastructure as a Service). Die Server oder virtuellen Maschinen in dem Diagramm können je nach Umgebung und verwendeter Datenbanktechnologie unterschiedlich sein. Darüber hinaus werden die SAP HANA-Daten in der Architekturübersicht vom primären Rechenzentrum zu Wiederherstellungszwecken (Disaster Recovery, DR) in das sekundäre Rechenzentrum übertragen. Bei anderen Datenbanken sind ebenfalls Konfigurationen wie in Abbildung 1 möglich, wobei es sich um andere Konfigurationen handelt.

In Abbildung 1 werden replizierte Systeme im Data-Recovery-Rechenzentrum so konfiguriert, dass sie die DR-Fähigkeiten beibehalten, die auf verschiedenen Ebenen implementiert werden müssen. Weitere Informationen finden Sie unter [Wiederherstellung (Disaster-Recovery)](/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#dr). 

Abbildung 1. Beispielreferenzarchitektur

![Abbildung 1. Beispielreferenzarchitektur](/images/ref_architecture.png "Beispielreferenzarchitektur")

## SAP-Systeme
{: #sap-systems}

Die SAP-Systeme (Advanced Business Application Programming (ABAP), Java und SAP HANA) bieten granulare Autorisierungsobjekte für das Benutzermanagement. Aus diesem Grund muss nur Fernzugriff von Desktops oder anderen Front-End-Geräten auf die {{site.data.keyword.cloud_notm}}-basierte Umgebung eingerichtet werden. Es muss kein Endbenutzerzugriff gewährt und in der Cloudumgebung verwaltet werden. Es kann mehrere Benutzer mit unterschiedlichen Verantwortlichkeiten geben, die Zugriff auf eine Datenbank über eine bestimmte Benutzerschnittstelle, auf Befehlszeilenebene oder die Latenzbeschränkungen benötigen, die Remote Desktop Protocol-basierten Zugriff erfordern. Um diese Art von Fernzugriff zu verwalten, kann ein "Jump-Host" in der Umgebung bereitgestellt werden, der als zentraler Zugriffspunkt für solche Szenarien dient. Abgesehen von diesen spezifischen Anforderungen haben die Benutzer Zugriff auf die cloudbasierten Systeme innerhalb Ihres Unternehmensnetzes und erfordern keine spezielle Administration.

## Netz
{: #network}

Jedes Gerät in einer {{site.data.keyword.cloud_notm}}-Umgebung kann mit verschiedenen internen und optional externen LAN-Zugriffsmöglichkeiten bestellt werden. Die externe Adresse ist eine weiterleitbare öffentliche IP-Adresse und sollte mit Vorsicht eingesetzt werden. Die interne Adresse wird durch das bestellte VLAN bestimmt und aus einem Unterbereich von 10.0.0.0/8 für das VLAN ausgewählt. Wenn Sie mehrere VLANs bestellen, können unterschiedliche Umgebungen oder Datenverkehrstypen nach Netzdesign und Sicherheitsanforderungen aufgeteilt werden.

Während eine öffentliche Schnittstelle mit einer konfigurierten Firewall bestimmte Szenarien abdecken kann - z. B. für einen Rapid-Prototyping-Konzeptnachweis mit unkritischen Daten -, sollte in den meisten Fällen ein Firewallgerät in Betracht gezogen werden. Die Beispielreferenzarchitektur bildet ein Produktionsszenario ab, sodass öffentliche Netzschnittstellen nicht berücksichtigt werden.

## Vyatta Network Gateway
{: #vyatta}

Vyatta bietet softwarebasierte virtuelle Router, virtuelle Firewall/NAT und VPN-Funktionen für IPv4 und IPv6. Sollen Benutzer remote auf Ihre {{site.data.keyword.cloud_notm}}-basierten Systeme zugreifen, können diese Geräte als Endpunkte für das "Side-to-Side VPN" oder das sogenannte "Road Warrior VPN" (Zugriffspunkt) dienen. Es können verschiedene Arten von VPN-Technologien - IPSec oder SSL-VPN-Tunnels wie z.B. OpenVPN - verwendet werden. Je nach verwendeter SAP-Technologie können diese VPN-Verbindungen für die Verbindung von SAP-Systemen (auch mit Nicht-SAP-Systemen) sowohl für die klassische GUI-Technologie als auch für die browserbasierte SAP-UI5-Technologie genutzt werden. Die Anbindung eines SAP Web Dispatcher hinter einem Vyatta-Gateway ermöglicht die Nutzung weiterer Features wie Lastausgleichs- oder Single-Sign-on-Szenarien. Weitere Informationen zum SAP Web Dispatcher finden Sie unter [Hohe Verfügbarkeit](/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#availability).

Das Vyatta-Gerät kann in einer hoch verfügbaren Clusterkonfiguration mit einer Bandbreite von bis zu 10 Gbps eingesetzt werden. Weitere Informationen finden Sie unter [Vyatta-Gateways](https://console.bluemix.net/docs/infrastructure/subnets/about.html#vyatta-gateways).

## Jump-Box-Server
{: #juump_box}

SAP-Systeme verfügen über ein integriertes Benutzermanagement und benötigen keine zentrale Benutzerverwaltung. Sie können das zentrale Benutzermanagement natürlich konfigurieren. Weitere Informationen finden Sie unter [Central User Administration](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm).

Ein Jump-Box-Server ermöglicht es Ihnen, bestimmten Benutzern Low-Level-Zugriff auf Ihre {{site.data.keyword.cloud_notm}}-Umgebung über Befehlszeilentools oder andere spezielle Tools wie SAP HANA Studio zu gewähren. Die Datenbankverwaltungstools sowie die Benutzer, denen Zugriff auf die Tools gewährt wird, werden zentral auf dem Jump-Box-Server verwaltet. Die Benutzer können sich von ihren Desktops aus über das Remote Desktop Protocol, das über das VPN-Gateway geleitet wird, bei Ihrer {{site.data.keyword.cloud_notm}}-Umgebung anmelden.

## SAP-Server - SAP HANA und SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}} bietet zahlreiche Server für SAP HANA und SAP NetWeaver im Rahmen des {{site.data.keyword.cloud_notm}} for SAP Applications-Angebots. Die Server sind {{site.data.keyword.baremetal_short}} mit einem Betriebssystem Ihrer Wahl (Red Hat Linux, SUSE Linux, Microsoft Windows Server oder bereitgestellt mit dem VMware ESX-Hypervisor). Weitere Informationen zu den SAP NetWeaver-zertifizierten Servern finden Sie unter [SAP-Hinweis 2414097](https://launchpad.support.sap.com/#/notes/2414097). Beachten Sie, dass Sie auf dem Hypervisor eines der in SAP-Hinweis 2414097 aufgeführten Betriebssysteme als Gastbetriebssystem bereitstellen. 

SAP HANA-Server verfügen über ein im Voraus gewähltes Speicherlayout, das die wesentlichen Leistungsindikatoren (KPIs) von SAP-Speicher für SAP HANA erfüllt. Sie können diese Layouts nicht ändern und Sie sollten keinen externen Speicher für SAP HANA verwenden. Externer Speicher unterschiedlicher Qualität, der über verschiedene Protokolle (NFS, CIFS, iSCSI) zugänglich ist, kann zur Sicherung und zu anderen Zwecken verwendet werden. Außerdem haben Sie bei SAP NetWeaver-Servern die Möglichkeit, andere unterstützte Datenbanksysteme auf externem Speicher auszuführen.

Alle SAP-Softwarelösungen auf Basis von SAP HANA oder SAP NetWeaver umfassen die gesamte SAP Business Suite und SAP S/4HANA kann in der {{site.data.keyword.cloud_notm}}-Umgebung bereitgestellt werden. Für alle anderen Softwarekomponenten müssen Sie sich an den SAP-Support wenden. Folgen Sie dem SAP-Prozess zur Dimensionierung, um die richtige Servergröße für Ihr Projekt zu ermitteln, und wählen Sie einen der aufgelisteten Server für das SAP HANA- oder SAP NetWeaver-Angebot aus. 

Weitere Informationen zu SAP HANA-zertifizierten Servern finden Sie unter [Certified and Supported SAP HANA Hardware Directory](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud).

Weitere Informationen zur SAP HANA-Dimensionierung finden Sie unter [4. Server dimensionieren](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-size-server.html#size_the_server). 

Weitere Informationen zur SAP NetWeaver-Dimensionierung finden Sie unter [4. Server dimensionieren](https://console.bluemix.net/docs/infrastructure/sap-netweaver/sap-size-server.html#size_the_server).
