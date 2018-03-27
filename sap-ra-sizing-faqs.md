---



copyright:
  years: 2018
lastupdated: "2018-03-27"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# FAQs: Sizing and architecture
{: #faqs_sizing}

## What are the SAP Application Performance Standard (SAPS) measurements for each SAP NetWeaver-certified IBM Cloud server (rate SAPS and core)?

Table 1 contains the SAP measurements for the SAP NetWeaver-certified {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}}.

Table 1. SAPS measurements for SAP NetWeaver-certified {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

| **Sever type** | **SAPS** | **RAM** | **Cores** | **SAPS/Core** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2745 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2292 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |
| BI.S3.NW32 | 11970 | 32 GB | 4 | 2992 |
| BI.S3.NW64 | 12750 | 64 GB | 4 | 3187 |
| BI.S3.NW192 | 78850 | 192 GB | 36 | 2190 |
| BI.S3.NW384 | 79430 | 384 GB | 36 | 2203 |
| BI.S3.NW768 | 79630 | 768 GB | 36 | 2211 |

## What are the databases supported by the IBM Cloud SAP-Certified Infrastructure offering?

For SAP HANA configurations, SAP HANA 1.0 and SAP HANA 2.0 are the supported database platforms. For full operating system and database support statements for SAP NetWeaver, see [SAP Note 2414097](https://launchpad.support.sap.com/#/notes/2414097).

## Can a Tier-2 configuration (application server, plus an SAP HANA database) be done with the SAP HANA-certified IBM Cloud Bare Metal Servers?

A Tier-2 configuration can't be done on the same piece of hardware. It can, however, be done using a combination of the SAP NetWeaver and SAP HANA configurations.

## Is virtualization (VMware) supported on the IBM Cloud SAP-certified infrastructure for SAP NetWeaver or SAP HANA?

Yes, the {{site.data.keyword.cloud_notm}} SAP-certified infrastructure supports VMware ESXi for SAP NetWeaver and SAP HANA. It's important to note that if you choose to order and implement a server running VMware, it's your responsibility to properly size and configure all virtual machines on the server to comply with SAP's restrictions and best practices. For additional information, see [SAP Note 2161991](https://launchpad.support.sap.com/#/notes/2161991).

## Can the configurations of the SAP-certified IBM Cloud Bare Metal Servers be changed?

SAP HANA-certified {{site.data.keyword.baremetal_short}} have fixed configurations for processor, RAM, and local storage based on the server you choose, and cannot be modified. Options for networking, operating system, and monitoring services can be configured.

SAP NetWeaver-certified {{site.data.keyword.baremetal_short}} have fixed configurations for processor and RAM; local storage can be configured as necessary to meet your needs. Options for networking, operating system, and monitoring services can be configured.

## Are there any leading methods by which to deploy an SAP solution in the IBM Cloud SAP-certified infrastructure?

Yes, [SAP Best Practices](https://help.sap.com/viewer/p/SAP_Best_Practices) offers options that you can use during your deployment. {{site.data.keyword.IBM_notm}} also offers cloud consulting services. For more information, see [{{site.data.keyword.cloud_notm}} Advisory Services](https://www.ibm.com/us-en/marketplace/cloud-consulting-services).

## Do I have to deploy SAP Solutions Manager and SAProuter? If yes, is there a recommended infrastructure?

No, deploying SAP Solutions Manager and SAProuter is not mandatory when working with a training, sandbox, or similar environment. However, it is best that these components be deployed in your production environment.

