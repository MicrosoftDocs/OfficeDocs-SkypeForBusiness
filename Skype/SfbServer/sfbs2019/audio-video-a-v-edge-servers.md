---
title: "Audio/Video (A/V) Edge Servers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b0cc538b-77eb-47fb-be82-5ab0631c6219
description: "The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). In addition to audio and video, the A/V Edge service also provides support for such things desktop sharing and file transfer."
---

# Audio/Video (A/V) Edge Servers in Lync Server 2013
[]
The A/V Edge service provide a way for your internal users (users who are logged on to your organizational network) to share audio and video with external users (users who are not logged on to your organizational network). In addition to audio and video, the A/V Edge service also provides support for such things desktop sharing and file transfer.
  
The A/V Edge service is primarily managed by using A/V Edge configuration; these settings enable you to manage the maximum amount of bandwidth to be allocated per port and per user, and to specify the length of time that an authentication token can be used before that token must be renewed. A/V Edge configuration settings can be applied to sites or to individual A/V Edge servers. When determining which collection of settings will take priority, use the following guide:
  
- Settings configured at the service scope (that is, on an individual server) take priority over everything.
    
- Settings configured at the site scope take priority over settings configured at the global scope. However, service scope settings will also supersede site-scope settings.
    
- Settings at the global scope will be used only if there are no service settings configured on the individual server and if there are no site settings for the site where that server is located.
    
The A/V Edge service can only be managed by using Lync Server PowerShell and the CsAVEdgeConfiguration cmdlets.
  
## In this section

- [Return A/V Edge Server configuration information in Lync Server 2013](return-a-v-edge-server-configuration-information.md)
    
- [Create or modify a collection of A/V Edge Server configuration settings in Lync Server 2013](create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)
    
- [Delete an existing collection of A/V Edge Server configuration settings in Lync Server 2013](delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)
    

