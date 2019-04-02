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

# FAQ: IBM Cloud SAP 인증 인프라(자체 관리)
{: #faqs}

## IBM Cloud SAP 인증 인프라는 무엇입니까?
{: faq}

{{site.data.keyword.cloud}} SAP 인증 인프라는 {{site.data.keyword.cloud_notm}} for SAP Applications 오퍼링의 자체 관리 컴포넌트입니다. 오퍼링의 이 컴포넌트를 통해 셀프 서비스 IaaS(Infrastructure-as-a-Service)로서 {{site.data.keyword.cloud_notm}}에서 SAP NetWeaver 및 SAP HANA를 실행할 수 있습니다.

## SAP 인증 인프라는 IBM Cloud for SAP Applications 오퍼링과 어떻게 다릅니까?
{: faq}

{{site.data.keyword.cloud_notm}} for SAP Applications 오퍼링에는 여러 컴포넌트가 포함되어 있고, {{site.data.keyword.cloud_notm}} SAP 인증 인프라는 오퍼링의 자체 관리 컴포넌트입니다.  관리 운영 체제(OS)를 찾고 있는 고객을 위해, 사용 가능한 *관리 서비스* 컴포넌트가 관리 SAP Basis 서비스까지 있습니다. {{site.data.keyword.cloud_notm}} SAP 인증 인프라는 OS부터 SAP 애플리케이션까지 인프라를 관리하려는 고객 또는 비즈니스 파트너를 위한 인프라입니다.

## 관리 서비스를 IBM Cloud 인프라와 사용할 수 있습니까?
{: faq}

예. {{site.data.keyword.IBM_notm}}에서는 {{site.data.keyword.cloud_notm}} for SAP Applications 오퍼링을 통해 운영 체제, 데이터베이스 및 SAP을 위한 관리 서비스를 제공할 수 있습니다. 자세한 정보는 [Managed Services for SAP Applications ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/sap/managed){: new_window}를 참조하십시오.

## IBM Cloud 서버에서 SAP을 실행할 수 있습니까?
{: faq}

아니오. SAP에 대해 인증된 서버 모델만 SAP HANA 또는 SAP NetWeaver를 실행하는 데 사용할 수 있습니다.

## 어떤 서버가 IBM Cloud 인프라에서 SAP과 함께 사용하도록 인증되었습니까?
{: faq}  

SAP 워크로드에 사용하도록 인증된 최신 서버 목록은 [SAP-certified infrastructure ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/bare-metal-servers/sap){: new_window}를 참조하십시오.

## 어떤 종류의 SAP 워크로드를 IBM Cloud 인프라에서 실행할 수 있습니까?
{: faq}

현재 SAP NetWeaver 애플리케이션에 대한 워크로드 및 비프로덕션/프로덕션용 SAP HANA를 {{site.data.keyword.cloud_notm}} 인프라에서 실행할 수 있습니다.

## 어떤 운영 체제가 SAP에 대해 지원됩니까?
{: faq}

  * SAP NetWeaver 기반 애플리케이션의 경우 Red Hat Enterprise Linux for SAP Business Applications 6.x, SUSE Enterprise Linux for SAP Applications 12 SP2 및 Microsoft Windows Server 2012 이상이 지원됩니다.
  * SAP HANA의 경우 Red Hat Enterprise Linux 7.4 for SAP HANA, SUSE Linux Enterprise Server 12 SP2 for SAP HANA 및 VMware Server Virtualization 6.5가 지원됩니다.

## 내가 변경할 수 있는 서버 구성은 무엇입니까?
{: faq}

연결된 스토리지, 네트워크, 보안, 모니터링, 침입 탐지, 공용 대역폭 및 포트 속도와 같은 대부분의 인프라 옵션을 추가할 수 있습니다. CPU, RAM 및 내부 스토리지는 서버 선택을 기반으로 기본값이 지정되며 주문 프로세스 중에 또는 지원 티켓을 통해 변경할 수 없습니다.

## SAP 인증 서버에 대한 추가 질문이 있는 경우 누구에게 문의해야 합니까?
{: faq}

담당 영업 팀에서 질문에 대한 답변을 제공할 뿐만 아니라 채팅, 전화 및 [{{site.data.keyword.cloud_notm}} 문서](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)와 같은 다른 {{site.data.keyword.cloud_notm}} 지원 옵션을 제공합니다.

## IBM, 고객 및 비즈니스 파트너에서 수행하는 관리 태스크를 표시하는 서비스 책임 매트릭스가 있습니까?
{: faq}

{{site.data.keyword.cloud_notm}} SAP 인증 인프라는 자체 관리 오퍼링입니다. 모든 인프라 관리는 고객 및 비즈니스 파트너의 책임입니다.
