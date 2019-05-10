---
title: "Manage archiving options in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 50399f26-58a3-4ce2-8229-32a8cafc7733
description: "Summary: Learn how to configure archiving options for Skype for Business Server."
---

# Manage archiving options in Skype for Business Server

**Summary:** Learn how to configure archiving options for Skype for Business Server.
  
You initially configure archiving at deployment, but you can change, add, and delete configurations after deployment. Archiving options determine whether to: 
  
- Enable or disable archiving
    
- Archive IM sessions
    
- Archive web conferencing sessions
    
- Block activity when archiving is not available
    
- Use Exchange integration
    
- Set up purging and exporting of data
    
You can specify configuration options at the following levels:
  
- Global-level configuration that is created by default when you deploy Skype for Business Server
    
- Optional site-level configurations that specify how archiving is implemented for a specific site
    
- Optional pool-level configurations that specify how archiving is implemented for a specific pool
    
You can delete a site configuration or pool configuration, but you cannot delete the global configuration. If you delete the global configuration, it is automatically reset to the default values. For details about how archiving configurations are implemented and the hierarchy of archiving configurations, see [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md).
  
## Configure archiving options by using the Control Panel

You can configure archiving options by using the Control Panel as follows:
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Archiving Configuration**.
    
## Configure archiving options by using Windows PowerShell

You can also configure archiving options by using the Windows PowerShell cmdlets listed in the following table. For details about syntax, including all available parameters, see [Skype for Business Server Management Shell](../management-shell.md).
  

|**Cmdlet**|**Description**|
|:-----|:-----|
|Get-CsArchivingConfiguration  <br/> |Returns information about the archiving configuration settings in your organization.  <br/> |
|New-CsArchivingConfiguration  <br/> |Creates a new set of instant messaging (IM) settings, which can be used to enable or disable the automatic saving of IM sessions, and to block any instant messages that cannot be archived.  <br/> |
|Remove-CsArchivingConfiguration  <br/> |Removes the specified collection of archiving settings that are used to enable or disable the automatic saving of instant messaging (IM) sessions, and to optionally block any instant message that cannot be archived.  <br/> |
|Set-CsArchivingConfiguration  <br/> |Modifies an existing collection of instant messaging (IM) archiving configuration options.  <br/> |
