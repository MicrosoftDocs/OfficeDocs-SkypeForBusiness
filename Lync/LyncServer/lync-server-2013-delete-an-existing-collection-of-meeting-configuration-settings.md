---
title: 'Delete an existing collection of meeting configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Delete an existing collection of meeting configuration settings
ms:assetid: 92ff8a91-05c5-4047-a533-5dff12f22299
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688136(v=OCS.15)
ms:contentKeyID: 49733736
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete an existing collection of meeting configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

You can delete a site or user configuration. The global configuration cannot be removed. If you delete the global configuration, it is automatically reset to the default values.

<div>

## To delete a site or user meeting configuration

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Conferencing** and then click **Meeting Configuration**.

4.  In the list of meeting configurations, click the site or pool configuration that you want to delete, click **Edit**, and then click **Delete**.

</div>

<div>

## Removing Meeting Configuration Settings by Using Windows PowerShell Cmdlets

Meeting settings can be deleted by using Windows PowerShell and the Remove-CsMeetingConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To remove a specified collection of meeting configuration settings

  - This command removes the meeting configuration settings applied to the Redmond site:
    
        Remove-CsMeetingConfiguration -Identity "site:Redmond"

</div>

<div>

## To remove all the meeting configuration settings applied to the site scope

  - This command removes all the meeting configuration settings applied to the site scope:
    
        Get-CsMeetingConfiguration -Filter "site:*" | Remove-CsMeetingConfiguration

</div>

<div>

## To remove all the meeting configuration settings that admit anonymous users by default

  - And this one removes all the settings that allow anonymous users to be admitted by default:
    
        Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True} | Remove-CsMeetingConfiguration

</div>

For more information, see the help topic for the [Remove-CsMeetingConfiguration](https://technet.microsoft.com/en-us/library/Gg412775(v=OCS.15)) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

