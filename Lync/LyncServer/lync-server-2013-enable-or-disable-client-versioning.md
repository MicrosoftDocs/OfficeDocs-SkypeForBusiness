---
title: 'Lync Server 2013: Enable or disable client versioning'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enable or disable client versioning
ms:assetid: 33a98cb9-a979-4bb6-afb2-512f601d7ac5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ898475(v=OCS.15)
ms:contentKeyID: 50873755
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable or disable client versioning in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Client version configuration settings are used to turn client version control on or off, either globally or for particular sites. The global client version configuration installs with Lync Server 2013 and is used to enable or disable client version control for the entire server deployment. When the global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can disable the global client version configuration if you do not want any client version control to occur. You can enable or disable client versioning from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.

<div>


> [!NOTE]  
> Because anonymous users are not associated with a user, site, or service, anonymous users are affected by global-level policies only.



</div>

<div>

## To enable or disable client versioning by using Lync Server Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Clients**, and then click the **Client Version Configuration** navigation button.

4.  Do the following:
    
      - To globally enable or disable client versioning, double-click the **Global** configuration, and then modify the settings.
    
      - To enable or disable client versioning for a particular site, click **New**, select the site, click **OK**, and then modify the settings for the site.

</div>

<div>

## Enabling or Disabling Client Versioning by Using Windows PowerShell Cmdlets

You can enable or disable client versioning by using the **Set-CsClientVersionConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To enable client versioning

  - You can enable client versioning by setting the **Enabled** property to True ($True).
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

</div>

<div>

## To disable client versioning

  - You can disable client versioning by setting the **Enabled** property to False ($False).
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

</div>

For details, see the Help topic for the [Set-CsClientVersionConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsClientVersionConfiguration) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

