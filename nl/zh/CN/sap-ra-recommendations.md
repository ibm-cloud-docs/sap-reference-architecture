---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Advanced Business Application Programming, ABAP, ABAP SAP Central Services, ASCS, SAP Central Services, SAP Software Provisioning Manager, SWPM, HANA System Replication, HSR, User Management Engine, UME, VLAN, SAP Web Dispatcher, SAP NetWeaver application servers, application servers, database, instance, load balancing, SAP logon groups, RFC server groups, high availability, highly available, HA, disaster recovery, DR, cluster software, Linux Pacemaker, virtual hostname

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud SAP 认证的基础架构指南
{: #recommendations}

您的需求可能与所提供的指南有所不同；不过，本指南可用作在 {{site.data.keyword.cloud}} 环境中构建 SAP 认证的服务器的起始点。

图 1. 样本参考体系结构

![图 1. 样本参考体系结构](/images/SAP-optimization-ref-architecture-20180527.png "样本参考体系结构")

## VLAN
{: #vlans}

SAP 的格局设计准则建议隔离不同网络接口控制器 (NIC) 上的服务器流量。例如，业务数据应该与管理和备份流量相隔离。将多个 NIC 分配给不同的子网可支持这种数据隔离。有关更多信息，请参阅 [Building High Availability for SAP NetWeaver and SAP HANA ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} (PDF) 中的 Network 部分。

为了遵循 NIC 建议，{{site.data.keyword.cloud_notm}} 支持在服务器上配置多个 VLAN。可以通过将多个 NIC 配置为位于结合接口 (Linux) 或组合接口 (Microsoft Windows) 下，从而使 VLAN 接口实现高可用性 (HA)。对于 {{site.data.keyword.baremetal_short}} 上的 HA 和灾难恢复 (DR) 功能，最好保留额外的 IP 地址，并在实现不同的 SAP 服务时，为这些服务分配保留的地址。有关如何在使用 SAP Software Provisioning Manager (SWPM) 进行安装期间分配地址，请查阅 SAP 安装文档以获取支持信息。对于虚拟机 (VM)，通常使用 VM 主界面的地址即可。

缺省情况下，{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 具有公共和专用接口。一般情况下，建议不要为 {{site.data.keyword.cloud_notm}} 基础架构中的所有服务器保持配置公共 LAN。应根据需要部署 Vyatta 网关的特定实例，以允许公众访问您的环境。有关更多信息，请参阅 [Vyatta 网关](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta)。

## {{site.data.keyword.cloud_notm}} 存储
{: #storage}

通过 SAP NetWeaver 认证的 {{site.data.keyword.cloud_notm}} 服务器可以配置使用不同数量的内部磁盘，并且这些磁盘可采用不同布局以实现 RAID 配置。请注意，这些布局可能不足以满足项目需求，例如大小不足或共享对存储器的访问权。

存储需求各不相同，因此指南会根据备份和恢复时隙、高可用性和故障转移需求，明确定义项目关键性能指标 (KPI)，然后确定要使用的存储类型。本指南的内容不会涵盖所有选项；但可以提供一些指导信息。

  * 使用共享 iSCSI 设备对在节点之间执行故障转移的数据库进行 HA 设置。您需要查看所需的最大 IOPS/秒。

  * 使用内部存储器对复制的数据库进行 HA 设置；例如，SAP HANA 系统复制。SAP NetWeaver 应用程序服务器可以位于内部存储器上，也可以位于共享网络连接存储器 (NAS) 上。

  * 使用共享存储器来帮助实现基于 VMware 的安装的故障转移功能。有关选择正确存储类型的更多信息，请参阅[用于 VMware 系统的存储](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems)。

所有选项都可在 {{site.data.keyword.cloud_notm}} 基础架构中进行选择。

## 高可用性
{: #availability}

在集中式数据库上分布式安装 SAP 应用程序时，会复制基本安装以实现高可用性。对于体系结构的每一层，高可用性设计各不相同。

  * **SAP Web 分派器**。通过对 SAP 应用程序流量使用多个冗余 SAP Web 分派器实例，可以实现高可用性。SAP Web 分派器可充当一组 SAP 系统和其他基于 `https` 的服务的潜在入口点。它通常位于因特网和后端系统之间，用于处理来自“外部世界”的基于网络协议的请求。SAP Web 分派器的工作方式类似于具有各种支持功能（如负载均衡和单点登录）的逆向代理。有关更多信息，请参阅 [SAP Web Dispatcher ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window}。

  * **ABAP SAP Central Services (ASCS)**。为了在 {{site.data.keyword.cloud_notm}} 环境中实现 ASCS 的高可用性，需要安装目标操作系统的集群软件，例如，Linux Pacemaker 或 Microsoft Cluster。ASCS（SAP 的排队服务）的单点故障需要配置为将其数据复制到排队复制服务 (ERS)。ERS 实例需要在 SAP 安装过程中进行安装，并且由 SAP 的 SWPM 进行支持。有关为 ASCS 和 ERS 安装和配置集群组件的详细信息，请查阅操作系统供应商的产品文档。

  * **SAP NetWeaver 应用程序服务器**。高可用性通过对应用服务器池内的流量进行负载均衡来实现。如果只需要有限数量的资源，那么可以将单个应用程序服务器配置为高可用性。应用程序服务器需要安装有可供所有潜在集群节点访问的存储器，以便可用于故障转移。另外，SAP NetWeaver 堆栈需要使用虚拟主机名。有关高可用性的必需配置和 SAP 文档的详细信息，请查阅操作系统供应商的操作系统文档。如果配置需要多个应用程序服务器，那么 SAP 应用程序服务器的配置也需要涵盖负载平衡，例如在 SAP 登录组和 RFC 服务器组中。有关更多信息，请参阅与您的 SAP NetWeaver 版本相对应的管理指南。

  * **数据库层**。示例参考体系结构部署了单个 SAP HANA（或其他数据库）实例。为了实现高可用性，请部署多个实例并使用 HANA System Replication (HSR) 来实施手动故障转移。要启用自动故障转移，需要针对特定 Linux 发行版的高可用性扩展。对于其他数据库，可以配置在共享存储器上进行数据库实例故障转移，也可以使用类似于 SAP HANA 情况的复制技术。设置高可用性或设置复制都需要一组选项，有关这些选项的信息，请参阅受支持数据库系统的文档。

  有关其他信息，请参阅[{{site.data.keyword.cloud_notm}}高可用性支持](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha)。

## 灾难恢复
{: #dr}

各层使用不同的策略来提供灾难恢复保护。

 * **SAP NetWeaver 应用程序服务器**。SAP 应用程序服务器不包含任何业务数据；但是，需要保留该服务器的安装和配置以便在发生灾难后持续运行。一种灾难恢复策略是在其他区域中具有 SAP 应用程序服务器。主应用程序服务器上的任何配置更改或内核更新，都必须复制到灾难恢复区域中的虚拟机或服务器。

 * **SAP Central Services (SCS)**。SAP 应用程序堆栈的 SCS 组件不会持久存储业务数据。您可以在灾难恢复区域中构建服务器或 VM 来运行 SCS 角色。主 SCS 注释中唯一要同步的内容是 `/sapmnt` 共享内容。另外，如果在主 SCS 服务器上执行配置更改或内核更新，那么必须在灾难恢复 SCS 上复制这些更改。要同步两台服务器，请使用定期复制作业将 `/sapmnt` 复制到灾难恢复服务器。有关 SCS 的更多信息，请参阅 [Central Services Instance ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window}。

 * **数据库层**。对于基于 SAP HANA 的系统，请使用 HANA 支持的复制解决方案，例如 HANA System Replication 或 {{site.data.keyword.cloud_notm}} 存储复制功能。对于其他受支持的数据库，请参阅数据库文档以获取其支持的功能。通常，从可用选项中进行选择时，需要清楚地了解底层 SAP 应用程序的业务需求。另外，还需要确定对单个事务潜在损失的影响，甚至还要确定对某个时间段内所有数据的影响。

 * **基础架构**。根据 {{site.data.keyword.cloud_notm}} 基础架构中 SAP 客户机的位置，该基础架构内的其他组件需要为灾难恢复方案做好准备。在示例参考体系结构中，客户机从内部部署端访问 SAP 系统，或者从客户的公司网络内部访问 SAP 系统。

## 安全性
{: #security}

### 用户管理

SAP 拥有自己的用户管理引擎 (UME)，可控制对 SAP 应用程序的基于角色的访问和授权。有关更多信息，请参阅 [SAP HANA Security - An Overview ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://archive.sap.com/documents/docs/DOC-62943){: new_window}。从用户管理角度来看，SAP 系统是否运行内部部署 {{site.data.keyword.cloud_notm}} 无关紧要。[跳板机服务器](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box)中提到了该规则的例外情况。

### 网络安全性

由于有不同的方式可供您访问基于 {{site.data.keyword.cloud_notm}} 的环境，因此需要对安全措施加以区分。

仅在概念验证类型的部署中，才应考虑使用公共接口进行外部访问。对于生产方案，由于设备具有所有必需的功能（VPN 防火墙等），因此可以部署 Vyatta 设备。如果 Vyatta 设备不能满足等待时间和/或吞吐量需求，请联系 {{site.data.keyword.cloud_notm}} 支持，以讨论除了 Vyatta 设备外可以使用的其他所有可能的步骤和配置。
