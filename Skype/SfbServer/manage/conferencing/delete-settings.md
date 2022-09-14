---
title: "Delete meeting configuration settings in Skype for Business Server"
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
ms.assetid: 8ebafb86-13b9-468e-beda-f85f6786da85
description: "Summary: Learn how to delete meeting configuration settings in Skype for Business Server."
---

# Delete meeting configuration settings in Skype for Business Server
 
**Summary:** Learn how to delete meeting configuration settings in Skype for Business Server.
  
You can delete meeting configuration settings by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
You can delete a site or user configuration, but you cannot delete the global configuration. If you attempt to delete the global configuration, it is automatically reset to the default values.
  
## Delete meeting configuration settings by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Meeting Configuration**.
    
4. In the list of meeting configurations, click the site or pool configuration that you want to delete, click **Edit**, and then click **Delete**.
    
## Delete meeting configuration settings by using Skype for Business Server Management Shell

To delete meeting settings, use the **Remove-CsMeetingConfiguration** cmdlet.
  
The following command removes the meeting configuration settings applied to the Redmond site:
  
```PowerShell
Remove-CsMeetingConfiguration -Identity "site:Redmond"
```

The next command removes all the meeting configuration settings applied to the site scope:
  
```PowerShell
Get-CsMeetingConfiguration -Filter "site:*" | Remove-CsMeetingConfiguration
```

For more information, including a complete list of parameters, see [Remove-CsMeetingConfiguration](/powershell/module/skype/remove-csmeetingconfiguration?view=skype-ps).
