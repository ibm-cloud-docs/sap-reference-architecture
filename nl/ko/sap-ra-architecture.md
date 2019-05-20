---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-05"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, VLAN, SAP Web Dispatcher, load balancing, database, high availability, disaster recovery, HA, DR

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# SAP 참조 아키텍처 외의 아키텍처에 대한 이해
{: #architecture}

그림 1의 아키텍처 예는 사용자 아키텍처와 다를 수 있으며 SAP {{site.data.keyword.cloud}} 기반 배치의 일반적인 개념을 보여줍니다. 온프레미스 시스템이 인터넷을 통해 {{site.data.keyword.cloud_notm}} 인프라에 연결됩니다.

환경을 주문하여 배치한 후에 관리 VPN을 통해 {{site.data.keyword.cloud_notm}} 인프라에 연결합니다. VPN이 온프레미스 시스템을 클라우드 기반 시스템에 연결하는 데 충분하지 않을 수 있으며 Vyatta 네트워크 어플라이언스를 {{site.data.keyword.cloud_notm}} 환경에 배치할 수 있는 이유가 됩니다. 더 높은 대역폭 및 낮은 대기 시간 요구사항을 위해 클라우드 환경으로 이더넷 회선 핸드오버도 지원됩니다.

그림 1에 표시된 대로 두 가지 다른 데이터 센터가 있으며 SAP NetWeaver 및 SAP HANA 둘 다를 위한 여러 SAP 인증 {{site.data.keyword.baremetal_short}}로 구성되어 있습니다. 다이어그램에 있는 {{site.data.keyword.baremetal_short}} 또는 가상 머신은 사용자가 사용 중인 환경 및 데이터베이스 기술에 따라 다를 수 있습니다. 또한 아키텍처 개요의 SAP HANA 데이터는 재해 복구(DR)를 위해 기본 데이터 센터에서 보조 데이터 센터로 전송됩니다. 다른 데이터베이스도 다른 설정으로 그림 1처럼 설정할 수 있습니다.

그림 1의 DR 데이터 센터 사이트에서, 다른 레이어에서 구현되어야 하는 DR 기능을 유지보수하도록 복제된 시스템이 구성됩니다. 자세한 정보는 [재해 복구 고려사항](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr)을 참조하십시오.

그림 1. 샘플 참조 아키텍처

![그림 1. 샘플 참조 아키텍처](/images/SAP-optimization-ref-architecture-20180527.png "샘플 참조 아키텍처")

## SAP 시스템
{: #sap-systems}

SAP 시스템(ABAP(Advanced Business Application Programming), Java 및 SAP HANA)에는 사용자 관리를 위한 세부 단위의 권한 오브젝트 세트가 있습니다. 이러한 이유로 데스크탑 또는 다른 프론트 엔드 디바이스에서 {{site.data.keyword.cloud_notm}} 기반 환경으로 원격 액세스만 설정해야 합니다. 일반 사용자 액세스를 클라우드 환경에 부여하고 관리하면 안 됩니다. 명령행 레벨에서 특정 GUI를 통해 데이터베이스에 액세스해야 하는 다른 책임이 있는 사용자 또는 원격 데스크탑 프로토콜 기반 액세스가 필요한 대기 시간 제한사항이 있는 사용자와 같이 다양한 사용자가 있을 수 있습니다. 이 유형의 원격 액세스를 관리하기 위해, 이러한 시나리오에 대한 중앙 액세스 지점 역할을 수행하도록 "점프 호스트"를 환경에 배치할 수 있습니다. 이러한 특정 요구사항을 제외하고, 사용자는 기업 네트워크 내에서 클라우드 기반 시스템에 대한 액세스 권한을 가지고 있으며 특정 방식으로 관리할 필요가 없습니다. 

## 네트워크
{: #network}

{{site.data.keyword.cloud_notm}} 환경의 디바이스를 원하는 내부 및 선택적 외부 LAN 액세스로 주문할 수 있습니다. 외부 주소는 라우트 가능한 공인 IP 주소이며 신중하게 처리해야 합니다. 내부 주소는 주문한 VLAN에 의해 결정되며 VLAN에 대한 하위 범위 10.0.0.0/8에서 선택됩니다. 여러 VLAN을 주문하면 다양한 환경 또는 트래픽 유형을 네트워크 디자인 및 보안 요구사항별로 구분할 수 있습니다.

방화벽이 구성된 공용 인터페이스가 중요한 데이터 없이 단기간의 빠른 프로토타입 작성 개념 증명과 같은 일부 시나리오를 처리할 수 있는 반면, 대부분의 경우 방화벽 디바이스를 고려해야 합니다. 예제 참조 아키텍처는 프로덕션 시나리오에 맵핑되므로 공용 네트워크 인터페이스는 범위에 포함되지 않습니다.

## Vyatta 네트워크 게이트웨이
{: #vyatta}

Vyatta는 IPv4 및 IPv6 둘 다를 위한 소프트웨어 기반의 가상 라우터, 가상 방화벽/NAT 및 VPN 기능을 제공합니다. 사용자가 {{site.data.keyword.cloud_notm}} 기반 시스템에 원격으로 연결되는 경우, 병렬 VPN 또는 "로드 워리어 VPN"(액세스 지점)이라고 하는 두 가지 모두에 대한 엔드포인트로 이러한 디바이스를 사용할 수 있습니다. VPN 기술 IPSec의 다른 종류 또는 OpenVPN과 같은 SSL VPN 터널을 사용할 수 있습니다. 사용 중인 SAP 기술에 따라 (비SAP 시스템에서도) 브라우저 기반 SAP UI5 기술뿐만 아니라 일반 GUI 기술에 대한 SAP 시스템을 서로 연결하는 데 이러한 VPN 연결을 사용할 수 있습니다. Vyatta 게이트웨이 뒤에서 SAP Web Dispatcher에 연결하면 로드 밸런싱 또는 싱글 사인온 시나리오와 같은 추가 기능을 사용할 수 있습니다. SAP Web Dispatcher에 대한 자세한 정보는 [고가용성](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#availability)을 참조하십시오.

Vyatta 디바이스를 최대 10Gbps 대역폭으로 고가용성 클러스터 구성에 배치할 수 있습니다. 자세한 정보는 [Vyatta 5400 고가용성 구성](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-vyatta-5400-high-availability-configuration#vyatta-5400-high-availability-configuration)을 참조하십시오.

## 점프 박스 서버
{: #jump_box}

SAP 시스템에는 임베드된 사용자 관리가 있으며 중앙 집중식 사용자 관리는 필요하지 않습니다. 물론 중앙 집중식 사용자 관리를 설정할 수 있습니다. 자세한 정보는 [중앙 사용자 관리![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm){: new_window}를 참조하십시오.

점프 박스 서버를 통해 특정 사용자에게 명령행 액세스 기반 도구 또는 SAP HANA Studio와 같은 다른 특수 목적 도구를 통해 {{site.data.keyword.cloud_notm}} 환경에 대한 하위 레벨 액세스를 제공할 수 있습니다. 도구에 대한 액세스가 있는 사용자 뿐만 아니라 데이터베이스 관리 도구도 점프 박스 서버에서 중앙 집중식으로 관리됩니다. VPN 게이트웨이를 통해 라우팅되는 원격 데스크탑 프로토콜을 통해 사용자 데스크탑에서 {{site.data.keyword.cloud_notm}} 환경에 로그인할 수 있습니다.

## SAP 서버 - SAP HANA 및 SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}}에서는 {{site.data.keyword.cloud_notm}} for SAP Applications 오퍼링을 통해 SAP HANA 및 SAP NetWeaver에 대한 다양한 서버를 제공합니다. 서버는 원하는 운영 체제(OS)(Red Hat Linux, SUSE Linux, Microsoft Windows Server 또는 VMware ESX 하이퍼바이저와 함께 배치됨)의 {{site.data.keyword.baremetal_short}}입니다. SAP NetWeaver 인증 서버에 대한 세부사항은 [SAP Note 2414097 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}를 참조하십시오. 하이퍼바이저에서는 게스트 OS로 SAP Note 2414097에 나열된 운영 체제 중 하나를 배치해야 한다는 것을 기억하십시오.

SAP HANA 서버는 SAP HANA에 대한 SAP의 스토리지 핵심성과지표(KPI)를 준수하는 사전 선택 스토리지 레이아웃으로 제공됩니다. 이러한 레이아웃을 변경할 수 없으며 SAP HANA에 대해 외부 스토리지를 사용하지 않도록 요구됩니다. 다른 품질 및 다른 프로토콜(NFS, CIFS, iSCSI)을 통해 액세스 가능한 외부 스토리지를 백업 및 다른 목적으로 사용할 수 있습니다. 또한 SAP NetWeaver 서버의 경우 외부 스토리지에서 지원되는 다른 데이터베이스 시스템을 실행하도록 선택할 수 있습니다.

SAP HANA 또는 SAP NetWeaver를 기반으로 하는 모든 SAP 소프트웨어 솔루션에는 전체 SAP 비즈니스 스위트가 포함되며 SAP S/4HANA를 {{site.data.keyword.cloud_notm}} 환경에 배치할 수 있습니다. 이를 제외한 다른 소프트웨어 컴포넌트는 SAP 지원 팀에 문의해야 합니다. SAP 크기 조정 프로세스에 따라 프로젝트에 적합한 서버 크기를 결정하고 SAP HANA 또는 SAP NetWeaver 오퍼링에 대해 나열된 서버 중에 선택하십시오.

SAP HANA 인증 서버에 대한 자세한 정보는 [Certified and Supported SAP HANA Hardware Directory![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud){: new_window}를 참조하십시오.

SAP HANA 크기 조정 프로세스에 대한 자세한 정보는 [서버 크기 조정(SAP HANA)](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server)을 참조하십시오.

SAP NetWeaver 크기 조정 프로세스에 대한 자세한 정보는 [서버 크기 조정(SAP NetWeaver)](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-size_the_server#size_the_server)을 참조하십시오.
