---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Advanced Business Application Programming, ABAP, ABAP SAP Central Services, ASCS, SAP Central Services, SAP Software Provisioning Manager, SWPM, HANA System Replication, HSR, User Management Engine, UME, VLAN, SAP Web Dispatcher, SAP NetWeaver application servers, application servers, database, instance, load balancing, SAP logon groups, RFC server groups, high availability, highly available, HA, disaster recovery, DR, cluster software, Linux Pacemaker, virtual hostname

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Indicazioni per IBM Cloud SAP-Certified Infrastructure
{: #recommendations}

I tuoi requisiti potrebbero essere diversi dalle indicazioni offerte, tuttavia servono come punto di partenza per la creazione del tuo server certificato SAP nell'ambiente {{site.data.keyword.cloud}}.

Figura 1. Architettura di riferimento di esempio

![Figura 1. Architettura di riferimento di esempio](/images/SAP-optimization-ref-architecture-20180527.png "Architettura di riferimento di esempio")

## VLAN
{: #vlans}

Le indicazioni SAP per la progettazione dello scenario consigliano una separazione del traffico server su NIC (network interface controller) differenti. Ad esempio, i dati aziendali dovrebbero essere separati da quelli di gestione e di backup. L'assegnazione di più NIC a sottoreti differenti consente la separazione di questi dati. Per ulteriori informazioni, consulta la sezione Network in [Building High Availability for SAP NetWeaver and SAP HANA ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} (PDF).

Per seguire il suggerimento della NIC, {{site.data.keyword.cloud_notm}} consente la configurazione di più VLAN sui server. Le interfacce VLAN possono essere create con alta disponibilità (HA) tramite la configurazione di più NIC in interfacce associate (Linux) o interfacce di team (Microsoft Windows). Per entrambe le capacità HA e ripristino di emergenza (DR) su {{site.data.keyword.baremetal_short}}, è meglio riservare indirizzi IP aggiuntivi e assegnare indirizzi ai diversi servizi SAP mentre vengono implementati i servizi. Consulta la documentazione sull'installazione di SAP per supporto su come assegnare gli indirizzi durante l'installazione con SAP Software Provisioning Manager (SWPM). Per le macchine virtuali (VM), di norma è sufficiente l'indirizzo dell'interfaccia principale della VM.

Per impostazione predefinita, {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} hanno un'interfaccia pubblica e una privata. In generale, si consiglia di non tenere la LAN pubblica configurata per tutti i server nella tua infrastruttura {{site.data.keyword.cloud_notm}}. Se necessario, per consentire l'accesso pubblico al tuo ambiente, dovrai eseguire specifiche istanze del gateway di rete Vyatta. Per ulteriori informazioni, vedi [Gateway di rete Vyatta](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta).

## Archiviazione {{site.data.keyword.cloud_notm}}
{: #storage}

I server {{site.data.keyword.cloud_notm}} certificati per SAP NetWeaver possono essere configurati con un diverso numero di dischi interni come pure con diversi layout per tali dischi per la configurazione RAID. Tieni presente che questi layout potrebbero non essere sufficienti per i requisiti del progetto, ad esempio, dimensione insufficiente o accesso condiviso all'archiviazione.

I requisiti di archiviazione differiscono al tal punto che l'indicazione è quella di definire chiaramente i KPI (Key Performance Indicator) del progetto in termini di slot temporali di backup e di ripristino, di alta disponibilità e di requisiti di failover e poi decidere il tipo di archiviazione da utilizzare. La copertura di tutte le opzioni supera il proposito di questo contenuto, tuttavia possono essere fornite delle indicazioni.

  * Usa dispositivi iSCSI condivisi per le configurazioni HA con un database che presenta errori tra i nodi. Dovrai tenere presente il numero massimo richiesto di IOPS/sec.

  * Usa l'archiviazione interna per le configurazioni HA con un database che viene replicato, ad esempio la replica di sistema SAP HANA. I server delle applicazioni SAP NetWeaver possono risiedere nell'archiviazione interna o nella NAS (network-attached storage) condivisa.

  * Usa l'archiviazione condivisa per facilitare le capacità di failover con le installazioni basate su VMware. Per ulteriori informazioni sulla selezione del tipo corretto di archiviazione, vedi [Storage to use with VMware Systems](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems).

Tutte le opzioni possono essere selezionate dall'infrastruttura {{site.data.keyword.cloud_notm}}.

## Alta disponibilità (HA)
{: #availability}

In un'installazione distribuita delle applicazioni SAP su un database centralizzato, l'installazione di base viene replicata per raggiungere l'alta disponibilità. Per ciascun livello dell'architettura, la progettazione dell'alta disponibilità varia.

  * **SAP Web Dispatcher**. L'alta disponibilità viene raggiunta con più istanze SAP Web Dispatcher ridondanti con il traffico dell'applicazione SAP. SAP Web Dispatcher funziona come potenziale punto di entrata per una serie di sistemi SAP e altri servizi basati su `https`. Di norma risiede tra internet e i sistemi di backend e gestisce le richieste basate sul protocollo web provenienti dall'esterno. SAP Web Dispatcher funziona come un proxy inverso con diverse funzioni supportate come ad esempio il bilanciamento del carico e SSO (single sign on). Per ulteriori informazioni, vedi [SAP Web Dispatcher ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window}.

  * **ABAP SAP Central Services (ASCS)**. Per l'alta disponibilità di ASCS in un ambiente {{site.data.keyword.cloud_notm}}, devi installare il software cluster del sistema operativo di destinazione, ad esempio, Linux Pacemaker o Microsoft Cluster. Devi configurare il punto di errore singolo di ASCS (servizio di accodamento di SAP) per replicarne i dati in un ERS (Enqueue Replication Service). Devi installare un'istanza ERS come parte del processo di installazione di SAP ed è supportato da SWPM di SAP. Per dettagli sull'installazione e la configurazione dei componenti cluster sia per ASCS che per ERS, consulta la documentazione dell'offerta del fornitore del sistema operativo.

  * **Server delle applicazioni SAP NetWeaver**. L'alta disponibilità viene raggiunta dal bilanciamento del carico del traffico all'interno di un pool di server delle applicazioni. Se è necessaria una quantità limitata di risorse, puoi configurare un singolo server della applicazioni come altamente disponibile. Il server delle applicazioni deve essere installato con archiviazione accessibile da tutti i potenziali nodi cluster che possono essere utilizzati per il failover. Inoltre, lo stack SAP NetWeaver deve utilizzare un nome host virtuale. Consulta la documentazione del fornitore del sistema operativo per dettagli sulla configurazione necessaria e la documentazione SAP per l'alta disponibilità. Se la tua configurazione richiede più server delle applicazioni, la configurazione dei server delle applicazioni SAP deve coprire anche il bilanciamento del carico, ad esempio nei gruppi di accesso SAP e nei gruppi server RFC. Per ulteriori informazioni, vedi la guida di gestione per la tua versione di SAP NetWeaver.

  * **Livello database**. L'architettura di riferimento di esempio distribuisce una singola istanza SAP HANA o di un altro database. Per l'alta disponibilità, distribuisci più di un'istanza e usa HSR (HANA System Replication) per implementare il failover manuale. Per abilitare il failover automatico, è necessaria un'estensione di alta disponibilità per la specifica distribuzione Linux. Per altri database, puoi configurare un failover dell'istanza database sull'archiviazione condivisa oppure puoi utilizzare una tecnica di replica simile al caso di SAP HANA. Consulta la documentazione del sistema di database supportato per la serie di opzioni richieste per configurare l'alta disponibilità o la replica.

  Per ulteriori informazioni, vedi [Supporto per l'alta disponibilità di {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha).

## Ripristino di emergenza
{: #dr}

Ciascun livello utilizza una strategia diversa per offrire una protezione per il ripristino di emergenza.

 * **Server delle applicazioni SAP NetWeaver**. I server delle applicazioni SAP non contengono dati aziendali; tuttavia, devi salvaguardare l'installazione e la configurazione del server per un funzionamento continuativo in caso di situazioni di emergenza. Una strategia di ripristino di emergenza consiste nell'avere i server delle applicazioni SAP in un'altra regione. Devi copiare le modifiche alla configurazione o gli aggiornamenti kernel presenti sul server delle applicazioni primario sulle macchine virtuali o sui server che si trovano nella regione per il ripristino di emergenza.

 * **SAP Central Services (SCS)**. Il componente SCS dello stack dell'applicazione SAP non conserva i dati aziendali. Puoi creare un server o una macchina virtuale nella regione per il ripristino di emergenza affinché abbia il ruolo SCS. L'unico contenuto proveniente dalla nota SCS primaria che devi sincronizzare è il contenuto della condivisione `/sapmnt`. Inoltre, se sui server primari SCS vengono eseguite le modifiche alla configurazione o gli aggiornamenti kernel, tali modifiche dovranno essere replicate anche sull'SCS per il ripristino di emergenza. Per sincronizzare i due server, usa regolarmente il lavoro di copia pianificato per copiare `/sapmnt` sui server per il ripristino di emergenza. Per ulteriori informazioni su SCS, vedi [Central Services Instance ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window}.

 * **Livello database**. Per i sistemi basati su SAP HANA, usa le soluzioni di replica supportate da HANA come ad esempio le funzioni di replica di sistema HANA o di replica di archiviazione {{site.data.keyword.cloud_notm}}. Per altri database supportati, fai riferimento alla documentazione database per le sue funzioni supportate. In generale, per scegliere tra le opzioni disponibili, devi aver compreso chiaramente i requisiti aziendali dell'applicazione SAP sottostante. Devi determinare l'impatto di una potenziale perdita di singole transazioni o anche di tutti i dati all'interno di una finestra temporale.

 * **Infrastruttura**. A seconda dell'ubicazione dei client SAP nella tua infrastruttura {{site.data.keyword.cloud_notm}}, devi preparare gli altri componenti al suo interno per gli scenari di ripristino di emergenza. Nell'architettura di riferimento di esempio, i client accedono ai sistemi SAP dal lato in loco oppure dalla rete aziendale del cliente.

## Sicurezza
{: #security}

### Gestione utente

SAP dispone di un proprio UME (Users Management Engine) per controllare l'accesso basato sul ruolo e l'autorizzazione con l'applicazione SAP. Per ulteriori informazioni, vedi [SAP HANA Security - An Overview ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://archive.sap.com/documents/docs/DOC-62943){: new_window}. Da una prospettiva di gestione utente, non è rilevante se i tuoi sistemi SAP vengono eseguiti su {{site.data.keyword.cloud_notm}} in loco. Le eccezioni a tale regola vengono menzionate in [Server Jump box](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box).

### Sicurezza di rete

Poiché hai diversi modi per accedere ad un ambiente basato su {{site.data.keyword.cloud_notm}}, devi differenziare le misure di sicurezza.

Devi considerare l'uso di un'interfaccia pubblica per l'accesso esterno solo nelle distribuzioni di tipo PoC (proof-of-concept). Per gli scenari di produzione, è disponibile la distribuzione delle applicazioni Vyatta in quanto le applicazioni dispongono di tutte le funzioni necessarie (firewall VPN e così via). Se i requisiti di latenza e/o di velocità effettiva non dovessero essere soddisfatti dalle applicazioni Vyatta, contatta il supporto {{site.data.keyword.cloud_notm}} per discutere di tutte le possibili procedure e configurazioni che possono essere rese disponibili oltre le applicazioni Vyatta.
