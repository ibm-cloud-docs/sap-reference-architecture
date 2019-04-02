---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP Reference Architecture, relational database management systems, RDBMS, SAP Web Dispatcher, SAP NetWeaver Application Servers, application servers, database, high availability, disaster recovery

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Introdução à arquitetura de referência do SAP do IBM Cloud
{: #getting-started}

A arquitetura do {{site.data.keyword.cloud}} fornece recursos técnicos superiores, tais como um ambiente definível por software crítico para uma infraestrutura em nuvem, interfaces programáveis e centenas de configurações de hardware e de rede. Ela foi projetada para fornecer um nível mais alto de flexibilidade (combinando servidores virtuais e dedicados para ajustar uma variedade de cargas de trabalho), automação de interfaces e opções de implementação híbridas. A oferta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure para SAP HANA e SAP NetWeaver fornece a você uma seleção mais adequada. Essa seleção inclui servidores bare metal e baseados em virtualização em cima dos quais a pilha de software SAP é executada.

## Arquitetura de referência
{: #ref-arch}

A Figura 1 é uma arquitetura de referência (RA) para uma paisagem composta por

  * Componentes de rede Vyatta
  * SAP Web Dispatcher
  * SAP NetWeaver Application Servers
  * Bancos de dados SAP HANA
  * Outros sistemas de gerenciamento de banco de dados relacional (RDBMS)

A RA de exemplo está configurada com alta disponibilidade e recuperação de desastre. Observe que na Figura 1, os servidores de banco de dados podem ser qualquer sistema de banco de dados suportado pelo SAP NetWeaver, por exemplo, SAP HANA.

Figura 1. Arquitetura de referência de amostra

![Figura 1. Arquitetura de referência de amostra](/images/SAP-optimization-ref-architecture-20180527.png "Arquitetura de referência de amostra")
