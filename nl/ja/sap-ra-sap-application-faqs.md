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

# FAQ: SAP アプリケーション
{: #application-faqs}

## SAP NetWeaver で認証された SAP アプリケーションはどちらにありますか?

SAP Business Suite (SAP S/4HANA SAP Business Warehouse on HANA を含む) がサポートされています。特定のアプリケーションについては、[SAP Product Availability Matrix](https://support.sap.com/en/release-upgrade-maintenance.html) および [SAP Notes](https://support.sap.com/en/index.html) を確認してください。どちらも、コンテンツにアクセスするには SAP S ユーザー ID が必要です。

## SAP Hybris や SAP BusinessObjects などの 非 SAP NetWeaver アプリケーションを実行することはできますか?

SAP BusinessObjects は、{{site.data.keyword.cloud}} 内の仮想サーバーで動作することが保証されています。詳しくは、[SAP Note 2279688](https://launchpad.support.sap.com/#/notes/2279688) を参照してください。SAP Hybris は、{{site.data.keyword.cloud_notm}} SAP 認定インフラストラクチャー製品の対象外です。複雑な SAP の実装では、{{site.data.keyword.IBM_notm}} が SAP の完全なマネージド・サービスを提供します。詳しくは、[{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed) を参照してください。

## SAP 認定のベア・メタル・サーバーでは SAP Business One がサポートされていますか?

SAP 認定の {{site.data.keyword.baremetal_short}} では、SAP Business One はサポートされていません。

## SAP NetWeaver はどのバージョンがサポートされていますか?

SAP カーネル 7.21 EXT (最小 PL #600)、7.22 EXT (最小 PL #100)、7.45 (最小 PL #100)、および 7.49 (最小 PL #100) を使用して、SAP NetWeaver 7.0 以降の一部としてアプリケーション・サーバー、SAP ABAP、または Java を実行するアプリケーションがサポートされています。
