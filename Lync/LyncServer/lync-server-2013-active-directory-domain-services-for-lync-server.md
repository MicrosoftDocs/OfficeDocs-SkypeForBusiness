---
title: 'Lync Server 2013: Active Directory Domain Services for Lync Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Active Directory Domain Services for Lync Server 2013
ms:assetid: 5483afd5-d8af-4825-ae95-a82dbe941dbf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn481129(v=OCS.15)
ms:contentKeyID: 59893871
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Active Directory Domain Services for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-13_

Active Directory Domain Services functions as the directory service for Windows Server 2003, Windows Server 2008, Windows Server 2012, and Windows Server 2012 R2 networks. Active Directory Domain Services also serves as the foundation on which the Microsoft Lync Server 2013 security infrastructure is built. The purpose of this section is to describe how Lync Server 2013 uses Active Directory Domain Services to create a trustworthy environment for IM, Web conferencing, media, and voice. For details about Lync Server extensions to Active Directory Domain Services and about preparing your environment for Active Directory Domain Services, see [Preparing Active Directory Domain Services for Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md) in the Deployment documentation. For details about the role of Active Directory Domain Services in Windows Server networks, see the documentation for the version of the operating system you are using.

Lync Server 2013 uses Active Directory Domain Services to store:

  - Global settings that all servers running Lync Server 2013 in a forest require.

  - Service information that identifies the roles of all servers running Lync Server 2013 in a forest.

  - Some user settings.

<div>

## Active Directory Infrastructure

Infrastructure requirements for Active Directory include the following:

  - Operating system requirements for domain controllers

  - Domain and forest functional level requirements

  - Global catalog domain requirements

For details, see [Active Directory infrastructure requirements for Lync Server 2013](lync-server-2013-active-directory-infrastructure-requirements.md) in the Deployment documentation.

</div>

<div>

## Active Directory Domain Services Preparation

<div>


> [!NOTE]  
> We recommend that you deploy global settings to the Configuration container instead of the System container. This does not enhance security, but can result in scalability improvements for some Active Directory Domain Services topologies. If you are migrating from Microsoft Office Communications Server 2007 and have used the System container but plan to use the Configuration container, you MUST move the settings in the System container BEFORE you do any upgrade preparations. To migrate your System container settings to the Configuration container, see Office Communications Server 2007 Global Settings Migration Tool at <A href="http://go.microsoft.com/fwlink/p/?linkid=145236">http://go.microsoft.com/fwlink/p/?LinkId=145236</A>.



</div>

When deploying Lync Server 2013, the first step is to prepare Active Directory Domain Services. Preparing Active Directory Domain Services for Lync Server 2013 consists of the following three steps:

  - **Prepare Schema**. This task extends the schema in Active Directory Domain Services to include classes and attributes specific to Lync Server 2013. For details about preparing the schema, see [Running Active Directory schema preparation in Lync Server 2013](lync-server-2013-running-schema-preparation.md) in the Deployment documentation. For more information, see [Migration from Office Communications Server 2007 R2 to Lync Server 2013](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md).

  - **Prepare Forest**. This task creates global settings and objects in the forest root domain, along with the universal service and administrative groups that govern access to these settings and objects. For details about preparing the forest, see [Running forest preparation for Lync Server 2013](lync-server-2013-running-forest-preparation.md) in the Deployment documentation.

  - **Prepare Domain**. This task adds the necessary access control entries (ACEs) to universal groups that grant permissions to host and manage users within the domain. This task must be completed in all domains where you want to deploy servers running Lync Server 2013 and any domains where your Lync Server users reside. For details about preparing the domain, see [Running domain preparation for Lync Server 2013](lync-server-2013-running-domain-preparation.md) in the Deployment documentation.

For an overview of the complete process for preparing Active Directory and the rights and permissions required to perform each step, see [Active Directory infrastructure requirements for Lync Server 2013](lync-server-2013-active-directory-infrastructure-requirements.md) in the Deployment documentation.

</div>

<div>

## Universal Groups

During preparation of the forest, Lync Server 2013 creates various universal groups within Active Directory Domain Services that have permission to access and manage global settings and services. These universal groups include:

  - **Administrative groups**. These groups define the fundamental administrator roles for a Lync Server network. During forest preparation, these administrator groups are added to Lync Server infrastructure groups.

  - **Service groups**. These groups are service accounts that are required to access various services provided by Lync Server.

  - **Infrastructure groups**. These groups provide permission to access specific areas of the Lync Server infrastructure. They function as components of administrative groups, and you should not modify them or add users to them directly. During forest preparation, specific service and administration groups are added to the appropriate infrastructure groups.

For details about the specific universal groups created when preparing AD for Lync Server, as well as the service and administration groups that get added to the infrastructure groups, see [Changes made by forest preparation in Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) in the Deployment documentation.

<div>


> [!NOTE]  
> Lync Server 2013 supports the universal groups in the Windows Server 2012 for servers running Lync Server 2013, as well as Windows Server 2003 operating systems for domain controllers. Members of universal groups can include other groups and accounts from any domain in the domain tree or forest and can be assigned permissions in any domain in the domain tree or forest. Universal group support, combined with administrator delegation, simplifies the management of a Lync Server deployment. For example, it is not necessary to add one domain to another to enable an administrator to manage both.



</div>

</div>

<div>

## Role-Based Access Control

