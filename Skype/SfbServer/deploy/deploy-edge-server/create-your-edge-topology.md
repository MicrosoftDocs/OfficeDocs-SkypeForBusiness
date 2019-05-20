---
title: "Create your Edge topology for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 5ea18841-afdc-4ccb-8d86-30584c1f5aca
description: "Summary: Learn how to build, publish, and export your Edge Server topology in Skype for Business Server."
---

# Create your Edge topology for Skype for Business Server
 
**Summary:** Learn how to build, publish, and export your Edge Server topology in Skype for Business Server.
  
Topology Builder is the tool you need to use to build your Edge Server topology, just as it's used for any topology component for Skype for Business Server. Before following the steps below, you will need to have set up at least one Front End pool or a Standard Edition server.
  
We cover the following topics in this article:
  
- Build your Edge Server topology
    
- Publish your Edge Server topology
    
- Export your Edge Server topology
    
  > [!NOTE]
  > To follow the steps below, you're going to need to log into the domain servers mentioned below as a user who's a member of the following domain groups: 
  
- RTCUniversalServerAdmins
    
- Domain Admins
    
## Build your Edge Server topology

The first deployment step is building your Skype for Business Server Edge Server topology, which consists of one of three options:
  
- A single Edge Server
    
- A DNS load balanced Edge pool (one or more servers)
    
- A hardware load balanced Edge pool (one or more servers)
    
If you aren't sure what you need, then before you start following these steps, it's a good time to go over the Planning documentation. Otherwise, let's begin.
  
### Defining the topology for a single Edge Server

1. Log onto your Skype for Business Server Standard Edition server, or a Skype for Business Server Front End pool.
    
2. Once there, open **Skype for Business Server Topology Builder**.
    
3. In the console tree, expand the site you're going to deploy the Edge Server to.
    
4. Right-click **Edge pools**, and then click **New Edge pool**.
    
5. You'll click **Next** on the **Define New Edge pool** screen.
    
6. On the **Define the Edge pool FQDN** screen, type the internal fully qualified domain name (FQDN) that the Edge Server is going to use, and select **Single computer pool**, clicking **Next** when done.
    
7. On the **Select features** screen, you have a choice:
    
   - You may intend to use the same FQDN and IP address for your SIP Access service, your Skype for Business Server Web Conferencing service, and your A/V Edge service. If so, you need to choose the **Use a single FQDN and IP address checkbox** (and keep this in mind for Step 9 below)
    
   - If you're planning to enable federation, choose the **Enable federation for this Edge pool (Port 5061)** check box.
    
