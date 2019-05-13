---
title: "Define additional trunks in Topology Builder in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: e68b8377-50a2-452a-bf5c-910929e34236
description: "Summary: Learn how to define an additional trunk between a Mediation Server and a gateway peer in Topology Builder in Skype for Business Server."
---

# Define additional trunks in Topology Builder in Skype for Business Server
 
**Summary:** Learn how to define an additional trunk between a Mediation Server and a gateway peer in Topology Builder in Skype for Business Server.
  
Follow these steps to define an additional trunk to which you can associate a peer with a Mediation Server. A peer provides users enabled for Enterprise Voice with connectivity to the Public Switched Telephone Network (PSTN). A peer can be a PSTN gateway, an IP-PBX, or a Session Border Controller (SBC) for an Internet Telephony Service Provider (ITSP).
  
A trunk is a logical connection between a Mediation Server and a gateway.
  
> [!NOTE]
> This topic assumes that you have setup a PSTN gateway and root trunk with at least one collocated or stand-alone Mediation Server or pool as described in [Define a gateway in Topology Builder in Skype for Business Server](define-a-gateway.md) in the Deployment documentation.
  
### To define an additional trunk between a Mediation Server and a gateway peer

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Skype for Business Server 2015Topology Builder**.
    
2. Under Skype for Business Server, your site name, **Shared Components**, right-click the **Trunks** node, and then click **New Trunk**.
   1. In **Define New Trunk**, specify a friendly name to uniquely identify the trunk. You cannot have two trunks with the same name.
    
      > [!NOTE]
      > If you specify Transport Layer Security (TLS) as the transport type, you must specify the FQDN instead of the IP address of the peer of the Mediation Server. 
  
3. Under **Associated PSTN gateway**, select the PSTN gateway peer to associate with this trunk.
    5. Under **Listening Port for PSTN gateway**, type the listening port that the peer (PSTN gateway, IP-PBX, or SBC) will receive SIP messages from the Mediation Server that is to be associated with this trunk. The default peer ports are 5066 for Transmission Control Protocol (TCP) and 5067 for Transport Layer Security (TLS). The default Survivable Branch Appliance ports are 5081 for TCP and 5082 for TLS.
    
4. Under **SIP Transport Protocol**, click the transport type that the peer uses.
    
    > [!NOTE]
    > For security reasons, we strongly recommend that you deploy a peer to the Mediation Server that can use TLS. 
  
5. Under **Associated Mediation Server**, select the Mediation Server pool to associate with the root trunk of this peer
    
6. Under **Associated Mediation Server port**, type the listening port that the Mediation Server will receive SIP messages from the peer.
    
    > [!NOTE]
    > With multiple trunk support in Skype for Business Server, two trunks with different trunk names cannot be configured with the same **Associated Mediation Server port** and **Listening Port for IP/PSTN gateway**
  
    > [!NOTE]
    > With multiple trunk support in Skype for Business Server, multiple SIP signaling ports can be defined on the Mediation Server for communication with multiple peers. When defining a trunk, the **Associated Mediation Server port** number must be within the range of the listening ports for the respective protocol allowed by the Mediation Server. This port range is defined under Skype for Business Server and Mediation Server pools. Right-click the relevant Mediation Server pool, and select **Edit Properties**. Specify the port range in the **Listening ports** field.
  
7. Click **OK**. 
    

