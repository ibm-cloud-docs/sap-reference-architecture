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

# IBM Cloud SAP 인증 인프라에 대한 지침
{: #recommendations}

요구사항은 제공된 안내와 다를 수 있지만, {{site.data.keyword.cloud}} 환경에서 SAP 인증 서버 빌드를 위한 시작점으로 제공됩니다.

그림 1. 샘플 참조 아키텍처

![그림 1. 샘플 참조 아키텍처](/images/SAP-optimization-ref-architecture-20180527.png "샘플 참조 아키텍처")

## VLAN
{: #vlans}

랜드스케이프 디자인에 대한 SAP 가이드라인에서는 서로 다른 네트워크 인터페이스 제어기(NIC)에서 서버 트래픽의 분리를 권장합니다. 예를 들어, 비즈니스 데이터를 관리 및 백업 트래픽에서 분리해야 합니다. 여러 NIC를 서로 다른 서브넷에 지정하면 이 데이터 분리가 사용으로 설정됩니다. 자세한 정보는 [Building High Availability for SAP NetWeaver and SAP HANA ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window}(PDF)의 네트워크 섹션을 참조하십시오.

NIC 권장사항을 따르기 위해, {{site.data.keyword.cloud_notm}}는 서버에서 여러 VLAN의 구성을 허용합니다. VLAN 인터페이스는 본드 인터페이스(Linux) 또는 팀 인터페이스(Microsoft Windows) 아래 구성될 여러 MIC를 통해 고가용성(HA)을 구성할 수 있습니다. {{site.data.keyword.baremetal_short}}에서 HA 및 재해 복구(DR) 기능 두 가지 모두를 위해, 서비스가 구현될 때 추가 IP 주소를 예약하고 주소를 다른 SAP 서비스에 지정하는 것이 좋습니다. SAP SWPM(Software Provisioning Manager) 설치 중에 주소를 지정하는 방법에 대한 지원은 SAP 설치 문서를 참조하십시오. 가상 머신(VM)의 경우 VM의 주요 인터페이스 주소는 보통 충분합니다.

기본적으로 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}에는 공용 및 사설 인터페이스가 있습니다. 일반적으로 공용 LAN을 {{site.data.keyword.cloud_notm}} 인프라에 있는 모든 서버에 대해 구성하는 것은 권장하지 않습니다. 필요한 경우 환경에 대한 공용 액세스를 허용하려면 Vyatta 네트워크 게이트웨이의 특정 인스턴스를 배치해야 합니다. 자세한 정보는 [Vyatta 네트워크 게이트웨이](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta)를 참조하십시오.

## {{site.data.keyword.cloud_notm}} 스토리지
{: #storage}

SAP NetWeaver에 대해 인증된 {{site.data.keyword.cloud_notm}} 서버를 내부 디스크의 다른 번호 및 RAID 구성에 대해 이러한 디스크의 다른 레이아웃으로 구성할 수 있습니다. 이러한 레이아웃은 프로젝트 요구사항에 충분하지 않을 수 있습니다(예: 충분하지 않은 크기 또는 스토리지에 대한 공유 액세스).

스토리지 요구사항은 백업 및 복원 시간 슬롯과 고가용성 및 장애 복구 요구사항에 관하여 프로젝트 핵심성과지표(KPI)를 명확하게 정의하도록 안내된다는 점에서 다릅니다. 모든 옵션에 대해 설명하는 것은 이 컨텐츠의 범위 밖이지만 일부 안내는 제공될 수 있습니다.

  * 노드 간에 장애를 복구하는 데이터베이스와 함께 HA 설정에 대한 공유 iSCSI 디바이스를 사용하십시오. 필요한 초당 최대 IOPS를 확인해야 합니다.

  * 복제되는 데이터베이스와 함께 HA 설정에 대한 내부 스토리지를 사용하십시오(예: SAP HANA 시스템 복제). SAP NetWeaver 애플리케이션 서버는 내부 스토리지 또는 공유 NAS(Network-attached Storage)에 상주할 수 있습니다.

  * 공유 스토리지를 사용하여 VMware 기반 설치로 장애 복구 기능을 이용하십시오. 적합한 스토리지 유형을 선택하는 데에 대한 자세한 정보는 [VMware 시스템과 사용할 스토리지](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems)를 참조하십시오.

{{site.data.keyword.cloud_notm}} 인프라 내에서 모든 옵션을 선택할 수 있습니다.

## 고가용성
{: #availability}

중앙 집중식 데이터베이스의 SAP 애플리케이션 분산 설치에서 고가용성을 달성하기 위해 기본 설치가 복제됩니다. 아키텍처의 각 계층의 경우 고가용성 디자인은 서로 다릅니다.

  * **SAP Web Dispatcher**. SAP 애플리케이션 트래픽에 대해 중복되는 여러 SAP Web Dispatcher 인스턴스로 고가용성을 달성합니다. SAP Web Dispatcher는 SAP 시스템 및 기타 `https` 기반 서비스 세트에 대한 잠재적인 시작점 역할을 합니다. 일반적으로 인터넷과 백엔드 시스템 간에 있으며 "외부 세계"의 웹 프로토콜 기반 요청을 처리합니다. SAP Web Dispatcher는 로드 밸런싱 및 싱글 사인온과 같이 지원되는 다양한 기능과 함께 역방향 프록시처럼 작동합니다. 자세한 정보는 [SAP 웹 디스패처![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window}를 참조하십시오.

  * **ASCS(ABAP SAP Central Service)**. {{site.data.keyword.cloud_notm}} 환경에서 ASCS의 고가용성을 위해 대상 운영 체제의 클러스터 소프트웨어를 설치해야 합니다(예: Linux Pacemaker 또는 Microsoft Cluster). 해당 데이터를 ERS(Enqueue Replication Service)로 복제하도록 ASCS의 단일 장애 지점(SAP의 Enqueue Service)을 구성해야 합니다. ERS 인스턴스는 SAP 설치 프로세스의 일부로 설치되어야 하며 SAP의 SWPM에서 지원합니다. ASCS 및 ERS 모두에 대한 클러스터 컴포넌트 설치 및 구성에 대한 세부사항은 운영 체제 벤더의 오퍼링 문서를 참조하십시오.

  * **SAP NetWeaver 애플리케이션 서버**. 고가용성은 애플리케이션 서버 풀 내에서 트래픽을 로드 밸런싱하여 달성됩니다. 제한된 크기의 리소스만 필요한 경우 고가용성을 위해 단일 애플리케이션 서버를 구성할 수 있습니다. 장애 복구에 사용할 수 있도록 애플리케이션 서버를 모든 잠재적인 클러스터 노드가 액세스할 수 있는 스토리지와 함께 설치해야 합니다. 또한 SAP NetWeaver 스택은 가상 호스트 이름을 사용해야 합니다. 고가용성을 위한 SAP 문서 및 필수 구성에 대한 세부사항은 운영 체제 벤더의 운영 체제 문서를 참조하십시오. 구성에 여러 애플리케이션 서버가 필요한 경우 SAP 애플리케이션 서버의 구성은 로드 밸런싱도 포함해야 합니다(예를 들어, SAP 로그온 그룹 및 RFC 서버 그룹에). 자세한 정보는 SAP NetWeaver 버전의 관리 안내서를 참조하십시오.

  * **데이터베이스 계층**. 예제 참조 아키텍처에서는 SAP HANA 또는 기타 데이터베이스의 단일 인스턴스를 배치합니다. 고가용성을 위해 하나 이상의 인스턴스를 배치하고 HSR(HANA System Replication)을 사용하여 수동 장애 복구를 구현하십시오. 자동 장애 복구를 사용으로 설정하려면 특정 Linux 배포판의 고가용성 확장이 필요합니다. 다른 데이터베이스의 경우에는 공유 스토리지에 데이터베이스 인스턴스의 장애 복구를 구성하거나 SAP HANA 경우와 유사한 복제 기술을 사용할 수 있습니다. 고가용성 또는 복제를 설정하는 데 필요한 옵션 세트에 대해서는 지원되는 데이터베이스 시스템의 문서를 참조하십시오.

  추가 정보는 [{{site.data.keyword.cloud_notm}} 고가용성 지원](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha)을 참조하십시오.

## 재해 복구
{: #dr}

각 계층은 재해 복구 보호를 제공하기 위해 서로 다른 전략을 사용합니다.

 * **SAP NetWeaver 애플리케이션 서버**. SAP 애플리케이션 서버에는 비즈니스 데이터가 없습니다. 그러나 재해가 발생한 후에 운영을 계속하려면 서버의 설치 및 구성을 유지해야 합니다. 한 가지 재해 복구 전략은 다른 지역에 SAP 애플리케이션 서버를 두는 것입니다. 기본 애플리케이션 서버의 구성 변경사항 또는 커널 업데이트를 재해 복구 지역에 있는 가상 머신 또는 서버에 복사해야 합니다.

 * **SCS(SAP Central Service)**. SAP 애플리케이션 스택의 SCS 컴포넌트는 비즈니스 데이터를 유지하지 않습니다. SCS 역할을 실행하기 위해 재해 복구 지역에 서버 또는 VM을 빌드할 수 있습니다. 동기화할 기본 SCS 노트의 유일한 컨텐츠는 `/sapmnt` 공유 컨텐츠입니다. 또한 구성 변경사항 또는 커널 업데이트가 기본 SCS 서버에서 발생하는 경우 변경사항을 재해 복구 SCS에 복제해야 합니다. 두 개의 서버를 동기화하려면 정기적으로 스케줄된 복사 작업을 사용하여 `/sapmnt`를 재해 복구 서버에 복사하십시오. SCS에 대한 자세한 정보는 [중앙 서비스 인스턴스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window}를 참조하십시오.

 * **데이터베이스 계층**. SAP HANA 기반 시스템의 경우 HANA 시스템 복제 또는 {{site.data.keyword.cloud_notm}} 스토리지 복제 기능과 같은 HANA 지원 복제 솔루션을 사용하십시오. 지원되는 다른 데이터베이스의 경우 해당 지원 기능은 데이터베이스 문서를 참조하십시오. 일반적으로, 사용 가능한 옵션 중에 선택하려면 기본 SAP 애플리케이션의 비즈니스 요구사항을 정확히 이해하고 있어야 합니다. 단일 트랜잭션의 잠재적 손실에 대한 영향 또는 일정 기간 내의 모든 데이터도 판별해야 합니다.

 * **인프라**. {{site.data.keyword.cloud_notm}} 인프라에서 SAP 클라이언트의 위치에 따라 인프라 내의 다른 컴포넌트를 재해 복구 시나리오에 대해 준비해야 합니다. 예제 참조 아키텍처에서 클라이언트는 온프레미스 측에서 또는 컴퓨터의 기업 네트워크 내에서 SAP 시스템에 액세스합니다.

## 보안
{: #security}

### 사용자 관리

SAP에는 SAP 애플리케이션에 대한 권한 및 역할 기반 액세스를 제어하기 위한 고유 UME(Users Management Engine)가 있습니다. 자세한 정보는 [SAP HANA Security - An Overview ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://archive.sap.com/documents/docs/DOC-62943){: new_window}를 참조하십시오. 사용자 관리 관점에서 SAP 시스템을 온프레미스 {{site.data.keyword.cloud_notm}}에서 실행하는 경우는 관련이 없습니다. 해당 규칙에 대한 예외는 [점프 박스 서버](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box)에서 언급되었습니다.

### 네트워크 보안

사용자가 {{site.data.keyword.cloud_notm}} 기반 환경 액세스에 다양한 방법을 사용하므로 보안 조치도 다양해야 합니다.

외부 액세스에 대해 공용 인터페이스를 사용하는 것은 개념 증명 유형 배치에서만 고려되어야 합니다. 프로덕션 시나리오의 경우 어플라이언스가 필요한 모든 기능(VPN 방화벽 등)을 수행하므로 Vyatta 어플라이언스의 배치를 사용할 수 있습니다. 대기 시간 및/또는 처리량 요구사항이 Vyatta 어플라이언스로 충족되지 않는 경우 {{site.data.keyword.cloud_notm}} 지원 팀에 문의하여 Vyatta 어플라이언스 외에 사용할 수 있는 가능한 모든 단계 및 구성에 대해 알아보십시오.
