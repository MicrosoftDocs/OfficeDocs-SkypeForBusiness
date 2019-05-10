---
title: 'Lync Server 2013: Reset the global policy for external user access'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Reset the global policy for external user access
ms:assetid: 8207e1b1-de9e-461f-975f-fcc5c526849a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182545(v=OCS.15)
ms:contentKeyID: 48184675
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Reset the global policy for external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

You cannot completely delete a global policy. Using the **Delete** option on the global policy only resets the global policy to the default settings, which do not include support for any external user access options.

<div>

## To reset the global policy to the default settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **External User Access**, click **External Access Policy**.

4.  On the **External Access Policy** tab, click the global policy, click **Edit**, and then click **Delete**.

5.  When prompted to confirm the deletion, click **OK**. A message appears at the top of the page informing you that the global policy has been reset.

</div>

<div>

## Resetting the Global External Access Policy by Using Windows PowerShell Cmdlets

The global external access policy can be reset by using Windows PowerShell and the Remove-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To reset the global external access policy

  - This command resets the global external access policy:
    
        Remove-CsExternalAccessPolicy -Identity "global"

</div>

For more information, see the help topic for the [Remove-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsExternalAccessPolicy) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

