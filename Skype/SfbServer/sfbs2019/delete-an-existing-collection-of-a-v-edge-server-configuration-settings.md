---
title: "Delete an existing collection of A/V Edge Server configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 668d3613-e464-4b68-967a-cfff90b9ce4b
description: "The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server)."
---

# Delete an existing collection of A/V Edge Server configuration settings in Lync Server 2013
[]
The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server).
  
When you install Lync Server, a global collection of A/V Edge configuration settings is created for you. This global collection cannot be deleted. However, you can use the Windows PowerShell and the Remove-CsAVEdgeConfiguration cmdlet to "reset" the global collection; that simply means that all the property values in the global collection will be reset to their default value. For example, if you have set the MaxTokenLifetime property for 16 hours, that property will be reset to its default value of 8 hours.
  
However, custom settings collections that you have created at either the site scope or the service scope can be deleted by using the Remove-CsAVEdgeConfiguration cmdlet. If you delete site settings then A/V Edge servers in that site will be managed by the global settings. If you delete service-scope settings,, that server will then be managed by its site settings, if they exist, or by the global settings if no site settings are available.
  
For more information, see the help topic for the [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md) cmdlet. 
  
### To reset the global collection

- The following command resets the global collection of A/V Edge configuration settings:
    
  ```
  Remove-CsAVEdgeConfiguration -Identity "global"
  ```

### To remove a collection from the site scope

- This command removes the A/V Edge configuration settings applied to the Redmond site:
    
  ```
  Remove-CsAVEdgeConfiguration -Identity "site:Redmond"
  ```

### To remove a collection from the service scope

- This command removes the settings applied to the A/V Edge server atl-edge-001.litwareinc.com:
    
  ```
  Remove-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"
  ```

## See also

#### 

[Return A/V Edge Server configuration information in Lync Server 2013](return-a-v-edge-server-configuration-information.md)
  
[Create or modify a collection of A/V Edge Server configuration settings in Lync Server 2013](create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)
#### 

[Audio/Video (A/V) Edge Servers in Lync Server 2013](audio-video-a-v-edge-servers.md)
  
[Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

