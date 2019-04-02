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

# 常见问题：IBM Cloud SAP 认证的基础架构（自我管理）
{: #faqs}

## 什么是 IBM Cloud SAP 认证的基础架构？
{: faq}

{{site.data.keyword.cloud}} SAP 认证的基础架构是 {{site.data.keyword.cloud_notm}} for SAP Applications 产品的自我管理组件。此产品组件支持在 {{site.data.keyword.cloud_notm}} 上将 SAP NetWeaver 和 SAP HANA 作为自助服务基础架构即服务 (IaaS) 运行。

## SAP 认证的基础架构与 IBM Cloud for SAP Applications 产品有何不同？
{: faq}

{{site.data.keyword.cloud_notm}} for SAP Applications 产品具有多个组件；{{site.data.keyword.cloud_notm}} SAP 认证的基础架构是该产品的自我管理组件。有一个*受管服务*组件可用，该组件适用于在寻找受管操作系统 (OS) 服务一直到受管 SAP 基础服务的客户。{{site.data.keyword.cloud_notm}} SAP 认证的基础架构针对的是，希望管理从操作系统到 SAP 应用程序在内的基础架构的客户或业务合作伙伴。

## IBM Cloud Infrastructure 提供受管服务吗？
{: faq}

提供，{{site.data.keyword.IBM_notm}} 通过 {{site.data.keyword.cloud_notm}} for SAP Applications 产品，为操作系统、数据库和 SAP 提供受管服务。有关更多信息，请参阅 [Managed Services for SAP Applications ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/sap/managed){: new_window}。

## SAP 可以在任何 IBM Cloud 服务器上运行吗？
{: faq}

不能，只有通过 SAP 认证的服务器型号才能用于运行 SAP HANA 或 SAP NetWeaver。

## 哪些服务器已通过认证，可在 IBM Cloud Infrastructure 中用于 SAP？
{: faq}  

有关通过认证可用于 SAP 工作负载的服务器的最新列表，请参阅 [SAP 认证的基础架构 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/bare-metal-servers/sap){: new_window}。

## 哪种类型的 SAP 工作负载可以在 IBM Cloud Infrastructure 上运行？
{: faq}

目前，用于非生产和生产用途的 SAP NetWeaver 应用程序和 SAP HANA 的工作负载可以在 {{site.data.keyword.cloud_notm}} 基础架构上运行。

## SAP 支持哪些操作系统？
{: faq}

  * 对于基于 SAP NetWeaver 的应用程序，支持 Red Hat Enterprise Linux for SAP Business Applications 6.x、SUSE Enterprise Linux for SAP Applications 12 SP2 和 Microsoft Windows Server 2012+。
  * 对于 SAP HANA，支持 Red Hat Enterprise Linux for SAP HANA 7.4、SUSE Linux Enterprise Server for SAP HANA 12 SP2 和 VMware Server Virtualization 6.5。

## 我可以更改哪些服务器配置？
{: faq}

您可以添加大多数基础架构选项，例如连接的存储器、网络、安全性、监视、入侵检测、公共带宽和端口速度。CPU、RAM 和内部存储器根据您的服务器选择使用缺省值，并且无法在订购过程中或通过支持凭单进行更改。

## 如果我对 SAP 认证的服务器有进一步的问题，应该联系谁？
{: faq}

您的销售团队可以回答问题，另外还可选择其他 {{site.data.keyword.cloud_notm}} 支持选项，例如聊天室、电话和 [{{site.data.keyword.cloud_notm}} 文档](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)。

## 有服务责任矩阵显示 IBM、客户和业务合作伙伴执行的管理任务吗？
{: faq}

{{site.data.keyword.cloud_notm}} SAP 认证的基础架构是一种自我管理产品。所有基础架构管理都由客户和业务合作伙伴负责。
