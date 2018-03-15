---
title: "Restore a Device Update rule in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ac490baf-c7a0-48d9-8fd0-ba5729489341
description: "To uninstall a device update rule from the devices in your deployment, restore it. Restoring a device update rule both uninstalls the update and reinstalls the previous version of that rule."
---

# Restore a Device Update rule in Lync Server 2013
[]
To uninstall a device update rule from the devices in your deployment, restore it. Restoring a device update rule both uninstalls the update and reinstalls the previous version of that rule.
  
You can restore a device update rule by using either Lync Server Control Panel or Windows PowerShell.
  
### To restore device update rules by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Device Update** navigation button. 
    
4. On the **Device Update** page, do one of the following: 
    
  - To restore one rule, select that rule.
    
  - To restore all rules, click **Edit**, and then click **Select All**.
    
5. Click the **Action** menu, and then click **Restore**.
    
## Restoring Device Update Rules by Using Windows PowerShell Cmdlets

Device updates rules can also be restored by using Windows PowerShell and the **Restore-CsDeviceUpdateRule** cmdlet.. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
### To restore a single device update rule on a server

- The following command restores the device update rule d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 on the Web server atl-cs-001.litwareinc.com:
    
  ```
  Restore-CsDeviceUpdateRule -Identity "service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9"
  ```

### To restore all the device update rules on a server

- This command restores all the device update rules on the web server atl-cs-001.litwareinc.com:
    
  ```
  Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*" | Restore-CsDeviceUpdateRule
  ```

For details, see the Help topic for the [Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md) cmdlet. 
  

