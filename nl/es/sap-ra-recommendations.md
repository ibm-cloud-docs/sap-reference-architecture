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

# Orientación para su infraestructura de IBM Cloud certificada por SAP
{: #recommendations}

Sus requisitos pueden diferir de la orientación que aquí se ofrece; sin embargo, sirve como punto de partida para definir su servidor SAP certificado en el entorno {{site.data.keyword.cloud}}.

Figura 1. Arquitectura de referencia de ejemplo

![Figura 1. Arquitectura de referencia de ejemplo](/images/SAP-optimization-ref-architecture-20180527.png "Arquitectura de referencia de ejemplo")

## Redes VLAN
{: #vlans}

Las directrices de SAP recomiendan una separación del tráfico del servidor en varios controladores de interfaz de red (NIC). Por ejemplo, los datos del negocio deberían separarse de tráfico administrativo y de seguridad. La asignación de varios NIC a varias subredes diferentes permite esta segregación de datos. Para obtener más información, consulte la sección de Red en [Building High Availability for SAP NetWeaver and SAP HANA ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} (PDF).

Para seguir la recomendación de los controladores (NIC), {{site.data.keyword.cloud_notm}} permite la configuración de varias VLAN en los servidores. Las interfaces de VLAN pueden ser de alta disponibilidad (HA) ofreciendo varios controladores (NIC) para configurarlos en interfaces de vinculadas (Linux) o interfaces de equipo (Microsoft Windows). Tanto para las funcionalidades de recuperación ante desastres (DR) como de alta disponibilidad (HA) en los {{site.data.keyword.baremetal_short}}, es recomendable reservar varias direcciones IP adicionales y asignar las direcciones a distintos servicios SAP a medida que se vayan implementando dichos servicios. Consulte la documentación de instalación de SAP para obtener más información sobre cómo asignar direcciones durante la instalación con SAP Software Provisioning Manager (SWPM). Para máquinas virtuales (VM), habitualmente es suficiente la dirección de la interfaz principal de la máquina virtual.

De forma predeterminada, los {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} tienen una interfaz pública y una interfaz privada. En general, no se recomienda mantener la LAN pública configurada para todos los servidores en su infraestructura de {{site.data.keyword.cloud_notm}}. Se deberían desplegar instancias específicas de la pasarela Vyatta Network para permitir el acceso público a su entorno en el caso de que fuese necesario. Para obtener más información, consulte [Pasarela Vyatta Network](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-vyatta#vyatta).

## Almacenamiento de {{site.data.keyword.cloud_notm}}
{: #storage}

Los servidores certificados de {{site.data.keyword.cloud_notm}} para SAP NetWeaver puede configurarse con un número diferente de discos internos, así como con diferentes configuraciones RAID para los mismos. Tenga en cuenta que estas configuraciones podrían no ser suficientes para los requisitos concretos del proyecto (por ejemplo, un tamaño insuficiente, o acceso compartido para el almacenamiento).

Los requisitos de almacenamiento difieren hasta un punto que esta orientación es para definir con claridad los indicadores clave de rendimiento (KPI) en términos de intervalos de tiempo de restauración y copia de seguridad, requisitos de migración tras error y alta disponibilidad y, después, decidir el tipo de almacenamiento a utilizar. Cubrir todas las opciones está fuera del ámbito de este contenido, sin embargo, se promocionan algunas directrices.

  * Utilice dispositivos iSCSI compartidos para las configuraciones de alta disponibilidad (HA) entre nodos cuando la base de datos falle. Necesitará conocer el máximo requerido de IOPS/sec.

  * Utilice almacenamiento interno para configuraciones de alta disponibilidad (HA) con bases de datos replicadas, por ejemplo, la réplica de sistema de SAP HANA. Los servidores de aplicaciones SAP NetWeaver pueden residir en el almacenamiento interno o en NAS (Network Attached Storage).

  * Utilice almacenamiento compartido para facilitar las capacidades de migración ante errores con instalaciones basadas en VMware. Para obtener más información sobre la selección del tipo de almacenamiento adecuado, consulte [Almacenamiento para utilizar con sistemas VMware](/docs/infrastructure/vmware?topic=VMware-storage-to-use-with-vmware-systems#storage-to-use-with-vmware-systems).

Todas las opciones se pueden seleccionar desde la infraestructura de {{site.data.keyword.cloud_notm}}.

## Alta disponibilidad
{: #availability}

En una instalación distribuida de aplicaciones SAP en una base de datos centralizada, la instalación base se replica para conseguir una alta disponibilidad. Para cada capa de la arquitectura, el diseño de la alta disponibilidad varía.

  * **SAP Web Dispatcher**. La alta disponibilidad se consigue con varias instancias de SAP Web Dispatcher redundantes con el tráfico de las aplicaciones SAP. SAP Web Dispatcher sirve como un posible punto de entrada para un conjunto de sistemas SAP y otros servicios basados en `https`. Normalmente se encuentra entre Internet y los sistemas de fondo y aborda solicitudes basadas en el protocolo web desde el "mundo exterior". SAP Web Dispatcher funciona como un proxy inverso con distintas características soportadas como, por ejemplo, equilibrio de carga e inicio de sesión único. Para obtener más información, consulte [SAP Web Dispatcher ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.sap.com/saphelp_nw73EhP1/helpdata/en/48/8fe37933114e6fe10000000a421937/frameset.htm){: new_window}.

  * **ABAP SAP Central Services (ASCS)**. Para la alta disponibilidad de ASCS en un entorno de {{site.data.keyword.cloud_notm}}, es necesario instalar el software de clúster del sistema operativo de destino, por ejemplo, Linux Pacemaker o Microsoft Cluster. Es necesario configurar el punto individual de anomalía del ASCS (servicio en cola de SAP) para replicar sus datos en un ERS (Enqueue Replication Service). Es necesario instalar una instancia de ERS como parte del proceso de instalación de SAP. El SWPM de SAP da soporte a dicha instancia. Para obtener detalles sobre la instalación y configuración de los componentes del clúster tanto para ASCS como para ERS, consulte la documentación del proveedor del sistema operativo de la oferta.

  * **Servidores de aplicaciones SAP NetWeaver**. La alta disponibilidad se logra equilibrando la carga del tráfico dentro de una agrupación de servidores de aplicaciones. Si sólo es necesaria una cantidad limitada de recursos, un servidor de aplicaciones individual puede configurarse como de alta disponibilidad. El servidor de aplicaciones se debe instalar con almacenamiento que sea accesible por todos los posibles nodos del clúster, que puede utilizarse para la migración tras error. Además, la pila de SAP NetWeaver necesita utilizar un nombre de host virtual. Consulte la documentación del sistema operativo del proveedor del sistema operativo para obtener detalles sobre la configuración necesaria y la documentación de SAP para la alta disponibilidad. Si su configuración precisa de varios servidores de aplicaciones, la configuración de los servidores de aplicaciones de SAP también deben cubrir el equilibrio de carga, por ejemplo, en grupos de inicio de sesión de SAP y en grupos de servidores RFC. Para obtener más información, consulte la guía de administración para la versión de SAP NetWeaver.

  * **Nivel de base de datos**. La arquitectura de referencia de ejemplo despliega una instancia de SAP HANA individual, u otra base de datos. Para la alta disponibilidad, despliegue más de una instancia y utilice HANA System Replication (HSR) para implementar la migración tras error manual. Para habilitar la migración automática tras un error, se necesita una extensión de alta disponibilidad para la distribución Linux específica. Para otras bases de datos, se pueden configurar la migración tras error de la instancia de la base de datos en el almacenamiento compartido, o una técnica de réplica similar en el caso de SAP HANA. Consulte la documentación del sistema de bases de datos soportado para el conjunto de operaciones necesarias para configurar la alta disponibilidad o la réplica.

  Para obtener información adicional, consulte [Soporte para alta disponibilidad de {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha).

## Recuperación ante desastres
{: #dr}

En cada nivel se utiliza una estrategia diferente para proporcionar protección para la recuperación ante desastres.

 * **Servidores de aplicaciones SAP NetWeaver**. Los servidores de aplicaciones SAP no contienen datos de negocio; sin embargo, es necesario preservar la instalación y configuración del servidor para un funcionamiento continuo después de un desastre. Una estrategia de recuperación ante desastres es tener servidores de aplicaciones SAP en otra región. Los cambios en la configuración o en las actualizaciones del kernel en el servidor de aplicaciones primario deben copiarse en las máquinas virtuales o servidores en la región de recuperación ante desastres.

 * **SAP Central Services (SCS)**. El componente SCS de la pila de aplicaciones SAP no ofrece persistencia de datos del negocio. Puede crear un servidor o una máquina virtual (VM) en la región de recuperación ante desastres para que desempeñe el rol de SCS. El único contenido desde el nodo SCS primario que hay que sincronizar es el contenido compartido de `/sapmnt`. Además, si la configuración cambia o si las actualizaciones del kernel tienen lugar en los servidores SCS primarios, los cambios se deben replicar en el SCS de recuperación ante desastres. Para sincronizar los dos servidores, utilice un trabajo de copia planificado que se ejecute regularmente para copiar `/sapmnt` a los servidores de recuperación ante desastres. Para obtener más información sobre SCS, consulte [Instancia de servicios centrales ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/48/0728f74c6a3837e10000000a42189b/frameset.htm){: new_window}.

 * **Nivel de base de datos**. Para sistemas basados en SAP HANA, utilice las soluciones de réplica soportadas para HANA como, por ejemplo, HANA System Replication o las características de réplica de almacenamiento de {{site.data.keyword.cloud_notm}}. Para otras bases de datos soportadas, consulte la documentación de las características soportadas de la base de datos. En general, la elección de las opciones disponibles requiere una comprensión clara de los requisitos empresariales de la aplicación SAP subyacente. Se debe determinar el impacto de una pérdida potencial de transacciones individuales o incluso de todos los datos dentro de una ventana temporal.

 * **Infraestructura**. Dependiendo de dónde se encuentren los clientes SAP en su infraestructura {{site.data.keyword.cloud_notm}}, es necesario preparar otros componentes dentro de la misma ante los escenarios para la recuperación ante desastres. En la arquitectura de referencia de ejemplo, los clientes acceden a los sistemas SAP desde el lado de las instalaciones locales, o desde dentro de la red corporativa del cliente.

## Seguridad
{: #security}

### Gestión de usuarios

SAP tiene su proprio motor de gestión de usuarios (Users Management Engine (UME)) para controlar las autorizaciones y los accesos basados en roles con la aplicación SAP. Para obtener más información, consulte [Seguridad SAP HANA - Visión general ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://archive.sap.com/documents/docs/DOC-62943){: new_window}. Desde una perspectiva de gestión de usuarios, no es relevante si los sistemas SAP ejecutan en {{site.data.keyword.cloud_notm}} local. Las excepciones a esta regla se mencionan en [Servidor administrativo (jump box)](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-jump_box#jump_box).

### Seguridad de red

Dado que existen diferentes formas de acceder a un entorno basado en {{site.data.keyword.cloud_notm}}, es necesario diferenciar las medidas de seguridad.

El uso de una interfaz pública para el acceso externo sólo debe considerarse en los despliegues de pruebas. Para escenarios de producción, está disponible el despliegue de dispositivos Vyatta puesto que los dispositivos ofrecen toda la funcionalidad necesaria (cortafuegos VPN, etc.). Si los dispositivos Vyatta no cumplen con sus requisitos de latencia y ancho de banda, póngase en contacto con el soporte de {{site.data.keyword.cloud_notm}} para considerar todas las configuraciones y los pasos necesarios disponibles más allá de los dispositivos Vyatta.
