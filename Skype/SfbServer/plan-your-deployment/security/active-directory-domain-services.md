---
title: "Active Directory Domain Services for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 5483afd5-d8af-4825-ae95-a82dbe941dbf
description: "Active Directory Domain Services functions as the directory service for Windows Server 2003, Windows Server 2008, Windows Server 2012, and Windows Server 2012 R2 networks. Active Directory Domain Services also serves as the foundation on which the Skype for Business Server security infrastructure is built. The purpose of this section is to describe how Skype for Business Server uses Active Directory Domain Services to create a trustworthy environment for IM, Web conferencing, media, and voice. For details about preparing your environment for Active Directory Domain Services, see Install Skype for Business Server in the Deployment documentation. For details about the role of Active Directory Domain Services in Windows Server networks, see the documentation for the version of the operating system you are using."
---

# Active Directory Domain Services for Skype for Business Server
 
Active Directory Domain Services functions as the directory service for Windows Server 2003, Windows Server 2008, Windows Server 2012, and Windows Server 2012 R2 networks. Active Directory Domain Services also serves as the foundation on which the Skype for Business Server security infrastructure is built. The purpose of this section is to describe how Skype for Business Server uses Active Directory Domain Services to create a trustworthy environment for IM, Web conferencing, media, and voice. For details about preparing your environment for Active Directory Domain Services, see [Install Skype for Business Server](../../deploy/install/install.md) in the Deployment documentation. For details about the role of Active Directory Domain Services in Windows Server networks, see the documentation for the version of the operating system you are using.
  
Skype for Business Server uses Active Directory Domain Services to store:
  
- Global settings that all servers running Skype for Business Server in a forest require.
    
- Service information that identifies the roles of all servers running Skype for Business Server in a forest.
    
- Some user settings.
    
## Active Directory Infrastructure

Infrastructure requirements for Active Directory include the following:
  
- Operating system requirements for domain controllers
    
- Domain and forest functional level requirements
    
- Global catalog domain requirements
    
For details, see [Environmental requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/environmental-requirements.md) or [Server requirements for Skype for Business Server 2019](../../../SfBServer2019/plan/system-requirements.md).
  
## Universal Groups

During preparation of the forest, Skype for Business Server creates various universal groups within Active Directory Domain Services that have permission to access and manage global settings and services. These universal groups include:
  
- **Administrative groups**. These groups define the fundamental administrator roles for a Skype for Business Server network. During forest preparation, these administrator groups are added to Skype for Business Server infrastructure groups.
    
- **Service groups**. These groups are service accounts that are required to access various services provided by Skype for Business Server.
    
- **Infrastructure groups**. These groups provide permission to access specific areas of the Skype for Business Server infrastructure. They function as components of administrative groups, and you should not modify them or add users to them directly. During forest preparation, specific service and administration groups are added to the appropriate infrastructure groups.
    
For details about the specific universal groups created when preparing AD for Skype for Business Server, as well as the service and administration groups that get added to the infrastructure groups, see [Changes made by forest preparation in Skype for Business Server](../../schema-reference/active-directory-schema-extensions-classes-and-attributes/changes-made-by-forest-preparation.md) in the Deployment documentation.
  
> [!NOTE]
> Skype for Business Server supports the universal groups in the Windows Server 2012, as well as Windows Server 2003 operating systems for domain controllers. Members of universal groups can include other groups and accounts from any domain in the domain tree or forest and can be assigned permissions in any domain in the domain tree or forest. Universal group support, combined with administrator delegation, simplifies the management of a Skype for Business Server deployment. For example, it is not necessary to add one domain to another to enable an administrator to manage both. 
  
## Role-Based Access Control

In addition to creating universal service and administration groups and adding service and administration groups to the appropriate universal groups, forest preparation also creates Role-Based Access Control (RBAC) groups. For details about the specific RBAC groups created by forest preparation, see [Changes made by forest preparation in Skype for Business Server](../../schema-reference/active-directory-schema-extensions-classes-and-attributes/changes-made-by-forest-preparation.md) in the Deployment documentation. For more information about RBAC groups, see [Role-based access control (RBAC) for Skype for Business Server](role-based-access-control-rbac.md).
  
## Access Control Entries (ACEs) and Inheritance

Forest preparation creates both private and public ACEs and, adding ACEs for the universal groups it creates. It creates specific private ACEs on the global settings container used by Skype for Business Server. This container is used only by Skype for Business Server and is located either in the Configuration container or the System container in the root domain, depending on where you store global settings.
  
