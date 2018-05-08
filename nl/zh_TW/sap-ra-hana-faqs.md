---



copyright:
  years: 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 常見問題：SAP HANA
{: #hana-faqs}

## 有哪些 IBM Cloud 裸機伺服器大小可供 SAP HANA 使用？

SAP 認證的 {{site.data.keyword.baremetal_long}} 有下列 RAM 大小可用：
  * 512 GB
  * 1 TB
  * 2 TB
  * 4 TB
  * 8 TB
  
## IBM Cloud 基礎架構中支援哪些硬體共用選項？例如，「虛擬 HANA」及「多方承租戶資料庫容器 (MDC)」。

「{{site.data.keyword.cloud_notm}} SAP 認證基礎架構」供應項目是 SAP 所認證的裸機伺服器部署，而且不包含虛擬化。您有責任確定此基礎架構上的任何變更依然符合 SAP 認證。

## 如何在 IBM Cloud 上部署 SAP HANA？

[{{site.data.keyword.cloud_notm}} 上的 SAP HANA](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started) 中有實作步驟的說明。因為這是自行管理的供應項目，所以您要負責在 {{site.data.keyword.cloud_notm}} 中實作 SAP HANA。{{site.data.keyword.IBM_notm}} 確實會提供諮詢及受管理 SAP 服務來協助您。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed)。

## SAP HANA 支援橫向擴充嗎？

目前 SAP HANA 不支援橫向擴充。

## SAP Business Suite on HANA 支援的伺服器大小上限為何？

8 TB 是支援 SAP Business Suite on HANA 的伺服器大小上限。

##  SAP Business Warehouse on HANA 支援的伺服器大小上限為何？

4 TB 是支援 SAP Business Warehouse on HANA 的伺服器大小上限。

## 如何備份我的 SAP HANA 認證伺服器？

自行管理的供應項目中不包含伺服器備份。在 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站中，有一些您可在伺服器訂購過程期間選取的選項。您也有整合協力廠商備份解決方案的選項。

## 如何將現有的 SAP HANA 資料庫或關聯式資料庫移轉至 IBM Cloud 中的 SAP HANA 認證伺服器？

自行管理服務未隨附任何移轉服務；任何移轉活動都是您的責任。{{site.data.keyword.IBM_notm}} 確實會提供一系列諮詢及受管理服務，可在 SAP 移轉規劃及執行時協助您。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 諮詢服務](https://ibm.com/us-en/marketplace/cloud-consulting-services)。

## 是否支援 SAP HANA 2.0 作為「IBM Cloud SAP 認證基礎架構」供應項目的一部分？

是，如果您訂購的 SAP 認證伺服器具有符合 SAP HANA 2.0 標準的作業系統，則支援 SAP HANA 2.0。如需相關資訊，請參閱 [SAP 附註 2235581](https://launchpad.support.sap.com/#/notes/2235581)。
