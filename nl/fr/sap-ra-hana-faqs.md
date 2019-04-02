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

# Foire aux questions : SAP HANA
{: #hana-faqs}

## Quelles sont les tailles de serveur bare metal (ou serveur physique) disponibles pour SAP HANA ?
{: faq}

Les serveurs {{site.data.keyword.baremetal_long}} certifiés SAP sont disponibles avec une mémoire vive proposée dans différentes tailles :
* 512 Go
* 1024 Go (1 To)
* 2048 Go (2 To)
* 4096 Go (4 To)
* 6144 Go (6 To)
* 8192 Go (8 To)
* 12288 Go (12 To)

## Quelles sont les options de partage matériel prises en charge dans l'infrastructure IBM Cloud (Virtual HANA et MDC (Multitenant Database Containers), par exemple) ?
{: faq}

L'offre d'infrastructure {{site.data.keyword.cloud_notm}} certifiée SAP, qui est un déploiement de serveur bare metal certifié par SAP, n'inclut pas la virtualisation. Il est de votre responsabilité de vous assurer que tout les changements effectués sur cette infrastructure restent conformes à la certification SAP.

## Comment déployer SAP HANA sur IBM Cloud ?
{: faq}

La procédure d'implémentation est décrite dans [SAP HANA on {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started). Comme il s'agit d'une offre autogérée, vous êtes responsable de l'implémentation de SAP HANA dans {{site.data.keyword.cloud_notm}}. {{site.data.keyword.IBM_notm}} fournit effectivement des services de recommandation et des services SAP gérés pour vous assister. Pour plus d'informations, voir [Managed Services for SAP Applications ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## L'évolutivité horizontale par ajout est-elle prise en charge pour SAP HANA ?
{: faq}

Oui. Pour plus d'informations, voir [Configuration de votre infrastructure {{site.data.keyword.cloud_notm}} pour la prise en charge d'un système SAP HANA à plusieurs noeuds](/docs/infrastructure/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage).

## Quelle est la taille serveur maximale prise en charge pour SAP Business Suite on HANA ?
{: faq}

8 To est la taille serveur certifié IaaS maximale pour prendre en charge SAP Business Suite on HANA. La valeur 12 To est proposée sous HANA TDI v5 pour les charges de travail approuvées.

##  Quelle est la taille serveur maximale prise en charge pour SAP Business Warehouse on HANA ?
{: faq}

4 To est la taille serveur maximale certifié IaaS pour prendre en charge SAP Business Warehouse on HANA.

## Comment sauvegarder mes serveurs certifiés SAP HANA ?
{: faq}

La sauvegarde de serveur n'est pas incluse dans l'offre autogérée. Il existe des options que vous pouvez sélectionner lors du processus de commande de serveur sur le portail client d'infrastructure {{site.data.keyword.cloud_notm}}. Vous avez aussi la possibilité d'intégrer une solution de sauvegarde tiers.

## Comment migrer une base de données SAP HANA ou une base de données relationnelle sur un serveur certifié SAP HANA dans IBM Cloud ?
{: faq}

Aucun service de migration n'est inclus avec le service autogéré ; aucune activité de migration n'est sous votre responsabilité. {{site.data.keyword.IBM_notm}} propose néanmoins une gamme de services de recommandation et de services gérés pouvant vous faciliter la planification et l'exécution de la migration SAP. Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} Advisory Services ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.com/us-en/marketplace/cloud-consulting-services){: new_window}. Sélectionnez *Services* > *Cloud Services*.

## SAP HANA 2.0 est-il pris en charge en tant qu'élément de l'offre d'infrastructure IBM Cloud certifiée SAP ?
{: faq}

Oui, SAP HANA 2.0 est pris en charge si vous commandez un serveur certifié SAP avec un système d'exploitation conforme à SAP HANA 2.0. Pour plus d'informations, voir [SAP Note 2235581 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://launchpad.support.sap.com/#/notes/2235581){: new_window}.
