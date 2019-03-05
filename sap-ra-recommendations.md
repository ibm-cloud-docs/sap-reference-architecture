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

# Guidance for your IBM Cloud SAP-Certified Infrastructure
{: #recommendations}

Your requirements might differ from the offered guidance; however, it serves as a starting point for building your SAP-certified server in the {{site.data.keyword.cloud}} environment.

Figure 1. Sample reference architecture

![Figure 1. Sample reference architecture](/images/SAP-optimization-ref-architecture-20180527.png "Sample reference architecture")

## VLANs
{: #vlans}

The SAP guidelines for landscape design recommend a segregation of server traffic on different network interface controllers (NICs). For example, business data should be separated from administrative and backup traffic. Assigning multiple NICs to different subnets enables this data segregation. For more information, see the Network section in [Building High Availability for SAP NetWeaver and SAP HANA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} (PDF).

To follow the NIC recommendation, {{site.data.keyword.cloud_notm}} allows for the configuration of multiple VLANs on the servers. The VLAN interfaces can be made high availability (HA) through multiple NICs to be configured under bond interfaces (Linux) or teaming interfaces (Microsoft Windows). For both HA and disaster recovery (DR) capabilities on the {{site.data.keyword.baremetal_short}}, it's best to reserve additional IP addresses and assign the addresses to the different SAP services as the services are implemented. Consult SAP installation documentation for support on how to assign addresses during the installation with the SAP Software Provisioning Manager (SWPM). For virtual machines (VMs), the address of the main interface of the VM is usually sufficient.

By default, {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} have a public and a private interface. In general, it's not recommended to keep the public LAN configured for all servers in your {{site.data.keyword.cloud_notm}} infrastructure. Specific instances of the Vyatta Network Gateway should be deployed to allow public access to your environment, if needed. For more information, see [Vyatta Network Gateway](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta).

## {{site.data.keyword.cloud_notm}} storage
{: #storage}

{{site.data.keyword.cloud_notm}} servers certified for SAP NetWeaver can be configured with a different number of internal disks as well as with different layouts for those disks for RAID configuration. Be aware that these layouts might not be sufficient for project requirements, for example, insufficient size, or shared access to storage.

Storage requirements differ to the point that the guidance is to clearly define the project Key Performance Indicators (KPIs) in terms of backup and restore time slots, high availability and failover requirements, and then decide on the storage type to use. Covering all options is beyond the scope of this content; however, some guidance can be provided.

  * Use shared iSCSI devices for HA setups with a database that fails over between nodes. You will need to look at the required maximum IOPS/sec.

  * Use internal storage for HA setups with a database that is replicated; for example, SAP HANA system replication. SAP NetWeaver application servers can either reside on internal storage or on shared network-attached storage (NAS).

  * Use shared storage to facilitate failover capabilities with VMware-based installations. For more information on selecting the right storage type, see [Storage to use with VMware Systems](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems).

All the options can be selected from within the {{site.data.keyword.cloud_notm}} infrastructure.

## High availability
{: #availability}

In a distributed installation of SAP applications on a centralized database, the base installation is replicated to achieve high availability. For each layer of the architecture, the high availability design varies.

  * **SAP Web Dispatcher**. High availability is achieved with multiple redundant SAP Web Dispatcher instances with SAP application traffic. The SAP Web Dispatcher serves as a potential entry point for a set of SAP systems and other `https`-based services. It typically lies between the internet and the backend systems and deals with web protocol-based requests from the "outside world." The SAP Web Dispatcher works like a reverse proxy with a variety of supported features, such as load balancing and single sign on. For more information, see [SAP Web Dispatcher ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window}.

  * **ABAP SAP Central Services (ASCS)**. For high availability of ASCS in an {{site.data.keyword.cloud_notm}} environment, the cluster software of the target operating system needs to be installed, for example, Linux Pacemaker or Microsoft Cluster. The single point of failure of the ASCS (SAP's enqueue service) needs to be configured to replicate its data to an Enqueue Replication Service (ERS). An ERS instance needs to be installed as part of the SAP installation process and is supported by SAP's SWPM. For details on installing and configuring the cluster components for both ASCS and ERS, consult the documentation of the operating system vendor's offering.

  * **SAP NetWeaver application servers**. High availability is achieved by load balancing traffic within a pool of application servers. If only a limited amount of resources are required, a single application server can be configured as highly available. The application server needs to be installed with storage that is accessible by all potential cluster nodes, which can be used for failover. Also, the SAP NetWeaver stack needs to use a virtual hostname. Consult the operating system documentation of the operating system vendor for details on the required configuration and SAP documentation for high availability. If your configuration requires multiple application servers, the configuration of the SAP application servers needs to cover load balancing, too, for example, in SAP logon groups and RFC server groups. For more information, see the administration guide for your SAP NetWeaver version.

  * **Database tier**. The example reference architecture deploys a single SAP HANA, or other database, instance. For high availability, deploy more than one instance and use HANA System Replication (HSR) to implement manual failover. To enable automatic failover, a high availability extension for the specific Linux distribution is required. For other databases, either  a failover of the database instance on shared storage can be configured, or a replication technique similar to the SAP HANA case can be used. Consult the documentation of the supported database system for the set of options that are required to set up either high availability or replication.

  For additional information, see [{{site.data.keyword.cloud_notm}} high-availability support](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha).

## Disaster recovery
{: #dr}

Each tier uses a different strategy to provide disaster recovery protection.

 * **SAP NetWeaver application servers**. SAP application servers contain no business data; however, the installation and configuration of the server needs to be preserved for continued operation after a disaster. One disaster recovery strategy is to have SAP application servers in another region. Any changes to configuration or kernel updates on the primary application server must be copied to the virtual machines or servers in the disaster recovery region.

 * **SAP Central Services (SCS)**. The SCS component of the SAP application stack doesn't persist business data. You can build a server or a VM in the disaster recovery region to run the SCS role. The only content from the primary SCS note to synchronize is the `/sapmnt` share content. Also, if configuration changes or kernel updates take place on the primary SCS servers, the changes must be replicated on the disaster recovery SCS. To synchronize the two servers, use a regularly scheduled copy job to copy `/sapmnt` to the disaster recovery servers. For more information on SCS, see [Central Services Instance ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window}.

 * **Database tier**. For SAP HANA-based systems, use HANA-supported replication solutions such as HANA System Replication or {{site.data.keyword.cloud_notm}} storage replication features. For other supported databases, refer to the database documentation for its supported features. In general, choosing from the available options requires a clear understanding of the business requirements of the underlying SAP application. The impact of a potential loss of single transactions or even all data within a time window needs to be determined.

 * **Infrastructure**. Depending on where the SAP clients are in your {{site.data.keyword.cloud_notm}} infrastructure, other components within it need to be prepared for disaster recovery scenarios. In the example reference architecture, clients access the SAP systems from the on-premises side, or from within the customer's corporate network.

## Security
{: #security}

### User management

SAP has its own Users Management Engine (UME) to control role-based access and authorization with the SAP application. For more information, see [SAP HANA Security - An Overview ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://archive.sap.com/documents/docs/DOC-62943){: new_window}. From a user management perspective, it's not relevant if your SAP systems run on-premises {{site.data.keyword.cloud_notm}}. Exceptions to that rule were mentioned under [Jump box server](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box).

### Network security

Since there are different ways for you to access an {{site.data.keyword.cloud_notm}}-based environment, security measures need to be differentiated.

The use of a public interface for external access should only be considered in proof-of-concept type deployments. For production scenarios, the deployment of Vyatta appliances is available since the appliances feature all required functionality (VPN firewall, and so on). Should latency and or through-put requirements not be met by Vyatta appliances, contact {{site.data.keyword.cloud_notm}} Support to discuss all the possible steps and configurations that can be made available beyond the Vyatta appliances.
