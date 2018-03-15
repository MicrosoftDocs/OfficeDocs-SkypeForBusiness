---
title: "Configuring a watcher node in Lync Server 2013 to participate in System Center discovery"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15c5dcfd-603b-47ea-af1b-8714c2ec08af
description: "To make sure that your watcher node participates in the discovery process for System Center Operations Manager, you must complete the following procedure on a computer where the System Center Operations Manager console has been installed:"
---

# Configuring a watcher node in Lync Server 2013 to participate in System Center discovery
[]
To make sure that your watcher node participates in the discovery process for System Center Operations Manager, you must complete the following procedure on a computer where the System Center Operations Manager console has been installed:
  
1. On the **Administration** tab, click **Agent Managed**.
    
2. Right-click the name of the watcher node computer, and then click **Properties**. In the **Properties** dialog box, on the **Security** tab, select **Allow this agent to act as a proxy and discover managed objects on other computers**, and then click **OK**.
    
After configuring the watcher node to act as a proxy, reboot the watcher node computer. After the computer has rebooted, verify that no error events are being recorded in the Operations Manager event log on that computer. After the computer has been running for 15 minutes or so, use the Operations Manager console to verify that your Lync Server computers are listed under the **Lync** category. 
  

