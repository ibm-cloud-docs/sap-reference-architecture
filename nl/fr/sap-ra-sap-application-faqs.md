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

# Foire aux questions : applications SAP
{: #application-faqs}

## Où trouver des applications SAP qui sont certifiées dans SAP NetWeaver ?
{: faq}

SAP Business Suite, incluant SAP S/4HANA et SAP Business Warehouse on HANA, sont pris en charge. Pour des applications spécifiques, voir [SAP Product Availability Matrix ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://support.sap.com/en/release-upgrade-maintenance.html){: new_window} and [SAP Notes ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://support.sap.com/en/index.html){: new_window}. Les deux applications générales requièrent un ID SAP S-user pour accéder au contenu.

## Puis-je exécuter des applications NetWeaver non SAP, comme SAP Hybris et SAP BusinessObjects ?
{: faq}

L'exécution de SAP BusinessObjects sur des serveurs virtuels au sein d'{{site.data.keyword.cloud}} est certifiée. Pour plus d'informations, voir [SAP Note 2279688 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://launchpad.support.sap.com/#/notes/2279688){: new_window}.SAP Hybris ne rentre pas dans le cadre de l'offre d'infrastructure {{site.data.keyword.cloud_notm}} certifiée SAP. Pour une implémentation SAP complexe, {{site.data.keyword.IBM_notm}} propose effectivement des services gérés complets pour SAP. Pour plus d'informations, voir [Managed Services for SAP Applications ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## SAP Business One est-il pris en charge sur les serveurs Bare Metal certifiés SAP ?
{: faq}

SAP Business One n'est pas pris en charge sur le serveurs {{site.data.keyword.baremetal_short}} certifiés SAP.

## Quelles sont les versions de SAP NetWeaver qui sont prises en charge ?
{: faq}

Sont prises en charge les applications exécutant des serveurs d'applications, SAP ABAP ou Java, dans le cadre de SAP NetWeaver version 7.0 ou supérieure, utilisant SAP kernel 7.21 EXT (PL #600 minimum), 7.22 EXT (PL #100 minimum), 7.45 (PL #100 minimum), et 7.49 (PL #100 minimum), ou des versions de noyau SAP supérieures.