8. Once you've clicked **Next**, you'll find yourself on the **IP Options** screen. Your options are as follows:
    
   - Enable IPv4 on the internal interface
    
   - Enable IPv6 on the internal interface
    
   - Enable IPv4 on the external interface
    
   - Enable IPv6 on the external interface
    
   These are pretty self-explanatory, whether you're using IPv4 or IPv6 addresses, and you're applying those addresses on your Edge Server internally or externally (you'll need to keep this in mind for Step 10). You also have the option of configuring your Edge Server or your Edge pool to use a network address translation (NAT) address for the external IP address. You can do this by choosing **The external IP address of this Edge pool is translated by NAT** check box . Click **Next** when ready.
    
9. On the External FQDNs screen, your choices depend on the selection you made in Step 7 above.
    
   - If you checked the **Use a single FQDN and IP Address** check box, you need to enter your single external FQDN in the **SIP Access** box. Then you'll need to enter different port numbers for each edge service to allow them all to connect independently. We recommend 5061 for the **SIP Access** Edge service, 444 for the **Web Conferencing** Edge service, and 443 for the **A/V** Edge service. Click **Next** when done.
    
   - If you didn't check the **Use a single FQDN and IP Address** check box, you'll now need to enter the three external FQDNs for the **SIP Access** Edge service, the **Web Conferencing** Edge service, and the **A/V** Edge service. Click **Next** when done.
    
10. You're now on the **Define the Internal IP address** screen. Here you'll type the IP address of your Edge Server in the **Internal IPv4 address** and **Internal IPv6 address** text boxes, depending on the choices you made back in Step 8. Click **Next** when ready.
    
11. On the **Define the External IP address** screen, you have a few options depending on your previous choices:
    
    - You may be using a single FQDN for all services. If so, type your external IPv4 or IPv6 address (whichever you're using) into the **SIP Access** text box, and then click **Next**.
    
    - You may have chosen to use three separate FQDNs and IP addresses for the services. If that's the case, enter your external IPv4 or IPv6 addresses for the **SIP Access** Edge service, the **Web Conferencing** Edge service, and the **A/V** Edge service, and then click **Next**.
    
    > [!NOTE]
    > If you didn't previously choose to enable and assign IPv6 addressing, you won't see this dialog box. That's normal, just go to the next step. 
  
12. If you chose to use NAT back in Step 8, you'll now get a screen with a **Public IP address** textbox. You'll need to enter the public IPv4 and/or IPv6 address you've set for the A/V Edge service, to be translated by NAT. Then click **Next**.
    
13. Next screen up is **Define the next hop**. In the **Next hop pool** box, select the name of your internal pool, which might be a Front End pool or a Standalone pool. If you have a Director in your environment, you should choose the Director. Then click **Next**.
    
14. On the **Associate Front End pools** screen, you'll need to specify one or more internal pools, including Front End pools and Standard Edition servers, to associate with this Edge Server. Just choose the names of the internal pools you want using this Edge Server to communicate with supported external users. Click **Next**.
    
    > [!NOTE]
    > Something to keep in mind here is, if your internal pools or standalone servers are already using a different Skype for Business Server Edge Server, they can't have multiple associations. If you choose an internal pool or standalone server that's in that situation, you'll see a warning appear telling you about the other Edge Server, and you can decide whether you want to continue or not. If you go ahead with this new association, the connection to the other Edge Server will stop. 
  
15. Click **Finish** on the next screen.
    
16. Now you'll be able to publish this updated technology, and follow the instructions in [Deploy Edge Servers in Skype for Business Server](deploy-edge-servers.md) to deploy to your Edge Server from here.
    
### Defining the topology for a DNS load balanced Edge Server pool

1. Log onto your Skype for Business Server Standard Edition server, or a Skype for Business Server Front End Server.
    
2. Once there, open **Skype for Business Server Topology Builder**.
    
3. In the console tree, expand the site you're going to deploy the Edge Server to.
    
4. Right-click **Edge pools**, and then click **New Edge pool**.
    
5. You'll click **Next** on the **Define New Edge pool** screen.
    
6. On the **Define the Edge pool FQDN** screen, type the internal fully qualified domain name (FQDN) that the Edge pool is going to use, and select **Multiple computer pool**, clicking **Next** when done.
    
7. On the **Select features** screen, you have a choice:
    
    - You may intend to use the same FQDN and IP address for your SIP Access service, your Skype for Business Server Web Conferencing Service, and your A/V Edge service. If so, you need to choose the **Use a single FQDN and IP address checkbox** (and keep this in mind for Step 9 below)
    
    - If you're planning to enable federation, choose the **Enable federation for this Edge pool (Port 5061)** check box.
    
8. Once you've clicked **Next**, you'll find yourself on the **IP Options** screen. Your options are as follows:
    
    - Enable IPv4 on the internal interface
    
   - Enable IPv6 on the internal interface
    
   - Enable IPv4 on the external interface
    
   - Enable IPv6 on the external interface
    
     These are pretty self-explanatory, whether you're using IPv4 or IPv6 addresses, and you're applying those addresses on your Edge Server internally or externally (you'll need to keep this in mind for Step 11). You also have the option of configuring your Edge Server or your Edge pool to use a network address translation (NAT) address for the external IP address. You can do this by choosing **The external IP address of this Edge pool is translated by NAT** check box . Click **Next** when ready.
    
9. On the External FQDNs screen, your choices depend on the selection you made in Step 7 above.
    
   - If you checked the **Use a single FQDN and IP Address** check box, you need to enter your single external FQDN in the **SIP Access** box. Then you'll need to enter different port numbers for each edge service to allow them all to connect independently. We recommend 5061 for the **SIP Access** Edge service, 444 for the **Web Conferencing** Edge service, and 443 for the **A/V** Edge service. Click **Next** when done.
    
   - If you didn't check the **Use a single FQDN and IP Address** check box, you'll now need to enter the three external FQDNs for the **SIP Access** Edge service, the **Web Conferencing** Edge service, and the **A/V** Edge service. Click **Next** when done.
    
10. Now you've reached the **Define the computers in this pool** screen. Click the **Add** button.
    
11. You're now on the **Define the Internal IP address** screen. Here you'll type the IP address of your Edge Server in the **Internal IPv4 address** and **Internal IPv6 address** text boxes, depending on the choices you made back in Step 8. Click **Next** when ready.
    
12. On the **Define the External IP address** screen, you have a few options depending on your previous choices:
    
    - You may be using a single FQDN for all services. If so, type your external IPv4 or IPv6 address (whichever you're using) into the **SIP Access** text box, and then click **Next**.
    
    - You may have chosen to use three separate FQDNs and IP addresses for the services. If that's the case, enter your external IPv4 or IPv6 addresses for the **SIP Access** Edge service, the **Web Conferencing** Edge service, and the **A/V** Edge service, and then click **Next**.
    
    > [!NOTE]
    > If you didn't previously choose to enable and assign IPv6 addressing, you won't see this dialog box. That's normal, just go to the next step. 
  
13. Click **Finish**. The Edge Server you just created should now be listed in the **Define the computers in this pool** dialog box.
    
14. While still on the **Define the computers in this pool** screen, click the **Add** button again and repeat steps 11 through 13 until you've added all the Edge Servers you intend to have in this pool. When this is complete, click **Next**.
    
15. If you chose to use NAT back in Step 8, you'll now get a screen with a **Public IP address** textbox. You'll need to enter the public IPv4 and/or IPv6 address you've set for the A/V Edge service, to be translated by NAT. Then click **Next**.
    
16. Next screen up is **Define the next hop**. In the **Next hop pool** box, select the name of your internal pool, which might be a Front End pool or a Standalone pool. If you have a Director in your environment, you should choose the Director. Then click **Next**.
    
17. On the **Associate Front End pools** screen, you'll need to specify one or more internal pools, including Front End pools and Standard Edition pools, to associate with this Edge Server. Just choose the names of the internal pools you want using this Edge Server to communicate with supported external users. Click **Next**.
    
    > [!NOTE]
    > Something to keep in mind here is, if your internal pools or standalone servers are already using a different Skype for Business Server Edge Server, they can't have multiple associations. If you choose an internal pool or standalone server that's in that situation, you'll see a warning appear telling you about the other Edge Server, and you can decide whether you want to continue or not. If you go ahead with this new association, the connection to the other Edge Server will stop. 
  
18. Click **Finish** on the next screen.
    
19. Now you'll be able to publish this updated technology, and follow the instructions in [Deploy Edge Servers in Skype for Business Server](deploy-edge-servers.md) to deploy to your Edge Server from here.
    
### Defining the topology for a hardware load balanced Edge Server pool

1. Log onto your Skype for Business Server Standard Edition server, or a Skype for Business Server Front End Server.
    
2. Once there, open **Skype for Business Server Topology Builder**.
    
3. In the console tree, expand the site you're going to deploy the Edge Server to.
    
4. Right-click **Edge pools**, and then click **New Edge pool**.
    
5. You'll click **Next** on the **Define New Edge pool** screen.
    
6. On the **Define the Edge pool FQDN** screen, type the internal fully qualified domain name (FQDN) that the Edge pool is going to use, and select **Multiple computer pool**, clicking **Next** when done.
    
7. On the **Select features** screen, you have a choice:
    
   - You may intend to use the same FQDN and IP address for your SIP Access service, your Skype for Business Server Web Conferencing Service, and your A/V Edge service. If so, you need to choose the **Use a single FQDN and IP address checkbox** (and keep this in mind for Step 9 below)
    
   - If you're planning to enable federation, choose the **Enable federation for this Edge pool (Port 5061)** check box.
    
8. Once you've clicked **Next**, you'll find yourself on the **IP Options** screen. Your options are as follows:
    
   - Enable IPv4 on the internal interface
    
   - Enable IPv6 on the internal interface
    
   - Enable IPv4 on the external interface
    
   - Enable IPv6 on the external interface
    
     These are pretty self-explanatory, whether you're using IPv4 or IPv6 addresses, and you're applying those addresses on your Edge Server internally or externally (you'll need to keep this in mind for Step 11).
    
     > [!NOTE]
     > Unlike the other two topology options, when using a hardware load balancer, you **MUST NOT** select the option **The external IP address of the Edge Pool is translated by NAT**. This is **not supported**.
  
9. On the External FQDNs screen, your choices depend on the selection you made in Step 7 above.
    
   - If you checked the **Use a single FQDN and IP Address** check box, you need to enter your single external FQDN in the **SIP Access** box. Then you'll need to enter different port numbers for each edge service to allow them all to connect independently. We recommend 5061 for the **SIP Access** Edge service, 444 for the **Web Conferencing** Edge service, and 443 for the **A/V** Edge service. Click **Next** when done.
    
   - If you didn't check the **Use a single FQDN and IP Address** check box, you'll now need to enter the three external FQDNs for the **SIP Access** Edge service, the **Web Conferencing** Edge service, and the **A/V** Edge service. Click **Next** when done.
    
10. Now you've reached the **Define the computers in this pool** screen. Click the **Add** button.
    
11. You're now on the **Define the Internal IP address** screen. Here you'll type the IP address of your Edge Server in the **Internal IPv4 address** and **Internal IPv6 address** text boxes, depending on the choices you made back in Step 8. Click **Next** when ready.
    
12. On the **Define the External IP address** screen, you have a few options depending on your previous choices:
    
    - You may be using a single FQDN for all services. If so, type your external IPv4 or IPv6 address (whichever you're using) into the **SIP Access** text box, and then click **Next**.
    
    - You may have chosen to use three separate FQDNs and IP addresses for the services. If that's the case, enter your external IPv4 or IPv6 addresses for the **SIP Access** Edge service, the **Web Conferencing** Edge service, and the **A/V** Edge service, and then click **Next**.
    
    > [!NOTE]
    > If you didn't previously choose to enable and assign IPv6 addressing, you won't see this dialog box. That's normal, just go to the next step. 
  
13. Click **Finish**. The Edge Server you just created should now be listed in the **Define the computers in this pool** dialog box.
    
14. While still on the **Define the computers in this pool** screen, click the **Add** button again and repeat steps 11 through 13 until you've added all the Edge Servers you intend to have in this pool. When this is complete, click **Next**.
    
15. Next screen up is **Define the next hop**. In the **Next hop pool** box, select the name of your internal pool, which might be a Front End pool or a Standalone pool. If you have a Director in your environment, you should choose the Director. Then click **Next**.
    
16. On the **Associate Front End pools** screen, you'll need to specify one or more internal pools, including Front End pools and Standard Edition pools, to associate with this Edge Server. Just choose the names of the internal pools you want using this Edge Server to communicate with supported external users. Click **Next**.
    
    > [!NOTE]
    > Something to keep in mind here is, if your internal pools or standalone servers are already using a different Skype for Business Server Edge Server, they can't have multiple associations. If you choose an internal pool or standalone server that's in that situation, you'll see a warning appear telling you about the other Edge Server, and you can decide whether you want to continue or not. If you go ahead with this new association, the connection to the other Edge Server will stop. 
  
17. Click **Finish** on the next screen.
    
18. Now you'll be able to publish this updated technology, and follow the instructions in [Deploy Edge Servers in Skype for Business Server](deploy-edge-servers.md) to deploy to your Edge Server from here.
    
## Publish your Edge Server topology

Once you've finished the steps above, it's time to publish this new topology, which will also allow you to export it to your Skype for Business Server Edge Server or Edge pool. Follow these steps:
  
1. Start **Topology Builder** (if it's not started already from the previous procedure).
    
2. In **Topology Builder**, in the console tree, right-click **Skype for Business Server** and then click **Skype for Business Server Topology Builder**.
    
3. On the **Welcome** page of the wizard, click **Next**.
    
4. On the **Create other databases** page, click **Next**.
    
5. When the status indicates that the database creation succeeded, do the following:
    
    - To view the log, click **View log**.
    
    - To close the wizard, click **Finish**.
    
## Export your Edge Server topology

To deploy successfully, the Skype for Business Server Deployment Wizard needs access to the Central Management store data. For internal servers in your domain or forest, this typically is straightforward. Edge Servers are outside of the domain, and so it's necessary to manually export the topology file to the Edge Server location, usually on a physical media. This export is done via PowerShell:
  
1. Start the **Skype for Business Server Management Shell**.
    
2. In the **Skype for Business Server Management Shell**, run the following:
    
   ```
   Export-CsConfiguration -FileName <ConfigurationFilePath.zip>
   ```

3. Copy the exported file to external media (for example, a USB drive or network share that you can reach from the Edge Server's location).
    

