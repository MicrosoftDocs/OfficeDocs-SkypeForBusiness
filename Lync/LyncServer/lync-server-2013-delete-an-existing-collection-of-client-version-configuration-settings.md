---
title: 'Delete an existing collection of client version configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Delete an existing collection of client version configuration settings
ms:assetid: 70bf1216-d0d2-45ce-881f-b8edadf3cec7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ898480(v=OCS.15)
ms:contentKeyID: 50873760
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete an existing collection of client version configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

If you want to remove the client configuration settings that have been previously configured for a site, you can remove the settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.

<div>

## To remove client configuration settings by using Lync Server Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Clients**, and then click the **Client Version Configuration** navigation button.

4.  Select the site, click **Edit**, click **Delete**, and then click **OK**.

</div>

<div>

## Removing Client Version Configuration Settings by Using Windows PowerShell Cmdlets

You can delete client version configuration settings by using the **Remove-CsClientVersionConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To remove a specified collection of client version configuration settings

  - The following command removes the client version configuration settings applied to the Redmond site:
    
        Remove-CsClientVersionConfiguration -Identity "site:Redmond"

</div>

<div>

## To remove all the client version configuration settings applied to the site scope

  - This command removes all the client version configuration settings configured at the site scope:
    
        Get-CsClientVersionConfiguration -Filter site:* | Remove-CsClientVersionConfiguration

</div>

<div>

## To remove all the client version configuration settings based on the value of the DefaultAction property

  - And this command removes all the client version configuration settings where the default action has been set to "Block":
    
        Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block" | Remove-CsClientVersionConfiguration

</div>

For details, see the Help topic for the [Remove-CsClientVersionConfiguration](https://technet.microsoft.com/en-us/library/Gg425925(v=OCS.15)) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

