---
title: Manage archiving policies in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 75ce32ba-eb82-4339-9c02-5df5f2c2ebd2
---


# Manage archiving policies in Skype for Business Server 2015
[] **Summary:** Learn how to manage user policies for archiving for Skype for Business Server 2015.
You initially set up archiving policies when you deploy archiving, but you can change, add, and delete configurations after deployment. Archiving policies determine whether to archive: 
  
    
    


- Internal communications
    
  
- External communications
    
  

Archiving policies can be set at the global, site, or user level.
  
    
    


> [!NOTE]
> If you enabled Microsoft Exchange integration for your deployment, Exchange policies control whether archiving is enabled for the users who are homed on Exchange and have their mailboxes put on In-Place Hold. For details, see  [Plan for archiving in Skype for Business Server 2015](plan-for-archiving-in-skype-for-business-server-2015.md) and [Configure integration with Exchange storage for Skype for Business Server 2015](configure-integration-with-exchange-storage-for-skype-for-business-server-2015.md). 
  
    
    


## Manage archiving policies by using the Control Panel

You can manage archiving policies by using the Control Panel as follows:
  
    
    

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
  
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
  
3. In the left navigation bar, click **Archiving Policy**
    
  

## Manage archiving policies by using Windows PowerShell

You can also configure archiving policies by using the Windows PowerShell cmdlets listed in the following table. For details about syntax, including all available parameters, see  [Skype for Business Server 2015 Management Shell](skype-for-business-server-2015-management-shell.md).
  
    
    

|
|
|**Cmdlet**|**Description**|
|:-----|:-----|
|Get-CsArchivingPolicy  <br/> |Returns information about your organization's instant messaging (IM) sessions archiving policies.  <br/> |
|Grant-CsArchivingPolicy  <br/> |Assigns instant messaging (IM) session archiving policies to users or sets of users. These policies give you the ability to archive all IM sessions that take place between internal users, and/or to archive all IM sessions that take place between internal users and external partners.  <br/> |
|New-CsArchivingPolicy  <br/> |Creates new instant messaging (IM) session archiving policies. These policies give you the ability to archive all IM sessions that take place between internal users, and/or to archive all IM sessions that take place between internal users and external partners.  <br/> |
|Remove-CsArchivingPolicy  <br/> |Removes the specified instant messaging (IM) archiving policy that determines whether Skype for Business Server will automatically save all IM sessions that take place between internal users, and/or all IM sessions between internal users and federated partners.  <br/> |
|Set-CsArchivingPolicy  <br/> |Modifies an existing instant messaging (IM) archiving policy. An archiving policy gives you the ability to archive all IM sessions and conferences that take place between internal users; you can also archive sessions that take place between internal users and federated partners.  <br/> |
   

