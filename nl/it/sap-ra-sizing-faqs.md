---



copyright:
  years: 2018
lastupdated: "2018-03-15"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Domande frequenti: prezzi e architettura
{: #faqs_sizing}

## Quali sono le misurazioni SAPS (SAP Application Performance Standard) per ciascun server IBM Cloud certificato SAP NetWeaver (rapporto SAPS e core)?

La Tabella 1 contiene le misurazioni SAP per {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} certificato SAP NetWeaver.

Tabella 1. Misurazioni SAPS per {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} certificato SAP NetWeaver.

| **Tipo server** | **SAPS** | **RAM** | **Core** | **SAPS/Core** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2688 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2293 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |

## Quali sono i database supportati dall'offerta IBM Cloud SAP-Certified Infrastructure?

Per le configurazioni SAP HANA, SAP HANA 1.0 e SAP HANA 2.0 sono le piattaforme database supportate. Per le istruzioni di supporto complete del sistema operativo e del database per SAP NetWeaver, vedi [SAP Note 2414097](https://launchpad.support.sap.com/#/notes/2414097).

## Posso eseguire una configurazione di livello 2 (server della applicazioni più un database SAP HANA) con i server bare metal IBM Cloud certificati SAP HANA?

Non puoi eseguire una configurazione di livello 2 sulla stessa parte di hardware. Puoi tuttavia eseguirla utilizzando una combinazione di configurazioni SAP NetWeaver e SAP HANA.

## La virtualizzazione (VMware) è supportata su IBM Cloud SAP-Certified Infrastructure per SAP NetWeaver o SAP HANA?

Sì, {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure supporta VMware ESXi per SAP NetWeaver e SAP HANA. Devi tenere presente che se scegli di ordinare e implementare un server su cui è in esecuzione VMware, è tua responsabilità dimensionare e configurare tutte le macchine virtuali sul server in modo che siano conformi alle procedure consigliate e alle limitazioni di SAP. Per ulteriori informazioni, vedi [SAP Note 2161991](https://launchpad.support.sap.com/#/notes/2161991).

## Posso modificare le configurazioni dei server bare metal IBM Cloud certificati SAP?

I {{site.data.keyword.baremetal_short}} certificati SAP HANA hanno configurazioni fisse per processore, RAM e archiviazione locale basate sul server che hai scelto e non possono essere modificate. Puoi configurare le opzioni per rete, sistema operativo e servizi di monitoraggio. 

I {{site.data.keyword.baremetal_short}} certificati SAP NetWeaver hanno configurazioni fisse per processore e RAM; puoi configurare l'archiviazione locale in base alle tue necessità. Puoi configurare le opzioni per rete, sistema operativo e servizi di monitoraggio. 

## Esistono metodi principali tramite cui distribuire una soluzione SAP in IBM Cloud SAP-Certified Infrastructure?

Sì, [SAP Best Practices](https://help.sap.com/viewer/p/SAP_Best_Practices) offre opzioni che puoi utilizzare durante la tua distribuzione. {{site.data.keyword.IBM_notm}} offre anche servizi di consulenza del cloud. Per ulteriori informazioni, vedi [{{site.data.keyword.cloud_notm}} Advisory Services](https://www.ibm.com/us-en/marketplace/cloud-consulting-services).

## Devo distribuire SAP Solutions Manager e SAProuter? Se sì, esiste un'infrastruttura consigliata?

No, la distribuzione di SAP Solutions Manager e SAProuter non è obbligatoria quando utilizzi un ambiente di formazione, sandbox o simili. Tuttavia, è meglio distribuire questi componenti nel tuo ambiente di produzione. 

