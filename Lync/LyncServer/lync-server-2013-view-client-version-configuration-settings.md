---
title: 'Lync Server 2013: View client version configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: View client version configuration settings
ms:assetid: c72df4e6-a889-4cb6-86f7-8334d7774c6e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ923062(v=OCS.15)
ms:contentKeyID: 50675353
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View client version configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Client version configuration settings are used to turn client version control on or off. The global client version configuration installs with Lync Server 2013 and is used to enable or disable client version control for the entire server deployment. When the Global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can view client version configuration settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.

<div>


> [!NOTE]  
> Because anonymous users are not associated with a user, site, or service, anonymous users are affected by global-level policies only.



</div>

<div>

## To view client version configuration settings by using Lync Server Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Clients**, and then click the **Client Version Configuration** navigation button.

4.  Double-click the name of the client version configuration you want to view.

</div>

<div>

## Viewing Client Version Configuration Settings by Using Windows PowerShell Cmdlets

You can view client version configuration settings by using the **Get-CsClientVersionConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To view client version configuration information

  - To view information about all your client version configuration settings, type the following command in the Lync Server Management Shell and then press ENTER:
    
        Get-CsClientVersionConfiguration
    
    That will return information similar to this:
    
        Identity      : Global
        DefaultAction : Allow
        DefaultURL    :
        Enabled       : True

</div>

For details, see the Help topic for the [Get-CsClientVersionConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsClientVersionConfiguration) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

