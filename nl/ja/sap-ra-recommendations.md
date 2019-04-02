---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, Advanced Business Application Programming, ABAP, ABAP SAP Central Services, ASCS, SAP Central Services, SAP Software Provisioning Manager, SWPM, HANA System Replication, HSR, User Management Engine, UME, VLAN, SAP Web Dispatcher, SAP NetWeaver application servers, application servers, database, instance, load balancing, SAP logon groups, RFC server groups, high availability, highly available, HA, disaster recovery, DR, cluster software, Linux Pacemaker, virtual hostname

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud SAP 認定インフラストラクチャーのガイダンス
{: #recommendations}

ここで提供するガイダンスは、実際の要件とは異なる可能性がありますが、{{site.data.keyword.cloud}} 環境で SAP 認定サーバーを構築するための開始点となります。

図 1. リファレンス・アーキテクチャー例

![図 1. リファレンス・アーキテクチャー例](/images/SAP-optimization-ref-architecture-20180527.png "リファレンス・アーキテクチャー例")

## VLAN
{: #vlans}

ランドスケープ設計の SAP ガイドラインでは、サーバー・トラフィックを複数のネットワーク・インターフェース・コントローラー (NIC) に分離することが推奨されています。 たとえば、ビジネス・データは管理トラフィックおよびバックアップ・トラフィックから分離する必要があります。 このようなデータ分離を行うには、複数の NIC を別々のサブネットに割り当てます。 詳しくは、[Building High Availability for SAP NetWeaver and SAP HANA![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} (PDF) の『Network』セクションを参照してください。

NIC の推奨に従うために、{{site.data.keyword.cloud_notm}} では、サーバー上で複数の VLAN を構成することができます。 VLAN インターフェースは、ボンド・インターフェース (Linux) またはチーミング・インターフェース (Microsoft Windows) で構成する複数の NIC を介して、高可用性 (HA) にすることができます。 {{site.data.keyword.baremetal_short}} では、HA 機能と災害復旧 (DR) 機能のどちらの場合でも、追加の IP アドレスを予約し、それらのアドレスをさまざまな SAP サービスに対してその実装時に割り当てるのが最善の方法です。 SAP Software Provisioning Manager (SWPM) でのインストール中にアドレスを割り当てる方法については、SAP インストールの資料を参照してください。 仮想マシン (VM) の場合は通常、VM のメイン・インターフェースのアドレスで十分です。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} にはデフォルトで、パブリック・インターフェースとプライベート・インターフェースがあります。 一般的に、{{site.data.keyword.cloud_notm}} インフラストラクチャー内のすべてのサーバーに対してパブリック LAN を構成しておくことはお勧めしません。 Vyatta Network Gateway の特定のインスタンスを配備して、必要に応じて環境へのパブリック・アクセスを可能にする必要があります。 詳しくは、[Vyatta Network Gateway](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta) を参照してください。

## {{site.data.keyword.cloud_notm}} ストレージ
{: #storage}

SAP NetWeaver 認定の {{site.data.keyword.cloud_notm}} サーバーは、RAID 構成用のディスクとは異なる数の内部ディスクおよび異なるレイアウトで構成することができます。 これらのレイアウトは、プロジェクト要件 (サイズなど) やストレージへの共有アクセスには不十分である場合があることに注意してください。

ストレージ要件はそれぞれ大きく異なるため、そのガイダンスは、バックアップとリストアのタイム・スロットおよび高可用性とフェイルオーバーの要件の観点でプロジェクトの重要パフォーマンス指標 (KPI) を明確に定義した後に、使用ストレージのタイプを決定することです。 このコンテンツでは、すべてのオプションをカバーすることはできませんが、一部のガイダンスを提供します。

  * ノード間でフェイルオーバーするデータベースを使用する HA セットアップには、共有 iSCSI デバイスを使用します。 必要な最大 IOPS/秒を確認する必要があります。

  * 複製されたデータベースを使用する HA セットアップ (たとえば、SAP HANA システム・レプリケーション) には、内部ストレージを使用します。 SAP NetWeaver アプリケーション・サーバーは、内部ストレージまたは共有 Network Attached Storage (NAS) のいずれかに配置できます。

  * VMware ベースのインストール環境でのフェイルオーバー機能を支援するには、共有ストレージを使用します。 適切なストレージ・タイプの選択について詳しくは、[VMware システムで使用するストレージ](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems)を参照してください。

オプションはすべて、{{site.data.keyword.cloud_notm}} インフラストラクチャー内から選択できます。

## 高可用性
{: #availability}

集中管理されるデータベースへの SAP アプリケーションの分散インストールでは、高可用性を実現するために基本インストールが複製されます。 アーキテクチャーの各層の高可用性設計は異なります。

  * **SAP Web ディスパッチャー**。 複数の冗長な SAP Web ディスパッチャー・インスタンスを使用して、SAP アプリケーション・トラフィックでの高可用性を実現します。 SAP Web ディスパッチャーは、一連の SAP システムおよびその他の `https` ベースのサービスの潜在的なエントリー・ポイントとして機能します。 これは通常、インターネットとバックエンド・システムの間にあり、「外部」からの Web プロトコル・ベースの要求を処理します。 SAP Web ディスパッチャーは、リバース・プロキシーのように機能し、ロード・バランシングやシングル・サインオンなど、さまざまな機能がサポートされます。 詳しくは、[SAP Web Dispatcher ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window} を参照してください。

  * **ABAP SAP Central Services (ASCS)**。 {{site.data.keyword.cloud_notm}} 環境で ASCS を高可用性にするには、ターゲット・オペレーティング・システムのクラスター・ソフトウェア (Linux Pacemaker や Microsoft Cluster など) をインストールする必要があります。 ASCS (SAP のエンキュー・サービス) の単一障害点を、そのデータをエンキュー・レプリケーション・サービス (ERS) に複製するように構成する必要があります。 ERS インスタンスは、SAP のインストール・プロセスの一部としてインストールする必要があり、SAP の SWPM でサポートされています。 ASCS と ERS の両方のクラスター・コンポーネントのインストールおよび構成について詳しくは、オペレーティング・システム・ベンダーの製品資料を参照してください。

  * **SAP NetWeaver アプリケーション・サーバー**。 高可用性は、アプリケーション・サーバーのプール内のトラフィックをロード・バランシングすることによって実現されます。 限られた量のリソースしか必要でない場合は、単一のアプリケーション・サーバーを高可用性として構成できます。 アプリケーション・サーバーは、フェイルオーバーに使用できるあらゆるクラスター・ノードからアクセス可能なストレージを使用してインストールされる必要があります。 また、SAP NetWeaver スタックは仮想ホスト名を使用する必要があります。 必要な構成について詳しくは、オペレーティング・システム・ベンダーのオペレーティング・システム資料を、高可用性については SAP 資料を参照してください。 構成に複数のアプリケーション・サーバーが必要である場合は、SAP アプリケーション・サーバーの構成で、ロード・バランシング (SAP ログオン・グループ内、RFC サーバー・グループ内など) もカバーする必要があります。 詳しくは、SAP NetWeaver バージョンの管理ガイドを参照してください。

  * **データベース層**。 リファレンス・アーキテクチャー例では、単一の SAP HANA (またはその他のデータベース) のインスタンスを配備します。 高可用性を実現するには、複数のインスタンスを配備し、HANA システム・レプリケーション (HSR) を使用して、手動フェイルオーバーを実装します。 自動フェイルオーバーを有効にするには、特定の Linux ディストリビューション用の高可用性拡張機能が必要です。 その他のデータベースの場合は、共有ストレージ上のデータベース・インスタンスのフェイルオーバーを構成することも、SAP HANA の場合と同様のレプリケーション技法を使用することもできます。 高可用性またはレプリケーションのセットアップに必要な一連のオプションについては、サポートされているデータベース・システムの資料を参照してください。

  詳しくは、[{{site.data.keyword.cloud_notm}} 高可用性サポート](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha)を参照してください。

## 災害復旧
{: #dr}

各層は、それぞれ異なる戦略を使用して、災害復旧の保護を提供します。

 * **SAP NetWeaver アプリケーション・サーバー**。 SAP アプリケーション・サーバーにはビジネス・データが含まれていませんが、災害発生後も継続的に動作させるためには、サーバーのインストールと構成を維持する必要があります。 災害復旧戦略の 1 つは、別の地域に SAP アプリケーション・サーバーを配置することです。 プライマリー・アプリケーション・サーバー上の構成の変更やカーネルの更新をすべて、災害復旧地域内の仮想マシンまたはサーバーにコピーする必要があります。

 * **SAP Central Services (SCS)**。 SAP アプリケーション・スタックの SCS コンポーネントはビジネス・データを保持しません。 災害復旧地域にサーバーまたは VM を構築すると、SCS の役割を実行できます。 プライマリー SCS ノートから同期する唯一のコンテンツは、`/sapmnt` 共有コンテンツです。 また、構成の変更やカーネルの更新がプライマリー SCS サーバー上で行われる場合は、変更内容を災害復旧 SCS に複製する必要があります。 2 つのサーバーを同期するには、定期的にスケジュールされたコピー・ジョブを使用して、災害復旧サーバーに `/sapmnt` をコピーします。 SCS について詳しくは、[Central Services Instance![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window} を参照してください。

 * **データベース層**。 SAP HANA ベースのシステムの場合は、HANA システム・レプリケーション機能や {{site.data.keyword.cloud_notm}} ストレージ複製機能など、HANA 対応レプリケーション・ソリューションを使用します。 サポートされているその他のデータベースの場合は、サポートされている機能について、データベースの資料を参照してください。 一般的に、利用可能なオプションから選択するには、基盤となる SAP アプリケーションのビジネス要件を明確に理解しておく必要があります。 単一のトランザクションについて、さらには時間枠内のすべてのデータについても、潜在的な損失の影響を判断する必要があります。

 * **インフラストラクチャー**。 SAP クライアントが {{site.data.keyword.cloud_notm}} インフラストラクチャー内でどこに配置されているかに応じて、インフラストラクチャー内の他のコンポーネントを災害復旧シナリオ用に準備する必要があります。 リファレンス・アーキテクチャー例では、クライアントはオンプレミス側から、または顧客の企業ネットワーク内から、SAP システムにアクセスします。

## セキュリティー
{: #security}

### ユーザー管理

SAP には独自のユーザー管理エンジン (UME) があり、SAP アプリケーションでの役割ベースのアクセスと承認を制御します。 詳しくは、[SAP HANA Security - An Overview![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://archive.sap.com/documents/docs/DOC-62943){: new_window} を参照してください。ユーザー管理の観点からは、SAP システムがオンプレミスの {{site.data.keyword.cloud_notm}} を実行するかどうかは関係ありません。 そのルールの例外については、[ジャンプ・ボックス・サーバー](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box)で説明しています。

### ネットワーク・セキュリティー

{{site.data.keyword.cloud_notm}} ベースの環境にはさまざまな方法でアクセスできるため、セキュリティー対策をアクセス方法に応じて確立する必要があります。

外部アクセスへのパブリック・インターフェースの使用の検討は、PoC (概念検証) タイプの配備以外では推奨されません。 実動シナリオでは、Vyatta アプライアンスの配備が可能です。このアプライアンスは、必要な機能 (VPN ファイアウォールなど) をすべて備えています。 Vyatta アプライアンスが待ち時間およびスループットの要件を満たさない場合は、{{site.data.keyword.cloud_notm}} サポートに連絡して、Vyatta アプライアンス以外のものが使用できるようになるステップや構成がないか検討してください。
