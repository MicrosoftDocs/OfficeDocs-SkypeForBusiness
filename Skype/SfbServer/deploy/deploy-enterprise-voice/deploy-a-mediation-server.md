---
title: "Deploy a Mediation Server in Topology Builder in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 59d8f5ba-5064-4ea5-b4bf-2b9736e0fedd
description: "Summary: Learn how to define and deploy a Mediation Server in Topology Builder in Skype for Business Server."
---

# Deploy a Mediation Server in Topology Builder in Skype for Business Server
 
**Summary:** Learn how to define and deploy a Mediation Server in Topology Builder in Skype for Business Server.
  
The Enterprise Voice workload, dial-in conferencing, and advanced Enterprise Voice applications (Response Group application, Call Park application, call admission control (CAC), and so on), are available in Front End pools. The functionality of the Mediation Server is built into the Front End Server. A separate stand-alone Mediation Server is not necessary. 
  
The only exception is if you configure a SIP trunk to connect to a Session Border Controller for an Internet Telephony Service Provider. To connect your Enterprise Voice infrastructure to your SIP trunk provider, a separate Mediation Server must be deployed.
  
The connection between Skype for Business Server (either a Mediation Server collocated on a Front End pool or stand-alone Mediation Server) and a gateway is defined as a logical association called a trunk. The topics in this section describe how to define a trunk and how to deploy a stand-alone Mediation Server, if you connect to a SIP trunk.
  
## Define a Mediation Server in Topology Builder

You can add Mediation Server as a collocated role on a Front End pool, or define a separate standalone Mediation Server pool.
  
### To add a Mediation Server to a Front End pool

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Skype for Business Server 2015Topology Builder**.
    
2. In Topology Builder, in the console tree, expand the name of the site for which you want to define a Front End pool.
    
3. In the console tree, right-click the type of Front End pool you want, and then click **New Front End pool..**.
    
4. Navigate through the **Define New Front End Pool** wizard until you reach the **Select collocated server roles** page.
    
5. In **Select collocated server roles**, check the option **Collocate Mediation Server**.
    
    > [!NOTE]
    > If the type of Front End pool you selected is the Enterprise Edition, then the Mediation Server component will be installed on all the Front End Servers of that Front End pool. 
  
    > [!NOTE]
    > The **Next hop pool** used by the Mediation Server will be the Front End pool where the Mediation Server is collocated on.
  
    > [!NOTE]
    > The **Edge pool** used by the Mediation Server will be the same Edge pool associated with the Front End pool where the Mediation Server is collocated on.
  
6. Click **Make Default** to use this Front End pool to route calls to the PSTN.
    
7. Click **Finish** when you are finished associating one or more peers to the Front End pool.
    
    > [!NOTE]
    > Before you proceed to the next step in the Enterprise Voice deployment process, make sure that the Mediation Server pool (i.e. Front End pool with the Mediation Server component collocated) is using the FQDNs that you specified. 
  
8. Right-click the **Skype for Business Server 2015** node, and then click **Publish Topology**.
    
### To add a standalone Mediation Server

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Skype for Business Server 2015Topology Builder**.
    
2. In Topology Builder, in the console tree, expand the name of the site for which you want to define a Mediation Server.
    
3. In the console tree, right-click the **Mediation pools** node, and then click **Mediation Server pool**.
    
4. In **Define New Mediation Pool**, type the Mediation Server pool fully qualified domain name (FQDN).
    
5. Next, do one of the following:
    
   - If you want to deploy multiple Mediation Servers in the pool to provide high availability, then select **Multiple computer pool**.
    
     > [!NOTE]
     > You must [deploy](../../plan-your-deployment/network-requirements/load-balancing.md#BKMK_DNSLoadBalancing) to support Mediation Server pools that have multiple Mediation Servers.
  
   - If you want to deploy only one Mediation Server in the pool because you do not require high availability, then select **Single computer pool**. Skip the following step.
    
6. If you selected **Multiple computer pool** in the previous step, on the **Define the computers in this pool** item, click **Computer FQDN**, type the FQDN of each server in the pool, and then click **Add**. Repeat this step for all other Mediation Servers that you want to add to the pool. When you have defined all the computers in the pool, click **Next**.
    
7. On the **Select the next hop** page, click **Next hop pool**, click the FQDN of the Front End pool that will use this Mediation Server pool, and then click **Next**.
    
8. On the **Select an Edge Server** page, do one of the following:
    
   - If you want to provide PSTN connectivity to external users enabled for Enterprise Voice, under **Select Edge Pool used by this Mediation Server**, click the FQDN of the Edge Server pool that will use this Mediation Server pool to provide PSTN connectivity to those external users, and then click **Next**.
    
   - If you do not plan to enable external users for Enterprise Voice, or if you do not want to provide PSTN connectivity to users when they are outside the internal network, click **Next**.
    
9. Right-click the **Skype for Business Server 2015** node, and then click **Publish Topology**.
    
## Define the Mediation Server Listening Ports

Follow the steps in this topic to use Topology Builder to define the listening ports a Mediation Server or pool will accept incoming connections from a gateway peer.
  
### To Modify the Mediation Server Listening Ports

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Skype for Business Server 2015Topology Builder**.
    
2. In Topology Builder, in the console tree, expand the **Mediation pools** node, and right-click the Mediation Server previously created.
    
3. By default, the SIP listening ports on the Mediation Server are 5070 for TLS traffic from Skype for Business Server, and 5067 for TLS traffic from peers (such as gateways, PBXes, or SBCs). TCP port is disabled by default. You must enable TCP port if you have gateways that do not support TLS.
    
4. Specify the desired TLS or TCP listening port range the Mediation Server will accept incoming connections from PSTN gateways.
    
    > [!NOTE]
    > Entering a TCP port range is not required if **Enable TCP port** is not checked. This setting is optional.
  

