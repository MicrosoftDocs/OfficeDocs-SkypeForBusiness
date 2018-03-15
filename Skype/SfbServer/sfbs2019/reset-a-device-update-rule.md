---
title: "Reset a Device Update rule in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d1f597e7-dffd-4756-af07-10613a5d8729
description: "If you don't like the way that an update works on your test devices, you can reset the device update rule, which removes the rule's pending status and uninstalls the update from the test devices."
---

# Reset a Device Update rule in Lync Server 2013
[]
If you don't like the way that an update works on your test devices, you can reset the device update rule, which removes the rule's pending status and uninstalls the update from the test devices.
  
You can remove a device update rule by using either Lync Server Control Panel or Windows PowerShell.
  
> [!NOTE]
> To uninstall a rule that you've already approved (that is, rolled out), restore it. For details, see [Restore a Device Update rule in Lync Server 2013](restore-a-device-update-rule.md). 
  
### To reset a device update rule by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Device Update** navigation button. 
    
4. On the **Device Update** page, do one of the following: 
    
  - To reset one rule, select the rule you want to reset.
    
  - To reset all rules, on the **Edit** menu, click **Select All**.
    
  - To reset all rules for one brand, use the ** Brand ** column menu. 
    
5. Click **Action**, and then click **Cancel pending updates**.
    
    > [!TIP]
    > If you're sure you'll never want to roll out the device update rule(s) that you cancelled, you might want to delete them. For details, see [Remove a Device Update rule in Lync Server 2013](remove-a-device-update-rule.md). 
  
## Resetting a Device Update Rule by Using Windows PowerShell Cmdlets

Device update rules can also be reset by using Windows PowerShell and the **Reset-CsDeviceUpdateRule** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
### To reset a specific device update rule on a server

- The following command resets the device update rule d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 on the Web server atl-cs-001.litwareinc.com:
    
  ```
  Reset-CsDeviceUpdateRule -Identity "service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9"
  ```

### To reset all the device update rules on a server

- This command resets all the device update rules on the Web server atl-cs-001.litwareinc.com:
    
  ```
  Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*"  | Reset-CsDeviceUpdateRule
  ```

### To reset all the device updates rules that have a specific brand

- In this example, all the device updates throughout the organization that have a Brand equal to Microsoft are reset:
    
  ```
  Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "Microsoft"} | Reset-CsDeviceUpdateRule
  ```

For details, see the Help topic for the [Reset-CsDeviceUpdateRule](reset-csdeviceupdaterule.md) cmdlet. 
  
## See also

#### 

[Approve a Device Update rule in Lync Server 2013](approve-a-device-update-rule.md)

