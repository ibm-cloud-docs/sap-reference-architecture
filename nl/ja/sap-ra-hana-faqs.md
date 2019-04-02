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

# FAQ: SAP HANA
{: #hana-faqs}

## SAP HANA ではどのサイズの IBM Cloud ベア・メタル・サーバーを使用できますか?
{: faq}

SAP 認定の {{site.data.keyword.baremetal_long}} は、以下の RAM サイズで使用できます。
* 512 GB
* 1024 GB (1 TB)
* 2048 GB (2 TB)
* 4096 GB (4 TB)
* 6144 GB (6 TB)
* 8192 GB (8 TB)
* 12288 GB (12 TB)

## IBM Cloud インフラストラクチャーでは、どのようなハードウェア共有オプションがサポートされていますか? たとえば、仮想 HANA およびマルチテナント・データベース・コンテナー (MDC) はサポートされていますか?
{: faq}

{{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャー製品は、SAP 認定のベア・メタル・サーバーの配備を提供するものであり、仮想化は含まれていません。 このインフラストラクチャー上の変更が引き続き SAP 認定に準拠しているかどうかの確認は、お客様の責任で行っていただきます。

## IBM HANA を IBM Cloud に配備するにはどうすればいいですか?
{: faq}

実装手順は、[SAP HANA on {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-getting-started#getting-started) に記載されています。 これは自己管理型製品であるため、{{site.data.keyword.cloud_notm}} で SAP HANA を実装するのはお客様の責任です。 {{site.data.keyword.IBM_notm}} では、SAP のアドバイザリー・サービスやマネージド・サービスを提供してお客様を支援しています。 詳しくは、[Managed Services for SAP Applications ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/sap/managed){: new_window} を参照してください。

## SAP HANA ではスケール・アウトがサポートされていますか?
{: faq}

はい。 詳しくは、[SAP HANA マルチノードをサポートするための {{site.data.keyword.cloud_notm}} インフラストラクチャーの構成](/docs/infrastructure/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage)を参照してください。

## SAP Business Suite on HANA でサポートされるサーバーの最大サイズは何バイトでしょうか?
{: faq}

SAP Business Suite on HANA をサポートする IaaS 認定サーバーの最大サイズは 8 TB です。HANA TDI v5 では、承認済みワークロード用に 12 TB が提供されます。

##  SAP Business Warehouse on HANA でサポートされるサーバーの最大サイズは何バイトでしょうか?
{: faq}

SAP Business Warehouse on HANA をサポートする IaaS 認定サーバーの最大サイズは 4 TB です。

## SAP HANA 認定サーバーをバックアップするにはどうすればいいですか?
{: faq}

サーバーのバックアップは、自己管理型製品には含まれていません。 {{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータルでのサーバーの注文プロセス中に選択できるオプションがあります。 また、サード・パーティー製のバックアップ・ソリューションを統合するオプションもあります。

## 既存の SAP HANA データベースまたはリレーショナル・データベースを IBM Cloud 内の SAP HANA 認定サーバーに移行するにはどうすればいいですか?
{: faq}

自己管理型サービスには移行サービスは含まれていません。あらゆる移行をお客様の責任で行っていただく必要があります。 {{site.data.keyword.IBM_notm}} では、SAP 移行の計画と実行に役立つさまざまなアドバイザリー・サービスおよびマネージド・サービスを提供しています。 詳しくは、[{{site.data.keyword.cloud_notm}} アドバイザリー・サービス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.com/us-en/marketplace/cloud-consulting-services){: new_window} を参照してください。*「サービス」* > *「クラウド・サービス」*を選択します。

## SAP HANA 2.0 は IBM Cloud SAP 認定インフラストラクチャー製品の一部としてサポートされていますか?
{: faq}

はい、SAP HANA 2.0 対応のオペレーティング・システムを使用して SAP 認定サーバーを注文する場合は、SAP HANA 2.0 がサポートされます。 詳しくは、[SAP Note 2235581 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/2235581){: new_window} を参照してください。
