---



copyright:
  years: 2018
lastupdated: "2018-03-15"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Perguntas frequentes: dimensionamento e arquitetura
{: #faqs_sizing}

## Quais são as medições do SAP Application Performance Standard (SAPS) para cada servidor IBM Cloud certificado por SAP NetWeaver (taxar SAPS e núcleo)?

A Tabela 1 contém as medições da SAP para o {{site.data.keyword.baremetal_short}} do {{site.data.keyword.cloud}} certificado por SAP NetWeaver.

Tabela 1. Medições do SAPS para {{site.data.keyword.baremetal_short}} do {{site.data.keyword.cloud_notm}} certificado por SAP NetWeaver.

| **Tipo de servidor** | **SAPS** | **RAM** | **Núcleos** | **SAPS/Núcleo** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2688 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2293 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |

## Quais são os bancos de dados suportados pela oferta IBM Cloud SAP-Certified Infrastructure?

Para configurações do SAP HANA, SAP HANA 1.0 e SAP HANA 2.0 são as plataformas de banco de dados suportadas. Para obter instruções completas de suporte ao sistema operacional e ao banco de dados para SAP NetWeaver, consulte [Nota 2414097 do SAP](https://launchpad.support.sap.com/#/notes/2414097).

## Uma configuração da Camada 2 (servidor de aplicativos, mais um banco de dados SAP HANA) pode ser feita com os Servidores Bare Betal do IBM Cloud certificados por SAP HANA?

Uma configuração da Camada 2 não pode ser feita na mesma parte do hardware. Ela pode, no entanto, ser feita usando uma combinação das configurações do SAP NetWeaver e do SAP HANA.

## A virtualização (VMware) é suportada na infraestrutura certificada pela SAP do IBM Cloud para SAP NetWeaver ou SAP HANA?

Sim, a infraestrutura certificada pela SAP do {{site.data.keyword.cloud_notm}} suporta VMware ESXi para SAP NetWeaver e SAP HANA. É importante observar que, se você optar por pedir e implementar um servidor que executa o VMware, é sua responsabilidade dimensionar e configurar adequadamente todas as máquinas virtuais no servidor para conformidade com restrições e melhores práticas do SAP. Para obter informações adicionais, consulte [Nota 2161991 do SAP](https://launchpad.support.sap.com/#/notes/2161991).

## As configurações dos Servidores Bare Metal do IBM Cloud certificados pela SAP mudaram?

Os {{site.data.keyword.baremetal_short}} certificados por SAP HANA têm configurações fixas para processador, RAM e armazenamento local com base no servidor escolhido e elas não podem ser modificadas. As opções para rede, sistema operacional e serviços de monitoramento podem ser configuradas.

Os {{site.data.keyword.baremetal_short}} certificados por SAP NetWeaver têm configurações fixas para processador e RAM; o armazenamento local pode ser configurado conforme necessário para atender às suas necessidades. As opções para rede, sistema operacional e serviços de monitoramento podem ser configuradas.

## Existem quaisquer métodos principais pelos quais implementar uma solução SAP na infraestrutura certificada pela SAP do IBM Cloud?

Sim, as [Melhores práticas do SAP](https://help.sap.com/viewer/p/SAP_Best_Practices) oferecem opções que podem ser usadas durante a sua implementação. O {{site.data.keyword.IBM_notm}} também oferece serviços de consultoria em nuvem. Para obter mais informações, consulte [{{site.data.keyword.cloud_notm}} Advisory Services](https://www.ibm.com/us-en/marketplace/cloud-consulting-services).

## Preciso implementar o SAP Solutions Manager e o SAProuter? Se sim, há uma infraestrutura recomendada?

Não, a implementação do SAP Solutions Manager e do SAProuter não é obrigatória ao trabalhar com um ambiente de treinamento, de simulação ou com um ambiente semelhante. No entanto, é melhor que esses componentes sejam implementados em seu ambiente de produção.

