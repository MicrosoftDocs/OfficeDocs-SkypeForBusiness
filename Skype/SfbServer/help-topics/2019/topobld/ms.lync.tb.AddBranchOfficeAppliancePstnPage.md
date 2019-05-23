---
title: "Add Survivable Branch Appliance PSTN"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddBranchOfficeAppliancePstnPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7c55a43d-2589-48f9-972b-1e48a3dca52a
ROBOTS: NOINDEX, NOFOLLOW
description: "To define the public switched telephone network (PSTN) gateway for a Survivable Branch Appliance at a branch site, specify the following:"
---

# Add Survivable Branch Appliance PSTN
 
To define the public switched telephone network (PSTN) gateway for a Survivable Branch Appliance at a branch site, specify the following: 
  
- A fully qualified domain name (FQDN) or IP address for the gateway peer that the Survivable Branch Appliance or Survivable Branch Server is associated with for routing inbound and outbound PSTN calls.
    
    > [!IMPORTANT]
    > If you are defining a Survivable Branch Appliance, this is the gateway to which the Mediation Server inside the Survivable Branch Appliance will connect for PSTN connectivity. 
  
- The listening port to be used for Session Initiation Protocol (SIP) messages. By default, the ports are 5066 for Transmission Control Protocol (TCP) and 5067 for Transport Layer Security (TLS) on a gateway, private branch exchange (PBX), or Session Border Controller (SBC). On a Survivable Branch Appliance at a branch site, the default ports are 5081 for TCP and 5082 for TLS.
    
- For security reasons, we strongly recommend that you use TLS. If you are defining a Survivable Branch Appliance, refer to your Survivable Branch Appliance vendor documentation to verify that your Survivable Branch Appliance supports the TLS protocol.
    
    > [!IMPORTANT]
    > For security reasons, we strongly recommended that you deploy a gateway that can use TLS. 
  
> [!NOTE]
> If you want to add a PSTN gateway, you can set it up later, but full functionality will be limited until the PSTN gateway is defined and configured. 
  

