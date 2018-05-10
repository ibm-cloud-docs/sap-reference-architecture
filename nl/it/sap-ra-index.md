---



copyright:
  years: 2018
lastupdated: "2018-03-26"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Introduzione all'architettura di riferimento SAP IBM Cloud
{: #getting-started}

L'architettura {{site.data.keyword.cloud}} offre capacità tecniche superiori come ad esempio un ambiente software definibile critico per un'infrastruttura, interfacce programmabili e centinaia di configurazioni hardware e di rete. È progettata per offrire un livello elevato di flessibilità (combinando server virtuali e dedicati per soddisfare diversi tipi di carico di lavoro), l'automazione di interfacce e le opzioni di distribuzione ibrida. L'offerta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure per SAP HANA e SAP NetWeaver ti fornisce una selezione che più si adatta alle esigenze. Questa selezione include server bare metal e basati sulla virtualizzazione su cui può essere eseguito lo stack di software SAP.

## Architettura di riferimento
{: #ref-arch}

La Figura 1 è un'architettura di riferimento (RA) per una panoramica che comprende: 

  * Componenti di rete Vyatta
  * SAP Web Dispatcher
  * Server delle applicazioni SAP NetWeaver
  * Database SAP HANA
  * Altri RDBMS (relational database management systems) 
  
L'architettura di riferimento (RA) di esempio è configurata con alta disponibilità e ripristino di emergenza. Nota che nella Figura 1, i server database possono essere qualsiasi sistema di database supportato da SAP NetWeaver, ad esempio, SAP HANA. 

Figura 1. Architettura di riferimento di esempio

![Figura 1. Architettura di riferimento di esempio](/images/ref_architecture.png "Architettura di riferimento di esempio")
