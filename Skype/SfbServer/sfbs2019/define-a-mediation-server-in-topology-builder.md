---
title: "Define a Mediation Server in Topology Builder in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 59d8f5ba-5064-4ea5-b4bf-2b9736e0fedd
description: "In this articleDefine Mediation Server collocated to a Front End poolDefine stand-alone Mediation ServerDefine the Mediation Server Listening Ports"
---

# Define a Mediation Server in Topology Builder in Lync Server 2013
[]
 **In this article**
  
[Define Mediation Server collocated to a Front End pool](#sectionSection0)
  
[Define stand-alone Mediation Server](#sectionSection1)
  
[Define the Mediation Server Listening Ports](#sectionSection2)
  
Follow the steps in this topic to use Topology Builder to define a stand-alone Mediation Server or a pool collocated with a Front End pool at a site for which you did not previously deploy Enterprise Voice. 
  
You can define a topology using an account that is a member of the Administrators group.
  
## Define Mediation Server collocated to a Front End pool
<a name="sectionSection0"> </a>

Follow the steps in this topic to use Topology Builder to define a Mediation Server collocated to a Front End pool in a site where Enterprise Voice has not been previously deployed.
  
### To Add a Mediation Server to a Front End pool

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. In Topology Builder, in the console tree, expand the name of the site for which you want to define a Front End pool.
    
3. In the console tree, right-click the type of Front End pool you want, and then click **New Front End pool..**.
    
4. Navigate through the **Define New Front End Pool** wizard until you reach the **Select collocated server roles** page. 
    
5. In **Select collocated server roles**, check the option **Collocate Mediation Server**.
    
    > [!NOTE]
    >  If the type of Front End pool you selected is the Enterprise Edition, then the Mediation Server component will be installed on all the Front End Servers of that Front End pool. >  The **Next hop pool** used by the Mediation Server will be the Front End pool where the Mediation Server is collocated on. >  The **Edge pool** used by the Mediation Server will be the same Edge pool associated with the Front End pool where the Mediation Server is collocated on. 
  
6. Click **Make Default** to use this Front End pool to route calls from Microsoft Office Communications Server 2007 R2 to the PSTN. 
    
7. Click **Finish** when you are finished associating one or more peers to the Front End pool. 
    
    > [!NOTE]
    > Before you proceed to the next step in the Enterprise Voice deployment process, make sure that the Mediation Server pool (i.e. Front End pool with the Mediation Server component collocated) is using the FQDNs that you specified. 
  
8. Next, follow the procedures in [Publish the topology in Lync Server 2013](publish-the-topology.md) in the Deployment Guide documentation to add the Mediation Server to your topology before proceeding to the next step of modifying the listening ports of the Mediation Server if needed. You must publish your topology each time you use Topology Builder to define or modify your topology. 
    
## Define stand-alone Mediation Server
<a name="sectionSection1"> </a>

Follow the steps in this topic to use Topology Builder to define a stand-alone Mediation Server or pool at a site where Enterprise Voice has not been previously deployed.
  
If you already deployed Mediation Servers collocated to Front End pools at this site, you can skip this section and [Install the files for Mediation Server in Lync Server 2013](install-the-files-for-mediation-server.md) before proceeding to [Configuring trunks in Lync Server 2013](configuring-trunks.md).
  
> [!NOTE]
> This section assumes that you have already setup at least one Front End pool, as described in [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](define-and-configure-a-front-end-pool-or-standard-edition-server.md) and [Publish the topology in Lync Server 2013](publish-the-topology.md) in the Deployment Guide documentation. 
  
### To Add a Mediation Server

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. In Topology Builder, in the console tree, expand the name of the site for which you want to define a Mediation Server.
    
3. In the console tree, right-click the **Mediation pools** node, and then click **Mediation Server pool**.
    
4. In **Define New Mediation Pool**, type the Mediation Server pool fully qualified domain name (FQDN).
    
5. Next, do one of the following:
    
  - If you want to deploy multiple Mediation Servers in the pool to provide high availability, then select **Multiple computer pool**.
    
    > [!NOTE]
    > You must deploy DNS load balancing to support Mediation Server pools that have multiple Mediation Servers. For details, see the Using DNS Load Balancing on Mediation Server Pools section of [DNS load balancing in Lync Server 2013](dns-load-balancing.md) in the Planning documentation. 
  
  - If you want to deploy only one Mediation Server in the pool because you do not require high availability, then select **Single computer pool**. Skip the following step.
    
6. If you selected **Multiple computer pool** in the previous step, on the **Define the computers in this pool** item, click **Computer FQDN**, type the FQDN of each server in the pool, and then click **Add**. Repeat this step for all other Mediation Servers that you want to add to the pool. When you have defined all the computers in the pool, click **Next**.
    
7. On the **Select the next hop** page, click **Next hop pool**, click the FQDN of the Front End pool that will use this Mediation Server pool, and then click **Next**.
    
8. On the **Select an Edge Server** page, do one of the following: 
    
  - If you want to provide PSTN connectivity to external users enabled for Enterprise Voice, under **Select Edge Pool used by this Mediation Server**, click the FQDN of the Edge Server pool that will use this Mediation Server pool to provide PSTN connectivity to those external users, and then click **Next**.
    
  - If you do not plan to enable external users for Enterprise Voice, or if you do not want to provide PSTN connectivity to users when they are outside the internal network, click **Next**.
    
9. Next, follow the procedures in [Publish the topology in Lync Server 2013](publish-the-topology.md) in the Deployment documentation to add the Mediation Server to the topology. You must publish your topology each time you use Topology Builder to build or modify your topology so that the data can be used to install the files for servers that are running Lync Server. Then continue to the next steps to modify the listening ports on the Mediation Server, if necessary. 
    
## Define the Mediation Server Listening Ports
<a name="sectionSection2"> </a>

Follow the steps in this topic to use Topology Builder to define the listening ports a Mediation Server or pool will accept incoming connections from a gateway peer.
  
### To Modify the Mediation Server Listening Ports

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. In Topology Builder, in the console tree, expand the **Mediation pools** node, and right-click the Mediation Server previously created. 
    
3. By default, the SIP listening ports on the Mediation Server are 5070 for TLS traffic from Lync Server, 5067 for TLS traffic from peers (gateways, PBXes, or SBCs). TCP port is disabled by default. You must enable TCP port if you have gateways that do not support TLS.
    
4. Specify the desired TLS or TCP listening port range the Mediation Server will accept incoming connections from PSTN gateways.
    
    > [!NOTE]
    > Entering a TCP port range is not required if **Enable TCP port** is not checked. This setting is optional. 
  
Next, [Define a gateway in Topology Builder in Lync Server 2013](define-a-gateway-in-topology-builder.md) and install the files on each Mediation Server in the pool by following the procedures in [Install the files for Mediation Server in Lync Server 2013](install-the-files-for-mediation-server.md).

