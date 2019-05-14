---
title: 'Lync Server 2013: Return A/V Edge Server configuration information'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Return A/V Edge Server configuration information
ms:assetid: b041f5a4-2387-4075-846c-ec4f99640903
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721850(v=OCS.15)
ms:contentKeyID: 49733783
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Return A/V Edge Server configuration information in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server).

To return information about the A/V Edge configuration settings in use in your organization, you must use Windows PowerShell and the Get-CsAVEdgeConfiguration cmdlet. For more information, see the help topic for the [Get-CsAVEdgeConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsAVEdgeConfiguration) cmdlet.

Information returned from the Get-CsAVEdgeConfiguration cmdlet will look similar to this:

    Identity              : Global
    MaxTokenLifetime      : 08:00:00
    MaxBandwidthPerUserKb : 10000
    MaxBandwidthPerPortKb : 3000

<div>

## To return information for all your A/V Edge configuration settings

  - The following command returns information about all the A/V Edge configuration settings currently in use in your organization:
    
        Get-CsAVEdgeConfiguration

</div>

<div>

## To return information for site-scoped A/V Edge configuration settings

  - To return information about a specific collection of A/V Edge configuration settings, specify the Identity of that collection when running the Get-CsAVEdgeConfiguration cmdlet. For example, this command returns information only for the settings applied to the Redmond site:
    
        Get-CsAVEdgeConfiguration -Identity "site:Redmond"

</div>

<div>

## To return information for service-scoped A/V Edge configuration settings

  - And this command returns information only for settings applied the a specific A/V Edge server:
    
        Get-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"

</div>

<div>

## See Also


[Create or modify a collection of A/V Edge Server configuration settings in Lync Server 2013](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)  
[Delete an existing collection of A/V Edge Server configuration settings in Lync Server 2013](lync-server-2013-delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)  


[Audio/Video (A/V) Edge Servers in Lync Server 2013](lync-server-2013-audio-video-a-v-edge-servers.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

