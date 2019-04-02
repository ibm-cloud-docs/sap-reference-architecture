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

# Présentation de l'architecture de référence SAP
{: #architecture}

Même si l'architecture exemple de la figure 1 risque de ne pas être identique à votre propre architecture, elle montre les concepts généraux d'un déploiement SAP {{site.data.keyword.cloud}}. Vos systèmes sur site sont connectés via internet à votre infrastructure {{site.data.keyword.cloud_notm}}.

Une fois votre environnement organisé et déployé, vous vous connectez via un VPN d'administration à votre infrastructure {{site.data.keyword.cloud_notm}}. Il se peut que le VPN ne soit pas suffisant pour connecter vos systèmes sur site à vos systèmes reposant sur le cloud, ce qui explique pourquoi vous pouvez déployer une appliance Vyatta Network dans l'environnement {{site.data.keyword.cloud_notm}}. Pour une bande passante supérieure et des exigences de temps de latence réduit, le transfert d'un circuit Ethernet dans l'environnement de cloud est aussi pris en charge.

La figure 1 montre deux centres de données différents qui se composent de plusieurs serveurs SAP-certified {{site.data.keyword.baremetal_short}} certifiés SAP pour SAP NetWeaver et SAP HANA. Les {{site.data.keyword.baremetal_short}} ou les machines virtuelles du diagramme peuvent différer, selon votre environnement ou la technologie de base de  données que vous utilisez. De plus, les données SAP HANA de cette présentation d'architecture sont transférées depuis le centre de données principal vers le centre de données secondaire pour la reprise après incident (ou DR, pour Disaster Recovery). D'autres bases de données permettent aussi des configurations similaires à celles de la figure 1.

Dans la figure 1, sur le site du centre de données DR, les systèmes répliqués sont configurés pour gérer des fonctionnalités de reprise après incident, qui doivent être implémentées sur différentes couches. Pour plus d'informations, voir les [considérations relatives à la reprise après incident](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Figure 1. Architecture de référence exemple

![Figure 1. Architecture de référence exemple](/images/SAP-optimization-ref-architecture-20180527.png "Architecture de référence exemple")

## Systèmes SAP
{: #sap-systems}

Les systèmes SAP (ABAP, pour Advanced Business Application Programming, Java et SAP HANA) disposent d'un ensemble granulaire d'objets d'autorisation pour la gestion des utilisateurs. De ce fait, seul l'accès distant depuis des bureaux ou d'autres appareils frontaux vers l'environnement {{site.data.keyword.cloud_notm}} doivent être configurés. Aucun accès utilisateur final n'a besoin d'être accordé et géré dans l'environnement de cloud. Il peut y avoir plusieurs utilisateurs avec différentes responsabilités qui doivent accéder à une base de données via une interface utilisateur graphique spécifique ou au niveau d'une ligne de commande, ou des restrictions de latence nécessitant un accès via un protocole Remote Desktop Protocol. Pour gérer ce type d'accès distant, un "hôte jump" peut être déployé dans l'environnement afin de servir de point d'accès central pour ces scénarios. A part ces exigences spécifiques, les utilisateurs ont accès aux systèmes reposant sur le cloud au sein de votre réseau d'entreprise et n'ont donc pas besoin d'être administrés d'une façon spécifique.

## Réseau
{: #network}

Tout appareil d'un environnement {{site.data.keyword.cloud_notm}} peut être organisé en utilisant un choix d'accès LAN (Local Area Network) externe facultatif et interne. L'adresse externe est une adresse IP publique routable qui doit être gérée avec soin. L'adresse interne est déterminée par le réseau VLAN (Virtual Local Area Network) organisé et choisi depuis une sous-plage de 10.0.0.0/8 pour le réseau VLAN. En organisant des réseaux VLAN multiples, différents environnements, ou types de trafic, peuvent être isolés, selon vos exigences de sécurité et de conception réseau.

Alors qu'une interface publique avec un pare-feu configuré peut couvrir certains exemples de scénarios, une validation du concept par prototypage rapide à court terme avec un appareil en pare-feu configuré pour les données non critiques doit être envisagée dans la plupart des cas. L'architecture de référence exemple mappant un scénario de production, les interfaces de réseau public sont hors cadre.

## Vyatta Network Gateway
{: #vyatta}

Vyatta fournit un routeur virtuel logiciel, un NAT/pare-feu virtuel et des fonctionnalités VPN pour IPv4 et IPv6. Si les utilisateurs doivent se connecter à distance à vos systèmes {{site.data.keyword.cloud_notm}}, ces appareils peuvent servir de noeuds finaux aussi bien pour les réseaux VPN côte à côte que pour les réseaux VPN "road warrior" (point d'accès). Différents types de technologies VPN (IPSec ou tunnels SSL VPN, comme OpenVPN) peuvent être utilisés. Selon la technologie SAP dont vous vous servez, ces connexions VPN peuvent être utilisées pour interconnecter les systèmes SAP (même avec des systèmes non SAP) pour la technologie d'interface utilisateur graphique traditionnelle, ainsi que pour la technologie SAP UI5 à base de navigateur. La connexion d'un répartiteur Web SAP derrière une passerelle Vyatta Gateway permet l'utilisation d'autres fonctions, comme l'équilibrage de charge ou les scénarios SSO (Single Sign-On). Pour plus d'informations sur le répartiteur Web SAP, voir [Haute disponibilité](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#availability).

L'appareil Vyatta peut être déployé dans une cluster à haute disponibilité avec une bande passante pouvant aller jusqu'à 10 Gbps. Pour plus d'informations, voir [Vyatta 5400 High Availability Configuration](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-vyatta-5400-high-availability-configuration#vyatta-5400-high-availability-configuration).

## Serveur jump box
{: #jump_box}

Les systèmes SAP disposent d'une gestion utilisateur intégrée et ne requiert pas d'administration utilisateur centralisée. Vous pouvez, bien sûr, configurer une gestion utilisateur centralisée. Pour plus d'informations, voir [Central User Administration ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm){: new_window}.

Un serveur jump box vous permet de donner à des utilisateurs spécifiques un accès de bas niveau à votre environnement {{site.data.keyword.cloud_notm}} via des outils accessibles par ligne de commande ou d'autre outils à objectifs spécifiques, comme SAP HANA Studio. Les outils d'administration de base de données, comme les utilisateurs qui ont accès aux outils, sont gérés de façon centrale sur le serveur jump box. Les utilisateurs peuvent se connecter à votre environnement {{site.data.keyword.cloud_notm}} depuis leurs bureaux par le biais du protocole Remote Desktop Protocol, qui est routé via la passerelle VPN.

## Serveurs SAP - SAP HANA et SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}} propose différents serveurs pour SAP HANA et SAP NetWeaver via l'offre {{site.data.keyword.cloud_notm}} for SAP Applications. Il s'agit de serveurs {{site.data.keyword.baremetal_short}} avec votre choix de système d'exploitation (Red Hat Linux, SUSE Linux, Microsoft Windows Server, ou déploiement avec l'hyperviseur VMware ESX). Pour plus de détails sur les serveurs certifiés SAP NetWeaver, voir [SAP Note 2414097 ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. Sachez que sur l'hyperviseur, vous déployez l'un des systèmes d'exploitation répertoriés dans SAP Note 2414097 comme système d'exploitation invité.

Les serveurs SAP HANA sont livrés avec un agencement de stockage présélectionné qui répond aux indicateurs KPI (Key Performance Indicator) de stockage SAP pour SAP HANA. Vous ne pouvez pas changer ces agencements et il est vivement conseillé de ne pas utiliser de stockage externe pour SAP HANA. Un stockage externe de qualité différente et accessible via divers protocoles (NFS, CIFS, iSCSI) peut être utilisé pour des objectifs de sauvegarde ou autres. De plus, pour les serveurs SAP NetWeaver, vous avez la possibilité d'exécuter d'autres systèmes de base de données pris en charge sur stockage externe.

Toutes les solutions logicielles SAP reposant sur SAP HANA ou SAP NetWeaver incluent l'intégralité de SAP Business Suite, et SAP S/4HANA peut être déployé dans l'environnement {{site.data.keyword.cloud_notm}}. Pour les autres composants logiciels, vous devez contacter le support SAP. Suivez le processus de dimensionnement SAP pour déterminer la taille serveur correcte pour votre projet et choisir parmi les serveurs répertoriés pour l'offre SAP HANA ou SAP NetWeaver.

Pour plus d'informations sur les serveurs certifiés SAP HANA, voir [Certified and Supported SAP HANA Hardware Directory ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud){: new_window}.

Pour plus d'informations sur le processus de dimensionnement SAP HANA, voir [Sizing the server (SAP HANA)](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server).

Pour plus d'informations sur le processus de dimensionnement SAP NetWeaver, voir [Sizing the server (SAP NetWeaver)](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-size_the_server#size_the_server).
