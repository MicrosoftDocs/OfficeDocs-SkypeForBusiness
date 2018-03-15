---
title: "Define a PSTN gateway for a branch site in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 87be2fe2-1d56-4062-b430-439d4536414c
description: "Perform this procedure at the central site, which contains at least one Front End pool or Standard Edition server."
---

# Define a PSTN gateway for a branch site in Lync Server 2013
[]
Perform this procedure at the central site, which contains at least one Front End pool or Standard Edition server.
  
> [!IMPORTANT]
>  Before you perform the procedure, the following conditions must be in place: >  Lync Server 2013 communications software must be set up at the central site. >  Mediation Server must be deployed at the central site. 
  
### To define a PSTN gateway

1. Click **Start**, click **All Programs**, click **Microsoft Lync Server**, and then click **Lync Server Topology Builder**.
    
2. In the console tree, expand the central site, expand **Branch Office Sites**, expand name of the branch site that you want to define a public switched telephone network (PSTN) gateway for, and then expand **Shared Components**.
    
3. Right-click **PSTN gateways**, and then click **New IP/PSTN Gateway**.
    
4. In the **Define New IP/PSTN Gateway** dialog box, click **Gateway FQDN or IP Address**, and then type the fully qualified domain name (FQDN) or IP address of the gateway that you are deploying at the branch site.
    
5. Click **Listening Port for IP/PSTN Gateway**, and then accept the default values.
    
6. In the **SIP Transport Protocol** list, click the transport protocol the gateway uses, and then click **OK**.
    
    > [!NOTE]
    > For security reasons, we strongly recommend that you use a PSTN gateway that supports Transport Layer Security (TLS). 
  
> [!TIP]
> Use the cmdlet **Set-CsPstnGateway** to modify properties of a PSTN gateway. For details, see [Set-CsPstnGateway](set-cspstngateway.md), in the Lync Server Management Shell Help. 
  
 **Next step** for branch-site resiliency: [Configuring users for branch site resiliency in Lync Server 2013](configuring-users-for-branch-site-resiliency.md)
## See also

#### 

[PSTN gateway deployment options in Lync Server 2013](pstn-gateway-deployment-options.md)

