---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-05"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, application servers

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# FAQs: SAP applications
{: #application-faqs}

## Where can I find the SAP applications that are certified within SAP NetWeaver?
{: faq}

The SAP Business Suite, including SAP S/4HANA and SAP Business Warehouse on HANA, are supported. For specific applications, see the [SAP Product Availability Matrix](https://support.sap.com/en/release-upgrade-maintenance.html){: external} and [SAP Notes](https://support.sap.com/en/index.html){: external}. Both require an SAP S-user ID to access content.

## Can I run non-SAP NetWeaver applications, such as SAP Hybris and SAP BusinessObjects?
{: faq}

SAP BusinessObjects is certified to run on virtual servers within the {{site.data.keyword.cloud}}. For more information, see [SAP Note 2279688](https://launchpad.support.sap.com/#/notes/2279688){: external}. SAP Hybris is out-of-scope for the {{site.data.keyword.cloud}} SAP-Certified Infrastructure offering. For complex SAP implementations, {{site.data.keyword.IBM_notm}} does offer fully managed services for SAP. For more information, see [Managed Services for SAP Applications](https://www.ibm.com/cloud/sap/managed){: external}.

## Is SAP Business One supported on the SAP-certified {{site.data.keyword.baremetal_short}}?
{: faq}

SAP Business One is not supported on the SAP-certified {{site.data.keyword.baremetal_short}} at this time.

## Which version of SAP NetWeaver is supported?
{: faq}

Applications running application servers, SAP ABAP, or Java as part of SAP NetWeaver 7.0 or higher, using SAP kernel 7.21 EXT (minimum PL #600), 7.22 EXT (minimum PL #100), 7.45 (minimum PL #100), and 7.49 (minimum PL #100), or higher SAP kernel versions are supported.
