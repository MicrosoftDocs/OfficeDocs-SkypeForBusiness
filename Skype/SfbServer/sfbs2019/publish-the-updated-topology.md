---
title: "Publish the updated topology in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 59455dd1-6a9e-433f-a714-d3636c068100
description: "After updating your topology in Topology Builder, you must publish the topology to the Central Management store before you can configure and use Persistent Chat Server. Read-only copies of the data are replicated to all servers in the topology to keep all servers in sync with topology and other configuration changes."
---

# Publish the updated topology in Lync Server 2013
[]
After updating your topology in Topology Builder, you must publish the topology to the Central Management store before you can configure and use Persistent Chat Server. Read-only copies of the data are replicated to all servers in the topology to keep all servers in sync with topology and other configuration changes.
  
## To publish an updated topology

Before you publish your topology, install the databases for Persistent Chat Server. Use Topology Builder to install databases by selecting **Action** and **Install Database**.
  
1. On a computer that is running Lync Server 2013 or on which the Lync Server administrative tools are installed, log on using an account that is a member of both the **Domain Admins** group and the **RTCUniversalServerAdmins** group, and that has full control permissions (that is, read, write, and modify) on the file store to be used for the Persistent Chat Server file store (so that Topology Builder can configure the required discretionary access control lists (DACLs)), or an account with equivalent user rights. 
    
2. Start Topology Builder. Select **Download Topology from existing deployment**, or **Open Topology from a local file** if you saved it locally. 
    
3. In the console tree, right-click **Lync Server 2013**, and then click **Publish Topology**.
    
4. On the **Publish the topology** page, click **Next**.
    
5. On the **Publishing wizard complete** page, verify that the topology was successfully published, and then click **Finish**.
    
    > [!IMPORTANT]
    > After publishing the topology, you must configure support for Persistent Chat Server before any content can be archived. 
  

