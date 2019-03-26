---
title: 'Delete an existing collection of A/V Edge Server configuration settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Delete an existing collection of A/V Edge Server configuration settings
ms:assetid: 668d3613-e464-4b68-967a-cfff90b9ce4b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688077(v=OCS.15)
ms:contentKeyID: 49733673
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete an existing collection of A/V Edge Server configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server).

When you install Lync Server, a global collection of A/V Edge configuration settings is created for you. This global collection cannot be deleted. However, you can use the Windows PowerShell and the Remove-CsAVEdgeConfiguration cmdlet to "reset" the global collection; that simply means that all the property values in the global collection will be reset to their default value. For example, if you have set the MaxTokenLifetime property for 16 hours, that property will be reset to its default value of 8 hours.

However, custom settings collections that you have created at either the site scope or the service scope can be deleted by using the Remove-CsAVEdgeConfiguration cmdlet. If you delete site settings then A/V Edge servers in that site will be managed by the global settings. If you delete service-scope settings,, that server will then be managed by its site settings, if they exist, or by the global settings if no site settings are available.

For more information, see the help topic for the [Remove-CsAVEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg398786(v=OCS.15)) cmdlet.

<div>

## To reset the global collection

  - The following command resets the global collection of A/V Edge configuration settings:
    
        Remove-CsAVEdgeConfiguration -Identity "global"

</div>

<div>

## To remove a collection from the site scope

  - This command removes the A/V Edge configuration settings applied to the Redmond site:
    
        Remove-CsAVEdgeConfiguration -Identity "site:Redmond"

</div>

<div>

## To remove a collection from the service scope

  - This command removes the settings applied to the A/V Edge server atl-edge-001.litwareinc.com:
    
        Remove-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"

</div>

<div>

## See Also


[Return A/V Edge Server configuration information in Lync Server 2013](lync-server-2013-return-a-v-edge-server-configuration-information.md)  
[Create or modify a collection of A/V Edge Server configuration settings in Lync Server 2013](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)  


[Audio/Video (A/V) Edge Servers in Lync Server 2013](lync-server-2013-audio-video-a-v-edge-servers.md)  
[Remove-CsAVEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg398786(v=OCS.15))  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

