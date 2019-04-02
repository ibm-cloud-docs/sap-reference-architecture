---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, relational database management systems, RDBMS, SAP Web Dispatcher, SAP NetWeaver Application Servers, application servers, database, high availability, disaster recovery

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud SAP 参考体系结构入门
{: #getting-started}

{{site.data.keyword.cloud}} 体系结构提供了多种卓越的技术能力，例如对云基础架构至关重要的软件可定义环境、可编程接口以及数百种硬件和网络配置。此体系结构旨在提供更高级别的灵活性（将虚拟和专用服务器混合使用，以适应各种工作负载）、接口自动化和混合部署选项。用于 SAP HANA 和 SAP NetWeaver 的 {{site.data.keyword.cloud_notm}} SAP 认证的基础架构产品为您提供了最佳匹配选择。此选择包括裸机和基于虚拟化的服务器，SAP 软件堆栈会在其上运行。

## 参考体系结构
{: #ref-arch}

图 1 是面向一种格局的参考体系结构 (RA)，该格局由以下部分组成：

  * Vyatta 网络组件
  * SAP Web 分派器
  * SAP NetWeaver 应用程序服务器
  * SAP HANA 数据库
  * 其他关系数据库管理系统 (RDBMS)

示例 RA 配置为具有高可用性和灾难恢复功能。请注意，在图 1 中，数据库服务器可以是 SAP NetWeaver 支持的任何数据库系统，例如 SAP HANA。

图 1. 样本参考体系结构

![图 1. 样本参考体系结构](/images/SAP-optimization-ref-architecture-20180527.png "样本参考体系结构")
