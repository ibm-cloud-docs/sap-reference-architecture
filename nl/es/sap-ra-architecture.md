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

# Comprensión de la arquitectura de referencia SAP
{: #architecture}

El ejemplo de la arquitectura en la Figura 1, que puede diferir de su arquitectura, muestra los conceptos generales de un despliegue basado en SAP {{site.data.keyword.cloud}}. Los sistemas locales están conectados a través de Internet a su infraestructura {{site.data.keyword.cloud_notm}}.

Una vez que haya solicitado y desplegado el entorno, se conectará a su infraestructura {{site.data.keyword.cloud_notm}} a través de una VPN administrativa. La VPN podría no ser suficiente para conectar sus sistemas locales con sistemas basados en la nube, por lo que podría ser necesario desplegar un dispositivo Vyatta Network en el entorno {{site.data.keyword.cloud_notm}}. Para unos requisitos de mayor ancho de banda y menor latencia, también se da soporte a la entrega de un circuito Ethernet en el entorno de nube.

En la Figura 1 se muestran dos centros de datos que están formados por varios {{site.data.keyword.baremetal_short}} certificados por SAP tanto para SAP NetWeaver como para SAP HANA. Los {{site.data.keyword.baremetal_short}} o máquinas virtuales en el diagrama pueden ser diferentes, dependiendo del entorno y de la tecnología de base de datos que utilice. Además, los datos de SAP HANA en la visión general de la arquitectura se transfieren desde el centro de datos primario al centro de datos secundario para la recuperación ante desastres (DR). Otras bases de datos también permiten configuraciones como las de la Figura 1.

En la Figura 1, en el sitio del centro de datos para la recuperación ante desastres (DR), se configuran sistemas replicados para mantener las capacidades de recuperación ante desastres (DR), que es necesario implementar en las distintas capas. Para obtener más información, consulte [Consideraciones para la recuperación ante desastres](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Figura 1. Arquitectura de referencia de ejemplo

![Figura 1. Arquitectura de referencia de ejemplo](/images/SAP-optimization-ref-architecture-20180527.png "Arquitectura de referencia de ejemplo")

## Sistemas SAP
{: #sap-systems}

Los sistemas SAP (ABAP (Advanced Business Application Programming), Java y SAP HANA)proporcionan un conjunto de objetos de autorización granular para la gestión de usuarios. Debido a esto, únicamente es necesario configurar el acceso remoto desde sistemas de escritorio y otros dispositivos frontales para el entorno basado en {{site.data.keyword.cloud_notm}}. No es necesario otorgar accesos ni gestionar usuarios en el entorno de nube. Podrían haber distintos usuarios con distintas responsabilidades que tuviesen la necesidad de acceder a la base de datos mediante una interfaz gráfica de usuario específica, una línea de mandatos, o que tuviesen restricciones de latencia que podrían precisar de acceso basado en RDP (Remote Desktop Protocol). Para gestionar este tipo de acceso remoto, es posible desplegar un host administrativo ("jump host") para servir como un punto central de acceso para estos escenarios. Aparte de estos requisitos específicos, los usuarios tienen acceso a los sistemas basados en la nube dentro de la red corporativa sin que sea necesario administrarlos específicamente.

## Red
{: #network}

Cualquier dispositivo en un entorno {{site.data.keyword.cloud_notm}} se puede solicitar con un acceso de LAN interno o externo opcional. La dirección externa es una dirección IP pública direccionable que se debe tratar con cuidado. La dirección interna está determinada por la VLAN solicitada y que se elige del subrango 10.0.0.0/8 para la VLAN. Solicitando varias VLAN, es posible segregar distintos entornos, o tipos de tráfico, según el diseño de su red y sus requisitos de seguridad.

Mientras que una interfaz pública con un cortafuegos configurado podría cubrir algunos casos - por ejemplo, para realizar pruebas de concepto de forma rápida y a corto plazo - en la mayoría de los casos se debería considerar un dispositivo cortafuegos. La arquitectura de referencia de ejemplo muestra un escenario de producción, de forma que no se consideran interfaces de red públicas.

## Pasarela de Vyatta Network
{: #vyatta}

Vyatta proporciona direccionadores (routers) virtuales basados en software, NAT y cortafuegos virtuales y funcionalidades de VPN tanto para IPv4 como para IPv6. Si los usuarios se conecten remotamente a los sistemas basados en {{site.data.keyword.cloud_notm}}, estos dispositivos pueden servir como puntos de extremo a extremo de la VPN como, por ejemplo, para el denominado "road warrior VPN" (punto de acceso). También se pueden utilizar varios tipos de tecnologías VPN IPSec, o túneles SSL VPN como, por ejemplo, OpenVPN. Dependiendo de la tecnología SAP que utilice, estas conexiones VPN se pueden utilizar para interconectar sistemas SAP (incluso con sistemas no SAP) para la tecnología de interfaz gráfica de usuario tradicional, así como la tecnología de interfaz de usuario IU5 SAP basada en navegadores. La conexión de SAP Web Dispatcher detrás de una pasarela de Vyatta permite la utilización de características adicionales como, por ejemplo, el equilibro de carga o el inicio de sesión único. Para obtener más información sobre SAP Web Dispatcher, consulte [Alta disponibilidad](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#availability).

El dispositivo Vyatta puede desplegarse en una configuración de clúster de alta disponibilidad con un ancho de banda de hasta 10 Gbps. Para obtener más información, consulte [Configuración de alta disponibilidad de Vyatta 5400](/docs/infrastructure/virtual-router-appliance?topic=virtual-router-appliance-vyatta-5400-high-availability-configuration#vyatta-5400-high-availability-configuration).

## Servidor administrativo (jump box)
{: #jump_box}

Los sistemas SAP incluyen la gestión de usuarios y no precisan una administración de usuarios centralizada. También puede, por supuesto, configurar una gestión de usuarios centralizada. Para obtener más información, consulte [Administración de usuarios centralizada ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://help.sap.com/saphelp_nw73/helpdata/en/bf/b0b13bb3acd607e10000000a11402f/frameset.htm){: new_window}.

Un servidor administrativo (jump box) permite proporcionar un acceso de bajo nivel a usuarios específicos a su entorno de {{site.data.keyword.cloud_notm}} a través de herramientas basadas en el acceso a línea de mandatos u otras herramientas especializadas como, por ejemplo, SAP HANA Studio. Las herramientas de administración de bases de datos, así como los usuarios a los que se les otorga acceso a las herramientas, se gestionan de forma centralizada en el servidor administrativo (jump box). Los usuarios pueden iniciar la sesión en el entorno de {{site.data.keyword.cloud_notm}} desde sus escritorios mediante RDP (Remote Desktop Protocol), que se direcciona a través de la pasarela VPN.

## Servidores SAP - SAP HANA y SAP NetWeaver
{: #sap_servers}

{{site.data.keyword.IBM_notm}} ofrece distintos servidores para SAP HANA y SAP NetWeaver mediante la oferta {{site.data.keyword.cloud_notm}} for SAP Applications. Se trata de servidores {{site.data.keyword.baremetal_short}} con el sistema operativos (SO) que elija (Red Hat Linux, SUSE Linux, Microsoft Windows Server o desplegado con el hipervisor VMware ESX). Para obtener más detalles sobre los servidores certificados para SAP NetWeaver, consulte la [Nota SAP 2414097 ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. Tenga en cuenta que en el hipervisor, despliega uno de los sistemas operativos listados en la nota SAP 2414097 como sistema operativo invitado.

Los servidores SAP HANA vienen con un diseño de almacenamiento preseleccionado que cumple con los indicadores clave de rendimiento (KPI) de SAP para SAP HANA. No puede cambiar estos diseños y se le recomienda encarecidamente no utilizar almacenamiento externo para SAP HANA. A efectos de copias de seguridad y otros propósitos se puede utilizar almacenamiento externo de distintos niveles y con distintos protocolos de acceso como, por ejemplo, NFS, CIFS e iSCSI. Además, para los servidores SAP NetWeaver, tiene una opción para ejecutar otros sistemas de bases de datos soportados en almacenamiento externo.

Todas las soluciones de software SAP basadas en SAP HANA o SAP NetWeaver incluyen toda la SAP Business Suite. S/4HANA se puede desplegar en el entorno {{site.data.keyword.cloud_notm}}. Para otros componentes de software que no sean los indicados, necesita ponerse en contacto con el soporte de SAP. Siga el proceso de dimensionamiento SAP para determinar el tamaño del servidor correcto para su proyecto, y elija de la lista de servidores para la oferta SAP HANA o SAP NetWeaver.

Para obtener más información sobre los servidores certificados para SAP HANA, consulte [Directorio de hardware SAP HANA soportado y certificado ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.sap.com/dmc/exp/2014-09-02-hana-hardware/enEN/iaas.html#categories=IBM%20Cloud){: new_window}.

Para obtener más información sobre el proceso de dimensionamiento SAP HANA, consulte [Dimensionamiento del servidor (SAP HANA)](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server).

Para obtener más información sobre el proceso de dimensionamiento de SAP NetWeaver, consulte [Dimensionamiento del servidor (SAP NetWeaver)](/docs/infrastructure/sap-netweaver?topic=sap-netweaver-size_the_server#size_the_server).
