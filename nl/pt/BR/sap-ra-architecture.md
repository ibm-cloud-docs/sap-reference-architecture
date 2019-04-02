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

# Entendendo a arquitetura por trás da arquitetura de referência do SAP
{: #architecture}

O exemplo de arquitetura na Figura 1 pode diferir de sua arquitetura; ele mostra os conceitos gerais de uma implementação baseada em SAP {{site.data.keyword.cloud}}. Seus sistemas no local estão conectados por meio da Internet à sua infraestrutura do {{site.data.keyword.cloud_notm}}.

Depois que seu ambiente é solicitado e implementado, você se conecta por meio de uma VPN administrativa à sua infraestrutura do {{site.data.keyword.cloud_notm}}. A VPN pode não ser suficiente para conectar seus sistemas no local com sistemas baseados em nuvem, por isso é possível implementar um dispositivo Vyatta Network no ambiente do {{site.data.keyword.cloud_notm}}. Para largura da banda maior e requisitos de latência inferiores,
um circuito de Ethernet no ambiente de nuvem também é suportado.

Há dois data centers diferentes mostrados na Figura 1 que consistem em vários {{site.data.keyword.baremetal_short}} certificados pelo SAP para o SAP NetWeaver e o SAP HANA. O {{site.data.keyword.baremetal_short}} ou as máquinas virtuais no diagrama podem ser diferentes, dependendo de seu ambiente e da tecnologia de banco de dados que você está usando. Além disso, os dados do SAP HANA na visão geral arquitetural são transferidos do data center primário para o data center secundário para recuperação de desastre (DR). Outros bancos de dados também permitem configurações como a Figura 1, com as configurações sendo diferentes.

Na Figura 1, no site do data center DR, sistemas replicados são configurados para manter os recursos DR, que precisam ser implementados em diferentes camadas. Para obter mais informações, consulte [Considerações de recuperação de desastre](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Figura 1. Arquitetura de referência de amostra

![Figura 1. Arquitetura de referência de amostra](/images/SAP-optimization-ref-architecture-20180527.png "Arquitetura de referência de amostra")

## Sistemas SAP
{: #sap-systems}

Os sistemas SAP (Advanced Business Application Programming (ABAP), Java e SAP HANA) têm um conjunto granular de objetos de autorização para gerenciamento de usuários. Devido a isso, somente o acesso remoto por meio de áreas de trabalho ou outros dispositivos front-end ao ambiente baseado no {{site.data.keyword.cloud_notm}} precisa ser configurado. Nenhum acesso de usuário final precisa ser concedido e gerenciado no ambiente de nuvem. Pode haver vários usuários com responsabilidades diferentes que precisam acessar um banco de dados por meio de uma GUI ou uma linha de comandos específica ou tenham restrições de latência que requerem acesso com base no Protocolo de Área de Trabalho Remota. Para gerenciar esse tipo de acesso remoto, um "host de salto" pode ser implementado no ambiente para servir como um ponto central de acesso para esses cenários. Além desses requisitos específicos, os usuários têm acesso a sistemas baseados em nuvem dentro de sua rede corporativa e não precisam ser administrados de nenhuma maneira específica.

## Rede
{: #network}

Qualquer dispositivo em um ambiente do {{site.data.keyword.cloud_notm}} pode ser solicitado com uma opção de acesso à LAN interno e externo opcional. O endereço externo é um endereço IP público roteável e deve ser manipulado com cuidado. O endereço interno é determinado pela VLAN solicitada e escolhido em um subintervalo de 10.0.0.0/8 para a VLAN. Ao solicitar várias VLANs, ambientes ou tipos de tráfego diferentes podem ser segregados, conforme seu design de rede e requisitos de segurança.

Embora uma interface pública com um firewall configurado possa cobrir alguns cenários - por exemplo, uma prova de conceito de protótipo rápida de curto prazo com dados não críticos - um dispositivo de firewall deve ser considerado para a maioria dos casos. A arquitetura de referência de exemplo mapeia um cenário de produção, portanto, interfaces de rede pública estão fora do escopo.

## Vyatta Network Gateway
{: #vyatta}

O Vyatta fornece roteador virtual baseado em software, firewall virtual/NAT e recursos de VPN para Protocolo da Internet versão 4 e Protocolo da Internet versão 6. Se os usuários se conectarem remotamente aos seus sistemas baseados no {{site.data.keyword.cloud_notm}}, esses dispositivos poderão servir como terminais para a VPN lado a lado ou a chamada "VPN road warrior" (ponto de acesso). Diferentes tipos de tecnologias de VPN - IPSec ou túneis VPN SSL, como OpenVPN - podem ser usados. Dependendo da tecnologia SAP que você está usando, essas conexões VPN poderão ser usadas para interconectar sistemas SAP (mesmo com sistemas não SAP) para a tecnologia da GUI tradicional, bem como a tecnologia SAP UI5 baseada em navegador. A conexão de um SAP Web Dispatcher por trás de um Gateway Vyatta permite que recursos adicionais sejam usados, como o balanceamento de carga ou cenários de conexão única. Para obter mais informações sobre o SAP Web Dispatcher, consulte [Alta disponibilidade](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#availability).

O dispositivo Vyatta pode ser implementado em uma configuração de cluster de alta disponibilidade com uma largura da banda de até 10 Gbps. Para obter mais informações, consulte [Configuração de alta disponibilidade do
Vyatta 5400](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-vyatta-5400-high-availability-configuration#vyatta-5400-high-availability-configuration).

## Servidor jump box
{: #jump_box}

Os sistemas SAP têm gerenciamento de usuário integrado e não requerem administração de usuário centralizada. Obviamente, é possível configurar o gerenciamento de usuário centralizado. Para obter mais informações, consulte [Administração central de usuário ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm){: new_window}.

Um servidor jump box permite conceder a usuários específicos acesso de baixo nível ao seu ambiente do {{site.data.keyword.cloud_notm}} por meio de ferramentas baseadas em acesso da linha de comandos ou de outras ferramentas de propósito especial, como o SAP HANA Studio. As ferramentas de administração do banco de dados, bem como os usuários que recebem acesso às ferramentas, são gerenciados centralmente no servidor jump box. Os usuários podem efetuar login em seu ambiente do {{site.data.keyword.cloud_notm}} por meio de suas áreas de trabalho usando Remote Desktop Protocol, o qual é roteado por meio do gateway da VPN.

## Servidores SAP - SAP HANA e SAP NetWeaver
{: #sap_servers}

O {{site.data.keyword.IBM_notm}} oferece uma variedade de servidores para SAP HANA e SAP NetWeaver por meio do {{site.data.keyword.cloud_notm}} para a oferta SAP Applications. Os servidores são {{site.data.keyword.baremetal_short}} com sua opção de sistema operacional (S.O.) (Red Hat Linux, SUSE Linux, Microsoft Windows Server ou implementado com o hypervisor VMware ESX). Para obter detalhes sobre os servidores certificados pelo SAP NetWeaver, consulte a [Nota SAP 2414097 ![Ícone de linkexterno](../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. Esteja ciente de que no hypervisor você implementa um dos sistemas operacionais listados na Nota 2414097 do SAP como um S.O. guest.


Os servidores SAP HANA vêm com um layout de armazenamento pré-selecionado que atende aos Principais Indicadores de Desempenho (KPIs) de armazenamento do SAP para SAP HANA. Não é possível mudar esses layouts e você é encorajado a não usar armazenamento externo para SAP HANA. Armazenamento externo de qualidade diferente e acessível por meio de diferentes protocolos - NFS, CIFS, iSCSI - pode ser usado para backup e outros propósitos. Além disso, para os servidores SAP NetWeaver, você tem a opção de executar outros sistemas de banco de dados suportados no armazenamento externo.

Todas as soluções de software SAP baseadas no SAP HANA ou no SAP NetWeaver incluem o SAP Business Suite completo e o SAP S/4HANA pode ser implementado no ambiente do {{site.data.keyword.cloud_notm}}. Para outros componentes de software diferentes desses, é necessário entrar em contato com o Suporte do SAP. Siga o processo de dimensionamento do SAP para determinar o tamanho correto do servidor para seu projeto e escolha dentre os servidores listados para a oferta SAP HANA ou SAP NetWeaver.

Para obter mais informações sobre os servidores certificados pelo SAP HANA, consulte o [Diretório de hardware SAP HANA certificado e suportado ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud){: new_window}.

Para obter mais informações sobre o processo de dimensionamento do SAP HANA, consulte [Dimensionando o servidor (SAP HANA)](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server).

Para obter mais informações sobre o processo de dimensionamento do SAP NetWeaver, consulte [Dimensionando o servidor (SAP NetWeaver)](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-size_the_server#size_the_server).
