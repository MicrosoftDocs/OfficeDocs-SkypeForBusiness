---
title: 'Lync Server 2013: Define additional trunks in Topology Builder'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Define additional trunks in Topology Builder
ms:assetid: e68b8377-50a2-452a-bf5c-910929e34236
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721915(v=OCS.15)
ms:contentKeyID: 49733849
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Define additional trunks in Topology Builder in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-04_

Follow these steps to use Topology Builder to define an additional trunk to which you can associate a *peer* with a Mediation Server. A peer provides users enabled for Enterprise Voice with connectivity to the public switched telephone network (PSTN). A peer can be a PSTN gateway, an IP-PBX, or a Session Border Controller (SBC) for an Internet Telephony Service Provider (ITSP). The trunk defines this connection between the Mediation Server and peer. Multiple trunks can be defined per Mediation Server. A Mediation Server can be associated with multiple peers.

A trunk is a logical connection between a Mediation Server and a gateway uniquely identified by the tuple:

{Mediation Server FQDN, Mediation Server listening port (TLS or TCP) : gateway IP and FQDN, gateway listening port}

<div>


> [!NOTE]  
> This topic assumes that you have setup a PSTN gateway and root trunk with at least one collocated or stand-alone Mediation Server or pool as described in <A href="lync-server-2013-define-a-gateway-in-topology-builder.md">Define a gateway in Topology Builder in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>


> [!NOTE]  
> This topic assumes that you have set up at least one Front End pool or Standard Edition server in at least one central site, as described in <A href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Define and configure a Front End pool or Standard Edition server in Lync Server 2013</A> and <A href="lync-server-2013-publish-the-topology.md">Publish the topology in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## To Define an additional Trunk between a Mediation Server and a Gateway Peer

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  Under Lync Server 2013, your site name, **Shared Components**, right-click the **Trunks** node, and then click **New Trunk**.
    
    ![Lync Server Topology Builder file structure screen](images/JJ721915.90d5b349-aa1e-407a-87ed-fa112f478560(OCS.15).png "Lync Server Topology Builder file structure screen")

3.  In **Define New Trunk**, specify a friendly name to uniquely identify the trunk. You cannot have two trunks with the same name.
    
    <div>
    

    > [!NOTE]  
    > If you specify Transport Layer Security (TLS) as the transport type, you must specify the FQDN instead of the IP address of the peer of the Mediation Server.

    
    </div>

4.  Under **Associated PSTN gateway**, select the PSTN gateway peer to associate with this trunk.
    
    ![Property settings for PSTN gateway peer for trunk](images/JJ721915.7c3fe8ee-8f4c-4413-8462-8347228e61bb(OCS.15).png "Property settings for PSTN gateway peer for trunk")

5.  Under **Listening Port for PSTN gateway**, type the listening port that the peer (PSTN gateway, IP-PBX, or SBC) will receive SIP messages from the Mediation Server that is to be associated with this trunk. The default peer ports are 5066 for Transmission Control Protocol (TCP) and 5067 for Transport Layer Security (TLS). The default Survivable Branch Appliance ports are 5081 for TCP and 5082 for TLS.

6.  Under **SIP Transport Protocol**, click the transport type that the peer uses.
    
    <div>
    

    > [!NOTE]  
    > For security reasons, we strongly recommend that you deploy a peer to the Mediation Server that can use TLS.

    
    </div>

7.  Under **Associated Mediation Server**, select the Mediation Server pool to associate with the root trunk of this peer

8.  Under **Associated Mediation Server port**, type the listening port that the Mediation Server will receive SIP messages from the peer.
    
    <div>
    

    > [!NOTE]  
    > With multiple trunk support in Lync Server 2013, two trunks with different trunk names cannot be configured with the same <STRONG>Associated Mediation Server port</STRONG> and <STRONG>Listening Port for IP/PSTN gateway</STRONG>

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > With multiple trunk support in Lync Server 2013, multiple SIP signaling ports can be defined on the Mediation Server for communication with multiple peers. When defining a trunk, the <STRONG>Associated Mediation Server port</STRONG> number must be within the range of the listening ports for the respective protocol allowed by the Mediation Server. This port range is defined under Lync Server 2013 and Mediation Server pools. Right-click the relevant Mediation Server pool, and select <STRONG>Edit Properties</STRONG>. Specify the port range in the <STRONG>Listening ports</STRONG> field.

    
    </div>

9.  Click **OK**.

</div>

<div>

## See Also


[Modify a trunk in Topology Builder in Lync Server 2013](lync-server-2013-modify-a-trunk-in-topology-builder.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

