---
title: "Deploy Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8373c93b-92a7-4932-bc1f-00fc08955426
description: "Summary: Read this topic to learn how to deploy Skype for Business Server 2015 Persistent Chat Server."
---

# Deploy Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Read this topic to learn how to deploy Skype for Business Server 2015 Persistent Chat Server.
  
To deploy Persistent Chat Server, you: 
  
- Use Topology Builder to define, or import, and subsequently publish your topology and the components that you want to deploy
    
- Prepare your environment for deploying Persistent Chat Server components
    
- Install and configure Persistent Chat Server components for your deployment
    
Before you deploy Persistent Chat Server, you should read [Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md). The planning topics describe hardware and software requirements, possible topologies, and collocation scenarios. 
  
> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 

## Deployment checklist

You can deploy Persistent Chat Server after you deploy your initial topology, including at least one Skype for Business Server Front End pool or one Skype for Business Standard Edition Server. The deployment checklist describes the basic steps required to deploy Persistent Chat Server and provides links for more details.
  
**Persistent Chat Server Deployment Process**

|**Task**|**Steps**|**Required roles and group memberships**|**Related topics**|
|:-----|:-----|:-----|:-----|
|**Install prerequisite hardware and software** <br/> | On hardware that meets system requirements, install the following: <br/>  On the Persistent Chat Server Front End Servers: <br/>  An operating system that meets system requirements <br/>  Software prerequisites for computers running Skype for Business Server <br/>  On the server that will host the Persistent Chat Server database: <br/>  A supported version of SQL Server <br/>  If Persistent Chat Server compliance is required: <br/>  SQL Server on the server that will host the Persistent Chat Server compliance database <br/> |Any user who is a member of the local Administrators group.  <br/> |[Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md) <br/> [Environmental requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/environmental-requirements.md) <br/> [Hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/hardware-and-software-requirements.md) <br/> |
|**Create the appropriate internal topology to support Persistent Chat Server (and optionally, Persistent Chat compliance)** <br/> | Run Topology Builder to add a Persistent Chat Server pool to your topology: <br/>  Add Persistent Chat Server components to the topology <br/>  Create a SQL Server database for the Persistent Chat Server store (and a backup SQL Server for disaster recovery) <br/>  Define a new Skype for Business File Store or use an existing Skype for Business File Store for Persistent Chat Server files <br/>  Associate the Skype for Business Server pool that can route requests to this Persistent Chat Server pool <br/>  If Persistent Chat compliance is required: <br/>  Add Persistent Chat Compliance Store <br/>  Click the Persistent Chat Server pool definition check box for enabling compliance <br/>  Publish the topology. <br/>  If you install Persistent Chat Server on Standard Edition, the fully qualified domain name (FQDN) of the Persistent Chat Server pool must match the Standard Edition server, and the SQL Server databases are collocated on the SQL Server Express instance on the Standard Edition server <br/> |To define a topology, an account that is a member of the local Users group.  <br/> To publish the topology, an account that is a member of the Domain Admins group and RTCUniversalServerAdmins group, and the user should also have full control permissions (read/write/modify) on the Skype for Business File Store for Persistent Chat Server files (so that Topology Builder can configure the required DACLs).  <br/> |[Create and publish new topology in Skype for Business Server 2015](../../deploy/install/create-and-publish-new-topology.md) <br/> [Add Persistent Chat Server to your Skype for Business Server 2015 topology](add-persistent-chat-server.md) <br/> |
|**Deploy Persistent Chat Server** <br/> | Run the Skype for Business Server setup on all the computers running Persistent Chat Server. The Persistent Chat Server setup is integrated into the Skype for Business Server Deployment wizard that provides the following instructions: <br/>  Deploy local management store <br/>  Install Persistent Chat services <br/>  Request and assign certificates <br/>  Run and start the services <br/> |Any user who is a member of the local Administrators group.  <br/> |[Deploy Persistent Chat Server in Skype for Business Server 2015](deploy-persistent-chat-server.md) <br/> |
|**Create a Persistent Chat administrator** <br/> |Add users to the CsPersistentChatAdministrator security group.  <br/> |Any user who is a member of domain administrators.  <br/> |[Create a Persistent Chat administrator in Skype for Business Server 2015](create-a-persistent-chat-administrator.md) <br/> |
|**Configure Persistent Chat Server** <br/> | Configure users: <br/>  User has to be enabled by policy to access Persistent Chat Server. By default, the policy is turned off for all users and can be defined at global/site/pool/user scopes. <br/>  Configure settings <br/> |User must be a member of CsPersistentChatAdministrator. To change policy, user must be in CsUserAdministrator, at a minimum.  <br/> |[Manage Persistent Chat Server in Skype for Business Server 2015](../../manage/persistent-chat/persistent-chat.md) <br/> |
   

