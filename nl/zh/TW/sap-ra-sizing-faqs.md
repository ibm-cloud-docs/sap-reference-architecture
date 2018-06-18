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

# 常見問題：調整大小及架構
{: #faqs_sizing}

## 哪些「SAP 應用程式效能標準 (SAPS)」措施適用於每個 SAP NetWeaver 認證的 IBM Cloud 伺服器（評定 SAPS 及核心）？

表 1. 包含適用於 SAP NetWeaver 認證之 {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} 的 SAP 措施。

表 1. 適用於 SAP NetWeaver 認證之 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 的 SAP 措施。

| **伺服器類型** | **SAPS** | **RAM** | **核心** | **SAPS/核心** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2688 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2293 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |

## 「IBM Cloud SAP 認證基礎架構」供應項目支援哪些資料庫？

對於 SAP HANA 配置，SAP HANA 1.0 及 SAP HANA 2.0 是支援的資料庫平台。如需 SAP NetWeaver 的完整作業系統及資料庫支援聲明，請參閱 [SAP 附註 2414097](https://launchpad.support.sap.com/#/notes/2414097)。

## 可以利用 SAP HANA 認證的「IBM Cloud 裸機伺服器」完成「層級 2」配置（應用程式伺服器加上 SAP HANA 資料庫）嗎？

無法在相同的硬體部分上完成「層級 2」配置。不過，可以使用 SAP NetWeaver 與 SAP HANA 配置的組合來完成。

## 在適用於 SAP NetWeaver 或 SAP HANA 的 IBM Cloud SAP 認證基礎架構上，是否支援虛擬化 (VMware)？

是，{{site.data.keyword.cloud_notm}} SAP 認證基礎架構支援適用於 SAP NetWeaver 及 SAP HANA 的 VMware ESXi。請務必注意，如果您選擇訂購及實作執行 VMware 的伺服器，則對伺服器上的所有虛擬機器進行適當的大小調整及配置，以符合 SAP 的限制及最佳作法，這都是您的責任。如需相關資訊，請參閱 [SAP 附註 2161991](https://launchpad.support.sap.com/#/notes/2161991)。

## 可以變更 SAP 認證的「IBM Cloud 裸機伺服器」的配置嗎？

根據您選擇的伺服器，SAP HANA 認證的 {{site.data.keyword.baremetal_short}} 具有處理器、RAM 及本端儲存空間的固定配置，而且無法修改。可以配置網路、作業系統及監視服務的選項。

SAP NetWeaver 認證的 {{site.data.keyword.baremetal_short}} 具有處理器及 RAM 的固定配置；可以視需要配置本端儲存空間，以符合您的需求。可以配置網路、作業系統及監視服務的選項。

## 有任何先進方法可藉以在 IBM Cloud SAP 認證基礎架構中部署 SAP 解決方案嗎？

有，[SAP 最佳作法](https://help.sap.com/viewer/p/SAP_Best_Practices)提供您可在部署期間使用的選項。{{site.data.keyword.IBM_notm}} 也提供雲端諮詢服務。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 諮詢服務](https://www.ibm.com/us-en/marketplace/cloud-consulting-services)。

## 是否必須部署 SAP Solutions Manager 及 SAProuter？若是，有任何建議的基礎架構嗎？

否，使用訓練、沙盤推演或類似環境時，部署 SAP Solutions Manager 及 SAProuter 不是必要動作。不過，最好將這些元件部署在您的正式作業環境中。

