---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-12"

keywords: SAP Reference Architecture, Multitenant Database Containers, MDC, database, SAP HANA

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# FAQs: SAP HANA
{: #hana-faqs}

## What are the IBM Cloud bare metal server sizes available for SAP HANA?
{: faq}

The SAP-certified {{site.data.keyword.baremetal_long}} are available in the following RAM sizes:
* 512 GB
* 1024 GB (1 TB)
* 2048 GB (2 TB)
* 4096 GB (4 TB)
* 6144 GB (6 TB)
* 8192 GB (8 TB)
* 12288 GB (12 TB)

## What hardware sharing options are supported in the {{site.data.keyword.cloud_notm}} infrastructure? For example, Virtual HANA and Multitenant Database Containers (MDC).
{: faq}

The {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure offering is a bare metal server deployment certified by SAP and doesn't include virtualization. It's your responsibility to make sure that any changes on top of this infrastructure remain in compliance with respect to the SAP certification.

## How do I deploy SAP HANA on the {{site.data.keyword.cloud_notm}}?
{: faq}

Implementation steps are described in [SAP HANA on {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started). As this is a self-managed offering, you're responsible for implementing SAP HANA in the {{site.data.keyword.cloud_notm}}. {{site.data.keyword.IBM_notm}} does provide advisory and managed SAP services to assist you. For more information, see [Managed Services for SAP Applications](https://www.ibm.com/cloud/sap/managed){: external}.

## Is scale-out supported for SAP HANA?
{: faq}

Yes. See [Configuring your {{site.data.keyword.cloud_notm}} infrastructure to support SAP HANA multi-node](/docs/infrastructure/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage) for more information.

## What is the maximum server size supported for SAP Business Suite on HANA?
{: faq}

8 TB is the maximum IaaS-certified server size to support SAP Business Suite on HANA.  12 TB is offered under HANA TDI v5 for approved workloads.

##  What is the maximum server size supported for SAP Business Warehouse on HANA?
{: faq}

4 TB is the maximum IaaS-certified server size to support SAP Business Warehouse on HANA.

## How do I back up my SAP HANA-certified servers?
{: faq}

Server backup is not included in the self-managed offering. There are options that you can select during the server ordering process in the {{site.data.keyword.cloud_notm}} console. You also have the option to integrate a third-party backup solution.

## How do I migrate an existing SAP HANA database or relational database to an SAP HANA-certified server in the {{site.data.keyword.cloud_notm}}?
{: faq}

No migration services are included with the self-managed service; any migration activities are your responsibility. {{site.data.keyword.IBM_notm}} does offer a range of advisory and managed services that can assist you in SAP migration planning and execution. For more information, see the [{{site.data.keyword.cloud_notm}} Marketplace)](https://www.ibm.com/products?loc=us-en){: external}. Select *Services* > *Managed Cloud Services*.

## Is SAP HANA 2.0 supported as part of the {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure offering?
{: faq}

Yes, SAP HANA 2.0 is supported if you order an SAP-certified server with an operating system that is compliant with SAP HANA 2.0. For more information, see [SAP Note 2235581](https://launchpad.support.sap.com/#/notes/2235581){: external}.
