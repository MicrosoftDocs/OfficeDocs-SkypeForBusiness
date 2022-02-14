---
title: "Delete an archiving configuration in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: fed12cb5-2c80-476a-af3b-d55b450c5fbc
description: "Summary: Learn how to delete an archiving configuration in Skype for Business Server."
---

# Delete an archiving configuration in Skype for Business Server

**Summary:** Learn how to delete an archiving configuration in Skype for Business Server.
  
You can delete a site configuration or pool configuration, but you cannot delete the global configuration. If you delete the global configuration, it is automatically reset to the default values.
  
## Delete an archiving configuration by using the Control Panel

To delete an archiving configuration by using the Control Panel:
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. In the list of archiving configurations, click the site or pool configuration that you want to delete, click **Edit**, and then click **Delete**.
    
    > [!NOTE]
    > You can also click the Global configuration, but choose this option only if you want to reset the Global configuration to the default values. 
  
5. Click **Commit**.
    
## Delete an archiving configuration by using Windows PowerShell

You can also delete an archiving configuration by using the **Remove-CsArchivingConfiguration** cmdlet.
  
For example, the following command removes the archiving configuration settings applied to the Redmond site. When a policy configured at the site scope is deleted, users previously managed by the site policy will automatically be governed by the global archiving policy instead:
  
```PowerShell
Remove-CsArchivingConfiguration -Identity "site:Redmond"
```

The following command removes all the archiving configuration settings applied to the service scope:
  
```PowerShell
Get-CsArchivingConfiguration -Filter "site:*" | Remove-CsArchivingConfiguration
```

The next command removes all the archiving configuration settings where Exchange archiving has been disabled:
  
```PowerShell
Get-CsArchivingConfiguration | Where-Object {$_.EnableExchangeArchiving -eq $False} | Remove-CsArchivingConfiguration
```

You can also use the **Remove-CsArchivingConfiguration** cmdlet to reset the global settings to default values. For example, suppose you have enabled IM session archiving at the global level; the following command will reset the value to the default of None, which will disable archiving at the global level:
  
```PowerShell
Remove-CsArchivingConfiguration -Identity global
```

For more information, see the help topic for the [Remove-CsArchivingConfiguration](/powershell/module/skype/remove-csarchivingconfiguration?view=skype-ps) cmdlet.