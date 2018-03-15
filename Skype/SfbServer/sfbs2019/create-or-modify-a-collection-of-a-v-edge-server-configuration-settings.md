---
title: "Create or modify a collection of A/V Edge Server configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 43899518-59c6-4be4-8892-d6f6207bfaab
description: "The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server)."
---

# Create or modify a collection of A/V Edge Server configuration settings in Lync Server 2013
[]
The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). The A/V Edge service is primarily managed by using A/V Edge configuration settings, setting that can be configured at the site scope or at the service scope (that is, can be configured for an individual A/V Edge server).
  
When you install Lync Server, a global collection of A/V Edge configuration settings is created for you. In addition to that, you can use the Windows PowerShell and the New-CsAVEdgeConfiguration cmdlet to create new settings at the site scope or the service scope (that is, for an individual A/V Edge server). If you create new settings keep in mind that:
  
- Settings configured at the service scope (that is, on an individual server) take priority over everything.
    
- Settings configured at the site scope take priority over settings configured at the global scope. However, service scope settings will also supersede site-scope settings.
    
- Settings at the global scope will be used only if there are no service settings configured on the individual server and if there are no site settings for the site where that server is located.
    
Any of your settings can then be modified by using the Set-CsAVEdgeConfiguration cmdlet. For more information, see the help topics for the [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md) and the [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md) cmdlets. 
  
### To create new A/V Edge configuration settings at the site scope

- The following command creates a new collection of A/V Edge configuration settings for the Redmond site:
    
  ```
  New-CsAVEdgeConfiguration -Identity "site:Redmond"
  ```

### To create custom A/V Edge configuration settings at the site scope

- Because no additional parameters were included, these new settings will use the default values for the A/V Edge service. Alternatively, you can add additional parameters and parameter values to create a custom collection. For example, this command sets the MaxTokenLifetime property to 4 hours (04 hours : 00 minutes : 00 seconds):
    
  ```
  New-CsAVEdgeConfiguration -Identity "site:Redmond" -MaxTokenLifetime "04:00:00"
  ```

### To create custom A/V Edge configuration settings at the service scope

- This command creates a similar collection applied to the A/V Edge server atl-edge-001.litwareinc.com:
    
  ```
  New-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com" -MaxTokenLifetime "04:00:00"
  ```

### To modify existing A/V Edge configuration settings

- In this example, the Set-CsAVEdgeConfiguration cmdlet is used to change the maximum token lifetime for the Redmond site to 12 hours:
    
  ```
  Set-CsAVEdgeConfiguration -Identity "site:Redmond" -MaxTokenLifetime "12:00:00"
  ```

## See also

#### 

[Return A/V Edge Server configuration information in Lync Server 2013](return-a-v-edge-server-configuration-information.md)
  
[Delete an existing collection of A/V Edge Server configuration settings in Lync Server 2013](delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)
#### 

[Audio/Video (A/V) Edge Servers in Lync Server 2013](audio-video-a-v-edge-servers.md)
  
[New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)
  
[Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

