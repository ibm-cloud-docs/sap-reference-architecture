---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Multitenant Database Containers, MDC, database, SAP HANA

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Domande frequenti: SAP HANA
{: #hana-faqs}

## Quali sono le dimensioni del server bare metal IBM Cloud disponibili per SAP HANA?
{: faq}

I {{site.data.keyword.baremetal_long}} certificati SAP sono disponibili nelle seguenti dimensioni di RAM:
* 512 GB
* 1024 GB (1 TB)
* 2048 GB (2 TB)
* 4096 GB (4 TB)
* 6144 GB (6 TB)
* 8192 GB (8 TB)
* 12288 GB (12 TB)

## Quali sono le opzioni di condivisione hardware supportate nell'infrastruttura IBM Cloud? Ad esempio, Virtual HANA e Multitenant Database Containers (MDC).
{: faq}

L'offerta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure è una distribuzione server bare metal certificata da SAP e non include la virtualizzazione. È tua responsabilità accertarti che le modifiche a questa infrastruttura rimangano conformi alla certificazione SAP.

## Come distribuisco SAP HANA su IBM Cloud?
{: faq}

La procedura di implementazione è descritta in [SAP HANA on {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started). Poiché si tratta di un'offerta autogestita, sei responsabile dell'implementazione di SAP HANA in {{site.data.keyword.cloud_notm}}. {{site.data.keyword.IBM_notm}} fornisce servizi di sicurezza e SAP gestiti per assistenza. Per ulteriori informazioni, vedi [Managed Services for SAP Applications ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## Lo scaling incrementale è supportato per SAP HANA?
{: faq}

Sì. Per ulteriori informazioni, vedi [Configurazione della tua infrastruttura {{site.data.keyword.cloud_notm}} per supportare SAP HANA a più nodi](/docs/infrastructure/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage).

## Qual è la dimensione massima del server supportata per SAP Business Suite su HANA?
{: faq}

La dimensione del server certificato IaaS massima per supportare SAP Business Suite su HANA è di 8 TB. 12 TB vengono offerti nella HANA TDI v5 per carichi di lavoro approvati.

##  Qual è la dimensione massima del server supportata per SAP Business Warehouse su HANA?
{: faq}

La dimensione del server certificato IaaS massima per supportare SAP Business Warehouse su HANA è di 4 TB.

## Come eseguo il backup dei miei server certificati SAP HANA?
{: faq}

Il backup del server non è incluso nell'offerta autogestita. Durante il processo di ordinazione del server, sono presenti opzioni che puoi selezionare nel portale clienti dell'infrastruttura {{site.data.keyword.cloud_notm}}. Hai anche la possibilità di integrare una soluzione di backup di terze parti.

## Come migro un database SAP HANA esistente o un database relazionale in un server certificato SAP HANA in IBM Cloud?
{: faq}

Non sono inclusi servizi di migrazione con il servizio autogestito; le attività di migrazione sono una tua responsabilità. {{site.data.keyword.IBM_notm}} offre una gamma di servizi di sicurezza e gestiti che possono esserti di supporto nella pianificazione e nell'esecuzione della migrazione SAP. Per ulteriori informazioni, vedi [{{site.data.keyword.cloud_notm}} Advisory Services ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.com/us-en/marketplace/cloud-consulting-services){: new_window}. Seleziona *Services* > *Cloud Services*.

## SAP HANA 2.0 è supportato come parte dell'offerta IBM Cloud SAP-Certified Infrastructure ?
{: faq}

Sì, SAP HANA 2.0 è supportato se ordini un server certificato SAP con un sistema operativo conforme a SAP HANA 2.0. Per ulteriori informazioni, vedi [SAP Note 2235581 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/2235581){: new_window}.
