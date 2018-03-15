---
title: "Define a SIP/CSTA gateway IP address in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ae944057-3ad6-4474-a09b-81a3d27bd50f
description: "If Lync Server will connect to the SIP/CSTA gateway that you deployed for remote call control by using a Transmission Control Protocol (TCP) connection, then you must define the IP address of the gateway in Topology Builder. This step is not necessary for gateways that support Transport Layer Security (TLS) connections. For any gateway that supports TLS connections, you can skip this procedure and continue deployment of remote call control by following the steps in Enable Lync users for remote call control in Lync Server 2013."
---

# Define a SIP/CSTA gateway IP address in Lync Server 2013
[]
If Lync Server will connect to the SIP/CSTA gateway that you deployed for remote call control by using a Transmission Control Protocol (TCP) connection, then you must define the IP address of the gateway in Topology Builder. This step is not necessary for gateways that support Transport Layer Security (TLS) connections. For any gateway that supports TLS connections, you can skip this procedure and continue deployment of remote call control by following the steps in [Enable Lync users for remote call control in Lync Server 2013](enable-lync-users-for-remote-call-control.md).
  
### To define the SIP/CSTA gateway IP address by using Topology Builder

1. Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    
2. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
3. Choose the option to download an existing topology.
    
4. Expand the **Trusted application servers** node. 
    
5. Right-click the trusted application pool that you created, as described in [Configure a trusted application entry for remote call control in Lync Server 2013](configure-a-trusted-application-entry-for-remote-call-control.md), and then click **Edit Properties**.
    
6. Clear the **Enable replication of configuration data to this pool** check box. 
    
7. Click **Limit service usage to selected IP addresses**. The default setting is **Use all configured IP addresses**.
    
8. In the **Primary IP address** text box, enter the IP address of the SIP/CSTA gateway. 
    
9. To update the topology in the Central Management store, in the console tree, click **Lync Server**, and then, from the **Actions** pane, click **Publish**.
    
## See also

#### 

[Configure a static route for remote call control in Lync Server 2013](configure-a-static-route-for-remote-call-control.md)
  
[Configure a trusted application entry for remote call control in Lync Server 2013](configure-a-trusted-application-entry-for-remote-call-control.md)

