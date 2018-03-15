---
title: "Enabling or disabling push notifications for iPhones in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8bbf531a-807f-4a8f-814a-94bfed8f97ef
description: "Push notifications, in the form of badges, icons, or alerts, can be sent to an iPhone even when the mobile application is inactive. Push notifications notify a user of events such as a new or missed IM invitation and voice mail. You can enable or disable push notifications for iPhone by using either Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# Enabling or disabling push notifications for iPhones in Lync Server 2013
[]
Push notifications, in the form of badges, icons, or alerts, can be sent to an iPhone even when the mobile application is inactive. Push notifications notify a user of events such as a new or missed IM invitation and voice mail. You can enable or disable push notifications for iPhone by using either Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
### To enable push notifications for iPhone by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Push Notification Configuration** navigation button. 
    
4. On the **Push Notification Configuration** page, click the site you want to edit, click the **Edit** menu, and then click **Show details**.
    
5. Click the **Enable Apple push notifications** checkbox. 
    
6. Click **Commit**.
    
### To disable push notifications for iPhone by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Push Notification Configuration** navigation button. 
    
4. On the **Push Notification Configuration** page, click the site you want to edit, click the **Edit** menu, and then click **Show details**.
    
5. Clear the **Enable Apple push notifications** checkbox. 
    
6. Click **Commit**.
    
## Enabling or Disabling Push Notifications to iPhone by Using Windows PowerShell Cmdlets

Push notifications to Apple iPhone can be enabled or disabled by using the **Set-CsPushNotificationConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To enable push notifications for iPhone

- To enable push notifications for iPhone set the value of the EnableApplePushNotificationService property to True ($True). For example:
    
  ```
  Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $True
  
  ```

### To disable push notifications for iPhone

- To disable push notifications for iPhone set the value of the EnableApplePushNotificationService property to False ($False). For example:
    
  ```
  Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $False
  
  ```

For more information, see the help topic for the [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet. 
  
## See also

#### 

[Configuring for push notifications in Lync Server 2013](configuring-for-push-notifications.md)

