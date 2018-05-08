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

# 瞭解 SAP 參照架構背後的架構
{: #architecture}

圖 1 中的架構範例可能不同於您的架構；它會顯示 SAP {{site.data.keyword.cloud}} 型部署的一般概念。您的內部部署系統是透過網際網路連接至您的 {{site.data.keyword.cloud_notm}} 基礎架構。

在訂購並部署您的環境之後，可以透過管理 VPN 連接至您的 {{site.data.keyword.cloud_notm}} 基礎架構。VPN 可能不足以連接您的內部部署系統與雲端型系統，這就是您為何可在 {{site.data.keyword.cloud_notm}} 環境中部署「Vyatta 網路應用裝置」的原因。對於更高頻寬及更低延遲需求，也支援將乙太網路電路移交給雲端環境。

圖 1 中顯示兩個不同的資料中心，其由 SAP NetWeaver 及 SAP HANA 的數個「SAP 基礎架構即服務 (IaaS)」認證伺服器組成。圖表中的伺服器或虛擬機器可以不同，視您的環境及您正在使用的資料庫技術而定。此外，架構概觀中的 SAP HANA 資料也會從主要資料中心傳送至次要資料中心，以進行災難回復 (DR)。其他資料庫也容許如圖 1 的設定，但這些設定會有所不同。

在圖 1 的 DR 資料中心網站上，抄寫的系統會配置為維護 DR 功能，這些功能需要在不同層上實作。如需相關資訊，請參閱[災難回復考量](/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#dr)。 

圖 1. 範例參照架構

![圖 1. 範例參照架構](/images/ref_architecture.png "範例參照架構")

## SAP 系統
{: #sap-systems}

SAP 系統（「進階商業應用程式設計 (ABAP)」、Java 及 SAP HANA）具有一組精細的授權物件，適用於使用者管理。因此，只需設定從桌上型電腦或其他前端系統裝置至 {{site.data.keyword.cloud_notm}} 型環境的遠端存取。在雲端環境中，不需要授與及管理一般使用者存取權。可能有數個具有不同責任的使用者，他們需要根據指令行層次或要求「遠端桌面通訊協定」型存取的延遲限制，透過特定 GUI 存取資料庫。若要管理此類型的遠端存取，可在環境中部署「跳躍主機」，充當這些類型之情境的存取中心點。除了這些特定需求外，使用者還可以存取組織網路內的雲端型系統，而不需要以任何特定方式加以管理。

## 網路
{: #network}

可以訂購 {{site.data.keyword.cloud_notm}} 環境中的任何裝置，其選擇有內部存取及選用的外部 LAN 存取。外部位址是可遞送的公用 IP 位址，應該要小心處理。內部位址是由訂購的 VLAN 所決定，並選自 VLAN 的子範圍 10.0.0.0/8。藉由訂購多個 VLAN，可以根據您的網路設計及安全需求，隔離不同的環境或資料流量類型。

儘管已配置防火牆的公用介面可以涵蓋部分情境（例如，具有非重要資料之短期且快速的概念驗證原型），但是大部分情況應該考量使用防火牆裝置。範例參照架構會對映正式作業情境，因此公用網路介面將超出範圍。

## Vyatta 網路閘道
{: #vyatta}

Vyatta 提供軟體型虛擬路由器、虛擬防火牆/NAT，以及適用於 IPv4 與 IPv6 的 VPN 功能。如果使用者將在遠端連接至您的 {{site.data.keyword.cloud_notm}} 型系統，則這些裝置可以充當這兩個端對端 VPN 或是所謂「道路戰士 VPN」的端點（存取點）。可以使用不同類型的 VPN 技術（IPSec 或 SSL VPN 通道，例如 OpenVPN）。根據您所使用的 SAP 技術，這些 VPN 連線可以用來交互連接適用於傳統 GUI 技術，以及瀏覽器型 SAP UI5 技術的 SAP 系統（甚至與非 SAP 系統交互連接）。連接「Vyatta 閘道」背後的「SAP Web 分派器」容許使用進一步的特性，例如負載平衡或單一登入情境。如需「SAP Web 分派器」的相關資訊，請參閱[可用性](/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#availability)。

Vyatta 裝置可以部署在高可用性叢集配置中，頻寬最高可達 10 Gbps。如需相關資訊，請參閱 [Vyatta 閘道](https://console.bluemix.net/docs/infrastructure/subnets/about.html#vyatta-gateways)。

## Jump Box 伺服器
{: #juump_box}

SAP 系統具有內嵌式使用者管理，因此不需要集中化的使用者管理。當然，您可以設定集中化的使用者管理。如需相關資訊，請參閱[集中使用者管理](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm)。

Jumb Box 伺服器可讓您向特定使用者提供低階存取權，以透過指令行存取型工具或其他特殊用途工具（例如 SAP HANA Studio）來存取您的 {{site.data.keyword.cloud_notm}} 環境。資料庫管理工具以及獲授權可以存取工具的使用者是集中在 Jump Box 伺服器上管理。使用者可以從其桌上型電腦透過「遠端桌面通訊協定」（透過 VPN 閘道來遞送）登入您的 {{site.data.keyword.cloud_notm}} 環境。

## SAP 伺服器 - SAP HANA 及 SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}} 透過 {{site.data.keyword.cloud_notm}} for SAP Applications 供應項目，提供各種適用於 SAP HANA 及 SAP NetWeaver 的伺服器。這些伺服器是具有您選擇之作業系統 (OS)（Red Hat Linux、SUSE Linux、Microsoft Windows Server），或是搭配 VMware ESX Hypervisor 部署的 {{site.data.keyword.baremetal_short}}。如需 SAP NetWeaver 認證伺服器的詳細資料，請參閱 [SAP 附註 2414097](https://launchpad.support.sap.com/#/notes/2414097)。請注意，在 Hypervisor 上，您可以部署「SAP 附註 2414097」中列出的其中一個作業系統，作為來賓作業系統。 

SAP HANA 伺服器隨附有預先選取的儲存空間佈置，用來針對 SAP HANA 執行 SAP 的儲存空間「關鍵績效指標 (KPI)」。您無法變更這些佈置，而且也不會驅策您針對 SAP HANA 使用外部儲存空間。不同品質且可以透過不同通訊協定（NFS、CIFS、iSCSI）存取的外部儲存空間可用於備份及其他用途。此外，若為 SAP NetWeaver 伺服器，您可以選擇在外部儲存空間上執行其他支援的資料庫系統。

所有以 SAP HANA 或 SAP NetWeaver 為基礎的 SAP 軟體解決方案都包括整個 SAP Business Suite，而且 SAP S/4HANA 可以部署在 {{site.data.keyword.cloud_notm}} 環境中。如需這些項目以外的其他軟體元件，您必須聯絡「SAP 支援中心」。請遵循 SAP 調整大小處理程序，來決定您專案的正確伺服器大小，並從針對 SAP HANA 或 SAP NetWeaver 供應項目列出的伺服器中進行選擇。 

如需 SAP HANA 認證伺服器的相關資訊，請參閱[認證及支援的 SAP HANA 硬體目錄](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud)。

如需 SAP HANA 調整大小處理程序的相關資訊，請參閱 [4. 調整伺服器大小](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-size-server.html#size_the_server)。 

如需 SAP NetWeaver 調整大小處理程序的相關資訊，請參閱 [4. 調整伺服器大小](https://console.bluemix.net/docs/infrastructure/sap-netweaver/sap-size-server.html#size_the_server)。
