---
title: "Configure integration with Office Web Apps Server in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b7e9149e-bf16-4120-afe0-3ee09c88f5eb
description: "Summary: Read this topic to learn how to configure integration between Office Web Apps Server and Skype for Business Server to enable PowerPoint presentations for web conferencing."
---

# Configure integration with Office Web Apps Server in Skype for Business Server
 
**Summary:** Read this topic to learn how to configure integration between Office Web Apps Server and Skype for Business Server to enable PowerPoint presentations for web conferencing.
  
Skype for Business Server employs Office Web Apps Server to handle PowerPoint presentations for web conferencing. For information about the advantages to this approach, see [Plan for conferencing in Skype for Business Server](../../plan-your-deployment/conferencing/conferencing.md).
  
Before you can configure Skype for Business Server to use Office Web Apps Server, you must ensure that Office Web Apps Server is already deployed and configured. For information on Office Web Apps Server, see the article [Deploy the infrastructure: Office Online Server](https://go.microsoft.com/fwlink/p/?linkid=257525). 
  
After Office Web Apps Server has been successfully installed and your Web farm correctly configured, you must then configure Skype for Business Server to communicate with the new server by adding the Office Web Apps Server discovery URL to your Skype for Business Server topology. 
  
> [!NOTE]
> The latest iteration of Office Web Apps Server is named Office Online Server, which is supported by Skype for Business Server. For more detail, refer to the [Office Online Server documentation](https://technet.microsoft.com/en-us/library/jj219456%28v=office.16%29.aspx). 
  
## Configure Skype for Business Server to communicate with Office Web Apps Server

To add Office Web Apps Server to your topology, complete the following steps:
  
1. Open Skype for Business Server Topology Builder.
    
2. In the **Topology Builder** dialog box, select **Download Topology from existing deployment** and then click **OK**.
    
3. In the **Save Topology As** dialog box, type a name for your topology document (for example, **PreWebAppsServerTopology**) in the **File name** box and then click **Save**. This topology can later be retrieved and republished if you encounter problems with your new topology.
    
4. In Topology Builder, expand **Skype for Business Server**, expand the name of your site, expand **Enterprise Edition Front End pools**, right-click the name of one of your pools, and then click **Edit Properties**.
    
5. In the **Edit Properties** dialog box, on the **General** tab, find the heading **Associate Office Web Apps Server** and then click **New** (or select an existing Office Web Apps Server from the drop-down list).
    
6. In the **Define New Office Web Apps Server** dialog box, type the fully qualified domain name (FQDN) of your Office Web Apps Server computer in the **Office Web Apps Server FQDN** box; when you do this, your Office Web Apps Server discovery URL should automatically be entered into the **Office Web Apps Server discovery URL** box.
    
   - If the Office Web Apps Server is installed on-premises and in the same network zone as Skype for Business Server then the option **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)** should not be selected.
    
   - If the Office Web Apps Server is deployed outside your internal firewall, then select the option **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)**.
    
7. In the **Define New Office Web Apps Server** dialog box, click **OK**, and then click **OK** in the **Edit Properties** dialog box. The Office Online discovery URL will then be listed as one of the pool's Associations.
    
You will have to repeat this process for each pool that needs to be associated with your Office Web Apps Server.
  
After you have added the discovery URL to the topology, you must then publish the updated topology. To do that in Topology Builder:
  
1. Click **Action** and then click **Publish Topology**.
    
2. In the Publish Topology wizard, on the **Publish the Topology** page, click **Next**.
    
3. On the **Publishing wizard complete** page, click **Finish**.
    
4. Close Topology Builder.
    
## Configure access for external users

If you want external users (that is, users logging on from outside your organization's firewall) to have access to Office Web Apps Server PowerPoint presentations, then you will need to use Office Web Apps Server and a reverse proxy server. You will also need to create and configure a website publishing rule, which will help ensure that users are able to connect to the server. 
  
## Validate the configuration

After Office Web Apps Server has been added to the topology, and after that topology has been published, you should see two new event log events in the Skype for Business Server event log. First, an LS Data MCU event (event ID 41034) should be added; this event will report that the Office Web Apps Server has been discovered:
  
 **Web Conferencing Server Office Web Apps Server is discovered, PowerPoint content is enabled.**
  
In addition to that you should see another LS Data MCU event (event ID 41032) that reports back Office Web Apps Server URLs. For example, you should see something similar to this:
  
 **Web Conferencing Server Office Web Apps Server discovery has succeeded.**
  
 **Office Web Apps Server internal presenter page: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0&amp;embed=**
  
 **Office Web Apps Server internal attendee page: https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0&amp;embed=true&amp;=**
  
If you have configured access for external users, you will also see something similar to:
  
 **Office Web Apps Server external presenter page: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0&amp;embed**
  
 **Office Web Apps Server internal attendee page: <https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0&amp;embed=true&amp>;**
  
If you see an LS Data MCU event with the event ID of 41033 that means that Office Web Apps Server discovery has failed. In that case, Skype for Business Server will try as many times as needed to discover the newly-configured Office Web Apps Server. If the discovery process fails repeatedly you should remove Office Web Apps Server from your topology document, publish the updated topology, and then try adding Office Web Apps Server back to the topology after the connectivity issues have been resolved.
  
If Office Web Apps Server appears to be configured correctly and has been recognized by the discovery process you can verify that Office Web Apps Server is working as expected by sharing a PowerPoint presentation between a pair of Skype for Business clients. If User A can load and display the PowerPoint presentation and if User B can then join the meeting and see that presentation then Office Web Apps Server is working.
  
Even if Office Web Apps Server appears to be configured correctly, you could potentially receive the error message "Some sharing features are unavailable due to server connectivity issues" when you try sharing a PowerPoint presentation. If you receive that error message you should restart the Front End server (or servers) associated with the new Office Web Apps Server.
  

