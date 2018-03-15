---
title: "Requirements to publish a topology in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 841cdf5d-d884-414d-ab50-3bb681b622ed
description: "This topic describes the infrastructure and software requirements that are specific to publishing a topology, whether by using Topology Builder or the Lync Server 2013 Management Shell command-line interface. These requirements are in addition to the general operating system, software, and permissions requirements applicable to all Lync Server 2013 administrative tools. Make sure that you satisfy all administrative tools requirements before you publish a topology."
---

# Requirements to publish a topology in Lync Server 2013
[]
This topic describes the infrastructure and software requirements that are specific to publishing a topology, whether by using Topology Builder or the Lync Server 2013 Management Shell command-line interface. These requirements are in addition to the general operating system, software, and permissions requirements applicable to all Lync Server 2013 administrative tools. Make sure that you satisfy all administrative tools requirements before you publish a topology.
  
- You must run Topology Builder on a computer that is joined to the same domain or forest of the Lync Server 2013 deployment you are creating so that Active Directory Domain Services preparation steps are already completed, enabling you to use the administrative tools on that computer to successfully publish your topology.
    
- The computers defined in the topology must be joined to the domain, except for Edge Servers, and in AD DS. However, the computers do not need to be online when you publish the topology.
    
- The file share for the pool must be created and available to remote users.
    
- In order to publish an Enterprise Edition Front End pool, the SQL Server-based Back End Server must be joined to the domain in which you are deploying the servers, online, and configured with the appropriate firewall rules to make it available to remote users. For details about specifying firewall exceptions, see [Understanding firewall requirements for SQL Server with Lync Server 2013](understanding-firewall-requirements-for-sql-server.md). For other details about configuring SQL Server, see [Configure SQL Server for Lync Server 2013](configure-sql-server-for-lync-server-2013.md).
    
    > [!NOTE]
    > Standard Edition server has a collocated database that will accept the published configuration. You must first run the **Prepare first Standard Edition server** setup task in the Lync Server Deployment Wizard. 
  
## See also

#### 

[Publish the topology in Lync Server 2013](publish-the-topology.md)
  
[Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md)
#### 

[Administrative tools software requirements in Lync Server 2013](administrative-tools-software-requirements.md)
  
[Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md)
#### 

[Administrator rights and permissions required for setup and administration of Lync Server 2013](administrator-rights-and-permissions-required-for-setup-and-administration.md)

