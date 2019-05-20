---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Frequently Asked Questions, FAQs, {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure implementation and operations

subcollection: sap-reference-architiecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Foire aux questions : implémentation et opérations de l'infrastructure IBM Cloud certifiée SAP

## IBM Cloud propose-t-il des serveurs gérés pour SAP ?
{: faq}

Oui, IBM offre un composant de services gérés pour l'offre {{site.data.keyword.cloud}} for SAP Applications. Pour plus d'informations, voir [Managed Services for SAP Applications ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/sap/managed){: new_window}.

## Comment installer mes applications SAP sur l'infrastructure IBM Cloud ?
{: faq}

Les applications SAP sont installées manuellement et cette tâche est de votre responsabilité, car il n'existe pas d'image d'application préconfigurée. Si vous avez besoin de services SAP gérés supplémentaires, contactez le responsable des ventes des services {{site.data.keyword.cloud_notm}}.

## Où trouver des informations sur la façon d'implémenter SAP sur l'infrastructure IBM Cloud ?
{: faq}

  * Pour plus d'informations sur la façon d'implémenter votre environnement SAP NetWeaver sur l'infrastructure {{site.data.keyword.cloud_notm}}, voir [SAP NetWeaver on {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-getting-started#getting-started).

  * Pour plus d'informations sur la façon d'implémenter votre environnement SAP HANA sur l'infrastructure {{site.data.keyword.cloud_notm}}, voir [SAP HANA on {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started).

## Comment accéder à mes systèmes SAP qui s'exécutent sur IBM Cloud ?
{: faq}

Vous accédez initialement à votre infrastructure via le portail client d'infrastructure {{site.data.keyword.cloud_notm}}. Le portail client fournit des options de connectivité supplémentaires (réseau VPN, par exemple). Comme il s'agit d'options autogérées, il est de votre responsabilité d'implémenter l'option de connectivité choisie.

## Comment connecter mes systèmes SAP qui s'exécutent sur l'infrastructure IBM Cloud à mes systèmes sur site ?
{: faq}

La connectivité entre vos systèmes sur site et l'infrastructure {{site.data.keyword.cloud_notm}} est de votre responsabilité, puisqu'il s'agit d'une offre autogérée. {{site.data.keyword.IBM_notm}} fournit effectivement des options de connectivité supplémentaires. Pour plus d'informations, voir [{{site.data.keyword.BluDirectLink}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/direct-link){: new_window}.

## Comment effectuer des sauvegardes de mes systèmes SAP qui s'exécutent sur l'infrastructure IBM Cloud ?
{: faq}

Les sauvegardes ne sont pas incluses dans l'offre autogérée. Il existe toutefois des solutions de sauvegarde que vous pouvez vous procurer via le portail client d'infrastructure {{site.data.keyword.cloud_notm}}. Vous avez aussi la possibilité d'acquérir et d'intégrer des solutions de sauvegarde tiers.

## Comment migrer mes systèmes sur site vers IBM Cloud ?
{: faq}

Aucun serveur de migration n'est inclus avec le service autogéré ; aucune activité de migration n'est sous votre responsabilité. {{site.data.keyword.IBM_notm}} propose néanmoins une gamme de services de recommandation et de services gérés pouvant vous faciliter la planification et l'exécution de la migration SAP. Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} Advisory Services ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.com/us-en/marketplace/cloud-consulting-services). Sélectionnez *Services* > *Cloud Services*.
