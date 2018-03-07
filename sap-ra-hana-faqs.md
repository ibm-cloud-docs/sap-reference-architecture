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

# FAQs: SAP HANA
{: #hana-faqs}

## What are the IBM Cloud bare metal server sizes available for SAP HANA?

The SAP-certified {{site.data.keyword.baremetal_long}} are available in the following RAM sizes:
  * 512 GB
  * 1 TB
  * 2 TB
  * 4 TB
  * 8 TB
  
## What hardware sharing options are supported in the IBM Cloud infrastructure? For example, Virtual HANA and Multitenant Database Containers (MDC).

The {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure offering is a bare metal server deployment certified by SAP and doesn't include virtualization. It's your responsibility to make sure that any changes on top of this infrastructure remain in compliance with respect to the SAP certification.

## How do I deploy SAP HANA on the IBM Cloud?

Implementation steps are described in [SAP HANA on {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started). As this is a self-managed offering, you're responsible for implementing SAP HANA in the {{site.data.keyword.cloud_notm}}. {{site.data.keyword.IBM_notm}} does provide advisory and managed SAP services to assist you. For more information, see [{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed).

## Is scale-out supported for SAP HANA?

Currently, scale-out is not supported for SAP HANA.

## What is the maximum server size supported for SAP Business Suite on HANA?

8 TB is the maximum server size to support SAP Business Suite on HANA.

##  What is the maximum server size supported for SAP Business Warehouse on HANA?

4 TB is the maximum server size to support SAP Business Warehouse on HANA.

## How do I back up my SAP HANA-certified servers?

Server backup is not included in the self-managed offering. There are options that you can select during the server ordering process in the {{site.data.keyword.cloud_notm}} infrastructure customer portal. You also have the option to integrate a third-party backup solution.

## How do I migrate an existing SAP HANA database or relational database to an SAP HANA-certified server in the IBM Cloud?

No migration services are included with the self-managed service; any migration activities are your responsibility. {{site.data.keyword.IBM_notm}} does offer a range of advisory and managed services that can assist you in SAP migration planning and execution. For more information, see [{{site.data.keyword.cloud_notm}} Advisory Services](https://ibm.com/us-en/marketplace/cloud-consulting-services).

## Is SAP HANA 2.0 supported as part of the IBM Cloud SAP-Certified Infrastructure offering?

Yes, SAP HANA 2.0 is supported if you order an SAP-certified server with an operating system that is compliant with SAP HANA 2.0. For more information, see [SAP Note 2235581](https://launchpad.support.sap.com/#/notes/2235581).
