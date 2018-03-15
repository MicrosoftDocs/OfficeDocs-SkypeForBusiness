---
title: "Install Edge Servers for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1655ab69-3899-4ee4-a1cc-8243bc1bfa0f
description: "You install Lync Server 2013 on Edge Servers by using Lync Server Deployment Wizard. By running the Deployment Wizard on each Edge Server, you can complete most of the tasks required to set up the Edge Server. In order to deploy Lync Server 2013 on an Edge Server, you must have already run Topology Builder to define and publish your Edge Server topology, and exported it to media that is available from the Edge Server. For details, see Scenarios for external user access in Lync Server 2013 and Export your Lync Server 2013 topology and copy it to external media for edge installation."
---

# Install Edge Servers for Lync Server 2013
[]
You install Lync Server 2013 on Edge Servers by using Lync Server Deployment Wizard. By running the Deployment Wizard on each Edge Server, you can complete most of the tasks required to set up the Edge Server. In order to deploy Lync Server 2013 on an Edge Server, you must have already run Topology Builder to define and publish your Edge Server topology, and exported it to media that is available from the Edge Server. For details, see [Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md) and [Export your Lync Server 2013 topology and copy it to external media for edge installation](export-your-topology-and-copy-it-to-external-media-for-edge-installation.md).
  
After using the Deployment Wizard to install each Edge Server, install and assign the required certificates, and start the required services, you can complete the setup by using the information in [Configuring support for external user access in Lync Server 2013](configuring-support-for-external-user-access.md) to enable and configure external user access and the information in [Verifying your edge deployment in Lync Server 2013](verifying-your-edge-deployment.md) to validate the setup, including server and client connectivity. 
  
### To install an Edge Server

1. Log on to the computer on which you want to install your Edge Server as a member of the local Administrators group or an account with equivalent user rights and permissions.
    
2. Ensure that the topology configuration file you created using Topology Builder, and then exported and copied to external media, is available on the Edge Server (for example, access to the USB drive onto which you copied the topology configuration file, or verify access to the network share where you copied the file).
    
3. Start the Deployment Wizard. 
    
    > [!NOTE]
    > If you get a message saying that you need to install Microsoft Visual C++ Redistributable, click **Yes**. In the next dialog box, you can accept the default **Installation Location** or click the **Browse** to select an alternate location, and then click **Install**. In the next dialog box, select the **I accept the terms in the license agreement** check box, and then click **OK**. 
  
4. In the Deployment Wizard, click **Install or Update Lync Server System**.
    
5. After the wizard determines the deployment state, for **Step 1. Install Local Configuration Store**, click **Run** and then do the following: 
    
  - In the **Configure Local Replica of Central Management Store** dialog box, click **Import from a file (Recommended for Edge Servers)**, go to the location of the exported topology configuration file, select the .zip file, click **Open**, and then click **Next**.
    
  - The Deployment Wizard reads the configuration information from the configuration file and writes the XML configuration file to the local computer.
    
  - After the **Executing Commands** process is finished, click **Finish**.
    
6. In the Deployment Wizard, click **Step 2: SetUp or Remove Lync Server Components** to install the Lync Server 2013 edge components specified in the XML configuration file that is stored on the local computer. 
    
7. After completing the installation, use the information in [Set up Edge certificates for Lync Server 2013](set-up-edge-certificates.md) to install and assign the required certificates before you start services. 
    

