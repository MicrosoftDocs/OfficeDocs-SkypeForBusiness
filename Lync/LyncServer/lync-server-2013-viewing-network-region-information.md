---
title: 'Lync Server 2013: Viewing network region information'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Viewing network region information
ms:assetid: 665740d0-a3ed-460f-8337-5ed945f90589
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688076(v=OCS.15)
ms:contentKeyID: 49733672
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Viewing network region information in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use Lync Server Control Panel to view network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. Use this topic to view existing network regions. For details about creating or modifying existing network regions, see [Creating or modifying network regions in Lync Server 2013](lync-server-2013-creating-or-modifying-network-regions.md).

<div>

## To view information about a network region with Lync Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region**.

4.  On the **Region** page, click the region you want to view.
    
    <div>
    

    > [!NOTE]  
    > You can only view one region at a time.

    
    </div>

5.  On the **Edit** menu, click **Show details**.

</div>

<div>

## Viewing Network Region Information by Using Windows PowerShell Cmdlets

You can view network region information by using Windows PowerShell and the **Get-CsNetworkRegion** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To view network region information

  - To view information about all your network regions, type the following command in the Lync Server Management Shell and then press ENTER:
    
        Get-CsNetworkRegion
    
    That will return information similar to this:
    
        Identity         : Pacific Northwest
        Description      :
        BypassID         : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        CentralSite      : Site:Redmond1
        BWAlternatePaths : {BWPolicyModality=Audio;AlternatePath=True, 
                           BWPolicyModality=Video;AlternatePath=True}
        NetworkRegionID  : Pacific Northwest

</div>

For more information, see the help topic for the [Get-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkRegionLink) cmdlet.

</div>

<div>

## See Also


[Creating or modifying network regions in Lync Server 2013](lync-server-2013-creating-or-modifying-network-regions.md)  
[Deleting existing network regions in Lync Server 2013](lync-server-2013-deleting-existing-network-regions.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

