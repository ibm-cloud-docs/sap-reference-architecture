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

# Domande frequenti: SAP HANA
{: #hana-faqs}

## Quali sono le dimensioni del server bare metal IBM Cloud disponibili per SAP HANA?

I {{site.data.keyword.baremetal_long}} certificati SAP sono disponibili nelle seguenti dimensioni di RAM:
  * 512 GB
  * 1 TB
  * 2 TB
  * 4 TB
  * 8 TB
  
## Quali sono le opzioni di condivisione hardware supportate nell'infrastruttura IBM Cloud? Ad esempio, Virtual HANA e Multitenant Database Containers (MDC).

L'offerta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure è una distribuzione server bare metal certificata da SAP e non include la virtualizzazione. È tua responsabilità accertarti che le modifiche a questa infrastruttura rimangano conformi alla certificazione SAP. 

## Come distribuisco SAP HANA su IBM Cloud?

La procedura di implementazione è descritta in [SAP HANA on {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started). Poiché si tratta di un'offerta autogestita, sei responsabile dell'implementazione di SAP HANA in {{site.data.keyword.cloud_notm}}. {{site.data.keyword.IBM_notm}} fornisce servizi di sicurezza e SAP gestiti per assistenza. Per ulteriori informazioni, vedi [{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed).

## Lo scaling incrementale è supportato per SAP HANA?

Al momento, lo scaling incrementale non è supportato per SAP HANA.

## Qual è la dimensione massima del server supportata per SAP Business Suite su HANA?

La dimensione server massima per supportare SAP Business Suite su HANA è di 8 TB.

##  Qual è la dimensione massima del server supportata per SAP Business Warehouse su HANA?

La dimensione server massima per supportare SAP Business Warehouse su HANA è di 4 TB.

## Come eseguo il backup dei miei server certificati SAP HANA?

Il backup del server non è incluso nell'offerta autogestita. Durante il processo di ordinazione del server, sono presenti opzioni che puoi selezionare nel portale clienti dell'infrastruttura {{site.data.keyword.cloud_notm}}. Hai anche la possibilità di integrare una soluzione di backup di terze parti. 

## Come migro un database SAP HANA esistente o un database relazionale in un server certificato SAP HANA in IBM Cloud?

Non sono inclusi servizi di migrazione con il servizio autogestito; le attività di migrazione sono una tua responsabilità. {{site.data.keyword.IBM_notm}} offre una gamma di servizi di sicurezza e gestiti che possono esserti di supporto nella pianificazione e nell'esecuzione della migrazione SAP. Per ulteriori informazioni, vedi [{{site.data.keyword.cloud_notm}} Advisory Services](https://ibm.com/us-en/marketplace/cloud-consulting-services).

## SAP HANA 2.0 è supportato come parte dell'offerta IBM Cloud SAP-Certified Infrastructure ?

Sì, SAP HANA 2.0 è supportato se ordini un server certificato SAP con un sistema operativo conforme a SAP HANA 2.0. Per ulteriori informazioni, vedi [SAP Note 2235581](https://launchpad.support.sap.com/#/notes/2235581).
