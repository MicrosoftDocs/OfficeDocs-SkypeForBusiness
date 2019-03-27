---
title: 'Lync Server 2013: Configuring voice routes for outbound calls'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring voice routes for outbound calls
ms:assetid: 3c182cdd-7a4a-4a9d-bdac-4199f0abd947
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425890(v=OCS.15)
ms:contentKeyID: 48183875
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring voice routes for outbound calls in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

A Lync Server 2013 voice route associates destination phone numbers with one or more public switched telephone network (PSTN) gateways or SIP trunks and one or more PSTN usage records.

**To view voice routes by using Lync Server Control Panel**

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Click **Voice Routing**.

3.  Click **Route**.

4.  Double-click a voice route to view additional properties from the list of voice routes, or select the route and click **Edit**. Then click **Show details**.
    
    <div>
    

    > [!NOTE]  
    > You can only view detailed information for a single route at a time.

    
    </div>

**To view voice routes by using Windows PowerShell**

  - Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**. Voice routes can be viewed by using Windows PowerShell and the **Get-CsVoiceRoute** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    To view information about all of your voice routes, type the following command in the Lync Server Management Shell, and then press ENTER:
    
        Get-CsVoiceRoute
    
    That will return information similar to this:
    
        Identity          : global
        Priority          : -1
        Description       :
        NumberPattern     : ^(\+1[0-9]{10})$
        PstnUsages        : {}
        PstnGatewayList   : {}
        Name              : global
        SuppressCallerId  :
        AlternateCallerId :

<div>


> [!NOTE]  
> For details, see <A href="lync-server-2013-voice-routes.md">Voice routes in Lync Server 2013</A> in the Planning documentation.



</div>

<div>

## In This Section

  - [Create a voice route in Lync Server 2013](lync-server-2013-create-a-voice-route.md)

  - [Modify a voice route in Lync Server 2013](lync-server-2013-modify-a-voice-route.md)

</div>

<div>

## See Also


[Managing voice routing in Lync Server 2013](lync-server-2013-managing-voice-routing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

