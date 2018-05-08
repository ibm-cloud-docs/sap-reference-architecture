---



copyright:
  years: 2018
lastupdated: "2018-03-28"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Orientação para seu SAP no ambiente do IBM Cloud
{: #recommendations}

Seus requisitos podem diferir da orientação oferecida; no entanto, ela serve como um ponto de início para construir seu servidor certificado pela SAP no ambiente do {{site.data.keyword.cloud}}.

Figura 1. Arquitetura de referência de amostra

![Figura 1. Arquitetura de referência de amostra](/images/ref_architecture.png "Arquitetura de referência de amostra")

## VLANs
{: #vlans}

As diretrizes do SAP para design de paisagem recomendam uma segregação de tráfego do servidor em diferentes controladores de interface de rede (NICs). Por exemplo, os dados de negócios devem ser separados do tráfego administrativo e de backup. Designar vários NICs para diferentes sub-redes permite essa segregação de dados. Para obter mais informações, consulte a seção Rede em [Construindo alta disponibilidade para SAP NetWeaver e SAP HANA](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf) (PDF).

Para seguir a recomendação de NIC, o {{site.data.keyword.cloud_notm}} permite a configuração de várias VLANs nos servidores. As interfaces de VLAN podem ser feitas com alta disponibilidade (HA) por meio de vários NICs a serem configurados sob interfaces de ligação (Linux) ou interfaces de equipe (Microsoft Windows). Para os recursos de HA e de recuperação de desastre (DR) no {{site.data.keyword.baremetal_short}}, é melhor reservar endereços IP adicionais e designar os endereços aos diferentes serviços SAP à medida que os serviços são implementados. Consulte a documentação de instalação do SAP para obter suporte sobre como designar endereços durante a instalação com o SAP Software Provisioning Manager (SWPM). Para máquinas virtuais (VMs), o endereço da interface principal da VM geralmente é suficiente.

Por padrão, {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}} têm uma interface pública e privada. Em geral, não é recomendável manter a LAN pública configurada para todos os servidores em sua infraestrutura do {{site.data.keyword.cloud_notm}}. Instâncias específicas do Vyatta Network Gateway devem ser implementadas para permitir o acesso público ao seu ambiente, se necessário. Para obter mais informações, consulte [Vyatta Network Gateway](/docs/infrastructure/sap-reference-architecture/sap-ra-architecture.html#vyatta). 

## Armazenamento do {{site.data.keyword.cloud_notm}}
{: #storage}

Servidores {{site.data.keyword.cloud_notm}} certificados para SAP NetWeaver podem ser configurados com um número diferente de discos internos, bem como com diferentes layouts para esses discos para configuração do RAID. Esses layouts podem não ser suficientes para os requisitos do projeto, por exemplo, tamanho insuficiente ou acesso compartilhado ao armazenamento.

Os requisitos de armazenamento diferem no ponto em que a orientação é definir claramente os Principais Indicadores de Desempenho (KPIs) do projeto em termos intervalos de tempo de backup e restauração, alta disponibilidade e requisitos de failover e, em seguida, decidir sobre o tipo de armazenamento a ser usado. A cobertura de todas as opções está além do escopo desse conteúdo; no entanto, algumas orientações podem ser fornecidas.

  * Use dispositivos iSCSI compartilhados para configurações de HA com um banco de dados que efetua failover entre nós. Será necessário observar o máximo de IOPS/s necessário.
  
  * Use o armazenamento interno para configurações de HA com um banco de dados que é replicado; por exemplo, replicação do sistema SAP HANA. Os servidores de aplicativos SAP NetWeaver podem residir no armazenamento interno ou no armazenamento conectado à rede (NAS) compartilhado.
  
  * Use o armazenamento compartilhado para facilitar recursos de failover com instalações baseadas em VMware. Para obter mais informações sobre como selecionar o tipo de armazenamento correto, consulte [Armazenamento para usar com Sistemas VMware](https://console.bluemix.net/docs/infrastructure/vmware/select-storage-option-use-vmware.html#storage-to-use-with-vmware-systems).
  
Todas as opções podem ser selecionadas dentro da infraestrutura do {{site.data.keyword.cloud_notm}}.

## Alta disponibilidade
{: #availability}

Em uma instalação distribuída de aplicativos SAP em um banco de dados centralizado, a instalação base é replicada para alcançar a alta disponibilidade. Para cada camada da arquitetura, o design de alta disponibilidade varia. 

  * **SAP Web Dispatcher**. A alta disponibilidade é alcançada com várias instâncias do SAP Web Dispatcher redundantes com o tráfego de aplicativo SAP. O SAP Web Dispatcher serve como um ponto de entrada em potencial para um conjunto de sistemas SAP e outros serviços baseados em `https`. Ele geralmente fica entre a Internet e os sistemas backend e lida com solicitações baseadas em protocolo da web do "mundo exterior". O SAP Web Dispatcher funciona como um proxy reverso com uma variedade de recursos suportados, como balanceamento de carga e conexão única. Para obter mais informações, consulte [SAP Web Dispatcher](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm).
  
  * **ABAP SAP Central Services (ASCS)**. Para alta disponibilidade de ASCS em um ambiente do {{site.data.keyword.cloud_notm}}, o software de cluster do sistema operacional de destino precisa ser instalado, por exemplo, Linux Pacemaker ou Microsoft Cluster. O ponto único de falha do ASCS (serviço de enfileiramento do SAP) precisa ser configurado para replicar seus dados para um Serviço de Replicação de Enfileiramento (ERS). Uma instância do ERS precisa ser instalada como parte do processo de instalação do SAP e é suportada pelo SWPM do SAP. Para obter detalhes sobre como instalar e configurar os componentes do cluster para ASCS e ERS, consulte a documentação da oferta do fornecedor do sistema operacional.
  
  * **Servidores de aplicativos SAP NetWeaver**. A alta disponibilidade é alcançada pelo balanceamento de carga do tráfego dentro de um conjunto de servidores de aplicativos. Se apenas uma quantidade limitada de recursos for necessária, um único servidor de aplicativos poderá ser configurado como altamente disponível. O servidor de aplicativos precisa ser instalado com armazenamento que seja acessível por todos os nós do cluster em potencial, que possa ser usado para failover. Além disso, a pilha do SAP NetWeaver precisa usar um nome do host virtual. Consulte a documentação do sistema operacional do fornecedor do sistema operacional para obter detalhes sobre a configuração necessária e a documentação do SAP para alta disponibilidade. Se sua configuração requerer vários servidores de aplicativos, a configuração dos servidores de aplicativos SAP precisará cobrir o balanceamento de carga também, por exemplo, em grupos de logon SAP e grupos de servidores RFC. Para obter mais informações, consulte o guia de administração para sua versão do SAP NetWeaver.
  
  * **Camada de banco de dados**. A arquitetura de referência de exemplo implementa uma única instância do SAP HANA ou de outro banco de dados. Para alta disponibilidade, implemente mais de uma instância e use a Replicação do Sistema HANA (HSR) para implementar o failover manual. Para ativar o failover automático, é necessária uma extensão de alta disponibilidade para a distribuição específica do Linux. Para outros bancos de dados, um failover da instância de banco de dados no armazenamento compartilhado pode ser configurado ou uma técnica de replicação semelhante ao caso do SAP HANA pode ser usada. Consulte a documentação do sistema de banco de dados suportado para o conjunto de opções necessárias para configurar a alta disponibilidade ou a replicação.
  
## Recuperação de desastre
{: #dr}

Cada camada usa uma estratégia diferente para fornecer proteção de recuperação de desastre.

 * **Servidores de aplicativos SAP NetWeaver**. Os servidores de aplicativos SAP não contêm dados de negócios. No entanto, a instalação e a configuração do servidor precisam ser preservadas para operação contínua após um desastre. Uma estratégia de recuperação de desastre é ter servidores de aplicativos SAP em outra região. Quaisquer mudanças na configuração ou nas atualizações do kernel no servidor de aplicativos primário devem ser copiadas para as máquinas virtuais ou servidores na região da recuperação de desastre.
 
 * **SAP Central Services (SCS)**. O componente SCS da pilha de aplicativos SAP não persiste dados de negócios. É possível construir um servidor ou uma VM na região da recuperação de desastre para executar a função de SCS. O único conteúdo da nota do SCS primário a ser sincronizado é o conteúdo compartilhado `/sapmnt`. Além disso, se ocorrerem mudanças na configuração ou atualizações do kernel nos servidores SCS primários, elas deverão ser replicadas no SCS de recuperação de desastre. Para sincronizar os dois servidores, use uma tarefa de cópia planejada regularmente para copiar `/sapmnt` para os servidores de recuperação de desastre. Para obter informações adicionais sobre SCS, consulte [Central Services Instance](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm).
 
 * **Camada de banco de dados**. Para sistemas baseados em SAP HANA, use as soluções de replicação suportadas por HANA, como a Replicação do Sistema HANA ou os recursos de replicação de armazenamento do {{site.data.keyword.cloud_notm}}. Para outros bancos de dados suportados, consulte a documentação do banco de dados para seus recursos suportados. Em geral, escolher dentre as opções disponíveis requer um entendimento claro dos requisitos de negócios do aplicativo SAP subjacente. O impacto de uma perda potencial de transações simples ou até mesmo de todos os dados dentro de um espaço de tempo precisa ser determinado. 
 
 * **Infraestrutura**. Dependendo de onde os clientes SAP estão em sua infraestrutura do {{site.data.keyword.cloud_notm}}, outros componentes dentro dela precisarão estar preparados para cenários de recuperação de desastre. Na arquitetura de referência de exemplo, os clientes acessam os sistemas SAP no local ou dentro da rede corporativa do cliente.
 
## Segurança
{: #security}

### Gerenciamento de usuários

A SAP tem seu próprio Mecanismo de Gerenciamento de Usuários (UME) para controlar o acesso baseado em função e a autorização com o aplicativo SAP. Para obter mais informações, consulte [Segurança do SAP HANA - Uma Visão Geral](https://archive.sap.com/documents/docs/DOC-62943). De uma perspectiva de gerenciamento de usuários, não é relevante se seus sistemas SAP executam {{site.data.keyword.cloud_notm}} no local. As exceções a essa regra foram mencionadas em [Servidor jump box](/docs/infrastructure/sap-reference-architecture/sap-ra-architecture.html#juump_box).

### Segurança de rede

Como existem maneiras diferentes de acessar um ambiente baseado no {{site.data.keyword.cloud_notm}}, as medidas de segurança precisam ser diferenciadas.

O uso de uma interface pública para acesso externo deve ser considerado apenas em implementações de prova de conceito. Para cenários de produção, a implementação de dispositivos Vyatta está disponível pois os dispositivos apresentam toda a funcionalidade necessária (firewall de VPN, e assim por diante). Se os requisitos de latência e/ou rendimento não forem atendidos pelos dispositivos Vyatta, entre em contato com o Suporte do {{site.data.keyword.cloud_notm}} para discutir todas as etapas e configurações possíveis que podem ser disponibilizadas além dos dispositivos Vyatta. 
  
