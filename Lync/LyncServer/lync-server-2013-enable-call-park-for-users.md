---
title: 'Lync Server 2013: Enable Call Park for users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enable Call Park for users
ms:assetid: 9430763f-3394-467c-9c6d-426bf761604e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398753(v=OCS.15)
ms:contentKeyID: 48184814
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable Call Park for users in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-11_

Users cannot park calls or retrieve parked calls until they are enabled for Call Park in voice policy.

<div>


> [!NOTE]  
> By default, Call Park is disabled for all users.



</div>

You can enable Call Park at the global scope, or at the site scope or user scope. User scope takes precedence over site scope, and site scope takes precedence over global scope. If you have multiple voice policies, review all the policies to enable Call Park, not just the global policy.

<div>

## To Use Lync Server Control Panel to Enable Call Park for Users

1.  Log on to the computer as a member of the **RTCUniversalServerAdmins** group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Routing**.

4.  Click the **Voice Policy** tab.

5.  Double-click an existing voice policy to open the **Edit Voice Policy** dialog box.

6.  Under **Calling features**, select **Enable call park**.

7.  Click **OK** to save the voice policy

</div>

<div>

## To Use Cmdlets to Enable Call Park for Users

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator administrative role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run:
    
        Set-CsVoicePolicy -Identity <VoicePolicy> -EnableCallPark $true
    
    For example, to enable Call Park for the default global voice policy:
    
        Set-CsVoicePolicy -EnableCallPark $true

</div>

<div>

## See Also


[Create a voice policy and configure PSTN usage records in Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

