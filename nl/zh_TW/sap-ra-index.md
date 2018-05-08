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

# 開始使用 IBM Cloud SAP 參照架構
{: #getting-started}

{{site.data.keyword.cloud}} 架構提供更為卓越的技術功能，例如對雲端基礎架構、可程式設計介面，以及數百種硬體與網路配置至關重要的軟體可定義環境。其設計旨在提供更高層次的彈性（藉由混合虛擬及專用伺服器以符合各種工作負載）、介面自動化，以及混合式部署選項。適用於 SAP HANA 與 SAP NetWeaver 的「{{site.data.keyword.cloud_notm}} SAP 認證基礎架構」供應項目會為您提供最適合的選項。此選項包含 SAP 軟體堆疊在其上執行的祼機及虛擬化型伺服器。

## 參照架構
{: #ref-arch}

圖 1 是架構圖的參照架構 (RA)，其中包含

  * Vyatta 網路元件
  * SAP Web 分派器
  * SAP NetWeaver 應用程式伺服器
  * SAP HANA 資料庫
  * 其他關聯式資料庫管理系統 (RDBMS) 
  
範例 RA 配置有高可用性及災難回復。請注意，在圖 1 中，資料庫伺服器可以是 SAP NetWeaver 支援的任何資料庫系統，例如 SAP HANA。 

圖 1. 範例參照架構

![圖 1. 範例參照架構](/images/ref_architecture.png "範例參照架構")
