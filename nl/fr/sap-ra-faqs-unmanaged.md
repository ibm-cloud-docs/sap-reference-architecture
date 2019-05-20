---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, database

subcollection: sap-reference-architecture, Frequently Asked Questions, FAQs

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Foire aux questions : infrastructure IBM Cloud certifiée SAP (autogérée)
{: #faqs}

## A quoi correspond l'infrastructure IBM Cloud certifiée SAP ?
{: faq}

L'infrastructure {{site.data.keyword.cloud}} certifiée SAP est le composant autogéré de l'offre {{site.data.keyword.cloud_notm}} for SAP Applications. Ce composant vous permet d'exécuter SAP NetWeaver et SAP HANA sur {{site.data.keyword.cloud_notm}} en tant qu'infrastructure IaaS (Infrastructure-as-a-Service) en libre-service.

## En quoi l'infrastructure certifiée SAP diffère-t-elle de l'offre IBM Cloud for SAP Applications ?
{: faq}

L'offre {{site.data.keyword.cloud_notm}} for SAP Applications dispose de composants multiples ; l'infrastructure {{site.data.keyword.cloud_notm}} certifiée SAP est le composant autogéré de l'offre.  Un composant de *service géré* est disponible pour les clients qui recherchent des services de type MOS (Managed Operating System) ou des services Managed SAP Basis. L'infrastructure {{site.data.keyword.cloud_notm}} certifiée SAP est destinée aux clients ou partenaires commerciaux qui veulent gérer l'infrastructure depuis le système d'exploitation dans les applications SAP.

## Les services gérés sont-ils proposés avec l'infrastructure IBM Cloud ?
{: faq}

Oui, {{site.data.keyword.IBM_notm}} peut fournir des services gérés pour le système d'exploitation, la base de données et SAP via l'offre {{site.data.keyword.cloud_notm}} for SAP Applications. Pour plus d'informations, voir [Managed Services for SAP Applications ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## SAP peut-il être exécuté sur tout serveur IBM Cloud ?
{: faq}

Non, seuls les modèles de serveur certifiés pour SAP peuvent être utilisés pour exécuter SAP HANA ou SAP NetWeaver.

## Quels sont les serveurs certifiés pour utilisation avec SAP dans une infrastructure IBM Cloud ?
{: faq}  

Pour une liste actualisée des serveurs certifiés pour utilisation avec une charge de travail SAP, voir [SAP-certified infrastructure ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/bare-metal-servers/sap){: new_window}.

## Quelle sorte de charge de travail SAP peut-elle être exécutée sur l'infrastructure IBM Cloud ?
{: faq}

Actuellement, les charges de travail pour les applications SAP NetWeaver et SAP HANA en utilisation de production ou de non production peuvent être exécutées sur l'infrastructure {{site.data.keyword.cloud_notm}}.

## Quels sont les systèmes d'exploitation pris en charge pour SAP ?
{: faq}

  * Pour les applications SAP NetWeaver, Red Hat Enterprise Linux for SAP Business Applications 6.x, SUSE Enterprise Linux for SAP Applications 12 SP2 et Microsoft Windows Server 2012+ sont pris en charge.
  * Pour les applications SAP HANA, Red Hat Enterprise Linux 7.4 for SAP HANA, SUSE Linux Enterprise Server 12 SP2 for SAP HANA et VMware Server Virtualization 6.5.

## Quelles sont les configurations serveur modifiables ?
{: faq}

Vous pouvez ajouter la plupart des options d'infrastructure (stockage connecté, réseau, sécurité, surveillance, détection d'intrusion, bande passante publique ou vitesse de port, par exemple). L'unité centrale, la mémoire vive et le stockage interne, qui correspondent par défaut à votre sélection de serveur, ne peuvent pas être modifiés lors du processus de commande ou via un ticket de support.

## Qui dois-je contacter si j'ai d'autres questions sur les serveurs certifiés SAP ?
{: faq}

Le service commercial est disponible pour répondre à vos questions, mais vous pouvez aussi utiliser les autres options de support {{site.data.keyword.cloud_notm}}, tel le dialogue en ligne, le téléphone et [{{site.data.keyword.cloud_notm}} Docs](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

## Existe-t-il une matrice de responsabilités des services qui montre les tâches de gestion exécutées par IBM, le client et le partenaire commercial ?
{: faq}

L'infrastructure {{site.data.keyword.cloud_notm}} certifiée SAP est une offre autogérée. Toute la gestion de l'infrastructure management relève de la responsabilité du client et du partenaire commercial.
