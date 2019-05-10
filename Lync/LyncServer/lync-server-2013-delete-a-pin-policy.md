---
title: 'Lync Server 2013: Delete a PIN policy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Delete a PIN policy
ms:assetid: 7c378927-2e41-418e-9721-327021bd2e45
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521020(v=OCS.15)
ms:contentKeyID: 48184609
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete a PIN policy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Follow these steps to delete a personal identification number (PIN) policy.

<div>


> [!NOTE]  
> You cannot delete the global PIN policy.



</div>

<div>

## To delete a PIN policy in Lync Server 2013 Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Security** and then click **PIN Policy**.

4.  On the **PIN Policy** page, and in the search field, type all or part of the name of the policy you want to delete.

5.  In the list of policies, click the policy that you want, click **Edit**, and then click **Delete**.

6.  Click **OK**.

</div>

<div>

## Removing PIN Policies by Using Windows PowerShell Cmdlets

You can delete PIN policies by using Windows PowerShell and the Remove-CsPinPolicy cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To remove a specific PIN policy

  - This command removes the PIN policy with the Identity RedmondPinPolicy:
    
        Remove-CsPinPolicy -Identity "RedmondPinPolicy"

</div>

<div>

## To remove all the PIN policies applied to the site scope

  - This command removes all the PIN policies configured at the site scope:
    
        Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy

</div>

<div>

## To remove all the PIN policies that allow the use of common patterns

  - And this one removes all the PIN policies that allow the use of common patterns:G
    
        et-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True} | Remove-CsPinPolicy

</div>

For more information, see the help topic for the [Remove-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsPinPolicy) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

