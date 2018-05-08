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

# Architecture de référence SAP IBM Cloud - Mise en route
{: #getting-started}

L'architecture {{site.data.keyword.cloud}} fournit des fonctionnalités techniques supérieures, comme un environnement logiciel définissable, essentiel pour une infrastructure de cloud, des interfaces programmables et des centaines de configurations logicielles et réseau. Elle est conçue pour offrir une très grande souplesse (en combinant des serveurs virtuels et dédiés afin de convenir à différentes charges de travail), une automatisation des interfaces et des options de déploiement hybrides. L'offre d'infrastructure {{site.data.keyword.cloud_notm}} certifiée SAP pour SAP HANA et SAP NetWeaver vous permet d'effectuer la sélection la plus appropriée à votre cas de figure, incluant des serveurs bare metal ou des serveurs de virtualisation sur lesquels s'exécute la pile de logiciels SAP.

## Architecture de référence
{: #ref-arch}

La figure 1 est une architecture de référence pour un environnement composé des éléments suivants :
  * Composants réseau Vyatta
  * Répartiteur Web SAP
  * Serveurs d'applications SAP NetWeaver
  * Bases de données SAP HANA
  * Autres systèmes de gestion de base de données relationnelle 
  
L'architecture de référence est configurée avec des fonctionnalités de haute disponibilité et de reprise après incident. Notez que dans la figure 1, les serveurs de base de données peuvent être des systèmes de base de données pris en charge par SAP NetWeaver, tel SAP HANA. 

Figure 1. Architecture de référence exemple

![Figure 1. Architecture de référence exemple](/images/ref_architecture.png "Architecture de référence exemple")
