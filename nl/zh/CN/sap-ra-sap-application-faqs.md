---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, application servers

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 常见问题：SAP 应用程序
{: #application-faqs}

## 在哪里可以找到在 SAP NetWeaver 中通过认证的 SAP 应用程序？
{: faq}

支持 SAP Business Suite，包括 SAP S/4HANA 和 SAP Business Warehouse on HANA。对于特定应用程序，请查看 [SAP Product Availability Matrix ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://support.sap.com/en/release-upgrade-maintenance.html){: new_window} 和 [SAP Note ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://support.sap.com/en/index.html){: new_window}。这两个网站都需要 SAP S 用户标识才能访问内容。

## 是否可以运行非 SAP NetWeaver 应用程序，例如 SAP Hybris 和 SAP BusinessObjects？
{: faq}

SAP BusinessObjects 已通过认证，可在 {{site.data.keyword.cloud}} 中的虚拟服务器上运行。有关更多信息，请参阅 [SAP Note 2279688 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/2279688){: new_window}。SAP Hybris 不属于 {{site.data.keyword.cloud_notm}} SAP 认证的基础架构产品的范围。对于复杂的 SAP 实施，{{site.data.keyword.IBM_notm}} 会为 SAP 提供完全受管服务。有关更多信息，请参阅 [Managed Services for SAP Applications ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/sap/managed){: new_window}。

## SAP 认证的裸机服务器上支持 SAP Business One 吗？
{: faq}

SAP 认证的 {{site.data.keyword.baremetal_short}} 上不支持 SAP Business One。

## 支持哪个版本的 SAP NetWeaver？
{: faq}

支持应用程序将应用程序服务器、SAP ABAP 或 Java 作为 SAP NetWeaver 7.0 或更高版本的一部分运行，并使用 SAP 内核 7.21 EXT（最小 PL #600）、7.22 EXT（最小 PL #100）、7.45（最小 PL #100）和 7.49（最小 PL #100）或更高版本的 SAP 内核版本。
