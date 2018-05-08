---



copyright:
  years: 2018
lastupdated: "2018-03-26"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud SAP 참조 아키텍처 시작하기
{: #getting-started}

{{site.data.keyword.cloud}} 아키텍처는 클라우드 인프라, 프로그래밍 가능 인터페이스 및 수백 개의 하드웨어 및 네트워크 구성에 중요한 소프트웨어 정의 가능 환경과 같은 우수한 기술적 기능을 제공합니다. (다양한 워크로드에 적합하도록 가상 및 전용 서버를 혼합하여) 더 높은 레벨의 유연성, 인터페이스 자동화 및 하이브리드 배치 옵션을 제공하도록 설계되었습니다. SAP HANA 및 SAP NetWeaver용 {{site.data.keyword.cloud_notm}} SAP 인증 인프라 오퍼링에서는 최적의 선택사항을 제공합니다. 이 선택사항에는 SAP 소프트웨어 스택이 실행되는 가상화 기반 서버 및 베어메탈이 포함되어 있습니다. 

## 참조 아키텍처
{: #ref-arch}

그림 1은 다음으로 구성된 랜드스케이프에 대한 참조 아키텍처(RA)입니다. 

  * Vyatta 네트워크 컴포넌트
  * SAP Web Dispatcher
  * SAP NetWeaver Application Servers
  * SAP HANA 데이터베이스
  * 기타 RDBMS(Relational Database Management System) 
  
예제 RA는 고가용성 및 재해 복구로 구성됩니다. 그림 1에서 데이터베이스 서버는 예를 들어, SAP HANA와 같은 SAP NetWeaver에서 지원하는 모든 데이터베이스 시스템일 수 있습니다.  

그림 1. 샘플 참조 아키텍처

![그림 1. 샘플 참조 아키텍처](/images/ref_architecture.png "샘플 참조 아키텍처")
