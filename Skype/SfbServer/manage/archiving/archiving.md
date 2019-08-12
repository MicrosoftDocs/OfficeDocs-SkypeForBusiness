---
title: "Manage archiving in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 63fd56cf-6d40-4db5-96fc-32d813930bcf
description: "Summary: Learn how to manage archiving for Skype for Business Server."
---

# Manage archiving in Skype for Business Server

**Summary:** Learn how to manage archiving for Skype for Business Server.
  
When you deploy archiving for your organization, you specify the initial configuration during deployment. However, there may be times when you want to change how you implement archiving support for day-to-day management or to meet new requirements for your organization. For example, you may need to set up archiving support differently for a specific site, a specific pool, or specific users within your organization. For users homed on Skype for Business Server, you do this by creating and customizing archiving configuration options and user policies. 
  
Before you read this topic, be sure you are familiar with the information in [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md) and [Deploy archiving for Skype for Business Server](../../deploy/deploy-archiving/deploy-archiving.md).
  
> [!NOTE]
> If you enable Microsoft Exchange integration for your deployment, Exchange policies control whether archiving is enabled for the users who are homed on Exchange and have their mailboxes put on In-Place Hold. For details, see [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md) and [Configure integration with Exchange storage for Skype for Business Server](../../deploy/deploy-archiving/configure-integration-with-exchange-storage.md). 
  
## Archiving configuration options

Archiving configuration options specify whether to:
  
- Enable or disable archiving
    
- Archive IM sessions
    
- Archive web conferencing sessions
    
- Block activity when archiving is not available
    
- Use Exchange integration
    
- Set up purging and exporting of data
    
These options can be set at the global, site, or pool level. For more information, see [Manage archiving options in Skype for Business Server](options.md).
  
## Archiving policies

Archiving policies determine whether to archive the following:
  
- Internal communications
    
- External communications
    
These policies can be set at the global, site, or user level. For more information, see [Manage archiving policies in Skype for Business Server](policies.md).
  
## Manage archiving by using the Control Panel or by using Windows PowerShell

You can manage archiving by using the Control Panel or by using Windows PowerShell. The following table summarizes the cmdlets available to help you manage archiving. For details about syntax, including all available parameters, see [Skype for Business Server Management Shell](../management-shell.md). 


|**Cmdlet**|**Description**|
|:-----|:-----|
|Export-CsArchivingData  <br/> |Exports records that have been stored in the Skype for Business Server Archiving database.  <br/> |
|Get-CsArchivingConfiguration  <br/> |Returns information about the archiving configuration settings in your organization.  <br/> |
|Get-CsArchivingPolicy  <br/> |Returns information about your organization's archiving policies for internal and external communications.  <br/> |
|Grant-CsArchivingPolicy  <br/> |Assigns instant messaging (IM) session archiving policies to users or sets of users. These policies give you the ability to archive all IM sessions that take place between internal users, and/or to archive all IM sessions that take place between internal users and external partners.  <br/> |
|Invoke-CsArchivingDatabasePurge  <br/> |Manually purges records from the Archiving database.  <br/> |
|New-CsArchivingConfiguration  <br/> |Creates a new set of instant messaging (IM) settings, which can be used to enable or disable the automatic saving of IM sessions, and to block any instant messages that cannot be archived.  <br/> |
|New-CsArchivingPolicy  <br/> |Creates new instant messaging (IM) session archiving policies. These policies give you the ability to archive all IM sessions that take place between internal users, and/or to archive all IM sessions that take place between internal users and external partners.  <br/> |
|Remove-CsArchivingConfiguration  <br/> |Removes the specified collection of archiving settings that are used to enable or disable the automatic saving of instant messaging (IM) sessions, and to optionally block any instant message that cannot be archived.  <br/> |
|Remove-CsArchivingPolicy  <br/> |Removes the specified instant messaging (IM) archiving policy that determines whether Skype for Business Server will automatically save all IM sessions that take place between internal users, and/or all IM sessions between internal users and federated partners.  <br/> |
|Set-CsArchivingConfiguration  <br/> |Modifies an existing collection of instant messaging (IM) archiving configuration options.  <br/> |
|Set-CsArchivingPolicy  <br/> |Modifies an existing instant messaging (IM) archiving policy. An archiving policy gives you the ability to archive all IM sessions and conferences that take place between internal users; you can also archive sessions that take place between internal users and federated partners.  <br/> |
|Set-CsArchivingServer  <br/> |Enables you to specify a new database location for one or more Archiving Servers.  <br/> |
   

