---
title: "Deploy pilot Edge Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "This topic highlights configuration settings you should be aware of prior to deploying your Skype for Business Server 2019 Edge Server. The deployment and configuration processes for Skype for Business Server 2019 are very similar to Skype for Business Server 2015. This section only highlights key points you should consider as part of your pilot pool deployment. For detailed steps, see Deploying external user access in Skype for Business Server 2019 in the Deployment documentation, which describes the deployment process and also gives configuration information for external user access."
---

# Deploy pilot Edge Server

This topic highlights configuration settings you should be aware of before deploying your Skype for Business Server 2019 Edge Server. The deployment and configuration processes for Skype for Business Server 2019 are very similar to Skype for Business Server 2015. This section only highlights key points you should consider as part of your pilot pool deployment. <!-- For detailed steps, see 
 [Deploying external user access in Skype for Business Server 2019](../deployment/deploying-external-user-access/deploying-external-user-access.md) in the Deployment documentation, which describes the deployment process and also gives configuration information for external user access.  -->
  
As you navigate through the **Define New Edge Pool** wizard, review the key configuration settings shown in the following steps. Note that only a few pages of the **Define New Edge Pool** wizard are shown. 
  
### To define an Edge Pool

1. Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    
2. Navigate to the Skype for Business Server 2019 node. Right-click **Edge pools**, and click **New Edge pool**.
    
     ![Define the New Edge Pool dialog box](../media/migration_ocs_topo_edgepool_page1.JPG)
  
3. An Edge pool can be a **Multiple computer pool** or **Single computer pool**.
    
     ![Define the Edge Pool FQDN dialog box](../media/migration_ocs_topo_edgepool_page2.JPG)
  
4. On the **Select features** page, do not enable federation or XMPP federation. Federation and XMPP federation are both currently routed through the legacy Edge Server. These features will be configured in a later phase of migration. 

  
5. Continue completing the following wizard pages: **External FQDNs**, **Define the internal IP address**, and **Define the external IP address**.
    
6. On the **Define the next hop server** page, select the Director for the next hop of the legacy Edge pool. 
    
     ![Define the Next Hop dialog box](../media/migration_ocs_topo_edgepool_page7.JPG)
  
7. On the **Associate Front End or Mediation pools** page, do not associate a pool with this Edge pool at this time. External media traffic is currently routed through the legacy Edge Server. This setting will be configured in a later phase of migration. 
    
     ![Associate Front End Pools dialog box](../media/migration_ocs_topo_edgepool_page8.JPG)
  
8. Click **Finish**, and then **Publish** the topology. 
    
9. Follow the steps in the Deployment documentation to install the files on the new Edge Server, configure certificates, and start the services. 
<!-- [Install Edge Servers for Skype for Business Server 2019](../deployment/deploying-external-user-access/install-edge-servers.md) in -->
    
It's very important that you follow the guidelines in the topics in the Deployment documentation. This section merely provided some guidance on configuration settings when installing these server roles. 
<!-- [Deploying external user access in Skype for Business Server 2019](../deployment/deploying-external-user-access/deploying-external-user-access.md) -->
  
You should now have a legacy Edge Server deployed in parallel with a Skype for Business Server 2019 Edge server deployment. Verify that both deployments are running properly, services are started, and you can administer each deployment prior to moving to the next phase. 
  