The domain preparation step adds the necessary access control entries (ACEs) to universal groups that grant permissions to host and manage users within the domain. Domain preparation creates ACEs on the domain root and three built-in containers: User, Computers, and Domain Controllers.
  
For details about the public ACEs created and added by forest preparation and domain preparation, see [Changes made by forest preparation in Skype for Business Server](../../schema-reference/active-directory-schema-extensions-classes-and-attributes/changes-made-by-forest-preparation.md) and [Changes made by domain preparation in Skype for Business Server](../../schema-reference/active-directory-schema-extensions-classes-and-attributes/changes-made-by-domain-preparation.md) in the Deployment documentation.
  
Organizations often lock down Active Directory Domain Services (AD DS) to help mitigate security risks. However, a locked-down Active Directory environment can limit the permissions that Skype for Business Server requires. This can include removal of ACEs from containers and OUs and disabling of permissions inheritance on User, Contact, InetOrgPerson, or Computer objects. In a locked down Active Directory environment, permissions must be set manually on containers and OUs that require them.
  
## Server Information

During activation, Skype for Business Server publishes server information to the three following locations in Active Directory Domain Services:
  
- A service connection point (SCP) on each Active Directory computer object corresponding to a physical computer on which Skype for Business Server is installed.
    
- Server objects created in the container of the **msRTCSIP-Pools** class.
    
- Trusted servers specified in Topology Builder.
    
## Service Connection Points

Each Skype for Business Server object in Active Directory Domain Services has an SCP called RTC Services, which in turn contains a number of attributes that identify each computer and specify the services that it provides. Among the more important SCP attributes are  *serviceDNSName*  , *serviceDNSNameType*  , *serviceClassname*  , and *serviceBindingInformation*  . Third-party asset management applications can retrieve server information across a deployment by querying against these and other SCP attributes.
  
## Active Directory Server Objects

Each Skype for Business Server server role has a corresponding Active Directory object whose attributes define the services provided by that role. Also, when a Standard Edition server is activated, or when an Enterprise Edition pool is created, Skype for Business Server creates a new **msRTCSIP-Pool** object in the **msRTCSIP-Pools** container. The **msRTCSIP-Pool** class specifies the fully qualified domain name (FQDN) of the pool, along with the association between the front-end and back-end components of the pool. (A Standard Edition server is regarded as a logical pool whose front and back ends are collocated on a single computer.)
  
## Trusted Servers

In Skype for Business Server, trusted servers are the ones specified when you run Topology Builder and publish your topology. The published topology, including all the server information, is stored in the Central Management store. Only servers defined in the Central Management store are trusted. In Skype for Business Server, a trusted server is one that meets the following criteria:
  
- The FQDN of the server occurs in the topology stored in Central Management store.
    
- The server presents a valid certificate from a trusted CA. For details, see [Environmental requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/environmental-requirements.md) or [System requirements for Skype for Business Server 2019](../../../SfBServer2019/plan/system-requirements.md).
    
If either of these criteria is missing, the server is not trusted and connection with it is refused. This double requirement prevents a possible, if unlikely, attack in which a rogue server attempts to take over a valid server's FQDN.
  
Additionally, to enable Microsoft Office Communications Server 2007 R2 and Microsoft Office Communications Server 2007 deployments to communicate with Skype for Business Server servers, Skype for Business Server creates containers during forest preparation for holding lists of trusted servers for previous releases. The following table describes the containers created to enable compatibility with previous deployments.
  
**Trusted Server Lists and Their Active Directory Containers for Compatibility with Previous Releases**

|**Trusted server list**|**Active Directory container**|
|:-----|:-----|
|Standard Edition servers and Enterprise pool Front End Servers  <br/> |RTC Service/Global Settings  <br/> |
|Conferencing Servers  <br/> |RTC Service/Trusted MCUs  <br/> |
|Web Components Servers  <br/> |RTC Service/TrustedWebComponentsServers  <br/> |
|Mediation Servers and Communicator Web Access Servers, Application Server, Registrar with QoE, A/V Conferencing Service (also 3rd-party SIP servers)  <br/> |RTC Service/Trusted Services  <br/> |
|Proxy Servers  <br/> |Skype for Business Server does not support backward compatibility for proxy servers  <br/> |
   

## See also

[Prepare Active Directory for Skype for Business Server](../../deploy/install/prepare-active-directory.md)
