---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-07"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, VLAN, SAP Web Dispatcher, load balancing, database, high availability, disaster recovery, HA, DR

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Understanding the architecture behind the SAP reference architecture
{: #architecture}

The architecture example in Figure 1 might differ from your architecture; it shows the general concepts of an SAP {{site.data.keyword.cloud}}-based deployment. Your on-premises systems are connected through the internet to your {{site.data.keyword.cloud_notm}} infrastructure.

After your environment is ordered and deployed, you connect through an administrative VPN to your {{site.data.keyword.cloud_notm}} infrastructure. The VPN might not be sufficient for connecting your on-premises systems with cloud-based systems, which is why you can deploy a Vyatta Network appliance in the {{site.data.keyword.cloud_notm}} environment. For higher bandwidth and lower latency requirements, an Ethernet circuit handover into the cloud environment is also supported.

There are two different data centers shown in Figure 1 that consist of several SAP-certified {{site.data.keyword.baremetal_short}} for both SAP NetWeaver and SAP HANA. The {{site.data.keyword.baremetal_short}} or {{site.data.keyword.virtualmachinesshort}} in the diagram can be different, depending on your environment and the database technology you're using. In addition, the SAP HANA data in the architectural overview is transferred from the primary data center to the secondary data center for disaster recovery (DR). Other databases also allow for setups like Figure 1, with the setups being different.

In Figure 1, on the DR data center site, replicated systems are configured to maintain DR capabilities, which need to be implemented on different layers. For more information, see [Disaster recovery considerations](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Figure 1. Sample reference architecture

![Figure 1. Sample reference architecture](/images/SAP-optimization-ref-architecture-20180527.png "Sample reference architecture")

## SAP systems
{: #sap-systems}

The SAP systems (Advanced Business Application Programming (ABAP), Java, and SAP HANA) have a granular set of authorization objects for user management. Because of this, only remote access from desktops or other front-end devices to the {{site.data.keyword.cloud_notm}}-based environment need to be set up. No end user access needs to be granted and managed in the cloud environment. There might be several users with different responsibilities who need access to a database through a specific interface, command-line, or have latency restrictions that require Remote Desktop Protocol (RDP)-based access. To manage RDP access, a "jump host" can be deployed in the environment to serve as a central point of access for these scenarios. Apart from these specific requirements, users have access to the cloud-based systems within your corporate network and do not need to be administered in any specific way.

## Network
{: #network}

Any device in an {{site.data.keyword.cloud_notm}} environment can be ordered with a choice of internal and optional external LAN access. The external address is a routable public IP address and should be handled with care. The internal address is determined by the ordered VLAN and chosen from a sub-range of 10.0.0.0/8. By ordering multiple VLANs, different environments, or traffic types, can be segregated as per your network design and security requirements.

While a public interface with a configured firewall can cover some scenarios - for example, short term, rapid prototyping proof of concept with non-critical data - a firewall device should be considered for most cases. The example reference architecture maps a production scenario, so public network interfaces are out-of-scope.

## Vyatta Network Gateway
{: #vyatta}

Vyatta provides software-based virtual router, virtual firewall/NAT, and VPN capabilities for both IPv4 and IPv6. If users are to connect remotely into your {{site.data.keyword.cloud_notm}}-based systems, these devices can serve as end-points for both side-to-side VPN or the so-called "road warrior VPN" (access point). Different kinds of VPN technologies - IPSec, or SSL VPN tunnels, such as OpenVPN - can be used. Depending on the SAP technology you're using, these VPN connections can be used to interconnect SAP systems (even with non-SAP systems) for traditional GUI technology, as well as browser-based SAP UI5 technology. Connecting an SAP Web Dispatcher behind a Vyatta Gateway allows for further features to be used, such as load balancing or single sign-on scenarios. For more information on the SAP Web Dispatcher, see [High availability](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#availability).

The Vyatta device can be deployed in a high-availability cluster configuration with a bandwidth up to 10 Gbps. For more information, see [Vyatta 5400 High Availability Configuration](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-vyatta-5400-high-availability-configuration#vyatta-5400-high-availability-configuration).

## Jump box server
{: #jump_box}

SAP systems have embedded user management and do not require centralized user administration. You can, of course, set up centralized user management. For more information, see [Central User Administration)](https://help.sap.com/viewer/c6e6d078ab99452db94ed7b3b7bbcccf/7.3.19/en-US/bfb0b13bb3acd607e10000000a11402f.html){: external}.

A jump box server lets you give specific users low-level access to your {{site.data.keyword.cloud_notm}} environment through command line access-based tools or other special purpose tools, such as SAP HANA Studio. Database administration tools, as well as the users who are granted access to the tools, are managed centrally on the jump box server. Users can log in to your {{site.data.keyword.cloud_notm}} environment from their desktops through Remote Desktop Protocol, which is routed through the VPN gateway.

## SAP servers - SAP HANA and SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}} offers a variety of SAP-certified servers for SAP HANA and SAP NetWeaver through the {{site.data.keyword.cloud_notm}} for SAP Applications offering. The servers are {{site.data.keyword.baremetal_short}} with your choice of operating system (OS) (Red Hat Linux, SUSE Linux, Microsoft Windows Server, or deployed with the VMware ESX hypervisor). For details on the SAP NetWeaver-certified servers, see [SAP Note 2414097)](https://launchpad.support.sap.com/#/notes/2414097){: external}. Be aware that on the hypervisor, you deploy one of the operating systems listed in SAP Note 2414097 as a guest OS.

SAP HANA servers come with a pre-selected storage layout that fulfills SAP's storage Key Performance Indicators (KPIs) for SAP HANA. You cannot change these layouts and you're urged not to use external storage for SAP HANA. External storage of different quality and accessible through different protocols - NFS, CIFS, iSCSI - can be used for backup and other purposes. Also, for the SAP NetWeaver servers, you have a choice to run other supported database systems on external storage.

All SAP software solutions based on either SAP HANA or on SAP NetWeaver include the entire SAP Business Suite, and SAP S/4HANA can be deployed in the {{site.data.keyword.cloud_notm}} environment. For other software components outside of these, you need to contact SAP Support. Follow the SAP sizing process to determine the right server size for your project, and choose from the servers listed for either the SAP HANA or SAP NetWeaver offering.

For more information on the SAP HANA-certified servers, see the [Certified and Supported SAP HANA Hardware Directory](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud){: external}.

For more information on the SAP HANA sizing process, see [Sizing the server (SAP HANA)](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server).

For more information on the SAP NetWeaver sizing processing, see [Sizing the server (SAP NetWeaver)](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-size_the_server#size_the_server).
