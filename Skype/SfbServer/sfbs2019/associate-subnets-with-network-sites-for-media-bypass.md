---
title: "Associate subnets with network sites for media bypass in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5bc632b7-1446-470f-b332-48ea0ca4d1fd
description: "Every subnet in your network must be associated with a specific network site. This is because subnet information is used to determine the network site on which an endpoint is located. When the locations of both parties in a session are known, media bypass can determine where to send media for processing."
---

# Associate subnets with network sites for media bypass in Lync Server 2013
[]
> [!NOTE]
> This topic assumes that you have configured media bypass global settings and that you have configured network region and network sites for media bypass. 
  
Every subnet in your network must be associated with a specific network site. This is because subnet information is used to determine the network site on which an endpoint is located. When the locations of both parties in a session are known, media bypass can determine where to send media for processing.
  
Media bypass does not have any special requirements for associating subnets with network sites. To create an association between the subnets and network sites in your topology, follow the procedures in [Associate a subnet with a network site in Lync Server 2013](associate-a-subnet-with-a-network-site.md).
  
## Next Steps: Create Bandwidth Policy Profiles

After you associate subnets with network sites for media bypass, you must create one or more bandwidth policy profiles that will partition subnets into those with good connectivity and those without, for the purposes of media bypass. All subnets within a network region with network sites that do not have bandwidth constraints have good connectivity, and, therefore, those subnets can use media bypass.
  
For procedures to configure bandwidth policy profiles, see [Create bandwidth policy profiles in Lync Server 2013](create-bandwidth-policy-profiles.md).
  

