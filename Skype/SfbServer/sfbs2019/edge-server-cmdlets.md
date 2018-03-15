---
title: "Edge Server cmdlets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1a5427f4-a0d1-4652-8135-91333158ffc8
description: "Edge Servers provide a way for you to extend the capabilities of Microsoft Lync Server 2013 to people who are not logged on to your internal network. For example, if you have remote users -- authenticated users who log on to Lync Server 2013 over the Internet rather than through the internal network -- you will need to set up an Edge Server that runs the Lync Server Access Edge service. Additionally, Edge Servers are required if you want to establish federation with another organization or if you want to give your users the right to communicate with people who have accounts with a public instant messaging service such as Yahoo!, AOL, or MSN."
---

# Edge Server cmdlets in Lync Server 2013
[]
Edge Servers provide a way for you to extend the capabilities of Microsoft Lync Server 2013 to people who are not logged on to your internal network. For example, if you have remote users -- authenticated users who log on to Lync Server 2013 over the Internet rather than through the internal network -- you will need to set up an Edge Server that runs the Lync Server Access Edge service. Additionally, Edge Servers are required if you want to establish federation with another organization or if you want to give your users the right to communicate with people who have accounts with a public instant messaging service such as Yahoo!, AOL, or MSN.
  
> [!IMPORTANT]
>  As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License ("PIC USL") is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see [Support for public instant messenger connectivity in Lync Server 2013](support-for-public-instant-messenger-connectivity.md). >  The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft's ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down. >  More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice. 
  
## Edge Server Cmdlets

The following is a list of cmdlets that relate directly to managing Edge Servers:
  
 **Edge Server**
  
> [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)
    
> [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)
    
> [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)
    
> [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)
    
> [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)
    
> [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)
    
> [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)
    
> [Set-CsEdgeServer](set-csedgeserver.md)
    
## See also

#### 

[Lync Server PowerShell Blog](https://go.microsoft.com/fwlink/p/?linkId=203150)

