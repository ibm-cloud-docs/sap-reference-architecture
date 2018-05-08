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

# Foire aux questions : dimensionnement et architecture
{: #faqs_sizing}

## Quelles sont les mesures SAPS (SAP Application Performance Standard) pour chaque serveur IBM Cloud certifié SAP NetWeaver (taux SAPS et coeur) ?

Le tableau 1 présente les mesures SAP pour les serveurs {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} certifiés SAP NetWeaver.

Tableau 1. Mesures SAPS  pour les serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} certifiés SAP NetWeaver.

| **Type de serveur** | **SAPS** | **RAM** | **Coeurs** | **SAPS/Coeur** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 Go | 4 | 2688 |
| BI.S1.NW128 | 54130 | 128 Go | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 Go | 24 | 2293 |
| BI.S2.NW512 | 65520 | 512 Go | 28 | 2340 |

## Quelles sont les bases de données prises en charge par l'offre d'infrastructure IBM Cloud certifiée SAP ?

Pour les configurations SAP HANA, les plateformes de base de données SAP HANA 1.0 et SAP HANA 2.0 sont prises en charge. Pour des déclarations complètes de prise en charge des bases de données et des systèmes d'exploitation pour SAP NetWeaver, voir [SAP Note 2414097](https://launchpad.support.sap.com/#/notes/2414097).

## Une configuration de niveau 2 (serveur d'applications, plus une base de données SAP HANA) peut-elle être effectuée avec les serveurs IBM Cloud Bare Metal certifiés SAP HANA ?

Il est impossible de mettre en place une configuration de niveau 2 sur le même composant matériel. Cette opération peut toutefois être effectuée en utilisant une combinaison de configurations SAP NetWeaver et SAP HANA.

## La virtualisation (VMware) est-elle prise en charge sur l'infrastructure IBM Cloud certifiée SAP pour SAP NetWeaver ou SAP HANA ?

Oui, l'infrastructure {{site.data.keyword.cloud_notm}} certifiée SAP prend en charge VMware ESXi for SAP NetWeaver et SAP HANA. Il est important de noter que si vous choisissez de commander et d'implémenter un serveur exécutant VMware, il est de votre responsabilité de dimensionner et de configurer correctement toutes les machines virtuelles du serveur afin qu'elles soient conformes aux restrictions et meilleures pratiques de SAP. Pour plus d'informations, voir [SAP Note 2161991](https://launchpad.support.sap.com/#/notes/2161991).

## Les configurations des serveurs IBM Cloud Bare Metal certifiés SAP peuvent-elles être modifiées ?

Les serveurs {{site.data.keyword.baremetal_short}} certifiés SAP HANA ont des configurations fixes pour le processeur, la mémoire vive et le stockage local, basées sur le serveur, et ne peuvent pas être modifiées. Il est possible de modifier la configuration des options de réseau, de système d'exploitation et de services de surveillance.

Les serveurs {{site.data.keyword.baremetal_short}} certifiés SAP NetWeaver ont des configurations fixes pour le processeur et la mémoire vive ; le stockage local peut être configuré si nécessaire en fonction de vos besoins. Il est possible de modifier la configuration des options de réseau, de système d'exploitation et de services de surveillance.

## Il y a-t-il des méthodes de premier plan permettant de déployer une solution SAP dans l'infrastructure IBM Cloud certifiée SAP ?

Oui, [SAP Best Practices](https://help.sap.com/viewer/p/SAP_Best_Practices) vous propose diverses options que vous pouvez utiliser lors de votre déploiement. {{site.data.keyword.IBM_notm}} offre aussi des services de conseils relatifs au cloud. Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} Advisory Services](https://www.ibm.com/us-en/marketplace/cloud-consulting-services).

## Faut-il déployer SAP Solutions Manager et SAProuter ? Si c'est le cas, une infrastructure spécifique est-elle recommandée ?

Non, le déploiement de SAP Solutions Manager et SAProuter n'est pas obligatoire quand vous utilisez un environnement de formation, de bac à sable ou tout environnement similaire. Il est toutefois recommandé de déployer ces composants dans votre environnement de production.

