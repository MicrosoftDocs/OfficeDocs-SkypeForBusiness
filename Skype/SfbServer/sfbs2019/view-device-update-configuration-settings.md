---
title: "View Device Update configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa6a70a9-bd77-4606-b797-ea6a3bab9cf2
description: "You can view the Device Update Service configuration settings by using Lync Server Management Shell and the Get-CsDeviceUpdateConfiguration cmdlet, which you can run from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell"
---

# View Device Update configuration settings in Lync Server 2013
[]
You can view the Device Update Service configuration settings by using Lync Server Management Shell and the **Get-CsDeviceUpdateConfiguration** cmdlet, which you can run from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
## 

- 
    
    To view information about all your voice routes, type the following command in the Lync Server Management Shell and press Enter:
    
  ```
  Get-CsDeviceUpdateConfiguration
  ```

    This command returns information similar to the following:
    
  ```
  Identity               : Global
  ValidLogFileTypes      : {Watson, Config, Diaglog, CELog}
  ValidLogFileExtensions : {.dmp, .clg, .clg1, .clg2...}
  MaxLogFileSize         : 1024000
  MaxLogCacheLimit       : 512000
  LogCleanUpInterval     : 10.00:00:00
  LogFlushInterval       : 00:05:00
  LogCleanUpTimeOfDay    :
  
  ```

For details about this cmdlet, see Help topic at [Get-CsDeviceUpdateConfiguration](https://technet.microsoft.com/en-us/library/gg399030%28v=ocs.14%29.aspx).
  

