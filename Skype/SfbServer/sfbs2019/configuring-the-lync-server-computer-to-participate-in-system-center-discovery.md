---
title: "Configuring the Lync Server 2013 computer to participate in System Center discovery"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2f9c9cb0-3120-4571-9cd2-657c2123fe21
description: "To make sure that your new Lync Server agent participates in discovery process for System Center Operations Manager, you must complete the following procedure on each computer where the System Center Operations Manager console has been installed:"
---

# Configuring the Lync Server 2013 computer to participate in System Center discovery
[]
To make sure that your new Lync Server agent participates in discovery process for System Center Operations Manager, you must complete the following procedure on each computer where the System Center Operations Manager console has been installed:
  
1. On the **Administration** tab, click **Agent Managed**.
    
2. Right-click the name of the computer, and then click **Properties**. In the **Properties** dialog box, on the **Security** tab, select **Allow this agent to act as a proxy and discover managed objects on other computers**, and then click **OK**.
    
After completing step 2, reboot the Health Agent service. (Rebooting the service will "force" discovery of the new machine. If you do not reboot the service, it could take as long as 4 hours before the new machine is discovered by System Center Operations Manager.). After the service has rebooted, verify that no error events are being recorded in the Operations Manager event log on that computer.
  

