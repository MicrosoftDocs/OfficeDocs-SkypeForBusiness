---
title: "Interoperability considerations for video conferencing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 31ead3b5-ed95-42d4-96e2-7d9403d5c026
description: "This section describes the user experience during the coexistence phase of migration, when there is interoperability between legacy clients and a Lync Server 2013 pool or Lync Server 2013 clients and a legacy pool."
---

# Interoperability considerations for video conferencing in Lync Server 2013
[]
This section describes the user experience during the coexistence phase of migration, when there is interoperability between legacy clients and a Lync Server 2013 pool or Lync Server 2013 clients and a legacy pool.
  
## Lync Server 2013 Pools

Users will experience the following behavior when a legacy client is used in a Lync Server 2013 pool:
  
- For two-party calls, video resolution is the same as in the legacy pool.
    
- For multiparty conferences, video resolution and video conferencing features are the same as in the legacy pool. Gallery View and high resolution are not available.
    
## Legacy Pools

Users will experience the following behavior when a Lync Server 2013 client is used in a legacy pool:
  
- For two-party calls, Lync Server 2013 clients can use new features as follows:
    
  - H.264 is available if both participants are using Lync Server 2013 clients.
    
  - The Lync Server 2013 client uses the default value for TotalReceiveVideoBitRateKb, since the legacy server doesn't send this information with in-band provisioning.
    
- For multiparty conferences, video resolution and video conferencing features are the same as experienced by a legacy client in the legacy pool.
    
> [!NOTE]
> When a legacy server hosts a Lync Server 2013 client, it's possible to configure video conferencing bandwidth so that all users on the pool receive only low-resolution video, but send high-resolution video. An example of this is when MaxVideoRateAllowed is set to CIF-250K in the media configuration and VideoBitRateKb is set to 2000 kbps in conferencing policy. The net effect in this situation is that high resolution is not possible for users on the pool. > Because MaxVideoRateAllowed is no longer used for Lync Server 2013 clients, it cannot prevent Lync Server 2013 clients from requesting high-resolution video. Instead, set VideoBitRateKb in conferencing policy for all users on the pool to the same value as MaxVideoRateAllowed (that is, CIF is set to 250 kbps, or VGA is set to 600 kbps, or HD is set to 1500 kbps). 
  

