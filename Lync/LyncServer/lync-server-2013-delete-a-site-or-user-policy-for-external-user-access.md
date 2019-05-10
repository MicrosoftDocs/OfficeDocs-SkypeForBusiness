---
title: 'Lync Server 2013: Delete a site or user policy for external user access'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Delete a site or user policy for external user access
ms:assetid: 6d907507-825b-4354-9c03-337a459f72de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521013(v=OCS.15)
ms:contentKeyID: 48184455
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete a site or user policy for external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

You can delete any site or user policy that is listed in Lync Server Control Panel on the **External Access Policy** page. Deleting the global policy does not actually delete it, but only resets it to the default settings, which do not include support for any external user access options. For details about resetting the global policy, see [Reset the global policy for external user access in Lync Server 2013](lync-server-2013-reset-the-global-policy-for-external-user-access.md).

<div>

## To delete a site or user policy for external user access

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Click **External User Access**, click **External Access Policy**.

4.  On the **External Access Policy** tab, click the site or user policy you want to delete, click **Edit**, and then click **Delete**.

5.  When prompted to confirm the deletion, click **OK**.

</div>

<div>

## Removing PIN Policies by Using Windows PowerShell Cmdlets

External access policies can be deleted by using Windows PowerShell and the Remove-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To remove a specific external access policy

  - This command removes the external access policy applied to the Redmond site:
    
        Remove-CsExternalAccessPolicy -Identity "site:Redmond"

</div>

<div>

## To remove all the external access policies applied to the per-user scope

  - This command removes all the external access policies configured at the per-user scope:
    
        Get-CsExternalAccessPolicy -Filter "tag:*" | Remove-CsExternalAccessPolicy

</div>

<div>

## To remove all the external access policies where outside user access is disabled

  - This command deletes all the external access policies where outside user access has been disabled:
    
        Get-CsExternalAccessPolicy | Where-Object {$_.EnableOutsideAccess -eq $False} | Remove-CsExternalAccessPolicy

</div>

For more information, see the help topic for the [Remove-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsExternalAccessPolicy) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

