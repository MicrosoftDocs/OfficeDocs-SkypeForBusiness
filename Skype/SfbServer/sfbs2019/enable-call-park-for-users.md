---
title: "Enable Call Park for users in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9430763f-3394-467c-9c6d-426bf761604e
description: "Users cannot park calls or retrieve parked calls until they are enabled for Call Park in voice policy."
---

# Enable Call Park for users in Lync Server 2013
[]
Users cannot park calls or retrieve parked calls until they are enabled for Call Park in voice policy.
  
> [!NOTE]
> By default, Call Park is disabled for all users. 
  
You can enable Call Park at the global scope, or at the site scope or user scope. User scope takes precedence over site scope, and site scope takes precedence over global scope. If you have multiple voice policies, review all the policies to enable Call Park, not just the global policy.
  
### To Use Lync Server Control Panel to Enable Call Park for Users

1. Log on to the computer as a member of the **RTCUniversalServerAdmins** group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing**.
    
4. Click the **Voice Policy** tab. 
    
5. Double-click an existing voice policy to open the **Edit Voice Policy** dialog box. 
    
6. Under **Calling features**, select **Enable call park**.
    
7. Click **OK** to save the voice policy 
    
### To Use Cmdlets to Enable Call Park for Users

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator administrative role.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run:
    
  ```
  Set-CsVoicePolicy -Identity <VoicePolicy> -EnableCallPark $true
  ```

    For example, to enable Call Park for the default global voice policy:
    
  ```
  Set-CsVoicePolicy -EnableCallPark $true
  ```

## See also

#### 

[Create a voice policy and configure PSTN usage records in Lync Server 2013](create-a-voice-policy-and-configure-pstn-usage-records.md)

