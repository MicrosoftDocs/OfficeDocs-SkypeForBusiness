---
title: "Remove Device Update files not associated with a device in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ecebbf73-b456-4990-a91d-308b84d39404
description: "Each time new device updates are uploaded to the system, a corresponding device update rule is created. By default, these new device update rules are assigned to the Pending state. This means that the rules can be downloaded and installed on test devices, but not on production devices, which enables you to test the updates before making them available to users. Based on the tests, you either accept and deploy or reject and delete the update. When you reject an update, the device update is disassociated from its device update rule."
---

# Remove Device Update files not associated with a device in Lync Server 2013
[]
Each time new device updates are uploaded to the system, a corresponding device update rule is created. By default, these new device update rules are assigned to the Pending state. This means that the rules can be downloaded and installed on test devices, but not on production devices, which enables you to test the updates before making them available to users. Based on the tests, you either accept and deploy or reject and delete the update. When you reject an update, the device update is disassociated from its device update rule. 
  
## 

Device update files that are no longer associated with a device can be removed by using Windows PowerShell and the **Clear-CsDeviceUpdateFile** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
- For example, the following command removes any device update rules on the Web server atl-cs-001.litwareinc.com that are no longer associated with a device:
    
  ```
  Clear-CsDeviceUpdateFile -Identity "service:WebServer:atl-cs-001.litwareinc.com"
  ```

For details, see the Help topic for the [Clear-CsDeviceUpdateFile](clear-csdeviceupdatefile.md) cmdlet. 
  

