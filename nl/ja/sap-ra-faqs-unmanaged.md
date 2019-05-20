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

# FAQ: IBM Cloud 認定インフラストラクチャー (自己管理)
{: #faqs}

## IBM Cloud SAP 認定インフラストラクチャーとは何ですか?
{: faq}

{{site.data.keyword.cloud}} SAP 認定インフラストラクチャーとは、{{site.data.keyword.cloud_notm}} for SAP Applications 製品の自己管理コンポーネントです。 この製品のコンポーネントにより、{{site.data.keyword.cloud_notm}} 上でセルフ・サービスの Infrastructure as a Service (IaaS) として SAP NetWeaver および SAP HANA を実行できます。

## SAP 認定インフラストラクチャーと IBM Cloud for SAP Applications 製品の違いは何ですか?
{: faq}

{{site.data.keyword.cloud_notm}} for SAP Applications 製品には複数のコンポーネントがあります。{{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャーは、その製品の自己管理コンポーネントです。  Managed Operating System (OS) サービス (Managed SAP ベースのサービスまで) を求めているお客様を対象とした*マネージド・サービス*・コンポーネントをご利用いただけます。 {{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャーは、OS から SAP アプリケーションに至るまで、インフラストラクチャーを管理するお客様またはビジネス・パートナー向けです。

## IBM Cloud インフラストラクチャーでマネージド・サービスは利用できますか?
{: faq}

はい、{{site.data.keyword.IBM_notm}} は、{{site.data.keyword.cloud_notm}} for SAP Applications 製品を使用して、オペレーティング・システム、データベース、および SAP 用のマネージド・サービスを提供します。 詳しくは、[Managed Services for SAP Applications ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/sap/managed){: new_window} を参照してください。

## SAP はどの IBM Cloud サーバーでも実行できますか?
{: faq}

いいえ、SAP HANA または SAP NetWeaver を実行するために使用できるのは、SAP 認定のサーバー・モデルのみです。

## IBM Cloud インフラストラクチャーでの使用が認定されているサーバーはどれですか?
{: faq}  

SAP ワークロードでの使用が認定されているサーバーの最新のリストについては、[SAP-certified infrastructure![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/bare-metal-servers/sap){: new_window} を参照してください。

## IBM Cloud インフラストラクチャーではどのような SAP ワークロードを実行できますか?
{: faq}

現時点では、SAP NetWeaver アプリケーションおよび非実稼働/実稼働環境向けの SAP HANA のワークロードを、{{site.data.keyword.cloud_notm}} インフラストラクチャー上で実行できます。

## SAP ではどのオペレーティング・システムがサポートされていますか?
{: faq}

  * SAP NetWeaver ベースのアプリケーションの場合は、Red Hat Enterprise Linux for SAP Business Applications 6.x、SUSE Enterprise Linux for SAP Applications 12 SP2、および Microsoft Windows Server 2012+ がサポートされています。
  * SAP HANA の場合は、Red Hat Enterprise Linux 7.4 for SAP HANA、SUSE Linux Enterprise Server 12 SP2 for SAP HANA、および VMware Server Virtualization 6.5 がサポートされています。

## どのようなサーバー構成を変更できますか?
{: faq}

付加されたストレージ、ネットワーク、セキュリティー、モニタリング、侵入検出、パブリック帯域幅、ポート速度など、ほとんどのインフラストラクチャー・オプションを追加できます。 CPU、RAM、および内部ストレージのデフォルトはサーバーの選択に基づいているため、注文処理中またはサポート・チケットを通じて変更することはできません。

## SAP 認定サーバーについて、さらに質問がある場合は、どちらに問い合わせればいいですか?
{: faq}

IBM のセールス・チームがご質問にお答えします。また、チャット、電話、[{{site.data.keyword.cloud_notm}} 資料](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)など、他の {{site.data.keyword.cloud_notm}} サポート・オプションもご利用いただけます。

## IBM、お客様、およびビジネス・パートナーが実行する管理タスクを示すサービス責任マトリックスはありますか?
{: faq}

{{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャーは、自己管理型製品です。 すべてのインフラストラクチャー管理を、お客様およびビジネス・パートナーの責任で行っていただく必要があります。
