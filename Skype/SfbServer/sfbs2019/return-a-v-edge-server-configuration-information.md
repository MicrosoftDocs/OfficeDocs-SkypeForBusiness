---
title: "Return A/V Edge Server configuration information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b041f5a4-2387-4075-846c-ec4f99640903
description: "The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server)."
---

# Return A/V Edge Server configuration information in Lync Server 2013
[]
The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server).
  
To return information about the A/V Edge configuration settings in use in your organization, you must use Windows PowerShell and the Get-CsAVEdgeConfiguration cmdlet. For more information, see the help topic for the [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md) cmdlet. 
  
Information returned from the Get-CsAVEdgeConfiguration cmdlet will look similar to this:
  
```
Identity              : Global
MaxTokenLifetime      : 08:00:00
MaxBandwidthPerUserKb : 10000
MaxBandwidthPerPortKb : 3000
```

### To return information for all your A/V Edge configuration settings

- The following command returns information about all the A/V Edge configuration settings currently in use in your organization:
    
  ```
  Get-CsAVEdgeConfiguration
  ```

### To return information for site-scoped A/V Edge configuration settings

- To return information about a specific collection of A/V Edge configuration settings, specify the Identity of that collection when running the Get-CsAVEdgeConfiguration cmdlet. For example, this command returns information only for the settings applied to the Redmond site:
    
  ```
  Get-CsAVEdgeConfiguration -Identity "site:Redmond"
  ```

### To return information for service-scoped A/V Edge configuration settings

- And this command returns information only for settings applied the a specific A/V Edge server:
    
  ```
  Get-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"
  ```

## See also

#### 

[Create or modify a collection of A/V Edge Server configuration settings in Lync Server 2013](create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)
  
[Delete an existing collection of A/V Edge Server configuration settings in Lync Server 2013](delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)
#### 

[Audio/Video (A/V) Edge Servers in Lync Server 2013](audio-video-a-v-edge-servers.md)

