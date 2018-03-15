---
title: "Import Device Update rules in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 919e9c87-912b-4bc9-92e7-5998fc2e0bf0
description: "Device update rules can be imported only by using Windows PowerShell and the Import-CsDeviceUpdate cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell."
---

# Import Device Update rules in Lync Server 2013
[]
Device update rules can be imported only by using Windows PowerShell and the **Import-CsDeviceUpdate** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
## 

### To import device update rules to a single web server

- The following command imports device update rules to the Web server atl-cs-001.litwareinc.com:
    
  ```
  Import-CsDeviceUpdate -Identity "service:WebServer:atl-cs-001.litwareinc.com" -FileName C:\Updates\UCUpdates.cab
  ```

### To import device update rules to all your web servers

- In this example, device update rules are imported to all the Web servers deployed in your organization. For this command to work, the folder \\atl-fs-001.litwareinc.com\Updates must be shared and available to all the Web servers.
    
  ```
  Get-CsService -WebServer | ForEach-Object {Import-CsDeviceUpdate -Identity $_.Identity -FileName \\atl-fs-001.litwareinc.com\Updates\UCUpdates.cab}
  ```

For details, see the Help topic for the [Import-CsDeviceUpdate](import-csdeviceupdate.md) cmdlet. 
  
## See also

#### 

[View information about Device Update rules in Lync Server 2013](view-information-about-device-update-rules.md)
  
[Approve a Device Update rule in Lync Server 2013](approve-a-device-update-rule.md)

