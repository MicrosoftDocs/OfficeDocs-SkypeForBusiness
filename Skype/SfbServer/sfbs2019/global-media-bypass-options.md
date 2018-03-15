---
title: "Global media bypass options in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1bd35f90-8587-48a1-b0c2-095a4053fc77
description: "In addition to enabling media bypass for individual trunk connections associated with a peer, you must also enable media bypass globally. Global media bypass settings can either specify that media bypass is always attempted for calls to the PSTN, or that media bypass is employed by using the mapping of subnets to network sites and network regions—similar to what is done by call admission control, another advanced voice feature. When media bypass and call admission control are both enabled, then the network region, network site, and subnet information that is specified for call admission control is automatically used when determining whether to employ media bypass. This means that you cannot specify that media bypass is always attempted for calls to the PSTN when call admission control is enabled."
---

# Global media bypass options in Lync Server 2013
[]
> [!NOTE]
> This topic assumes that you have already configured media bypass for any trunks to a peer (a public switched telephone network (PSTN) gateway, an IP-PBX, or a Session Border Controller (SBC) at an Internet Telephony Service Provider) for a specific site or service for which you want media to bypass the Mediation Server. 
  
In addition to enabling media bypass for individual trunk connections associated with a peer, you must also enable media bypass globally. Global media bypass settings can either specify that media bypass is always attempted for calls to the PSTN, or that media bypass is employed by using the mapping of subnets to network sites and network regions—similar to what is done by call admission control, another advanced voice feature. When media bypass and call admission control are both enabled, then the network region, network site, and subnet information that is specified for call admission control is automatically used when determining whether to employ media bypass. This means that you cannot specify that media bypass is always attempted for calls to the PSTN when call admission control is enabled.
  
This topic describes how to use Lync Server Control Panel and Lync Server Management Shell together to configure global media bypass settings.
  
> [!NOTE]
> When you use these steps to configure media bypass, the assumption is that you have good connectivity between clients and the Mediation Server peer (for example, a PSTN gateway, an IP-PBX, or an SBC at a SIP trunking provider). If there are any bandwidth limitations on the link, media bypass cannot be applied to the call. Media bypass will not interoperate with every PSTN gateway, IP-PBX, and SBC. Microsoft has tested a set of PSTN gateways and SBCs with certified partners and has done some testing with Cisco IP-PBXs. Media bypass is supported only with products and versions listed on Unified Communications Open Interoperability Program - Lync Server at [https://go.microsoft.com/fwlink/p/?linkId=214406](https://go.microsoft.com/fwlink/p/?linkId=214406). 
  
## Next Steps: Choose Global Media Bypass Settings

After you have enabled media bypass on any trunk connections to a peer for specific sites or services, use the following content to either:
  
- Enable media bypass always, as described in [Configure media bypass in Lync Server 2013 to always bypass the Mediation Server](configure-media-bypass-to-always-bypass-the-mediation-server.md).
    
- Or, configure media bypass to use site and region information, as described in [Configure media bypass global settings in Lync Server 2013 to use site and region information](configure-media-bypass-global-settings-to-use-site-and-region-information.md).
    
## See also

#### 

[Configure a trunk with media bypass in Lync Server 2013](configure-a-trunk-with-media-bypass.md)
  
[Associate a subnet with a network site in Lync Server 2013](associate-a-subnet-with-a-network-site.md)
#### 

[Configure media bypass in Lync Server 2013](configure-media-bypass.md)
  
[Media bypass and Mediation Server in Lync Server 2013](media-bypass-and-mediation-server.md)

