---
title: Move Exchange Unified Messaging Contact objects
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Move Exchange Unified Messaging Contact objects
ms:assetid: 35c7e987-41b5-4798-b617-3303f20e52e3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688022(v=OCS.15)
ms:contentKeyID: 49733612
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move Exchange Unified Messaging Contact objects

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

To migrate Auto Attendant (AA) and Subscriber Access (SA) contact objects to the new Lync Server 2013 deployment, you first move the objects from the legacy Office Communications Server 2007 R2 deployment to the new the Lync Server 2013 deployment using the **Get-CsExUmContact** and **Move-CsExUmContact** cmdlets. On the Exchange Server, you then run the **ExchUCUtil** Windows PowerShell script to do the following for the newly deployed Lync pool:

  - Add it to the Unified Messaging IP gateways.

  - Add it to the Unified Messaging hunt groups.

<div>


> [!NOTE]  
> In order to use the <STRONG>Get-CsExUmContact</STRONG> and <STRONG>Move-CsExUmContact</STRONG> cmdlets, you must be a member of the RTCUniversalUserAdmins group and have organizational unit (OU) permission to the OU where the contacts objects are stored. OU permission can be granted using the <STRONG>Grant-OUPermission</STRONG> cmdlet.



</div>

<div>

## To move contact objects by using the Lync Server Management Shell

1.  Open the Lync Server Management Shell.

2.  For each pool registered with Exchange UM (where pool1.contoso.net is a pool from the Office Communications Server 2007 R2 deployment and pool2.contoso.net is the pool from the Lync Server 2013 deployment) at the command line, type the following:
    
        Get-CsExUmContact -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsExUmContact -Target pool02.contoso.net
    
    To verify that the contact objects are moved, run the **Get-CsExumContact** cmdlet and confirm that **RegistrarPool** is now pointing to the new pool.

</div>

<div>

## To run the ExchUCUtil Windows PowerShell script

1.  Log on to the Exchange UM Server as a user with Exchange Organization Administrator privileges.

2.  Navigate to the ExchUCUtil Windows PowerShell script.
    
    In Exchange 2007, ExchUCUtil.ps1 is located at: **%Program Files%\\Microsoft\\Exchange Server\\Scripts\\ExchUCUtil.ps1**
    
    In Exchange 2010, ExchUCUtil.ps1 is located at: **%Program Files%\\Microsoft\\Exchange Server\\V14\\Scripts\\ExchUCUtil.ps1**

3.  If Exchange is deployed in a single forest, type:
    
        exchucutil.ps1
    
    Or, if Exchange is deployed in multiple forests, type:
    
        exchucutil.ps1 -Forest:" <forest FQDN>"
    
    where forest FQDN specifies the forest in which Lync Server 2013 is deployed.
    
    <div>
    

    > [!IMPORTANT]  
    > Be sure to restart the <STRONG>Lync Server Front-End</STRONG> service (rtcsrv.exe) <EM>after</EM> you run exchucutil.ps1. Otherwise, Lync Server 2013 will not detect Unified Messaging in the topology.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

