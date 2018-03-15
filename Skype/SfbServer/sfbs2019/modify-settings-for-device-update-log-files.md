---
title: "Modify settings for Device Update log files in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9b57f126-1853-43b3-bbd4-06401e6498bd
description: "You can change settings for how device update information is logged in your organization by using Lync Server Control Panel or Lync Server Management Shell. The following table shows which settings are modifiable, and which tool(s) you use to modify the settings."
---

# Modify settings for Device Update log files in Lync Server 2013
[]
You can change settings for how device update information is logged in your organization by using Lync Server Control Panel or Lync Server Management Shell. The following table shows which settings are modifiable, and which tool(s) you use to modify the settings. 
  
Log settings can be changed and applied globally, or per site.
  
|**To change**|**Use**|
|:-----|:-----|
|The maximum size (in bytes) for a log file  <br/> |Lync Server Control Panel  <br/> -or-  <br/> Lync Server Management Shell  <br/> |
|The maximum amount of information (in bytes) that can be held in the cache  <br/> |Lync Server Control Panel  <br/> -or-  <br/> Lync Server Management Shell  <br/> |
|How often (in minutes) to write cached information to the log file  <br/> |Lync Server Control Panel  <br/> -or-  <br/> Lync Server Management Shell  <br/> |
|How long (in days) to keep log files  <br/> |Lync Server Control Panel  <br/> -or-  <br/> Lync Server Management Shell  <br/> |
|When (time of day) to check for expired files that should be deleted  <br/> |Lync Server Management Shell  <br/> |
|What log file extensions to permit  <br/> |Lync Server Management Shell  <br/> |
|Which log file types to retain  <br/> |Lync Server Management Shell  <br/> |
   
### To change logging settings by using Lync Server Control Panel

1. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
2. In the left navigation bar, click **Clients**, and then click **Device Log Configuration**.
    
3. On the **Device Log Configuration** page, double-click the configuration that you want to change. 
    
4. In the **Edit Log Setting** dialog box, change any of the following settings: 
    
  - **Maximum file size (bytes)** Specifies the maximum size a log file can become before it is purged. The default is 1,024,000 bytes (1 MB). 
    
  - **Maximum cache size (bytes)** Specifies the maximum amount of information (in bytes) that can be held in the log file cache before that cache must be cleared and the data is written to a log file. The default is 512,000 bytes (0.5 MB). 
    
  - **Number of minutes to flush cache (1-60)** Indicates how often information stored in the log file cache is written to the actual log file. After the data is logged, the cache is cleared. The default is five minutes. 
    
  - **Number of days to keep log files (1-365)** Specifies the number of days the log files are kept before they are purged. The default is 10 days. 
    
5. Click **Commit**.
    
## Changing Logging Settings by Using Windows PowerShell Cmdlets

Device update log file settings can be modified by using Windows PowerShell and the **Set-CsDeviceUpdateConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. 
  
> [!NOTE]
> For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
The following examples show a couple of the ways that you can use **Set-CsDeviceUpdateConfiguration** to modify settings. 
  
### To modify the maximum log file size and the log cleanup interval

- The following command modifies the device update log settings applied to the Redmond site. In this example, the maximum log file size is set to 204800 bytes and the log cleanup interval is set to 14 days.
    
  ```
  Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -MaxLogFileSize 204800 -LogCleanUpInterval 14.00:00:00
  ```

### To modify the log cleanup time of day

- This command sets the log cleanup time for the Redmond site to 3:00 AM.
    
  ```
  Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupTimeOfDay 03:00
  ```

For details, see the Help topic for the [Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md) cmdlet. 
  

