---
title: "Define and configure a topology in Topology Builder for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 99231ff5-1c21-432b-ad65-8675fcd484f9
description: "Running Topology Builder to define a new topology or to modify an existing topology does not require membership in a local administrator or privileged domain group. Topology Builder guides you through the steps necessary to define your topology for an Enterprise Edition Front End pool or a Standard Edition, based on your configuration requirements."
---

# Define and configure a topology in Topology Builder for Lync Server 2013
[]
Running Topology Builder to define a new topology or to modify an existing topology does not require membership in a local administrator or privileged domain group. Topology Builder guides you through the steps necessary to define your topology for an Enterprise Edition Front End pool or a Standard Edition, based on your configuration requirements.
  
You must use Topology Builder to complete and publish the topology before you can install Lync Server 2013 on servers. The following procedure includes the steps required to define a new topology.
  
### To define a topology

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. In Topology Builder, select **New Topology**. You are prompted for a location and file name for saving the topology. Give the topology file a meaningful name and accept the default extension of .tbxml. Click **OK**.
    
3. Navigate to the location where you want to save the new topology XML file, enter a name for the file, and then click **Save**. 
    
4. On the **Define the primary domain** page, enter the name of the primary SIP domain for your organization, and then click **Next**.
    
5. On the **Specify additional supported domains** page, enter the names of additional domains, if any, and then click **Next**.
    
6. On the **Define the first site** page, enter a name and a description for the first site, and then click **Next**.
    
7. On the **Specify site details** page, enter the location information for the site, and then click **Next**.
    
8. On the **New topology was successfully defined** page, make sure the **Open the New Front End Wizard when this wizard closes** check box is selected, and then click **Finish**.
    
After you've defined and saved the topology, use the New Front End Wizard to define a Front End pool or Standard Edition server for your site. For details, see [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](define-and-configure-a-front-end-pool-or-standard-edition-server.md).

