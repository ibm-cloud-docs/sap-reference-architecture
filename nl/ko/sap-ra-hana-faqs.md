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

## SAP HANA에 사용 가능한 IBM Cloud 베어메탈 서버의 크기는 무엇입니까?

SAP 인증 {{site.data.keyword.baremetal_long}}는 다음 RAM 크기로 사용 가능합니다. 
  * 512GB
  * 1TB
  * 2TB
  * 4TB
  * 8TB
  
## IBM Cloud 인프라에서 지원되는 하드웨어 공유 옵션은 무엇입니까? (예: 가상 HANA 및 MDC(Multitenant Database Container)

{{site.data.keyword.cloud_notm}} SAP 인증 인프라 오퍼링은 SAP에서 인증한 베어메탈 서버 배치이며 가상화를 포함하지 않습니다. 이 인프라에 대한 변경사항은 SAP 인증과 관련된 규제를 준수해야 합니다. 

## SAP HANA를 어떻게 IBM Cloud에 배치합니까?

구현 단계는 [{{site.data.keyword.cloud_notm}}의 SAP HANA](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started)에 설명되어 있습니다. 자체 관리 오퍼링이므로 사용자가 {{site.data.keyword.cloud_notm}}에서 SAP HANA를 구현하는 것에 대해 책임이 있습니다. {{site.data.keyword.IBM_notm}}에서는 사용자를 지원하는 관리 SAP 서비스 및 자문 서비스를 제공합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed)를 참조하십시오.

## SAP HANA에 대한 스케일 확장이 지원됩니까?

현재 스케일 확장은 SAP HANA에 대해 지원되지 않습니다.

## HANA에서 SAP 비즈니스 스위트에 대해 지원되는 최대 서버 크기는 얼마입니까? 

HANA에서 SAP 비즈니스 스위트를 지원하는 최대 서버 크기는 8TB입니다. 

##  HANA에서 SAP Business Warehouse에 대해 지원되는 최대 서버 크기는 얼마입니까? 

HANA에서 SAP Business Warehouse를 지원하는 최대 서버 크기는 4TB입니다. 

## 내 SAP HANA 인증 서버를 어떻게 백업합니까?

서버 백업은 자체 관리 오퍼링에 포함되지 않습니다. {{site.data.keyword.cloud_notm}} 인프라 고객 포털에서 서버 주문 프로세스 중에 선택할 수 있는 옵션이 있습니다. 또한 써드파티 백업 솔루션을 통합하는 옵션도 있습니다. 

## 기존 SAP HANA 데이터베이스 또는 관계형 데이터베이스를 IBM Cloud에 있는 SAP HANA 인증 서버에 어떻게 마이그레이션합니까?

자체 관리 서비스에 마이그레이션 서비스는 포함되지 않습니다. 마이그레이션 활동은 사용자 책임입니다. {{site.data.keyword.IBM_notm}}에서는 SAP 마이그레이션 계획 및 실행에서 사용자를 지원할 수 있는 다양한 관리 서비스 및 자문 서비스를 제공합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} Advisory Services](https://ibm.com/us-en/marketplace/cloud-consulting-services)를 참조하십시오.

## SAP HANA 2.0이 IBM Cloud SAP 인증 인프라 오퍼링의 일부로 지원됩니까? 

예. SAP HANA 2.0을 준수하는 운영 체제로 SAP 인증 서버를 주문하는 경우 SAP HANA 2.0이 지원됩니다. 자세한 정보는 [SAP Note 2235581](https://launchpad.support.sap.com/#/notes/2235581)을 참조하십시오.
