---
title: "Deleting a location policy in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8ca9ba10-f45f-435a-b39c-519d251e9085
description: "In Lync Server 2013, you can use the location policy to apply settings that relate to Enhanced 9-1-1 (E9-1-1) functionality and to location settings for users or contacts. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (for example, 911 in the United States), whether corporate security should be automatically notified, and how the call should be routed."
---

# Deleting a location policy in Lync Server 2013
[]
In Lync Server 2013, you can use the location policy to apply settings that relate to Enhanced 9-1-1 (E9-1-1) functionality and to location settings for users or contacts. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (for example, 911 in the United States), whether corporate security should be automatically notified, and how the call should be routed.
  
You can configure location policies from the **Network Configuration** group in Lync Server 2013 Control Panel. From Lync Server Control Panel you can view, create, modify, or delete location policies. Use the following procedures delete a location policy. For details on creating or modifying location policies, see [Creating or modifying a location policy in Lync Server 2013](creating-or-modifying-a-location-policy.md).
  
### To delete a location policy

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Location Policy**.
    
4. On the **Location Policy** page, select the location policy that you want to delete. 
    
    > [!NOTE]
    > You can delete more than one location policy at a time. To do this, press CTRL and select multiple policies while holding down the CTRL key. Or, to select all policies, click **Select all** on the **Edit** menu. 
  
5. On the **Edit** menu, click **Delete**.
    
6. Click **OK**.
    
    > [!IMPORTANT]
    > You cannot delete the Global location policy. If you attempt to delete the Global policy you will receive a warning message and that policy will be reset to its default values. 
  
## See also

#### 

[Creating or modifying a location policy in Lync Server 2013](creating-or-modifying-a-location-policy.md)
  
[Viewing location policy information in Lync Server 2013](viewing-location-policy-information.md)

