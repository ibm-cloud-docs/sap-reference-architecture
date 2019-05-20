---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

keywords: SAP Reference Architecture, SAP Application Performance Standard, SAPS, application servers, database, SAProuter

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# FAQ: サイジングとアーキテクチャー
{: #faqs_sizing}

## SAP NetWeaver 認定の IBM Cloud サーバーの SAP アプリケーション・パフォーマンス標準 (SAPS) 測定値 (SAPS とコアのレート) はどのようになっていますか?
{: faq}

表 1 に、SAP NetWeaver 認定の {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} の SAP 測定値を示してあります。

表1. SAP NetWeaver 認定の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} の SAPS 測定値。

| **サーバー・タイプ** | **SAPS** | **RAM** | **コア** |**SAPS/コア** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2745 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2292 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |
| BI.S3.NW32 | 11970 | 32 GB | 4 | 2992 |
| BI.S3.NW64 | 12750 | 64 GB | 4 | 3187 |
| BI.S3.NW192 | 78850 | 192 GB | 36 | 2190 |
| BI.S3.NW384 | 79430 | 384 GB | 36 | 2203 |
| BI.S3.NW768 | 79630 | 768 GB | 36 | 2211 |

## IBM Cloud SAP 認定インフラストラクチャー製品でサポートされているのはどのデータベースですか?
{: faq}

SAP HANA 構成でサポートされているデータベース・プラットフォームは、SAP HANA 1.0 および SAP HANA 2.0 です。 SAP NetWeaver のオペレーティング・システムとデータベース・サポートに関する完全な記述については、[SAP Note 2414097![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/2414097){: new_window} を参照してください。

## SAP HANA 認定の IBM Cloud Bare Metal Servers を使用して、2 層の構成 (アプリケーション・サーバーと SAP HANA データベース) を実行することはできますか?
{: faq}

2 層の構成は、同じハードウェア上では実行できません。 ただし、SAP NetWeaver と SAP HANA の構成を組み合わせて使用すると実現できます。

## SAP NetWeaver または SAP HANA 向けの IBM Cloud SAP 認定インフラストラクチャーでは、仮想化 (VMware) がサポートされていますか?
{: faq}

はい、{{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャーは、SAP NetWeaver および SAP HANA 用の VMware ESXi をサポートしています。 VMware を実行するサーバーを注文して実装する場合は、お客様の責任で、サーバーのすべての仮想マシンを SAP の制限およびベスト・プラクティスに適合するように適切にサイジングして構成していただく必要があります。 詳しくは、[SAP Note 2161991 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/2161991){: new_window} を参照してください。

## SAP 認定の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} の構成を変更することはできますか?
{: faq}

SAP HANA 認定の {{site.data.keyword.baremetal_short}} では、選択したサーバーに基づいてプロセッサー、RAM、およびローカル・ストレージの構成が固定されており、変更することはできません。 ネットワーク、オペレーティング・システム、およびモニタリング・サービスのオプションは構成可能です。

SAP NetWeaver 認定の {{site.data.keyword.baremetal_short}} では、プロセッサーと RAM の構成が固定されています。ローカル・ストレージは、必要に応じてニーズに合わせて構成できます。 ネットワーク、オペレーティング・システム、およびモニタリング・サービスのオプションは構成可能です。

## {{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャーに SAP ソリューションを配備するための最善の方法はありますか?
{: faq}

はい、[SAP Best Practices![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.sap.com/viewer/p/SAP_Best_Practices){: new_window} には、配備の際に使用できるオプションがあります。また、{{site.data.keyword.IBM_notm}} は、クラウド・コンサルティング・サービスを提供しています。 詳しくは、[SAP-certified infrastructure ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/sap/certified-infrastructure){: new_window} を参照してください。

## SAP Solutions Manager と SAProuter を配備する必要はありますか? そうする必要がある場合、推奨されるインフラストラクチャーはありますか?
{: faq}

いいえ、トレーニング、サンドボックスなどの環境で作業する場合は、SAP Solutions Manager と SAProuter の配備は必須ではありません。 ただし、これらのコンポーネントを実稼働環境に配備することをお勧めします。
