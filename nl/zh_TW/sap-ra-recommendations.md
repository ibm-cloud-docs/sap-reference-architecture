---



copyright:
  years: 2018
lastupdated: "2018-03-28"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud 環境的 SAP 指引
{: #recommendations}

您的需求可能不同於所提供的指引；不過，它可以充當您在 {{site.data.keyword.cloud}} 環境中建置 SAP 認證伺服器的起點。

圖 1. 範例參照架構

![圖 1. 範例參照架構](/images/ref_architecture.png "範例參照架構")

## VLAN
{: #vlans}

架構圖設計的 SAP 準則建議隔離不同網路介面控制器 (NIC) 上的伺服器資料流量。例如，商業資料應該與管理及備份資料流量區隔。將多個 NIC 指派給不同子網路可啟用此資料隔離功能。如需相關資訊，請參閱[針對 SAP NetWeaver 及 SAP HANA 建置高可用性](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf) (PDF) 中的『網路』一節。

為了遵循 NIC 建議，{{site.data.keyword.cloud_notm}} 容許在伺服器上配置多個 VLAN。VLAN 介面可以設為高可用性 (HA)，方法是在結合介面 (Linux) 或團隊介面 (Microsoft Windows) 下配置多個 NIC。對於 {{site.data.keyword.baremetal_short}} 上的 HA 及災難回復 (DR) 功能，最好的方式為保留其他 IP 位址，並在實作服務時，將這些位址指派給不同的 SAP 服務。請參閱 SAP 安裝文件，以取得如何在安裝期間利用 SAP Software Provisioning Manager (SWPM) 來指派位址的支援。若為虛擬機器 (VM)，VM 主要介面的位址通常就足夠了。

依預設，{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 具有公用及專用介面。通常，不建議保留針對 {{site.data.keyword.cloud_notm}} 基礎架構中所有伺服器所配置的公用 LAN。必要的話，應該部署「Vyatta 網路閘道」的特定實例，以容許對環境的公用存取。如需相關資訊，請參閱 [Vyatta 網路閘道](/docs/infrastructure/sap-reference-architecture/sap-ra-architecture.html#vyatta)。 

## {{site.data.keyword.cloud_notm}} 儲存空間
{: #storage}

針對 SAP NetWeaver 認證的 {{site.data.keyword.cloud_notm}} 伺服器可以配置有不同數目的內部磁碟，以及供那些磁碟進行 RAID 配置的不同佈置。請注意，這些佈置可能不足以滿足專案需求，例如大小不足或對儲存空間共用存取。

儲存空間需求會有所不同，因為指引的目的在於根據備份及還原時段、高可用性及失效接手需求，清楚定義專案「關鍵績效指標 (KPI)」，然後決定要使用的儲存空間類型。涵蓋所有選項超出此內容的範圍；不過，可以提供部分指引。

  * 搭配在節點之間進行失效接手的資料庫，使用共用的 iSCSI 裝置進行 HA 設定。您將需要查看所需的 IOPS/秒上限。
  
  * 搭配抄寫的資料庫，使用內部儲存空間進行 HA 設定；例如，SAP HANA 系統抄寫。SAP NetWeaver 應用程式伺服器可位於內部儲存空間，或位於共用的網路連結儲存空間 (NAS)。
  
  * 利用 VMware 型安裝，使用共用儲存空間來協助失效接手功能。如需選取正確儲存空間類型的相關資訊，請參閱[要與 VMware 系統搭配使用的儲存空間](https://console.bluemix.net/docs/infrastructure/vmware/select-storage-option-use-vmware.html#storage-to-use-with-vmware-systems)。
  
所有選項都可以從 {{site.data.keyword.cloud_notm}} 基礎架構內進行選取。

## 高可用性
{: #availability}

在集中化資料庫上進行 SAP 應用程式的分散式安裝時，會抄寫基礎安裝來達到高可用性。對於每一個架構層，高可用性設計會有所不同。 

  * **SAP Web 分派器**。達到高可用性的方式為具有多個備用「SAP Web 分派器」實例與 SAP 應用程式資料流量搭配。「SAP Web 分派器」會充當一組 SAP 系統及其他 `https` 型服務的潛在進入點。通常它會位於網際網路與後端系統之間，並處理來自「外界」的 Web 通訊協定型要求。「SAP Web 分派器」的運作方式如同反向 Proxy 一般，但具有各種支援的特性，例如負載平衡及 Single Sign On。如需相關資訊，請參閱 [SAP Web 分派器](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm)。
  
  * **ABAP SAP 中央服務 (ASCS)**。如需 {{site.data.keyword.cloud_notm}} 環境中 ASCS 的高可用性，必須安裝目標作業系統的叢集軟體，例如 Linux Pacemaker 或 Microsoft Cluster。ASCS（SAP 的移入佇列服務）的單一失敗點需要配置為將其資料抄寫至「移入佇列抄寫服務 (ERS)」。ERS 實例需要安裝為 SAP 安裝處理程序的一部分，並受到 SAP 的 SWPM 支援，如需安裝及配置 ASCS 及 ERS 之叢集元件的詳細資料，請參閱作業系統供應商之供應項目的文件。
  
  * **SAP NetWeaver 應用程式伺服器**。高可用性是藉由應用程式伺服器之儲存區內的負載平衡資料流量來達到。如果只需有限數量的資源，可將單一應用程式伺服器配置為具有高可用性。安裝應用程式伺服器時，需要搭配所有潛在叢集節點可存取的儲存空間（可用於失效接手）。此外，SAP NetWeaver 堆疊需要使用虛擬主機名稱。請參閱作業系統供應商的作業系統文件，以取得必要配置的詳細資料，並參閱 SAP 文件，以取得高可用性的詳細資料。如果您的配置需要多部應用程式伺服器，則 SAP 應用程式伺服器的配置也需要涵蓋 SAP 登入群組及 RFC 伺服器群組中的負載平衡（舉例來說）。如需相關資訊，請參閱 SAP NetWeaver 版本的管理手冊。
  
  * **資料庫層級**。範例參照架構會部署單一 SAP HANA 或其他資料庫實例。如需高可用性，請部署多個實例，並使用「HANA 系統抄寫 (HSR)」來實作手動失效接手。若要啟用自動失效接手，需要特定 Linux 發行套件的高可用性延伸。若為其他資料庫，可以配置共用儲存空間上資料庫實例的失效接手，或者可以使用與 SAP HANA 案例類似的抄寫技術。請參閱所支援之資料庫系統的文件，以取得設定高可用性或抄寫所需的選項集。
  
## 災難回復
{: #dr}

每個層級都會使用不同的策略來提供災難回復保護。

 * **SAP NetWeaver 應用程式伺服器**。SAP 應用程式伺服器不包含任何商業資料；不過，需要保留伺服器的安裝與配置，才能在災難之後繼續作業。其中一個災難回復策略為在另一個地區具有 SAP 應用程式伺服器。對配置所做的任何變更，或主要應用程式上的任何核心更新都必須複製到災難回復地區中的虛擬機器或伺服器。
 
 * **SAP 中央服務 (SCS)**。SAP 應用程式堆疊的 SCS 元件不會持續保存商業資料。您可以在災難回復地區中建置伺服器或 VM 來執行 SCS 角色。來自主要 SCS 附註且要同步化的唯一內容為 `/sapmnt` 共用內容。此外，如果主要 SCS 伺服器上發生配置變更或核心更新，則必須在災難回復 SCS 上抄寫這些變更。若要同步化兩部伺服器，請使用定期排定的複製工作，將 `/sapmnt` 複製到災難回復伺服器。如需 SCS 的相關資訊，請參閱[中央服務實例](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm)。
 
 * **資料庫層級**。若為 SAP HANA 型系統，請使用 HANA 支援的抄寫解決方案，例如「HANA 系統抄寫」或 {{site.data.keyword.cloud_notm}} 儲存空間抄寫特性能。若為其他支援的資料庫，請參閱資料庫文件以取得其支援特性。通常，從可用選項進行選擇需要清楚瞭解基礎 SAP 應用程式的商業需求。需要判斷可能失去單一交易或甚至是時間範圍內所有資料的影響。 
 
 * **基礎架構**。根據 SAP 用戶端位於 {{site.data.keyword.cloud_notm}} 基礎架構中的位置，需要針對災難回復情境準備其中的其他元件。在範例參照架構中，用戶端會從內部部署端，或從客戶的組織網路內存取 SAP 系統。
 
## 安全
{: #security}

### 使用者管理

SAP 具有自己的「使用者管理引擎 (UME)」，利用 SAP 應用程式來控制角色型存取及授權。如需相關資訊，請參閱 [SAP HANA 安全 - 概觀](https://archive.sap.com/documents/docs/DOC-62943)。從使用者管理觀點來看，如果您的 SAP 系統執行內部部署 {{site.data.keyword.cloud_notm}}，則不相關。該規則的例外已在 [Jump Box 伺服器](/docs/infrastructure/sap-reference-architecture/sap-ra-architecture.html#juump_box)下提及。

### 網路安全

因為有不同方式供您存取 {{site.data.keyword.cloud_notm}} 型環境，所以需要區分安全措施。

只有在概念驗證類型部署中，才應該考量使用公用介面進行外部存取。對於正式作業情境，可以部署 Vyatta 應用裝置，因為應用裝置配有所有必要功能（VPN 防火牆等等）。如果 Vyatta 應用裝置未符合延遲及（或）傳輸量需求，請聯絡「{{site.data.keyword.cloud_notm}} 支援中心」，以討論 Vyatta 應用裝置以外所有可行的步驟及配置。 
  
