---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-04"

keywords: SAP reference architecture, {{site.data.keyword.baremetal_short}}, Advanced Business Application Programming, ABAP, application servers

subcollection: sap-reference-architecture

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Perguntas frequentes: aplicativos SAP
{: #application-faqs}

## Em que local posso localizar os aplicativos SAP que são certificados dentro do SAP NetWeaver?
{: faq}

O SAP Business Suite, incluindo o SAP S/4HANA e o SAP Business Warehouse on HANA, são suportados. Para aplicativos específicos, verifique a [Matriz de disponibilidade de produto SAP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://support.sap.com/en/release-upgrade-maintenance.html){: new_window} e as [Notas SAP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://support.sap.com/en/index.html){: new_window}. Ambos requerem um ID do usuário SAP S para acessar o conteúdo.

## Posso executar aplicativos não SAP NetWeaver, como SAP Hybris e SAP BusinessObjects?
{: faq}

O SAP BusinessObjects é certificado para execução em servidores virtuais dentro do {{site.data.keyword.cloud}}. Para obter mais informações, consulte a [Nota SAP 2279688 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2279688){: new_window}. O SAP Hybris está fora do escopo para a oferta {{site.data.keyword.cloud_notm}} SAP-Certified Infrastructure. Para a implementação complexa do SAP, o {{site.data.keyword.IBM_notm}} oferece serviços totalmente gerenciados para o SAP. Para obter mais informações, consulte [Serviços gerenciados para aplicativos SAP ![Ícone de linkexterno](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/sap/managed){: new_window}.


## O SAP Business One é suportado em servidores bare metal certificados por SAP?
{: faq}

O SAP Business One não é suportado no {{site.data.keyword.baremetal_short}} certificado pela SAP.

## Qual versão do SAP NetWeaver é suportada?
{: faq}

Aplicativos que executam servidores de aplicativos, SAP ABAP ou Java como parte do SAP NetWeaver 7.0 ou superior, usando o SAP kernel 7.21 EXT (mínimo PL #600), 7.22 EXT (mínimo PL #100), 7.45 (mínimo PL #100) e 7.49 (mínimo PL #100) ou versões de kernel do SAP superiores são suportados.
