---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, database

subcollection: sap-reference-architecture, Frequently Asked Questions, FAQs

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 常見問題：IBM Cloud SAP 認證基礎架構（自行管理）
{: #faqs}

## 何謂 IBM Cloud SAP 認證基礎架構？
{: faq}

「{{site.data.keyword.cloud}} SAP 認證基礎架構」是 {{site.data.keyword.cloud_notm}} for SAP Applications 供應項目的自行管理元件。供應項目的這個元件可讓您在 {{site.data.keyword.cloud_notm}} 上執行 SAP NetWeaver 及 SAP HANA，作為自助式「基礎架構即服務 (IaaS)」。

## 「SAP 認證基礎架構」與 IBM Cloud for SAP Applications 供應項目有何不同？
{: faq}

{{site.data.keyword.cloud_notm}} for SAP Applications 供應項目具有多個元件；「{{site.data.keyword.cloud_notm}} SAP 認證基礎架構」是供應項目的自行管理元件。有*受管理服務* 元件可供使用，其預期對象為正在尋找「受管理作業系統 (OS)」服務直到「受管理 SAP 基準」服務的客戶。「{{site.data.keyword.cloud_notm}} SAP 認證基礎架構」的對象為想要管理從作業系統至 SAP 應用程式之基礎架構的客戶或「事業夥伴」。

## 受管理服務是否可與 IBM Cloud 基礎架構搭配使用？
{: faq}

是，{{site.data.keyword.IBM_notm}} 可以透過 {{site.data.keyword.cloud_notm}} for SAP Applications 供應項目對作業系統、資料庫及 SAP 提供受管理服務。如需相關資訊，請參閱 [Managed Services for SAP Applications ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/sap/managed){: new_window}。

## SAP 是否可在任何 IBM Cloud 伺服器上執行？
{: faq}

否，只有針對 SAP 認證的伺服器機型才能用來執行 SAP HANA 或 SAP NetWeaver。

## 哪些伺服器已認證可在 IBM Cloud 基礎架構中與 SAP 搭配使用？
{: faq}  

如需已認證可與 SAP 工作負載搭配使用之伺服器的現行清單，請參閱 [SAP-certified infrastructure ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/bare-metal-servers/sap){: new_window}。

## 哪種類型的 SAP 工作負載可在 IBM Cloud 基礎架構上執行？
{: faq}

目前，針對非正式作業與正式作業使用之 SAP NetWeaver 應用程式及 SAP HANA 的工作負載可在 {{site.data.keyword.cloud_notm}} 基礎架構上執行。

## SAP 支援哪些作業系統？
{: faq}

  * 若為 SAP NetWeaver 型應用程式，支援 Red Hat Enterprise Linux for SAP Business Applications 6.x、SUSE Enterprise Linux for SAP Applications 12 SP2 及 Microsoft Windows Server 2012 以上版本。
  * 若為 SAP HANA，支援 Red Hat Enterprise Linux 7.4 for SAP HANA、SUSE Linux Enterprise Server 12 SP2 for SAP HANA 及 VMware Server Virtualization 6.5。

## 我可以變更哪些伺服器配置？
{: faq}

您可以新增大部分的基礎架構選項，例如連接儲存空間、網路、安全、監視、侵入偵測、公用頻寬，以及埠速度。CPU、RAM 及內部儲存空間預設為根據伺服器選項，因此無法在訂購過程期間或透過支援問題單進行變更。

## 如果對 SAP 認證伺服器有進一步的問題，我可以跟誰聯絡？
{: faq}

您的銷售團隊可以回答問題，另外還有其他 {{site.data.keyword.cloud_notm}} 支援選項，例如會談、電話及 [{{site.data.keyword.cloud_notm}} 文件](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)。

## 有服務責任矩陣顯示 IBM、客戶及「事業夥伴」所執行的管理作業嗎？
{: faq}

「{{site.data.keyword.cloud_notm}} SAP 認證基礎架構」是自行管理的供應項目。所有基礎架構管理都是客戶及「事業夥伴」的責任。
