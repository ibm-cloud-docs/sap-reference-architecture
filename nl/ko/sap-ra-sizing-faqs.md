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

# FAQ: 크기 조정 및 아키텍처
{: #faqs_sizing}

## 각 SAP NetWeaver 인증 IBM Cloud 서버에 대한 SAPS(SAP Application Performance Standard) 측정은 무엇입니까(비율 SAPS 및 코어)?
{: faq}

표 1에는 SAP NetWeaver 인증 {{site.data.keyword.cloud}} {{site.data.keyword.baremetal_short}}에 대한 SAP 측정이 포함되어 있습니다.

표 1. SAP NetWeaver 인증 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}에 대한 SAPS 측정.

|**서버 유형** |**SAPS** |**RAM** |**코어** |**SAPS/코어** |
| --- | --- | --- | --- | --- |
|BI.S1.NW32 |10,980 |32GB |4 | 2745 |
|BI.S1.NW128 |54,130 |128GB |24 |2,255 |
|BI.S1.NW256 |55,020 |256GB |24 | 2292 |
|BI.S2.NW512 |65,520 |512GB |28 |2,340 |
| BI.S3.NW32 | 11970 |32GB |4 | 2992 |
| BI.S3.NW64 | 12750 | 64GB |4 | 3187 |
| BI.S3.NW192 | 78850 | 192GB | 36 | 2190 |
| BI.S3.NW384 | 79430 | 384GB | 36 | 2203 |
| BI.S3.NW768 | 79630 | 768GB | 36 | 2211 |

## IBM Cloud SAP 인증 인프라 오퍼링에서 지원하는 데이터베이스는 무엇입니까?
{: faq}

SAP HANA 구성의 경우, 지원되는 데이터베이스 플랫폼은 SAP HANA 1.0 및 SAP HANA 2.0입니다. SAP NetWeaver에 대한 전체 운영 체제 및 데이터베이스 지원 명령문은 [SAP Note 2414097 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}을 참조하십시오.

## SAP HANA 인증 IBM Cloud 베어메탈 서버에 대해 Tier-2 구성(애플리케이션 서버 및 SAP HANA 데이터베이스)을 완료할 수 있습니까?
{: faq}

동일한 하드웨어에서는 Tier-2 구성을 완료할 수 없습니다. 그러나 SAP NetWeaver 및 SAP HANA 구성의 조합을 사용하면 완료할 수 있습니다.

## SAP NetWeaver 또는 SAP HANA용 IBM Cloud SAP 인증 인프라에서 가상화(VMware)가 지원됩니까?
{: faq}

예. {{site.data.keyword.cloud_notm}} SAP 인증 인프라는 SAP NetWeaver 및 SAP HANA용 VMware ESXi를 지원합니다. VMware를 실행 중인 서버를 주문하고 구현하도록 선택하는 경우 서버에서 모든 가상 머신을 적절히 크기 조정하고 구성하여 SAP의 제한사항 및 우수 사례를 준수하도록 하는 것은 사용자의 책임입니다. 추가 정보는 [SAP Note 2161991 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://launchpad.support.sap.com/#/notes/2161991){: new_window}을 참조하십시오.

## SAP 인증 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}의 구성을 변경할 수 있습니까?
{: faq}

SAP HANA 인증 {{site.data.keyword.baremetal_short}}에는 사용자가 선택한 서버에 따라 프로세서, RAM 및 로컬 스토리지에 대한 구성이 고정되며 수정할 수 없습니다. 네트워킹, 운영 체제 및 모니터링 서비스에 대한 옵션을 구성할 수 있습니다.

SAP NetWeaver 인증 {{site.data.keyword.baremetal_short}}에서는 프로세서 및 RAM에 대한 구성이 고정되며 로컬 스토리지는 필요한 경우 사용자 요구를 충족하도록 구성할 수 있습니다. 네트워킹, 운영 체제 및 모니터링 서비스에 대한 옵션을 구성할 수 있습니다.

## {{site.data.keyword.cloud_notm}} SAP 인증 인프라에서 SAP 솔루션을 배치하는 데 사용하는 주요 메소드가 있습니까? 
{: faq}

예. [SAP 우수 사례![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.sap.com/viewer/p/SAP_Best_Practices){: new_window}에서는 배치 중에 사용할 수 있는 옵션을 제공합니다.{{site.data.keyword.IBM_notm}}도 클라우드 컨설팅 서비스를 제공합니다. 자세한 정보는 [SAP 인증 인프라 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/sap/certified-infrastructure){: new_window}를 참조하십시오.

## SAP Solutions Manager 및 SAProuter를 배치해야 합니까? 만약 그렇다면 권장 인프라가 있습니까?
{: faq}

아니오. SAP Solutions Manager 및 SAProuter 배치는 교육, 샌드박스 또는 유사한 환경에서 작업하는 경우 필수가 아닙니다. 하지만 이러한 컴포넌트를 프로덕션 환경에 배치하는 것이 좋습니다.
