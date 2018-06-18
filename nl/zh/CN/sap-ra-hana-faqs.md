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

# 常见问题：SAP HANA
{: #hana-faqs}

## 可用于 SAP HANA 的 IBM Cloud 裸机服务器大小是多少？

SAP 认证的 {{site.data.keyword.baremetal_long}} 提供以下 RAM 大小：
  * 512 GB
  * 1 TB
  * 2 TB
  * 4 TB
  * 8 TB
  
## IBM Cloud 基础架构中支持哪些硬件共享选项？例如，虚拟 HANA 和多租户数据库容器 (MDC)。

{{site.data.keyword.cloud_notm}} SAP 认证的基础架构产品是通过 SAP 认证的裸机服务器部署，不包括虚拟化。确保基于此基础架构进行的任何更改都符合 SAP 认证是您的责任。

## 如何在 IBM Cloud 上部署 SAP HANA？

[{{site.data.keyword.cloud_notm}} 上的 SAP HANA](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started) 中描述了实施步骤。由于这是一个自我管理产品，因此在 {{site.data.keyword.cloud_notm}} 中实施 SAP HANA 是您的责任。{{site.data.keyword.IBM_notm}} 可提供咨询和受管 SAP 服务来为您提供帮助。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed)。

## SAP HANA 支持向外扩展吗？

目前，SAP HANA 不支持向外扩展。

## 对于 SAP Business Suite on HANA，支持的最大服务器大小是多少？

支持 SAP Business Suite on HANA 的最大服务器大小是 8 TB。

##  对于 SAP Business Warehouse on HANA，支持的最大服务器大小是多少？

支持 SAP Business Warehouse on HANA 的最大服务器大小是 4 TB。

## 如何备份 SAP HANA 认证服务器？

自我管理产品中不包含服务器备份。在 {{site.data.keyword.cloud_notm}} 基础架构客户门户网站中订购服务器的过程中，有一些相关选项可供选择。还可以选择集成第三方备份解决方案。

## 如何将现有 SAP HANA 数据库或关系数据库迁移到 IBM Cloud 中 SAP HANA 认证的服务器？

自我管理服务不随附迁移服务；执行任何迁移活动都是您的责任。{{site.data.keyword.IBM_notm}} 提供有一系列咨询和受管服务，可以帮助您计划和执行 SAP 迁移。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} Advisory Services](https://ibm.com/us-en/marketplace/cloud-consulting-services)。

## SAP HANA 2.0 是作为 IBM Cloud SAP 认证的基础架构产品的一部分进行支持吗？

是的，如果订购的 SAP 认证的服务器使用与 SAP HANA 2.0 兼容的操作系统，那么支持 SAP HANA 2.0。有关更多信息，请参阅 [SAP 注释 2235581](https://launchpad.support.sap.com/#/notes/2235581)。
