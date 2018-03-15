---
title: "Delete a collection of Device Update configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1a649136-34a9-42a7-a5b3-a78bbfe93f36
description: "Device update configuration settings can also be deleted by using Windows PowerShell and the Remove-CsdeviceUpdateConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog articleQuick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShellat https://go.microsoft.com/fwlink/p/?linkId=255876."
---

# Delete a collection of Device Update configuration settings in Lync Server 2013
[]
Device update configuration settings can also be deleted by using Windows PowerShell and the **Remove-CsdeviceUpdateConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
## 

### To remove a specific collection of device update configuration settings

- This command deletes the device update configuration settings applied to the Redmond site:
    
  ```
  Remove-CsDeviceUpdateConfiguration -Identity "site:Redmond"
  ```

### To remove all the device update configuration settings applied to the site scope

- This command deletes all the device update configuration settings applied to the site scope:
    
  ```
  Get-CsDeviceUpdateConfiguration -Filter "site:*" | Remove-CsDeviceUpdateConfiguration
  ```

### To remove device update configuration settings based on the value of the LogCleanUpInterval property

- The following command deletes all the device update configuration settings where the log cleanup interval is greater than 10 days (10.00:00:00):
    
  ```
  Get-CsDeviceUpdateConfiguration | Where-Object {$_.LogCleanUpInterval -gt "10.00:00:00" | Remove-CsDeviceUpdateConfiguration
  ```

For details, see the Help topic for the [Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md) cmdlet. 
  

