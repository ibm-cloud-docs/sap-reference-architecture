---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, relational database management systems, RDBMS, SAP Web Dispatcher, SAP NetWeaver Application Servers, application servers, database, high availability, disaster recovery

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud SAP リファレンス・アーキテクチャーの概要
{: #getting-started}

{{site.data.keyword.cloud}} のアーキテクチャーは、クラウド・インフラストラクチャーに不可欠なソフトウェア定義可能な環境、プログラム式のインターフェース、および多数のハードウェア構成とネットワーク構成など、優れた技術機能を提供します。 このアーキテクチャーは、より高いレベルの柔軟性 (さまざまなワークロードに合わせて仮想サーバーと専用サーバーを混在させる方法で実現)、インターフェースの自動化、およびハイブリッド配備オプションを提供するように設計されています。 SAP HANA および SAP NetWeaver 用の {{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャー製品により、最適な選択肢が提供されます。 この選択には、SAP ソフトウェア・スタックが実行されるベア・メタル・ベースおよび仮想化ベースのサーバーが含まれます。

## リファレンス・アーキテクチャー
{: #ref-arch}

図 1 は、以下から成るランドスケープのリファレンス・アーキテクチャー (RA) です。

  * Vyatta ネットワーク・コンポーネント
  * SAP Web ディスパッチャー
  * SAP NetWeaver アプリケーション・サーバー
  * SAP HANA データベース
  * 他のリレーショナル・データベース管理システム (RDBMS)

RA の例は、高可用性と災害復旧で構成されています。 なお、図 1 で、データベース・サーバーは、SAP NetWeaver でサポートされている任意のデータベース・システム (たとえば、SAP HANA) にすることができます。

図 1. リファレンス・アーキテクチャー例

![図 1. リファレンス・アーキテクチャー例](/images/SAP-optimization-ref-architecture-20180527.png "リファレンス・アーキテクチャー例")
