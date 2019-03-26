---
title: "Modify meeting configuration settings in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 11d1f9ac-0029-429b-be2b-d7591abfc192
description: "Summary: Learn how to modify meeting configuration settings in Skype for Business Server."
---

# Modify meeting configuration settings in Skype for Business Server
 
**Summary:** Learn how to modify meeting configuration settings in Skype for Business Server.
  
You can modify meeting configuration settings by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
## Modify meeting configuration settings by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Meeting Configuration**.
    
4. In the list of meeting configurations, click the configuration that you want to change, click **Edit**, and then click **Show details**.
    
5. In **Edit Meeting Configuration**, modify any of the configuration settings, except for the configuration name, which cannot be modified.
    
6. Click **Commit**.
    
## Modify meeting configuration settings by using Skype for Business Server Management Shell

To modify meeting configuration settings, use the **Set-CsMeetingConfiguration** cmdlet.
  
The command shown in the following example modifies the meeting configuration settings assigned to the Redmond site (-Identity site:Redmond). In this case, the value of the DesignateAsPresenter property is set to Everyone:
  
```
Set-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone"
```

For more information, including a complete list of parameters, see [Set-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csmeetingconfiguration?view=skype-ps).
  

