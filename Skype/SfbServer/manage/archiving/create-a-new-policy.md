---
title: "Create a new archiving policy in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 50c39731-ba2f-49c2-a571-6dc373f6aaeb
description: "Summary: Learn how to create a new archiving policy for Skype for Business Server."
---

# Create a new archiving policy in Skype for Business Server

**Summary:** Learn how to create a new archiving policy for Skype for Business Server.
  
You can create new archiving policies by using the Control Panel or by using Windows PowerShell cmdlets.
  
## Create a new archiving policy by using the Control Panel

To create a new archiving policy by using the Control Panel:
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. Click **New**, and then do one of the following: 
    
   - To create a site-level archiving policy, click **Site policy**, and then, in **Select a site**, click the site to which the policy is to be applied.
    
   - To create a user-level archiving policy, click **User policy**.
    
5. In **New Archiving Policy**, do the following:
    
   - In **Name**, specify a name for the new policy (for example, externalContoso).
    
   - In **Description**, provide details about what the policy is (for example, External user archiving policy for Contoso).
    
   - To control archiving of communications with internal users, select or clear the **Archive internal communications** check box.
    
   - To control archiving of communications with external users, select or clear the **Archive external communications** check box.
    
6. Click **Commit**.
    
    > [!IMPORTANT]
    > The settings of a user policy only apply to the specific users and user groups to which you apply the policy. For details, see [Apply an archiving policy to users in Skype for Business Server](apply-a-policy-to-users.md). 
  
## Create a new archiving policy by using Windows PowerShell

You can also create new archiving policies by using the Windows PowerShell **New-CsArchivingPolicy** cmdlet. For more information, see the help topic for the [New-CsArchivingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csarchivingpolicy?view=skype-ps) cmdlet.
  
### To create a new archiving policy at the site level

This command creates a new archiving policy for the Redmond site:
  
```
New-CsArchivingPolicy -Identity "site:Redmond"
```

### To create a new archiving policy at the per-user level

To create a new archiving policy at the per-user level, simply specify a unique Identity when creating the policy:
  
```
New-CsArchivingPolicy -Identity "RedmondArchivingPolicy"
```

### To create a new archiving policy that enables archiving of internal communication sessions

Because no parameters (other than the mandatory Identity parameter) were specified in the preceding commands, the new policies will use the default values for all their properties. To create policies that use different property values, simply include the appropriate parameter and parameter value. For example, the following command creates an archiving policy that permits archiving of internal instant messaging sessions: 
  
```
New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True
```

### To create a new archiving policy that enables archiving of both internal and external communication sessions

Multiple property values can be modified by including multiple parameters. For example, this command configures the new policy to archive both internal and external instant messaging sessions:
  
```
New-CsArchivingPolicy -Identity "site:Redmond" -ArchiveInternal $True -ArchiveExternal $True
```
