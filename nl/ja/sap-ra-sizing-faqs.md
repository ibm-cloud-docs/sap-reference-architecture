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

# FAQ: サイジングとアーキテクチャー
{: #faqs_sizing}

## SAP NetWeaver 認定の IBM Cloud サーバーの SAP アプリケーション・パフォーマンス標準 (SAPS) 測定値 (SAPS とコアのレート) はどのようになっていますか?

表 1 に、SAP NetWeaver 認定の {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}} の SAP 測定値を示してあります。

表1. SAP NetWeaver 認定の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} の SAPS 測定値。

| **サーバー・タイプ** | **SAPS** | **RAM** | **コア** | **SAPS/コア** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2688 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2293 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |

## IBM Cloud SAP 認定インフラストラクチャー製品でサポートされているのはどのデータベースですか?

SAP HANA 構成でサポートされているデータベース・プラットフォームは、SAP HANA 1.0 および SAP HANA 2.0 です。SAP NetWeaver のオペレーティング・システムとデータベース・サポートに関する完全な記述については、[SAP Note 2414097](https://launchpad.support.sap.com/#/notes/2414097) を参照してください。

## SAP HANA 認定の IBM Cloud Bare Metal Servers を使用して、2 層の構成 (アプリケーション・サーバーと SAP HANA データベース) を実行することはできますか?

2 層の構成は、同じハードウェア上では実行できません。ただし、SAP NetWeaver と SAP HANA の構成を組み合わせて使用すると実現できます。

## SAP NetWeaver または SAP HANA 向けの IBM Cloud SAP 認定インフラストラクチャーでは、仮想化 (VMware) がサポートされていますか?

はい、{{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャーは、SAP NetWeaver および SAP HANA 用の VMware ESXi をサポートしています。VMware を実行するサーバーを注文して実装する場合は、お客様の責任で、サーバーのすべての仮想マシンを SAP の制限およびベスト・プラクティスに適合するように適切にサイジングして構成していただく必要があります。詳しくは、[SAP Note 2161991](https://launchpad.support.sap.com/#/notes/2161991) を参照してください。

## SAP 認定の IBM Cloud Bare Metal Servers の構成を変更することはできますか?

SAP HANA 認定の {{site.data.keyword.baremetal_short}} では、選択したサーバーに基づいてプロセッサー、RAM、およびローカル・ストレージの構成が固定されており、変更することはできません。ネットワーク、オペレーティング・システム、およびモニタリング・サービスのオプションは構成可能です。

SAP NetWeaver 認定の {{site.data.keyword.baremetal_short}} では、プロセッサーと RAM の構成が固定されています。ローカル・ストレージは、必要に応じてニーズに合わせて構成できます。ネットワーク、オペレーティング・システム、およびモニタリング・サービスのオプションは構成可能です。

## IBM Cloud SAP 認定インフラストラクチャーに SAP ソリューションを配備するための最善の方法はありますか?

はい、[SAP Best Practices](https://help.sap.com/viewer/p/SAP_Best_Practices) には、配備の際に使用できるオプションがあります。また、{{site.data.keyword.IBM_notm}} は、クラウド・コンサルティング・サービスを提供しています。詳しくは、[{{site.data.keyword.cloud_notm}} アドバイザリー・サービス](https://www.ibm.com/us-en/marketplace/cloud-consulting-services)を参照してください。

## SAP Solutions Manager と SAProuter を配備する必要はありますか? そうする必要がある場合、推奨されるインフラストラクチャーはありますか?

いいえ、トレーニング、サンドボックスなどの環境で作業する場合は、SAP Solutions Manager と SAProuter の配備は必須ではありません。ただし、これらのコンポーネントを実稼働環境に配備することをお勧めします。

