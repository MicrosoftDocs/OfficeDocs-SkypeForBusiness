---
title: "Enable or disable dial-in conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c1f7cf91-8434-42ec-b09d-7d9d01e0b357
description: "Summary: Learn how to use Control Panel or Management Shell to enable or disable dial-in conferencing in Skype for Business Server."
---

# Enable or disable dial-in conferencing in Skype for Business Server
 
**Summary:** Learn how to use Control Panel or Management Shell to enable or disable dial-in conferencing in Skype for Business Server.
  
You can enable dial-in conferencing by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
## Enable or disable dial-in conferencing by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Conferencing Policy**.
    
4. In the list of conferencing policies, select the policy for which you want to enable dial-in conferencing, click **Edit**, and then click **Show details**. 
    
5. To allow users to join meeting by dialing in, check the **Enable PSTN dial-in conferencing** check box. By default, users can dial in to meetings by using the public switched telephone network (PSTN).
    
6. Click **Commit**. 
    
## Enable or disable dial-in conferencing by using Skype for Business Server Management Shell

To enable or disable dial-in conferencing, use the **Set-CsConferencingPolicy** cmdlet with the EnableDialInConferencing parameter as follows:
  
```
Set-CsConferencingPolicy  [-EnableDialInConferencing <$true | $false>] 
```

For more information, see [Set-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csconferencingpolicy?view=skype-ps).
  

