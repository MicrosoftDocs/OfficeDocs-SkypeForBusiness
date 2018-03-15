---
title: "Deployment checklist for Persistent Chat Server in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b1108f8f-88a2-4660-8086-d25ba76f7239
description: "Deployment of Lync Server 2013, Persistent Chat Server requires that you deploy it in the correct sequence and that you complete all required deployment steps."
---

# Deployment checklist for Persistent Chat Server in Lync Server 2013
[]
Deployment of Lync Server 2013, Persistent Chat Server requires that you deploy it in the correct sequence and that you complete all required deployment steps.
  
## Deployment Sequence

You can deploy Persistent Chat Server after you deploy your initial topology, including at least one Lync Server 2013, Front End pool or one Lync Server 2013, Standard Edition server. This topic describes how to deploy Persistent Chat Server by adding it to an existing deployment.
  
## Deployment Process

The following table lists the basic steps to deploy Persistent Chat Server and provides links for more details.
  
**Persistent Chat Server Deployment Process**

|**Task**|**Steps**|**Required roles and group memberships**|**Related topics**|
|:-----|:-----|:-----|:-----|
|**Install prerequisite hardware and software** <br/> | On hardware that meets system requirements, install the following:  <br/>  On the Persistent Chat Server Front End Servers:  <br/>  An operating system that meets system requirements  <br/>  Software prerequisites for computers running Lync Server 2013  <br/>  SQL Server on the server that will host Persistent Chat Server database  <br/>  If Persistent Chat Server compliance is required:  <br/>  SQL Server on the server that will host Persistent Chat Server compliance database  <br/> |Any user who is a member of the local Administrators group.  <br/> |[Supported hardware for Lync Server 2013](supported-hardware.md) in the Supportability documentation  <br/> [Server software and infrastructure support in Lync Server 2013](server-software-and-infrastructure-support.md) in the Supportability documentation  <br/> [Determining your system requirements for Lync Server 2013](determining-your-system-requirements.md) <br/> [Technical requirements for Persistent Chat Server in Lync Server 2013](technical-requirements-for-persistent-chat-server.md) <br/> |
|**Create the appropriate internal topology to support Persistent Chat Server (and optionally, Persistent Chat compliance)** <br/> | Run Topology Builder to add a Persistent Chat Server pool to your topology:  <br/>  Add Persistent Chat Server components to the topology  <br/>  Create a SQL Server database for the Persistent Chat Server store (and a backup SQL Server for disaster recovery)  <br/>  Define a new Lync File Store or use an existing Lync File Store for Persistent Chat Server files  <br/>  Associate the Lync Server 2013 pool that can route requests to this Persistent Chat Server pool  <br/>  If Persistent Chat compliance is required:  <br/>  Add Persistent Chat Compliance Store  <br/>  Click the Persistent Chat Server pool definition check box for enabling compliance  <br/>  Publish the topology  <br/>  If you install Persistent Chat Server on Standard Edition, the fully qualified domain name (FQDN) of the Persistent Chat Server pool must match the Standard Edition server, and the SQL Server databases are collocated on the SQL Server Express instance on the Standard Edition server  <br/> |To define a topology, an account that is a member of the local Users group.  <br/> To publish the topology, an account that is a member of the Domain Admins group and RTCUniversalServerAdmins group, and the user should also have full control permissions (read/write/modify) on the Lync File Store for Persistent Chat Server files (so that Topology Builder can configure the required DACLs).  <br/> |[Adding Persistent Chat Server to your deployment in Lync Server 2013](adding-persistent-chat-server-to-your-deployment.md) in the Deployment documentation  <br/> |
|**Deploy Persistent Chat Server** <br/> | Run the Lync Server setup on all the computers running Persistent Chat Server. The Persistent Chat Server setup is integrated into the Lync Server 2013 Deployment wizard that provides the following instructions:  <br/>  Deploy local management store  <br/>  Install Persistent Chat Server services  <br/>  Request and assign certificates  <br/>  Run and start the services  <br/> |Any user who is a member of the local Administrators group.  <br/> |[Deploying Persistent Chat Server in Lync Server 2013](deploying-persistent-chat-server.md) in the Deployment documentation  <br/> |
|**Create a Persistent Chat administrator** <br/> |Add users to the CsPersistentChatAdministrator security group.  <br/> |Any user who is a member of domain administrators.  <br/> |[Adding a Persistent Chat administrator in Lync Server 2013](adding-a-persistent-chat-administrator.md) in the Deployment documentation  <br/> |
|**Configure Persistent Chat Server** <br/> | Configure users:  <br/>  User has to be enabled by policy to access Persistent Chat Server. By default, the policy is turned off for all users and can be defined at global/site/pool/user scopes.  <br/>  Configure settings  <br/> |User must be a member of CsPersistentChatAdministrator. To change policy, user must be in CsUserAdministrator, at a minimum.  <br/> |[Configuring Persistent Chat Server in Lync Server 2013](configuring-persistent-chat-server.md) in the Deployment documentation  <br/> |
   
> [!IMPORTANT]
> You can deploy one or more Persistent Chat Server pools. We support multiple Persistent Chat Server pools for regulatory reasons whereby data generated in a given region is required to stay in that region. For example, if you deploy a Persistent Chat Server pool in Chicago, and another in Zurich to comply with regulations for data in Switzerland, users can connect to rooms in both the Persistent Chat Server pools, provided they have access. 
  

