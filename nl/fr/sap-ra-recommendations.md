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

# Conseils pour votre infrastructure IBM Cloud certifiée SAP
{: #recommendations}

Même si vos besoins risquent de différer des cas de figure décrits ici, cette rubrique peut vous servir de point de départ pour générer votre serveur certifié SAP dans l'environnement {{site.data.keyword.cloud}}.

Figure 1. Architecture de référence exemple

![Figure 1. Architecture de référence exemple](/images/SAP-optimization-ref-architecture-20180527.png "Architecture de référence exemple")

## Réseaux VLAN
{: #vlans}

Les instructions SAP de conception d'environnement recommandent une isolation du trafic serveur sur différents contrôleurs NIC (Network Interface Controller). Ainsi, les données professionnelles doivent être séparées du trafic d'administration et de sauvegarde. L'affectation de plusieurs contrôleurs NIC à différents sous-réseaux permet de mettre en place cette séparation des données. Pour plus d'informations, voir la section Network dans [Building High Availability for SAP NetWeaver and SAP HANA ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} (PDF).

Pour suivre les recommandations NIC, {{site.data.keyword.cloud_notm}} autorise la configuration de réseaux VLAN multiples sur les serveurs. Une haute disponibilité peut être affectée aux interfaces VLAN via la configuration de plusieurs contrôleurs NIC sous des interfaces liées (Linux) ou associées (Microsoft Windows). Pour les fonctionnalités de haute disponibilité et de reprise après incident sur les serveurs {{site.data.keyword.baremetal_short}}, la meilleure solution est de réserver des adresses IP supplémentaires et d'affecter ces adresses aux différents services SAP au fur et à mesure de leur implémentation. Consultez la documentation d'installation SAP pour savoir comment attribuer les adresses lors de l'installation avec le gestionnaire SWPM (SAP Software Provisioning Manager). Pour les machines virtuelles, l'adresse de l'interface principale de la machine virtuelle suffit généralement.

Par défaut, les serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} ont une interface publique et privée. En général, il n'est pas conseillé de conserver le réseau LAN public pour tous les serveurs de votre infrastructure {{site.data.keyword.cloud_notm}}. Des instances spécifiques de la passerelle Vyatta Network Gateway doivent être déployées pour permettre un accès public à votre environnement, si nécessaire. Pour plus d'informations, voir [Vyatta Network Gateway](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta).

## Stockage {{site.data.keyword.cloud_notm}}
{: #storage}

Les serveurs {{site.data.keyword.cloud_notm}} certifiés pour SAP NetWeaver peuvent être configurés avec un nombre différent de disques internes ainsi qu'avec des agencements différents pour ces disques pour la configuration RAID. Notez que ces agencements risquent de ne pas suffire par rapport aux exigences des projets (taille insuffisante, ou accès partagé au stockage, par exemple).

Les conseils donnés ici au niveau des exigences de stockage ont clairement pour objectif de définir les indicateurs KPI (Key Performance Indicator) en terme de plages horaires de sauvegarde et de restauration, d'établir les besoins en haute disponibilité et basculement, puis de décider le type de stockage à utiliser. Même si la présentation de l'ensemble des options disponibles dépasse le cadre de cette documentation, certains conseils peuvent toutefois être fournis.

  * Utilisez des appareils iSCSI partagés pour les configurations haute disponibilité avec basculement d'une base de données entre les noeuds. Tenez compte de la valeur maximale requise d'IOPS/sec.

  * Utilisez un stockage interne pour les configurations haute disponibilité avec une base de données qui est répliquée (réplication de système SAP HANA, par exemple). Les serveurs d'applications SAP NetWeaver peuvent résider sur un stockage interne ou sur un stockage NAS (Network Attached Storage).

  * Utilisez un stockage partagé pour faciliter la mise en oeuvre des fonctionnalités de basculement avec les installations VMware. Pour plus d'informations sur le bon type de stockage, voir [Storage to use with VMware Systems](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems).

Toutes les options peuvent être sélectionnées dans l'infrastructure {{site.data.keyword.cloud_notm}}.

## Haute disponibilité
{: #availability}

Dans une installation répartie d'applications SAP sur une base de données centralisée, l'installation de base est répliquée pour atteindre la haute disponibilité. Pour chaque couche de l'architecture, la conception de la haute disponibilité varie.

  * **Répartiteur Web SAP**. La haute disponibilité est atteinte avec des instances de répartiteur Web SAP multiples et redondantes associées au trafic des applications SAP. Le répartiteur Web SAP sert de point d'entrée potentiel pour un ensemble de systèmes SAP et d'autres services reposant sur `https`. Situé généralement entre internet et les systèmes de backend, il traite les demandes à base de protocole web en provenance du "monde extérieur". Le répartiteur Web SAP fonctionne comme un proxy inverse avec une grande variété de fonctions prises en charge, tel l'équilibrage de charge ou la connexion SSO (Single Sign On). Pour plus d'informations, voir [SAP Web Dispatcher ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window}.

  * **Services ASCS (ABAP SAP Central Services)**. Pour la haute disponibilité des services ASCS dans un environnement {{site.data.keyword.cloud_notm}}, le logiciel de cluster du système d'exploitation cible doit être installé (Linux Pacemaker ou Microsoft Cluster, par exemple). Le point de défaillance unique d'ASCS (service  de SAP mis en file d'attente) doit être configuré pour répliquer ses données dans un service ERS (Enqueue Replication Service). Une  instance ERS, qui doit être installée dans le cadre du processus d'installation SAP, est prise en charge par le gestionnaire SWPM (SAP Software Provisioning Manager) de SAP. Pour plus de détails sur l'installation et la configuration des composants de cluster pour les services ASCS et ERS, consultez la documentation de l'offre du système d'exploitation du fournisseur.

  * **Serveurs d'applications SAP NetWeaver**. La haute disponibilité est atteinte en équilibrant les charges du trafic à l'intérieur d'un pool de serveurs d'applications. Si seul un volume limité de ressources est requis, un serveur d'applications unique peut être configuré comme hautement disponible. Le serveur d'applications doit être installé avec un stockage accessible à tous les noeuds de cluster potentiels, pouvant servir pour le basculement. De plus, la pile SAP NetWeaver doit utiliser un nom d'hôte virtuel. Consultez la documentation de votre fournisseur de système d'exploitation pour plus de détails sur le configuration requise et la documentation SAP relative à la haute disponibilité. Si votre configuration requiert des serveurs d'applications multiples, la configuration des serveurs d'applications SAP doit aussi couvrir l'équilibrage de charge, dans les groupes de connexion SAP et les groupes de serveurs RFC, par exemple. Pour plus d'informations, voir le guide d'administration pour votre version SAP NetWeaver.

  * **Groupe de serveurs d'applications de base de données**. L'architecture de référence exemple déploie une instance SAP HANA (ou une autre base de données) unique. Pour la haute disponibilité, déployez plusieurs instances et utilisez la réplication HSR (HANA System Replication) pour implémenter un basculement manuel. Pour activer le basculement automatique, une extension de haute disponibilité pour la distribution Linux spécifique est requise. Pour les autres bases de données, un basculement de l'instance de base de données sur un stockage partagé peut être configuré ou une technique de réplication similaire au cas SAP HANA peut être utilisée. Consultez la documentation du système de base de données pris en charge pour connaître l'ensemble des options qui sont requises pour configurer la haute disponibilité ou la réplication.

  Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} high-availability support](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha).

## Reprise après incident
{: #dr}

Chaque groupe de serveurs d'applications utilise une stratégie différente pour fournir une protection de type reprise après incident.

 * **Serveurs d'applications SAP NetWeaver**. Les serveurs d'applications SAP ne contiennent aucune donnée professionnelle mais l'installation et la configuration du serveur doivent être préservées pour maintenir un fonctionnement continu après un incident. Une stratégie de reprise après incident consiste à disposer de serveurs d'applications SAP dans une autre région. Toute modification de configuration ou mise à jour du noyau sur le serveur d'applications principal doit être copiée sur les machines virtuelles ou les serveurs de la région concernée par la reprise après incident.

 * **Services SCS (SAP Central Services)**. Le composant SCS de la pile d'applications SAP ne conserve pas les données professionnelles. Vous pouvez mettre en place un serveur ou une machine virtuelle dans la région où s'effectue la reprise après incident pour exécuter le rôle SCS. Le seul contenu provenant de la note SCS principale à synchroniser est le contenu partagé `/sapmnt`. De plus, si des modifications de configuration ou des mises à jour du noyau se produisent sur les serveurs SCS principaux, les changements doivent être répliqués sur le SCS de reprise après incident. Pour synchroniser les deux serveurs, utilisez un travail de copie programmé de façon régulière pour copier `/sapmnt` vers les serveurs de reprise après incident. Pour plus d'informations sur SCS, voir [Central Services Instance ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window}.

 * **Groupe de serveurs d'applications de base de données**. Pour les systèmes SAP HANA, utilisez les solutions de réplication prises en charge par HANA comme HSR (HANA System Replication) ou les fonctions de réplication de stockage {{site.data.keyword.cloud_notm}}. Pour les autres bases de données prises en charge, consultez la documentation de base de données pour connaître les fonctions proposées. En général, le choix parmi les options disponibles nécessite une compréhension claire des exigences professionnelles de l'application SAP sous-jacente. L'impact d'une perte potentielle de quelques transactions uniques ou même de toutes les données dans une fenêtre de temps précise doit être déterminé.

 * **Infrastructure**. Selon l'endroit où se trouvent les clients SAP dans votre infrastructure {{site.data.keyword.cloud_notm}}, les autres composants inclus doivent être préparés pour les scénarios de reprise après incident. Dans l'architecture de référence exemple, les clients accèdent aux systèmes SAP sur site ou à partir du réseau d'entreprise du client.

## Sécurité
{: #security}

### Gestion des utilisateurs

SAP dispose de son propre moteur UME (Users Management Engine) pour gérer les autorisations et l'accès à base de rôle avec l'application SAP. Pour plus d'informations, voir [SAP HANA Security - An Overview ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://archive.sap.com/documents/docs/DOC-62943){: new_window}. Dans une perspective de gestion utilisateur, l'exécution d'{{site.data.keyword.cloud_notm}} sur site par vos systèmes SAP n'est pas pertinente. Des exceptions à cette règle sont mentionnées dans [Serveur jump box](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box).

### Sécurité du réseau

Puisqu'il existe différentes façons d'accéder à un environnement {{site.data.keyword.cloud_notm}}, une différenciation des mesures de sécurité doit être effectuée.

L'utilisation d'une interface publique pour un accès externe ne doit être envisagée que pour les déploiements de type validation de concept. Pour les scénarios de production, le déploiement d'appliances Vyatta est disponible, puisque ces appliances proposent toutes les fonctionnalités requises (pare-feu VPN, etc). Au cas où les exigences de temps de latence ou de capacité de traitement ne sont pas couvertes par les appliances Vyatta, contactez le support {{site.data.keyword.cloud_notm}} pour envisager toutes les configurations et procédures possibles qui peuvent être mises en oeuvre en plus des appliances Vyatta.
