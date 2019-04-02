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

# Domande frequenti: applicazioni SAP
{: #application-faqs}

## Dove posso trovare le applicazioni SAP certificate all'interno di SAP NetWeaver?
{: faq}

È supportato SAP Business Suite, inclusi SAP S/4HANA e SAP Business Warehouse on HANA. Per specifiche applicazioni, controlla [SAP Product Availability Matrix ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://support.sap.com/en/release-upgrade-maintenance.html){: new_window} e [SAP Notes ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://support.sap.com/en/index.html){: new_window}. Per accedere al contenuto di entrambi devi disporre di un ID utente SAP.

## Posso eseguire applicazioni non SAP NetWeaver come ad esempio SAP Hybris e SAP BusinessObjects?
{: faq}

SAP BusinessObjects è certificato per essere eseguito sui server virtuali all'interno di {{site.data.keyword.cloud}}. Per ulteriori informazioni, vedi [SAP Note 2279688 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/2279688){: new_window}.SAP Hybris è un'applicazione fuori ambito dell'offerta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure. Per l'implementazione SAP complessa, {{site.data.keyword.IBM_notm}} offre servizi gestiti completamente per SAP. Per ulteriori informazioni, vedi [Managed Services for SAP Applications ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## SAP Business One è supportato sui server bare metal certificati SAP?
{: faq}

SAP Business One non è supportato sui {{site.data.keyword.baremetal_short}} certificati SAP.

## Quale versione di SAP NetWeaver è supportata?
{: faq}

Sono supportate le applicazioni in esecuzione sui server delle applicazioni, SAP ABAP o Java come parte di SAP NetWeaver 7.0 o superiore, utilizzando il kernel SAP 7.21 EXT (minimo PL #600), 7.22 EXT (minimo PL #100), 7.45 (minimo PL #100) e 7.49 (minimum PL #100) o versioni kernel SAP superiori.
