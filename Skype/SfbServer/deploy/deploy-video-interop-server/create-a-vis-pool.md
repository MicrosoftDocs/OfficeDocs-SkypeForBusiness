---
title: "Create a VIS pool in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: abd8c4f7-057f-4360-8e3e-ec29b58f16a8
description: "Summary: Create a Video Interop Server pool in Skype for Business Server using Topology Builder."
---

# Create a VIS pool in Skype for Business Server
 
**Summary:** Create a Video Interop Server pool in Skype for Business Server using Topology Builder.
  
### Create a VIS or VIS pool using Topology Builder

1. Open Topology Builder on the front end server. From the left pane of Topology Builder, right click on **Video Interop Server Pools** and choose **New Video Interop Server Pool**. 
    
2. This will open up a **Create a new Video Interop Server Pool** wizard. Provide the Pool FQDN for the new Video Interop Server and select either **This pool has one server** or **This pool has multiple servers** based on your requirement, then press **Next**.
    
    If you want to deploy a Video Interop Server pool to provide high availability, select **This pool has multiple servers**. Keep in mind with this option that: 
    
    - You must deploy DNS load balancing to support Video Interop Server pools. 
    
   - On the next page, for the **Define the computers in this pool** item, enter the **Computer FQDN** of each server in the pool into the text field, and then click **Add**. Repeat this step to add another Video Interop Server to the pool. When you have defined all the computers in the pool, press **Next**.
    
     If you want to deploy only one Video Interop Server in the pool because you do not require high availability, then select **This pool has one server** and press **Next**.
    
3. Select the next hop pool/FE from the drop-down list and press **Next**.
    
4. Select an Edge Pool to associate with the VIS and press **Finish**.
    
5. Set a TCP or TLS port.
    
    Select the newly added Video Interop Server from the left pane of Topology Builder, right click it and choose **Edit Properties**. Enable or Update the TCP or TLS port per your requirement and choose **OK**. Although by default TLS is added, only TCP has been fully tested with Cisco Unified Communications Manager (CallManager, or CUCM).
    
6. Add a video gateway. To do this, Expand Shared Components, right click on **Video Gateways** and select **New Video Gateway**.
    
7. Provide the video gateway FQDN or IP address. The video gateway could be in a subdomain or a different domain. The CUCM used by your system's VTCs serves as a video gateway.
    
8. Select either IPv4 or IPv6 as appropriate. You can use all configured IP addresses or limit service usage to selected IP addresses.
    
9. Select the listening port of the video gateway. Select the Transport protocol (TCP or TLS) and associate it with a Video Interop Server which is set up for a video SIP trunk. The Transport Protocol for the video gateway should match the Transport Protocol configured for the VIS.
    
10. A corresponding SIP Video trunk is added after the above step is completed. Right click on the SIP Video Trunk, and select the trunk that was just added. The video SIP Trunk name, associated Video Interop Server, SIP Transport protocol and port can all be changed. 
    
    > [!NOTE]
    >  A Video Interop Server supports 1:N trunks. Hence multiple trunks can be added, which are associated with a single Video Interop Server, where each trunk terminates on a different Video Gateway. The limitation is that a particular Video Gateway has one and only one trunk that can be defined to the Skype for Business Server deployment.
  
11. Publish the Topology Document as described in [Create and publish new topology in Skype for Business Server 2015](../../deploy/install/create-and-publish-new-topology.md).
    
    > [!NOTE]
    > To improve resiliency, you may want to configure a second Video Interop Server or VIS pool, or a backup Front End pool. See [Resiliency mechanisms](../../plan-your-deployment/video-interop-server.md#resiliency) for more information.
  
All tasks performed using Topology Builder should now be complete. Proceed to installing the software on the new VIS server or servers.
## See also

[Deploy the VIS server role in Skype for Business Server](deploy-the-vis-server-role.md)

[Plan for Video Interop Server in Skype for Business Server](../../plan-your-deployment/video-interop-server.md)
  
[Create and publish new topology in Skype for Business Server 2015](../../deploy/install/create-and-publish-new-topology.md)
