---
title: "Configure archiving options to handle failures in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 31fd4e7c-3c68-48dd-9fad-8863831accd7
description: "Summary: Learn how to block IM and conferencing sessions in the case of a Skype for Business Server failure that would prevent archiving."
---

# Configure archiving options to handle failures in Skype for Business Server

**Summary:** Learn how to block IM and conferencing sessions in the case of a Skype for Business Server failure that would prevent archiving.
  
If archiving is a requirement for your organization, you can block IM and conferencing sessions in the event of a Skype for Business Server failure that would prevent archiving. This is sometimes called critical mode. For example, if there is a problem with a storage service, IM would be blocked for users whose communications are enabled for archiving. Both IM and conferencing automatically recover after the failures are corrected. 
  
## Configure critical mode by using the Control Panel

To specify whether communication sessions should be allowed in case of a failure that would prevent archiving:
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. Click the name of the appropriate global, site, or pool configuration in the list of archiving configurations, click **Edit**, and then click **Show details**.
    
5. To set how archiving behaves when a failure occurs, select or clear the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
6. Click **Commit**.
    
## Configure critical mode by using Windows PowerShell

You can also specify whether communication sessions should be allowed in case of a failure that would prevent archiving by using the **Set-CsArchivingConfiguration** cmdlet with the BlockOnArchiveFailure parameter.
  
For example, the following command disables communications in the case of an archiving failure:
  
```
Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $True
```

The next command enables communications in the case of an archiving failure:
  
```
Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $False
```

For more information, see the Help topic for the [Set-CsArchivingConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csarchivingconfiguration?view=skype-ps) cmdlet.
  

