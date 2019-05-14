---
title: "Deploy archiving for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 50fa535c-7347-4e33-80a3-296748ef6666
description: "Summary: Read this topic to learn how to deploy archiving for Skype for Business Server."
---

# Deploy archiving for Skype for Business Server
 
**Summary:** Read this topic to learn how to deploy archiving for Skype for Business Server.
  
Archiving is automatically installed on each Front End Server in your Skype for Business Server deployment, but you still need to perform initial setup and configuration steps before you can use it. Before you begin, be sure you are familiar with the concepts in [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md).
  
## Deployment checklist

How you set up archiving depends on which storage option you choose: 
  
- If you use Microsoft Exchange integration for all users in your deployment, you don't need to configure Skype for Business Server archiving policies for your users. Instead, you configure Exchange In-Place Hold policies to support archiving for users homed on Exchange, with their mailboxes put on In-Place Hold. For details about configuring these policies, see the Exchange product documentation.
    
- If you do not use Microsoft Exchange integration for all users in your deployment, you need to add Skype for Business Server archiving databases (SQL Server databases) to your topology, publish the updated topology, and then configure archiving policies and settings for your users. You can deploy archiving databases at the same time that you deploy your initial topology or after you have deployed at least one Front End pool or Standard Edition Server. This document describes how to deploy archiving databases by adding them to an existing deployment.
    
If you enable archiving on one Front End pool or Standard Edition Server, you should enable it for all other Front End pools and Standard Edition Servers in your deployment. This is because users whose communications are required to be archived can be invited to a group IM conversation or meetings hosted on a different pool. If archiving is not enabled on the pool where the conversation or meeting is hosted, the complete session may not be archived. In these cases, IMs with archiving-enabled users still can be archived, but not for conferencing content files, and conference join or leave events.
  
> [!IMPORTANT]
> If archiving is critical in your organization for compliance reasons, be sure to deploy archiving, configure policies and other options at the appropriate level, and then turn on archiving for all appropriate users, before you enable those users for Skype for Business Server. 
  
The following table provides an overview of the steps required to deploy archiving in an existing topology.
  
|**Phase**|**Steps**|**Roles and group memberships**|**Documentation**|
|:-----|:-----|:-----|:-----|
|**Install prerequisite hardware and software** <br/> |To use Microsoft Exchange integration (using Exchange for archiving storage for some or all users), you need an existing Exchange deployment.  <br/> To use separate archiving databases (using SQL Server databases) for archiving storage for some or all users, SQL Server on the server that will store archiving data.  <br/> Archiving runs on Front End Servers of an Enterprise pool and Standard Edition Servers. It has no additional hardware or software requirements beyond what is required to install those servers.  <br/> |Domain user who is a member of the local administrators group.  <br/> |[Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md) <br/> [Environmental requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/environmental-requirements.md) <br/>  [Plan to integrate Skype for Business and Exchange](../../plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md) <br/>[System requirements for Skype for Business Server 2019](../../../SfBServer2019/plan/system-requirements.md) |
|**Create the appropriate internal topology to support archiving (only if not using Microsoft Exchange integration for all users in your deployment)** <br/> |Run Topology Builder to add Skype for Business Server archiving databases (SQL Server databases) to the topology, and then publish the topology.  <br/> |To define a topology to incorporate archiving databases, an account that is a member of the local users group.  <br/> To publish the topology, an account that is a member of the domain admins group and RTCUniversalServerAdmins group, and that has full control permissions (read/write/modify) on the file share to be used for the Skype for Business Server file store (so that Topology Builder can configure the required DACLs).  <br/> |[Add archiving databases to an existing deployment in Skype for Business Server](add-archiving-databases.md) <br/> |
|**Configure server-to-server authentication (only if using Microsoft Exchange integration)** <br/> |Configure servers to enable authentication between Skype for Business Server and Exchange. We recommend running **Test-CsExchangeStorageConnectivity testuser_sipUri -Folder Dumpster** to validate Exchange archiving storage connectivity before enabling archiving. <br/> |An account with the appropriate permissions for managing certificates on the servers.  <br/> |Manage server-to-server authentication  <br/> |
|**Configure archiving options and policies** <br/> |Configure archiving, including whether to use Microsoft Exchange integration, the global policy and any site and user policies (when not using Microsoft Exchange integration for all data storage), and specific archiving options, such as critical mode and data export and purging.  <br/> If using Microsoft Exchange integration, configure Exchange In-Place Hold policies as appropriate.  <br/> |RTCUniversalServerAdmins group (Windows PowerShell only) or assign users to the CSArchivingAdministrator or CSAdministrator role.  <br/> |[Configure archiving options for Skype for Business Server](configure-archiving-options.md) <br/> Exchange product documentation (if using Microsoft Exchange integration).  <br/> |
   

