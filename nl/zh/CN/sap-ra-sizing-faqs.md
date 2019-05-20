---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

keywords: SAP Reference Architecture, SAP Application Performance Standard, SAPS, application servers, database, SAProuter

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 常见问题：大小调整和体系结构
{: #faqs_sizing}

## 什么是针对每个 SAP NetWeaver 认证的 IBM Cloud 服务器的 SAP 应用程序性能标准 (SAPS) 测量值（评价 SAPS 和核心）？
{: faq}

表 1 包含 SAP NetWeaver 认证的 {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} 的 SAP 测量值。

表 1：SAP NetWeaver 认证的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 的 SAP 测量值。

|**服务器类型** |**SAPS**|**RAM**|**核心数**|**SAPS/核心** |
| --- | --- | --- | --- | --- |
|BI.S1.NW32|10980|32 GB|4| 2745 |
|BI.S1.NW128|54130|128 GB|24|2255|
|BI.S1.NW256|55020|256 GB|24| 2292 |
|BI.S2.NW512|65520|512 GB|28|2340|
| BI.S3.NW32 | 11970 |32 GB|4| 2992 |
| BI.S3.NW64 | 12750 | 64 GB |4| 3187 |
| BI.S3.NW192 | 78850 | 192 GB | 36 | 2190 |
| BI.S3.NW384 | 79430 | 384 GB | 36 | 2203 |
| BI.S3.NW768 | 79630 | 768 GB | 36 | 2211 |

## IBM Cloud SAP 认证的基础架构产品支持哪些数据库？
{: faq}

对于 SAP HANA 配置，SAP HANA 1.0 和 SAP HANA 2.0 是受支持的数据库平台。有关 SAP NetWeaver 的完整操作系统和数据库支持声明，请参阅 [SAP Note 2414097 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}。

## 可以对 SAP HANA 认证的 IBM Cloud 裸机服务器执行第 2 层配置（应用服务器和 SAP HANA 数据库）吗？
{: faq}

不能在同一个硬件上执行第 2 层配置。不过，可以使用 SAP NetWeaver 和 SAP HANA 配置的组合来执行第 2 层配置。

## 在 IBM Cloud SAP 认证的基础架构上支持将虚拟化 (VMware) 用于 SAP NetWeaver 或 SAP HANA 吗？
{: faq}

支持，{{site.data.keyword.cloud_notm}} SAP 认证的基础架构支持 VMware ESXi 用于 SAP NetWeaver 和 SAP HANA。值得注意的是，如果选择订购并实施运行 VMware 的服务器，那么您要负责对该服务器上的所有虚拟机正确调整大小和进行配置，以符合 SAP 的限制和最佳实践。有关其他信息，请参阅 [SAP Note 2161991 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/2161991){: new_window}。

## 可以更改 SAP 认证的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 的配置吗？
{: faq}

SAP HANA 认证的 {{site.data.keyword.baremetal_short}} 具有固定的处理器、RAM 和本地存储器配置，这些配置根据您选择的服务器确定，无法进行修改。可以配置用于网络、操作系统和监视服务的选项。

SAP NetWeaver 认证的 {{site.data.keyword.baremetal_short}} 具有固定的处理器和 RAM 配置；本地存储器可根据需要进行配置，以满足您的需求。可以配置用于网络、操作系统和监视服务的选项。

## 对于在 {{site.data.keyword.cloud_notm}} SAP 认证的基础架构中部署 SAP 解决方案，有任何主要方法吗？
{: faq}

有，[SAP Best Practices ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.sap.com/viewer/p/SAP_Best_Practices){: new_window} 提供了可在部署期间使用的选项。{{site.data.keyword.IBM_notm}} 还提供了云咨询服务。有关更多信息，请参阅 [ SAP-certified infrastructure ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/sap/certified-infrastructure){: new_window}。

## 必须部署 SAP Solution Manager 和 SAProuter 吗？如果是，有建议的基础架构吗？
{: faq}

不是，在训练、沙箱或类似环境中工作时，部署 SAP Solution Manager 和 SAProuter 不是必需的。但在生产环境中最好部署这两个组件。
