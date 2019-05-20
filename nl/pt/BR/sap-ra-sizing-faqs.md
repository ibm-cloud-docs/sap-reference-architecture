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

# Perguntas frequentes: dimensionamento e arquitetura
{: #faqs_sizing}

## Quais são as medições do SAP Application Performance Standard (SAPS) para cada servidor IBM Cloud certificado por SAP NetWeaver (taxar SAPS e núcleo)?
{: faq}

A Tabela 1 contém as medições da SAP para o {{site.data.keyword.baremetal_short}} do {{site.data.keyword.cloud}} certificado por SAP NetWeaver.

Tabela 1. Medições do SAPS para {{site.data.keyword.baremetal_short}} do {{site.data.keyword.cloud_notm}} certificado por SAP NetWeaver.

| **Tipo de servidor** | **SAPS** | **RAM** | **Núcleos** | **SAPS/Núcleo** |
| --- | --- | --- | --- | --- |
| BI.S1.NW32 | 10980 | 32 GB | 4 | 2745 |
| BI.S1.NW128 | 54130 | 128 GB | 24 | 2255 |
| BI.S1.NW256 | 55020 | 256 GB | 24 | 2292 |
| BI.S2.NW512 | 65520 | 512 GB | 28 | 2340 |
| BI.S3.NW32 | 11970 | 32 GB | 4 | 2992 |
| BI.S3.NW64 | 12750 | 64 GB | 4 | 3187 |
| BI.S3.NW192 | 78850 | 192 GB | 36 | 2190 |
| BI.S3.NW384 | 79430 | 384 GB | 36 | 2203 |
| BI.S3.NW768 | 79630 | 768 GB | 36 | 2211 |

## Quais são os bancos de dados suportados pela oferta IBM Cloud SAP-Certified Infrastructure?
{: faq}

Para configurações do SAP HANA, SAP HANA 1.0 e SAP HANA 2.0 são as plataformas de banco de dados suportadas. Para obter instruções completas de suporte ao sistema operacional e ao banco de dados para SAP NetWeaver, consulte a [Nota SAP 2414097 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}.

## Uma configuração da Camada 2 (servidor de aplicativos, mais um banco de dados SAP HANA) pode ser feita com os Servidores Bare Betal do IBM Cloud certificados por SAP HANA?
{: faq}

Uma configuração da Camada 2 não pode ser feita na mesma parte do hardware. Ela pode, no entanto, ser feita usando uma combinação das configurações do SAP NetWeaver e do SAP HANA.

## A virtualização (VMware) é suportada na infraestrutura certificada pela SAP do IBM Cloud para SAP NetWeaver ou SAP HANA?
{: faq}

Sim, a infraestrutura certificada pela SAP do {{site.data.keyword.cloud_notm}} suporta VMware ESXi para SAP NetWeaver e SAP HANA. É importante observar que, se você optar por pedir e implementar um servidor que executa o VMware, é sua responsabilidade dimensionar e configurar adequadamente todas as máquinas virtuais no servidor para conformidade com restrições e melhores práticas do SAP. Para obter informações adicionais, consulte a [Nota SAP 2161991 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2161991){: new_window}.

## É possível mudar as configurações do {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} certificado por SAP?
{: faq}

Os {{site.data.keyword.baremetal_short}} certificados por SAP HANA têm configurações fixas para processador, RAM e armazenamento local com base no servidor escolhido e elas não podem ser modificadas. As opções para rede, sistema operacional e serviços de monitoramento podem ser configuradas.

Os {{site.data.keyword.baremetal_short}} certificados por SAP NetWeaver têm configurações fixas para processador e RAM; o armazenamento local pode ser configurado conforme necessário para atender às suas necessidades. As opções para rede, sistema operacional e serviços de monitoramento podem ser configuradas.

## Existe algum método principal para implementar uma solução SAP na infraestrutura certificada pelo SAP do {{site.data.keyword.cloud_notm}}?
{: faq}

Sim, as [Melhores práticas do SAP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.sap.com/viewer/p/SAP_Best_Practices){: new_window} oferecem opções que podem ser usadas durante sua implementação. O {{site.data.keyword.IBM_notm}} também oferece serviços de consultoria em nuvem. Para obter mais informações, consulte [Infraestrutura certificada por SAP ![Ícone de linkexterno](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/sap/certified-infrastructure){: new_window}.


## Preciso implementar o SAP Solutions Manager e o SAProuter? Se sim, há uma infraestrutura recomendada?
{: faq}

Não, a implementação do SAP Solutions Manager e do SAProuter não é obrigatória ao trabalhar com um ambiente de treinamento, de simulação ou com um ambiente semelhante. No entanto, é melhor que esses componentes sejam implementados em seu ambiente de produção.
