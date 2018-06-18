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

# 常见问题：大小调整和体系结构
{: #faqs_sizing}

## 什么是针对每个 SAP NetWeaver 认证 的 IBM Cloud 服务器的 SAP 应用标准性能值 (SAPS) 测量值（评价 SAPS 和核心）？

表 1 包含 SAP NetWeaver 认证的 {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} 的 SAP 测量值。

表 1：SAP NetWeaver 认证的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 的 SAP 测量值。

| **服务器类型** | **SAPS**| **RAM**| **核心数**| **SAPS/核心** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32| 10980| 32 GB| 4| 2688|
| BI.S1.NW128| 54130| 128 GB| 24| 2255|
| BI.S1.NW256| 55020| 256 GB| 24| 2293|
| BI.S2.NW512| 65520| 512 GB| 28| 2340|

## IBM Cloud SAP 认证的基础架构产品支持哪些数据库？

对于 SAP HANA 配置，SAP HANA 1.0 和 SAP HANA 2.0 是受支持的数据库平台。有关 SAP NetWeaver 的完整操作系统和数据库支持声明，请参阅 [SAP 注释 2414097](https://launchpad.support.sap.com/#/notes/2414097)。

## 可以对 SAP HANA 认证的 IBM Cloud 裸机服务器执行第 2 层配置（应用服务器和 SAP HANA 数据库）吗？

不能在同一个硬件上执行第 2 层配置。不过，可以使用 SAP NetWeaver 和 SAP HANA 配置的组合来执行第 2 层配置。

## 在用于 SAP NetWeaver 或 SAP HANA 的 IBM Cloud SAP 认证的基础架构上支持虚拟化 (VMware) 吗？

支持，{{site.data.keyword.cloud_notm}} SAP 认证的基础架构支持 VMware ESXi 用于 SAP NetWeaver 和 SAP HANA。值得注意的是，如果选择订购并实施运行 VMware 的服务器，那么正确调整和配置该服务器上的所有虚拟机，以符合 SAP 的限制和最佳实践是您的责任。有关其他信息，请参阅 [SAP 注释 2161991](https://launchpad.support.sap.com/#/notes/2161991)。

## 可以更改 SAP 认证的 IBM Cloud 裸机服务器的配置吗？

SAP HANA 认证的 {{site.data.keyword.baremetal_short}} 具有固定的处理器、RAM 和本地存储器配置，这些配置根据您选择的服务器确定，无法进行修改。可以配置用于网络、操作系统和监视服务的选项。

SAP NetWeaver 认证的 {{site.data.keyword.baremetal_short}} 具有固定的处理器和 RAM 配置；本地存储器可根据需要进行配置，以满足您的需求。可以配置用于网络、操作系统和监视服务的选项。

## 对于在 IBM Cloud SAP 认证的基础架构中部署 SAP 解决方案，有任何主要方法吗？

有，[SAP 最佳实践](https://help.sap.com/viewer/p/SAP_Best_Practices)提供了可在部署期间使用的选项。{{site.data.keyword.IBM_notm}} 还提供了云咨询服务。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} Advisory Services](https://www.ibm.com/us-en/marketplace/cloud-consulting-services)。

## 必须部署 SAP Solution Manager 和 SAProuter 吗？如果是，有建议的基础架构吗？

不是，在培训、沙箱或类似环境中工作时，部署 SAP Solution Manager 和 SAProuter 不是必需的。但是，最好在生产环境中部署这两个组件。