In addition to creating universal service and administration groups and adding service and administration groups to the appropriate universal groups, forest preparation also creates Role-Based Access Control (RBAC) groups. For details about the specific RBAC groups created by forest preparation, see [Changes made by forest preparation in Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) in the Deployment documentation. For more information about RBAC groups, see [Role-based access control (RBAC) for Lync Server 2013](lync-server-2013-role-based-access-control-rbac.md).

</div>

<div>

## Access Control Entries (ACEs) and Inheritance

Forest preparation creates both private and public ACEs and, adding ACEs for the universal groups it creates. It creates specific private ACEs on the global settings container used by Lync Server. This container is used only by Lync Server and is located either in the Configuration container or the System container in the root domain, depending on where you store global settings.

The domain preparation step adds the necessary access control entries (ACEs) to universal groups that grant permissions to host and manage users within the domain. Domain preparation creates ACEs on the domain root and three built-in containers: User, Computers, and Domain Controllers.

For details about the public ACEs created and added by forest preparation and domain preparation, see [Changes made by forest preparation in Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) and [Changes made by domain preparation in Lync Server 2013](lync-server-2013-changes-made-by-domain-preparation.md) in the Deployment documentation.

Organizations often lock down Active Directory Domain Services (AD DS) to help mitigate security risks. However, a locked-down Active Directory environment can limit the permissions that Lync Server 2013 requires. This can include removal of ACEs from containers and OUs and disabling of permissions inheritance on User, Contact, InetOrgPerson, or Computer objects. In a locked down Active Directory environment, permissions must be set manually on containers and OUs that require them. For details, see [Preparing a locked-down Active Directory Domain Services in Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md) in the Deployment documentation.

</div>

<div>

## Server Information

During activation, Lync Server 2013 publishes server information to the three following locations in Active Directory Domain Services:

  - A service connection point (SCP) on each Active Directory computer object corresponding to a physical computer on which Lync Server 2013 is installed.

  - Server objects created in the container of the **msRTCSIP-Pools** class.

  - Trusted servers specified in Topology Builder.

</div>

<div>

## Service Connection Points

Each Lync Server 2013 object in Active Directory Domain Services has an SCP called RTC Services, which in turn contains a number of attributes that identify each computer and specify the services that it provides. Among the more important SCP attributes are *serviceDNSName*, *serviceDNSNameType*, *serviceClassname*, and *serviceBindingInformation*. Third-party asset management applications can retrieve server information across a deployment by querying against these and other SCP attributes.

</div>

<div>

## Active Directory Server Objects

Each Lync Server 2013 server role has a corresponding Active Directory object whose attributes define the services provided by that role. Also, when a Standard Edition server is activated, or when an Enterprise Edition pool is created, Lync Server 2013 creates a new **msRTCSIP-Pool** object in the **msRTCSIP-Pools** container. The **msRTCSIP-Pool** class specifies the fully qualified domain name (FQDN) of the pool, along with the association between the front-end and back-end components of the pool. (A Standard Edition server is regarded as a logical pool whose front and back ends are collocated on a single computer.)

</div>

<div>

## Trusted Servers

In Lync Server 2013, trusted servers are the ones specified when you run Topology Builder and publish your topology. The published topology, including all the server information, is stored in the Central Management store. Only servers defined in the Central Management store are trusted. In Lync Server 2013, a trusted server is one that meets the following criteria:

  - The FQDN of the server occurs in the topology stored in Central Management store.

  - The server presents a valid certificate from a trusted CA. For details, see [Certificate infrastructure requirements for Lync Server 2013](lync-server-2013-certificate-infrastructure-requirements.md).

If either of these criteria is missing, the server is not trusted and connection with it is refused. This double requirement prevents a possible, if unlikely, attack in which a rogue server attempts to take over a valid server’s FQDN.

Additionally, to enable Microsoft Office Communications Server 2007 R2 and Microsoft Office Communications Server 2007 deployments to communicate with Lync Server 2013 servers, Lync Server 2013 creates containers during forest preparation for holding lists of trusted servers for previous releases. The following table describes the containers created to enable compatibility with previous deployments.

### Trusted Server Lists and Their Active Directory Containers for Compatibility with Previous Releases

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Trusted server list</th>
<th>Active Directory container</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standard Edition servers and Enterprise pool Front End Servers</p></td>
<td><p>RTC Service/Global Settings</p></td>
</tr>
<tr class="even">
<td><p>Conferencing Servers</p></td>
<td><p>RTC Service/Trusted MCUs</p></td>
</tr>
<tr class="odd">
<td><p>Web Components Servers</p></td>
<td><p>RTC Service/TrustedWebComponentsServers</p></td>
</tr>
<tr class="even">
<td><p>Mediation Servers and Communicator Web Access Servers, Application Server, Registrar with QoE, A/V Conferencing Service (also 3rd-party SIP servers)</p></td>
<td><p>RTC Service/Trusted Services</p></td>
</tr>
<tr class="odd">
<td><p>Proxy Servers</p></td>
<td><p>Lync Server 2013 does not support backward compatibility for proxy servers</p></td>
</tr>
</tbody>
</table>


To support trusted servers of previous releases, you must run the best practices analyzer tool. For details about running the best practices analyzer, see [http://go.microsoft.com/fwlink/p/?LinkId=330633](http://go.microsoft.com/fwlink/p/?linkid=330633).

</div>

</div>

<span> </span>

</div>

</div>

</div>

