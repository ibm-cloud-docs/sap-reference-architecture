---



copyright:
  years: 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# FAQ: SAP HANA
{: #hana-faqs}

## SAP HANA ではどのサイズの IBM Cloud ベア・メタル・サーバーを使用できますか?

SAP 認定の {{site.data.keyword.baremetal_long}} は、以下の RAM サイズで使用できます。
  * 512 GB
  * 1 TB
  * 2 TB
  * 4 TB
  * 8 TB
  
## IBM Cloud インフラストラクチャーでは、どのようなハードウェア共有オプションがサポートされていますか? たとえば、仮想 HANA およびマルチテナント・データベース・コンテナー (MDC) はサポートされていますか?

{{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャー製品は、SAP 認定のベア・メタル・サーバーの配備を提供するものであり、仮想化は含まれていません。このインフラストラクチャー上の変更が引き続き SAP 認定に準拠しているかどうかの確認は、お客様の責任で行っていただきます。

## IBM HANA を IBM Cloud に配備するにはどうすればいいですか?

実装手順は、[SAP HANA on {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started) に記載されています。これは自己管理型製品であるため、{{site.data.keyword.cloud_notm}} で SAP HANA を実装するのはお客様の責任です。{{site.data.keyword.IBM_notm}} では、SAP のアドバイザリー・サービスやマネージド・サービスを提供してお客様を支援しています。詳しくは、[{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed) を参照してください。

## SAP HANA ではスケール・アウトがサポートされていますか?

現在、SAP HANA ではスケール・アウトはサポートされていません。

## SAP Business Suite on HANA でサポートされるサーバーの最大サイズは何バイトでしょうか?

SAP Business Suite on HANA をサポートするサーバーの最大サイズは 8 TB です。

##  SAP Business Warehouse on HANA でサポートされるサーバーの最大サイズは何バイトでしょうか?

SAP Business Warehouse on HANA をサポートするサーバーの最大サイズは 4 TB です。

## SAP HANA 認定サーバーをバックアップするにはどうすればいいですか?

サーバーのバックアップは、自己管理型製品には含まれていません。{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータルでのサーバーの注文プロセス中に選択できるオプションがあります。また、サード・パーティー製のバックアップ・ソリューションを統合するオプションもあります。

## 既存の SAP HANA データベースまたはリレーショナル・データベースを IBM Cloud 内の SAP HANA 認定サーバーに移行するにはどうすればいいですか?

自己管理型サービスには移行サービスは含まれていません。あらゆる移行をお客様の責任で行っていただく必要があります。{{site.data.keyword.IBM_notm}} では、SAP 移行の計画と実行に役立つさまざまなアドバイザリー・サービスおよびマネージド・サービスを提供しています。詳しくは、[{{site.data.keyword.cloud_notm}} アドバイザリー・サービス](https://ibm.com/us-en/marketplace/cloud-consulting-services)を参照してください。

## SAP HANA 2.0 は IBM Cloud SAP 認定インフラストラクチャー製品の一部としてサポートされていますか?

はい、SAP HANA 2.0 対応のオペレーティング・システムを使用して SAP 認定サーバーを注文する場合は、SAP HANA 2.0 がサポートされます。詳しくは、[SAP Note 2235581](https://launchpad.support.sap.com/#/notes/2235581) を参照してください。
