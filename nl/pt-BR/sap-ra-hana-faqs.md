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

# Perguntas frequentes: SAP HANA
{: #hana-faqs}

## Quais são os tamanhos de servidor bare metal do IBM Cloud disponíveis para SAP HANA?

Os {{site.data.keyword.baremetal_long}} certificados por SAP estão disponíveis nos tamanhos de RAM a seguir:
  * 512 GB
  * 1 TB
  * 2 TB
  * 4 TB
  * 8 TB
  
## Quais opções de compartilhamento de hardware são suportadas na infraestrutura do IBM Cloud? Por exemplo, HANA Virtual e Contêineres de Banco de Dados de Vários Locatários (MDC).

A oferta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure é uma implementação de servidor bare metal certificada pela SAP e não inclui virtualização. É sua responsabilidade assegurar que quaisquer mudanças em cima dessa infraestrutura permaneçam em conformidade com relação à certificação SAP.

## Como implementar o SAP HANA no IBM Cloud?

As etapas de implementação são descritas em [SAP HANA no {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-index.html#getting-started). Como essa é uma oferta autogerenciada, você é responsável por implementar o SAP HANA no {{site.data.keyword.cloud_notm}}. O {{site.data.keyword.IBM_notm}} fornece serviços SAP consultivos e gerenciados para ajudá-lo. Para obter mais informações, consulte [{{site.data.keyword.cloud_notm}} for SAP Applications](https://www.ibm.com/cloud/sap/managed).

## O scale-out é suportado para SAP HANA?

Atualmente, a ampliação não é suportada para SAP HANA.

## Qual é o tamanho máximo do servidor suportado para SAP Business Suite on HANA?

8 TB é o tamanho máximo do servidor para suportar SAP Business Suite on HANA.

##  Qual é o tamanho máximo do servidor suportado para SAP Business Warehouse on HANA?

4 TB é o tamanho máximo do servidor para suportar SAP Business Warehouse on HANA.

## Como fazer backup de meus servidores certificados por SAP HANA?

O backup de servidor não está incluído na oferta autogerenciada. Existem opções que você pode selecionar durante o processo de pedido do servidor no portal do cliente da infraestrutura do {{site.data.keyword.cloud_notm}}. Você também tem a opção de integrar uma solução de backup de terceiros.

## Como migrar um banco de dados SAP HANA ou banco de dados relacional existente para um servidor certificado por SAP HANA no IBM Cloud?

Nenhum serviço de migração está incluído com o serviço autogerenciado; quaisquer atividades de migração são sua responsabilidade. O {{site.data.keyword.IBM_notm}} oferece diversos serviços consultivos e gerenciados que podem ajudar a planejar e a executar a migração do SAP. Para obter mais informações, consulte [{{site.data.keyword.cloud_notm}} Advisory Services](https://ibm.com/us-en/marketplace/cloud-consulting-services).

## O SAP HANA 2.0 é suportado como parte da oferta IBM Cloud SAP-Certified Infrastructure?

Sim, o SAP HANA 2.0 é suportado se você solicita um servidor certificado pela SAP com um sistema operacional que é compatível com o SAP HANA 2.0. Para obter mais informações, consulte [Nota 2235581 do SAP](https://launchpad.support.sap.com/#/notes/2235581).
