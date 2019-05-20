---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-05"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, VLAN, SAP Web Dispatcher, load balancing, database, high availability, disaster recovery, HA, DR

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Descrizione dell'architettura che sta dietro l'architettura di riferimento SAP
{: #architecture}

L'esempio di architettura della Figura 1 potrebbe essere diverso dalla tua architettura; mostra i concetti generali di una distribuzione basata su SAP {{site.data.keyword.cloud}}. I tuoi sistemi in loco sono connessi tramite Internet alla tua infrastruttura {{site.data.keyword.cloud_notm}}.

Una volta ordinato e distribuito il tuo ambiente, connettiti tramite una VPN di amministrazione alla tua infrastruttura {{site.data.keyword.cloud_notm}}. La VPN potrebbe non essere sufficiente per connettere i tuoi sistemi in loco con i sistemi basati su cloud, questo è il motivo per cui puoi distribuire un'applicazione di rete Vyatta nel tuo ambiente {{site.data.keyword.cloud_notm}}. Per requisiti di maggiore larghezza di banda e minore latenza, è supportato anche un handover del circuito Ethernet nell'ambiente cloud.

Nella Figura 1 vengono mostrati due diversi data center composti da diversi {{site.data.keyword.baremetal_short}} certificati SAP sia per SAP NetWeaver che per SAP HANA. I {{site.data.keyword.baremetal_short}} o le macchine virtuali nel diagramma possono essere diversi a seconda del tuo ambiente e della tecnologia database che stai utilizzando. Inoltre, i dati SAP HANA nella panoramica dell'architettura vengono trasferiti dal data center primario a quello secondario per il ripristino di emergenza (DR). Anche altri database consentono configurazioni simili alla Figura 1, con delle variazioni nella procedura.

Nella Figura 1, sul sito del data center DR, i sistemi replicati sono configurati per mantenere le capacità DR che devono essere implementate a diversi livelli. Per ulteriori informazioni, vedi [Considerazioni sul ripristino di emergenza (DR)](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Figura 1. Architettura di riferimento di esempio

![Figura 1. Architettura di riferimento di esempio](/images/SAP-optimization-ref-architecture-20180527.png "Architettura di riferimento di esempio")

## Sistemi SAP
{: #sap-systems}

I sistemi SAP (Advanced Business Application Programming (ABAP), Java e SAP HANA) dispongono di una serie granulare di oggetti di autorizzazione per la gestione utente. A causa di ciò, deve essere configurato solo l'accesso remoto dai desktop o da altri dispositivi di front-end all'ambiente basato su {{site.data.keyword.cloud_notm}}. Nessun accesso utente deve essere concesso e gestito nell'ambiente cloud. Potrebbero esserci diversi utenti con responsabilità differenti che necessitano dell'accesso a un database tramite una specifica GUI, una riga di comando, o che hanno delle limitazioni di latenza che richiedono un accesso basato su RDP (Remote Desktop Protocol). Per gestire questo tipo di accesso remoto, puoi distribuire un "jump host" nell'ambiente in modo che operi come punto centrale di accesso per questi scenari. Oltre a questi requisiti specifici, gli utenti hanno accesso ai sistemi basati su cloud all'interno della tua rete aziendale e non devono essere gestiti in un modo specifico. 

## Rete
{: #network}

Qualsiasi dispositivo in un ambiente {{site.data.keyword.cloud_notm}} può essere ordinato con una scelta di accesso LAN interno ed esterno facoltativo. L'indirizzo esterno è un indirizzo IP pubblico instradabile e deve essere utilizzato con attenzione. L'indirizzo interno viene determinato dalla VLAN ordinata e scelto da un sottointervallo di 10.0.0.0/8 per la VLAN. Ordinando più VLAN, puoi separare ambienti o tipi di traffico diversi, a seconda dei requisiti di progettazione della rete e di sicurezza. 

Mentre un'interfaccia pubblica con un firewall configurato può coprire alcuni scenari, ad esempio una prova di utilizzo di prototipazione rapida a breve termine con dati non critici, per la maggior parte dei casi devi valutare un dispositivo firewall. L'architettura di riferimento di esempio mappa uno scenario di produzione, quindi le interfacce di rete pubbliche non rientrano nell'ambito.

## Gateway di rete Vyatta
{: #vyatta}

Vyatta offre un router virtuale basato su software, un firewall/NAT virtuale e capacità VPN sia per IPv4 che per IPv6. Se gli utenti devono connettersi in remoto ai tuoi sistemi basati su {{site.data.keyword.cloud_notm}}, questi dispositivi possono funzionare come endpoint per una VPN side-to-side o per la cosiddetta "VPN road warrior" (punto di accesso). Puoi utilizzare diversi tipi di IPSec basato su tecnologie VPN o tunnel VPN SSL come OpenVPN. A seconda della tecnologia SAP che stai utilizzando, puoi usare queste connessioni VPN per interconnettere i sistemi SAP (anche con sistemi non SAP) per la tecnologia GUI tradizionale e per la tecnologia SAP UI5 basata su browser. La connessione di un SAP Web Dispatcher dietro un firewall Vyatta Gateway ti consente di utilizzare ulteriori funzioni come il bilanciamento del carico o scenari SSO (single sign-on). Per ulteriori informazioni su SAP Web Dispatcher, vedi [Alta disponibilità](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#availability).

Il dispositivo Vyatta può essere distribuito in una configurazione cluster ad alta disponibilità con una larghezza di banda massima di 10 Gbps. Per ulteriori informazioni, vedi [Configurazione dell'elevata disponibilità di Vyatta 5400](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-vyatta-5400-high-availability-configuration#vyatta-5400-high-availability-configuration).

## Server Jump box
{: #jump_box}

I sistemi SAP hanno una gestione utente integrata e non richiedono una gestione utente centralizzata. Ovviamente, puoi configurare la gestione utente centralizzata. Per ulteriori informazioni, vedi [Central User Administration ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm){: new_window}.

Un server jump box ti consente di fornire a specifici utenti un accesso di basso livello al tuo ambiente {{site.data.keyword.cloud_notm}} tramite strumenti basati su accesso da riga di comando o altri strumenti speciali per tale scopo, ad esempio SAP HANA Studio. Gli strumenti di gestione database, come pure gli utenti con accesso agli strumenti vengono gestiti centralmente sul server jump box. Gli utenti possono accedere al tuo ambiente {{site.data.keyword.cloud_notm}} dai loro desktop tramite RDP (Remote Desktop Protocol), che viene instradato tramite il gateway VPN.

## Server SAP - SAP HANA e SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}} offre diversi tipi di server per SAP HANA e SAP NetWeaver tramite l'offerta {{site.data.keyword.cloud_notm}} per applicazioni SAP. I server sono {{site.data.keyword.baremetal_short}} con il sistema operativo di tua scelta (Red Hat Linux, SUSE Linux, Microsoft Windows Server distribuito con l'hypervisor VMware ESX). Per dettagli sui server certificati SAP NetWeaver, vedi [SAP Note 2414097 ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. Tieni presente che sull'hypervisor, distribuisci uno dei sistemi operativi elencati nella nota SAP 2414097 come sistema operativo guest.

I server SAP HANA vengono forniti con un layout di archiviazione preselezionato che soddisfa i KPI (Key Performance Indicator) di archiviazione di SAP per SAP HANA. Non puoi modificare questi layout e sei esortato a non utilizzare un'archiviazione esterna per SAP HANA. Puoi utilizzare l'archiviazione esterna di qualità diversa e accessibile tramite diversi protocolli, NFS, CIFS, iSCSI, per il backup e altri scopi. Inoltre, per i server SAP NetWeaver, hai la possibilità di eseguire altri sistemi di database supportati sull'archiviazione esterna.

Tutte le soluzioni software SAP su SAP HANA o su un SAP NetWeaver includono l'intera SAP Business Suite e SAP S/4HANA può essere distribuito nell'ambiente {{site.data.keyword.cloud_notm}}. Per altri componenti software al di fuori di questi, devi contattare il supporto SAP. Segui il processo di ridimensionamento SAP per determinare la dimensione server corretta per il tuo progetto e scegli tra i server elencati per l'offerta SAP HANA o SAP NetWeaver.

Per ulteriori informazioni sui server certificati SAP HANA, vedi [Certified and Supported SAP HANA Hardware Directory ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud){: new_window}.

Per ulteriori informazioni sul processo di ridimensionamento SAP HANA, vedi [Ridimensionamento del server (SAP HANA)](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server).

Per ulteriori informazioni sul processo di ridimensionamento SAP NetWeaver, vedi [Ridimensionamento del server (SAP NetWeaver)](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-size_the_server#size_the_server).
