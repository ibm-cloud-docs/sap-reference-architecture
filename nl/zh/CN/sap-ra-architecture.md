---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-05"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, VLAN, SAP Web Dispatcher, load balancing, database, high availability, disaster recovery, HA, DR

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 了解 SAP 参考体系结构背后的体系结构
{: #architecture}

图 1 中的体系结构示例可能与您的体系结构不同；示例显示的是基于 {{site.data.keyword.cloud}} 的 SAP 部署的一般概念。您的内部部署系统通过因特网连接到您的 {{site.data.keyword.cloud_notm}} 基础架构。

在订购和部署环境后，您可通过管理 VPN 来连接到 {{site.data.keyword.cloud_notm}} 基础架构。该 VPN 可能不足以将内部部署系统与基于云的系统相连接，这就是为什么可以在 {{site.data.keyword.cloud_notm}} 环境中部署 Vyatta 网络设备的原因。为了满足对更高带宽和更短等待时间的需求，还支持将以太网电路切换到云环境。

图 1 中显示了两个不同的数据中心，由用于 SAP NetWeaver 和 SAP HANA 的多个经 SAP 认证的 {{site.data.keyword.baremetal_short}} 组成。根据您的环境和使用的数据库技术，图中的 {{site.data.keyword.baremetal_short}} 或虚拟机可能会有所不同。此外，在体系结构概览图中，SAP HANA 数据从主数据中心传输到辅助数据中心进行灾难恢复 (DR)。其他数据库也支持像图 1 这样的设置，但也支持不同的设置。

图 1 中，在 DR 数据中心站点上，将复制的系统配置为维护 DR 功能，这需要在不同的层上进行实施。有关更多信息，请参阅[灾难恢复注意事项](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr)。

图 1. 样本参考体系结构

![图 1. 样本参考体系结构](/images/SAP-optimization-ref-architecture-20180527.png "样本参考体系结构")

## SAP 系统
{: #sap-systems}

SAP 系统（高级业务应用程序编程 (ABAP)、Java 和 SAP HANA）提供了一组精细授权对象用于用户管理。因此，只需要设置从桌面或其他前端设备到基于 {{site.data.keyword.cloud_notm}} 的环境的远程访问。无需在云环境中授予和管理最终用户访问权。可能会有多名具有不同职责的用户需要通过特定 GUI 或通过命令行访问数据库，或者有要求基于远程桌面协议进行访问的等待时间限制。为了管理这种类型的远程访问，可以在环境中部署“跳转主机”，以充当这些方案的中心访问点。除了这些特定需求外，用户还有权访问公司网络中基于云的系统，并且无需以任何特定方式对用户进行管理。

## 网络
{: #network}

{{site.data.keyword.cloud_notm}} 环境中的任何设备都可以订购，并可以选择内部和可选外部 LAN 访问权。外部地址是可路由的公共 IP 地址，处理时应谨慎。内部地址由订购的 VLAN 确定，并从 VLAN 的子范围 10.0.0.0/8 中进行选择。通过订购多个 VLAN，可根据您的网络设计和安全需求，隔离不同的环境或流量类型。

虽然配置有防火墙的公共接口可以应对一些方案（例如，使用非关键数据在短时间内快速进行原型概念验证），但在大多数情况下，应考虑使用防火墙设备。示例参考体系结构描绘的是生产方案，因此公用网络接口超出范围。

## Vyatta 网关
{: #vyatta}

Vyatta 提供同时适用于 IPv4 和 IPv6 的基于软件的虚拟路由器、虚拟防火墙/NAT 和 VPN 功能。如果用户要远程连接到基于 {{site.data.keyword.cloud_notm}} 的系统，那么这些设备可以充当端到端 VPN 或所谓的“公路勇士 VPN”（访问点）的端点。可以使用不同类型的 VPN 技术（IPSec 或 SSL VPN 隧道，如 OpenVPN）。根据使用的 SAP 技术，可以使用这些 VPN 连接来互联支持传统 GUI 技术以及基于浏览器的 SAP UI5 技术的 SAP 系统（甚至可连接非 SAP 系统）。通过连接 Vyatta 网关后面的 SAP Web 分派器，支持使用进一步功能，例如负载平衡或单点登录方案。有关 SAP Web 分派器的更多信息，请参阅[高可用性](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#availability)。

Vyatta 设备可以部署在带宽高达 10 Gbps 的高可用性集群配置中。有关更多信息，请参阅 [Vyatta 5400 高可用性配置](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-vyatta-5400-high-availability-configuration#vyatta-5400-high-availability-configuration)。

## 跳板机服务器
{: #jump_box}

SAP 系统具有嵌入式用户管理功能，不需要集中用户管理。当然，您也可以设置集中用户管理。有关更多信息，请参阅 [Central User Administration ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm){: new_window}。

借助跳板机服务器，可以通过基于命令行访问的工具或其他特殊用途工具（如 SAP HANA Studio），授予特定用户对 {{site.data.keyword.cloud_notm}} 环境的低级别访问权。数据库管理工具以及授权其访问这些工具的用户可在跳板机服务器上进行集中管理。用户可以通过远程桌面协议从自己的桌面登录到 {{site.data.keyword.cloud_notm}} 环境，此过程通过 VPN 网关进行路由。

## SAP 服务器 - SAP HANA 和 SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}} 通过 {{site.data.keyword.cloud_notm}} for SAP Applications 产品，提供用于 SAP HANA 和 SAP NetWeaver 的各种服务器。这些服务器是 {{site.data.keyword.baremetal_short}}，使用您选择的操作系统 (OS)（Red Hat Linux、SUSE Linux、Microsoft Windows Server 或通过 VMware ESX 管理程序部署的操作系统）。有关 SAP NetWeaver 认证的服务器的详细信息，请参阅 [SAP Note 2414097 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}。请注意，在管理程序上，可将“SAP 注释 2414097”中列出的其中一个操作系统部署为访客操作系统。

SAP HANA 服务器随附预先选择的存储布局，可满足 SAP HANA 的 SAP 存储关键性能指标 (KPI)。您无法更改这些布局，也最好不要对 SAP HANA 使用外部存储器。质量不同且可通过不同协议（NFS、CIFS 或 iSCSI）访问的外部存储器可用于备份和其他目的。另外，对于 SAP NetWeaver 服务器，可以选择在外部存储器上运行其他受支持的数据库系统。

所有基于 SAP HANA 或 SAP NetWeaver 的 SAP 软件解决方案均包含整个 SAP Business Suite，并且 SAP S/4HANA 可以部署在 {{site.data.keyword.cloud_notm}} 环境中。对于除此以外的其他软件组件，您需要联系 SAP 支持。请遵循 SAP 大小调整流程，确定项目的适用服务器大小，然后从为 SAP HANA 或 SAP NetWeaver 产品列出的服务器中进行选择。

有关 SAP HANA 认证的服务器的更多信息，请参阅 [Certified and Supported SAP HANA Hardware Directory ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud){: new_window}。

有关 SAP HANA 大小调整过程的更多信息，请参阅[调整服务器大小 (SAP HANA)](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server)。

有关 SAP NetWeaver 大小调整过程的更多信息，请参阅[调整服务器大小 (SAP NetWeaver)](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-size_the_server#size_the_server)。
