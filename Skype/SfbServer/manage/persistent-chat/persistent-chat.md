---
title: "Manage Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c58ee4f4-563b-4d0c-be91-c62df886caa9
description: "Summary: Learn how to manage Persistent Chat Server in Skype for Business Server 2015."
---

# Manage Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Learn how to manage Persistent Chat Server in Skype for Business Server 2015.
  
When you set up Persistent Chat Server for your organization, you specify the initial configuration during deployment. However, there may be times when you want to change how you implement Persistent Chat Server support. For example you may need to set up Persistent Chat Server support and controls differently for a specific team or group within your organization. This section provides information and procedures to help you customize your Persistent Chat Server deployment. For details about the features and functionality that you can configure for Persistent Chat Server, see [Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md). For details about deploying Persistent Chat Server, see [Deploy Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-persistent-chat-server/deploy-persistent-chat-server.md). 

> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
  
You can manage Persistent Chat Server by using the Control Panel or by using Windows PowerShell cmdlets. 
  
To use the Control Panel:
  
1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Persistent Chat**.
    
The following table summarizes the Windows PowerShell cmdlets available to help you manage Persistent Chat Server. For details about syntax, including all available parameters, see [Skype for Business Server 2015 Management Shell](../management-shell.md).
  

|**Cmdlet**|**Description**|
|:-----|:-----|
|New-CsPersistentChatCategory  <br/> |Creates a new category  <br/> |
|Set-CsPersistentChatCategory  <br/> |Configures settings for an existing category  <br/> |
|Get-CsPersistentChatCategory  <br/> |Retrieves information about categories  <br/> |
|Remove-CsPersistentChatCategory  <br/> |Removes a category  <br/> |
|New-CsPersistentChatRoom  <br/> |Creates a new chat room  <br/> |
|Set-CsPersistentChatRoom  <br/> |Configures settings for an existing room; assign users and user groups to the room  <br/> |
|Get-CsPersistentChatRoom  <br/> |Retrieves information about rooms  <br/> |
|Clear-CsPersistentChatRoom  <br/> |Clears a room or messages from a room  <br/> |
|Remove-CsPersistentChatRoom  <br/> |Removes a room  <br/> |
|Remove-CsPersistentChatMessage  <br/> |Removes messages from a room  <br/> |
|New-CsPersistentChatAddin  <br/> |Creates a new add-in  <br/> |
|Set-CsPersistentChatAddin  <br/> |Configures settings for an existing add-in  <br/> |
|Get-CsPersistentChatAddin  <br/> |Retrieves information about add-ins  <br/> |
|Remove-CsPersistentChatAddin  <br/> |Removes an add-in  <br/> |
|Set-CsPersistentChatComplianceConfiguration  <br/> |Modifies an existing collection of compliance configuration settings  <br/> |
|Export-CsPersistentChatData  <br/> |Exports data from a Persistent Chat database  <br/> |
|Import-CsPersistentChatData  <br/> |Imports data that was exported from a previous version of Lync Server  <br/> |
   

