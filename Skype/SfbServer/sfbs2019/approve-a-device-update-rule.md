---
title: "Approve a Device Update rule in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9dbb1c9a-be0f-4e13-9234-05501ab43ac5
description: "After you import a device update rule, it's installed on your test devices. If your testing is successful, and you want to roll out the update to your organization, approve it by using either Lync Server Control Panel or Windows PowerShell."
---

# Approve a Device Update rule in Lync Server 2013
[]
After you import a device update rule, it's installed on your test devices. If your testing is successful, and you want to roll out the update to your organization, approve it by using either Lync Server Control Panel or Windows PowerShell.
  
### To approve a device update rule by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. On the **Device Update** page, do one of the following: 
    
  - To approve one rule, select that rule.
    
  - To approve all rules, click **Edit**, and then click **Select All**.
    
4. Click **Action**, and then click **Approve**.
    
## Approving a Device Update Rule by Using Windows PowerShell Cmdlets

Device update rules can also be approved by using Windows PowerShell and the **Approve-CsDeviceUpdateRule** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
### To approve a single device update rule

- The following command approves the device update rule d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 found on the Web server atl-cs-001.litwareinc.com:
    
  ```
  Approve-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9
  ```

### To approve multiple device update rules

- This command approves all the device update rules for Microsoft-branded devices:
    
  ```
  Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "Microsoft"} | Approve-CsDeviceUpdateRule
  ```

For details, see the Help topic for the [Approve-CsDeviceUpdateRule](approve-csdeviceupdaterule.md) cmdlet. 
  
## See also

#### 

[Import Device Update rules in Lync Server 2013](import-device-update-rules.md)
  
[Restore a Device Update rule in Lync Server 2013](restore-a-device-update-rule.md)

