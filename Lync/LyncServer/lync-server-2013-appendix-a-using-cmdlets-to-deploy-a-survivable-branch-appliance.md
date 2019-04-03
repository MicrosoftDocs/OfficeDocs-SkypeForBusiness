---
title: 'Lync Server 2013: Appendix A: Using cmdlets to deploy a Survivable Branch Appliance'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: 'Appendix A: Using cmdlets to deploy a Survivable Branch Appliance'
ms:assetid: 796a26cf-7ec9-453b-8757-6153a6dd86c5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398598(v=OCS.15)
ms:contentKeyID: 48184569
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Appendix A: Using cmdlets to deploy a Survivable Branch Appliance in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-07_

This topic describes how to deploy a Survivable Branch Appliance using the Lync Server Management Shell. Perform this procedure at the central site.

<div>

## To deploy a Survivable Branch Appliance remotely

1.  Follow the procedure in [Add branch sites to your topology in Lync Server 2013](lync-server-2013-add-branch-sites-to-your-topology.md) to add a new branch site.

2.  Join the branch site to the domain.

3.  Add the RTCUniversalSBATechnicians group to the local Administrators group.

4.  Restart the server, and log on to it as a member of the RTCUniversalSBATechnicians group.

5.  In the Lync Server Management Shell, type the following commands, replacing the placeholders with the correct information for your organization:
    
        Export-CsConfiguration -FileName C:\CSConfig.zip
        Import-CsConfiguration -LocalStore -FileName C:\CSConfig.zip -Verbose
        Enable-CSReplica -Verbose
        Enable-CsComputer -Verbose
        Request-CsCertificate -New -Type default -CA <YourCA> -Verbose
        Set-CsCertificate -Type Default -Thumbprint <YourCertThumbprint>
        Start-cswindowsservice -verbose

</div>

</div>

<span> </span>

</div>

</div>

</div>

