---
title: "Define additional trunks in Topology Builder in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e68b8377-50a2-452a-bf5c-910929e34236
description: "Follow these steps to use Topology Builder to define an additional trunk to which you can associate a peer with a Mediation Server. A peer provides users enabled for Enterprise Voice with connectivity to the public switched telephone network (PSTN). A peer can be a PSTN gateway, an IP-PBX, or a Session Border Controller (SBC) for an Internet Telephony Service Provider (ITSP). The trunk defines this connection between the Mediation Server and peer. Multiple trunks can be defined per Mediation Server. A Mediation Server can be associated with multiple peers."
---

# Define additional trunks in Topology Builder in Lync Server 2013
[]
Follow these steps to use Topology Builder to define an additional trunk to which you can associate a peer with a Mediation Server. A peer provides users enabled for Enterprise Voice with connectivity to the public switched telephone network (PSTN). A peer can be a PSTN gateway, an IP-PBX, or a Session Border Controller (SBC) for an Internet Telephony Service Provider (ITSP). The trunk defines this connection between the Mediation Server and peer. Multiple trunks can be defined per Mediation Server. A Mediation Server can be associated with multiple peers. 
  
A trunk is a logical connection between a Mediation Server and a gateway uniquely identified by the tuple:
  
{Mediation Server FQDN, Mediation Server listening port (TLS or TCP) : gateway IP and FQDN, gateway listening port}
  
> [!NOTE]
> This topic assumes that you have setup a PSTN gateway and root trunk with at least one collocated or stand-alone Mediation Server or pool as described in [Define a gateway in Topology Builder in Lync Server 2013](define-a-gateway-in-topology-builder.md) in the Deployment documentation. 
  
> [!NOTE]
> This topic assumes that you have set up at least one Front End pool or Standard Edition server in at least one central site, as described in [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](define-and-configure-a-front-end-pool-or-standard-edition-server.md) and [Publish the topology in Lync Server 2013](publish-the-topology.md) in the Deployment documentation. 
  
### To Define an additional Trunk between a Mediation Server and a Gateway Peer

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. Under Lync Server 2013, your site name, **Shared Components**, right-click the **Trunks** node, and then click **New Trunk**.
    
     ![Lync Server Topology Builder file structure screen](media/define_trunk01.png)
  
3. In **Define New Trunk**, specify a friendly name to uniquely identify the trunk. You cannot have two trunks with the same name.
    
    > [!NOTE]
    > If you specify Transport Layer Security (TLS) as the transport type, you must specify the FQDN instead of the IP address of the peer of the Mediation Server. 
  
4. Under **Associated PSTN gateway**, select the PSTN gateway peer to associate with this trunk.
    
     ![Property settings for PSTN gateway peer for trunk](media/edit_gateway02.png)
  
5. Under **Listening Port for PSTN gateway**, type the listening port that the peer (PSTN gateway, IP-PBX, or SBC) will receive SIP messages from the Mediation Server that is to be associated with this trunk. The default peer ports are 5066 for Transmission Control Protocol (TCP) and 5067 for Transport Layer Security (TLS). The default Survivable Branch Appliance ports are 5081 for TCP and 5082 for TLS.
    
6. Under **SIP Transport Protocol**, click the transport type that the peer uses.
    
    > [!NOTE]
    > For security reasons, we strongly recommend that you deploy a peer to the Mediation Server that can use TLS. 
  
7. Under **Associated Mediation Server**, select the Mediation Server pool to associate with the root trunk of this peer
    
8. Under **Associated Mediation Server port**, type the listening port that the Mediation Server will receive SIP messages from the peer.
    
    > [!NOTE]
    > With multiple trunk support in Lync Server 2013, two trunks with different trunk names cannot be configured with the same **Associated Mediation Server port** and **Listening Port for IP/PSTN gateway**
  
    > [!NOTE]
    > With multiple trunk support in Lync Server 2013, multiple SIP signaling ports can be defined on the Mediation Server for communication with multiple peers. When defining a trunk, the **Associated Mediation Server port** number must be within the range of the listening ports for the respective protocol allowed by the Mediation Server. This port range is defined under Lync Server 2013 and Mediation Server pools. Right-click the relevant Mediation Server pool, and select **Edit Properties**. Specify the port range in the **Listening ports** field. 
  
9. Click **OK**.
    
## See also

#### 

[Modify a trunk in Topology Builder in Lync Server 2013](modify-a-trunk-in-topology-builder.md)

