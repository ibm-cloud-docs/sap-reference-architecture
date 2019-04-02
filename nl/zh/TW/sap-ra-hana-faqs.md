---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Multitenant Database Containers, MDC, database, SAP HANA

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 常見問題：SAP HANA
{: #hana-faqs}

## 有哪些 IBM Cloud 裸機伺服器大小可供 SAP HANA 使用？
{: faq}

SAP 認證的 {{site.data.keyword.baremetal_long}} 有下列 RAM 大小可用：
* 512 GB
* 1024 GB (1 TB)
* 2048 GB (2 TB)
* 4096 GB (4 TB)
* 6144 GB (6 TB)
* 8192 GB (8 TB)
* 12288 GB (12 TB)

## IBM Cloud 基礎架構中支援哪些硬體共用選項？例如，「虛擬 HANA」及「多方承租戶資料庫容器 (MDC)」。
{: faq}

「{{site.data.keyword.cloud_notm}} SAP 認證基礎架構」供應項目是 SAP 所認證的裸機伺服器部署，而且不包含虛擬化。您有責任確定此基礎架構上的任何變更依然符合 SAP 認證。

## 如何在 IBM Cloud 上部署 SAP HANA？
{: faq}

[{{site.data.keyword.cloud_notm}} 上的 SAP HANA](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started) 中有實作步驟的說明。因為這是自行管理的供應項目，所以您要負責在 {{site.data.keyword.cloud_notm}} 中實作 SAP HANA。{{site.data.keyword.IBM_notm}} 確實會提供諮詢及受管理 SAP 服務來協助您。如需相關資訊，請參閱 [Managed Services for SAP Applications ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/sap/managed){: new_window}。

## SAP HANA 支援橫向擴充嗎？
{: faq}

是。如需相關資訊，請參閱[配置 {{site.data.keyword.cloud_notm}} 基礎架構以支援 SAP HANA 多節點](/docs/infrastructure/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage)。

## SAP Business Suite on HANA 支援的伺服器大小上限為何？
{: faq}

8 TB 是支援 SAP Business Suite on HANA 的 IaaS 認證伺服器大小上限。12 TB 是根據 HANA TDI v5 提供給核准的工作負載。

##  SAP Business Warehouse on HANA 支援的伺服器大小上限為何？
{: faq}

4 TB 是支援 SAP Business Warehouse on HANA 的 IaaS 認證伺服器大小上限。

## 如何備份我的 SAP HANA 認證伺服器？
{: faq}

自行管理的供應項目中不包含伺服器備份。在 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站中，有一些您可在伺服器訂購過程期間選取的選項。您也有整合協力廠商備份解決方案的選項。

## 如何將現有的 SAP HANA 資料庫或關聯式資料庫移轉至 IBM Cloud 中的 SAP HANA 認證伺服器？
{: faq}

自行管理服務未隨附任何移轉服務；任何移轉活動都是您的責任。{{site.data.keyword.IBM_notm}} 確實會提供一系列諮詢及受管理服務，可在 SAP 移轉規劃及執行時協助您。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} Advisory Services ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.com/us-en/marketplace/cloud-consulting-services){: new_window}。請選取 *Services* > *Cloud Services*。

## 是否支援 SAP HANA 2.0 作為「IBM Cloud SAP 認證基礎架構」供應項目的一部分？
{: faq}

是，如果您訂購的 SAP 認證伺服器具有符合 SAP HANA 2.0 標準的作業系統，則支援 SAP HANA 2.0。如需相關資訊，請參閱 [SAP 附註 2235581 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://launchpad.support.sap.com/#/notes/2235581){: new_window}。
