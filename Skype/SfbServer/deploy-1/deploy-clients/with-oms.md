---
title: "Deploy Skype Room Systems v2 management with OMS"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 3/20/2017
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Strat_SB_Admin
ms.assetid: d86ff657-ee92-4b06-aee3-d4c43090bdcb
description: "This article discusses how to deploy management of Skype Room Systems v2 devices in an integrated, end-to-end manner using Microsoft Operations Management Suite."
---

# Deploy Skype Room Systems v2 management with OMS
 
This article discusses how to deploy management of Skype Room Systems v2 devices in an integrated, end-to-end manner using Microsoft Operations Management Suite. 
  
You can configure Microsoft Operations Management Suite (OMS) to provide basic telemetry that will help you manage Skype meeting room devices. As your management solution matures, you can purchase additional data and management capabilities to create a more detailed view of device performance.
  
At a high level, you need to perform the following tasks:
  
1. [Configure devices for OMS Management ](with-oms.md#config_devices)
    
2. [Map custom fields](with-oms.md#Custom_fields)
    
3. [Define the SRS v2 views in OMS](with-oms.md#Views)
    
## Find and record device locations, capabilities, and configurations
<a name="find_devices"> </a>

The first step is to create a detailed database of all of the equipment in the system, the details of its capabilities and configuration, and its location. A spreadsheet may be adequate for this task in small to medium organizations. If you work at a larger organization, you may need to consider asset management tools and third-party services. What is important is that you record the location and all the relevant details of every device.
  
Once that work is done, you can use this information to dispatch technicians and manage device patches and upgrades.
  
## Configure devices for OMS Management
<a name="config_devices"> </a>

For each SRS device, follow the instructions found in [Connect Windows computers to the Log Analytics service in Azure](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-windows-agents).
  
## Configure OMS to collect device event logs
<a name="config_devices"> </a>

You will need to specifically configure OMS to collect event logs from SRS devices using the steps at [Windows event log data sources in Log Analytics](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-data-sources-windows-events). The SRS event log to select is "Skype Room System" and you should check the option boxes for all types: Error, Warning and Information.
  
## Map custom fields
<a name="Custom_fields"> </a>

Before the tiles created in the [Define the SRS v2 views in OMS](with-oms.md#Views) can be used, you'll need to create custom fields for your view. see [Custom fields in Log Analytics](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-custom-fields) for details on creating custom fields.
  
Use the mappings shown below, OMS will automatically add the _CF when defining the new field. 
  
> [!IMPORTANT]
> Remember that all JSON and OMS fields are case sensitive. 
  
**Custom fields mapping**

|**JSON field**|**OMS custom field**|
|:-----|:-----|
|Description  <br/> |SRSEventDescription_CF  <br/> |
|ResourceState  <br/> |SRSResourceState_CF  <br/> |
|OperationName  <br/> |SRSOperationName_CF  <br/> |
|OperationResult  <br/> |SRSOperationResult_CF  <br/> |
|OS  <br/> |SRSOSVersion_CF  <br/> |
|OSVersion  <br/> |SRSOSLongVersion_CF  <br/> |
|Alias  <br/> |SRSAlias_CF  <br/> |
|DisplayName  <br/> |SRSDisplayName_CF  <br/> |
|AppVersion  <br/> |SRSAppVersion_CF  <br/> |
|IPv4Address  <br/> |SRSIPv4Address_CF  <br/> |
|IPv6Address  <br/> |SRSIPv6Address_CF  <br/> |
   
## Define the SRS v2 views in OMS
<a name="Views"> </a>

Once data is collected and custom fields are mapped, you can use OMS View Designer to develop a Dashboard containing Tiles to monitor SRS v2 events. Use View Designer to create the following tiles, refer to [Use View Designer to create custom views in Log Analytics](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-view-designer) as necessary.
  
### Create a tile that shows healthy devices

1. Define the case: 
    
    This tile displays all devices that have sent a heartbeat message in the last 10 minutes.
    
2. Assign Group Title 
    
   ```
   SRS v2
   ```

3. Check the new group box
    
4. Add the Tile legend text
    
   ```
   All healthy devices (Heartbeat sent in last 10 minutes)
   ```

5. Enter the tile query
    
   ```
   Type:Event EventLog:"Skype Room System" SRSOperationName_CF:"Heartbeat" TimeGenerated >NOW-10MINUTES|measure count() by SRSDisplayName_CF 
   ```

6. Enter the list query
    
   ```
   Type:Event EventLog:"Skype Room System" SRSOperationName_CF:"Heartbeat" |measure max(TimeGenerated) as LastHB by SRSDisplayName_CF |Where LastHB>NOW-10MINUTES
   ```

7. Define column titles name
    
   ```
   Display Name
   ```

8. Define Column titles value
    
   ```
   Last HB
   ```

9. Enter Navigation query
    
   ```
   {selected item} EventLog:"Skype Room System" SRSOperationName_CF:"Heartbeat"|Dedup SRSDisplayName_CF|Select TimeGenerated, Computer, SRSOperationName_CF, SRSOperationResult_CF,SRSEventDescription_CF, SRSAppVersion_CF, SRSDisplayName_CF, SRSAlias_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF
   ```

### Create the tile that shows devices with connectivity issues

1. Define the case: 
    
    This tile displays all devices that have not sent a heartbeat message in the last 10 minutes. These devices may be experiencing issues with network connectivity, Exchange connectivity, or Skype for Business connectivity.
    
2. Assign Group Title 
    
   ```
   SRS v2
   ```

3. Do not check the new group box. You already did this when creating tile 1, and don't need to do it again.
    
4. Add the Tile legend text
    
   ```
   Devices no longer sending Heartbeat messages
   ```

5. Enter the tile query
    
   ```
   Type:Event EventLog:"Skype Room System" SRSOperationName_CF:"Heartbeat" |measure max(TimeGenerated) as LastHB by Computer|Where LastHB<NOW-10MINUTES
   ```

6. Enter the list query
    
   ```
   Type:Event EventLog:"Skype Room System" SRSOperationName_CF:"Heartbeat" |measure max(TimeGenerated) as LastHB by Computer|Where LastHB<NOW-10MINUTES
   ```

7. Define column titles name
    
   ```
   Device Name
   ```

8. Define Column titles Value 
    
   ```
   Last HB
   ```

9. Enter Navigation query
    
   ```
   {selected item} EventLog:"Skype Room System" SRSOperationName_CF:"Heartbeat" |Dedup SRSDisplayName_CF|Select TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF
   ```

### List devices with a hardware error

1. Define the case: 
    
   This tile displays all devices that sent a message indicating a one or more hardware component issues in the last 10 minutes. 
    
2. Assign Group Title 
    
   ```
   SRS v2
   ```

3. Do not check the new group box. You already did this when creating tile 1, and don't need to do it again.
    
4. Tile legend: 
    
   ```
   Devices with a Hardware Error
   ```

5. Tile Query
    
   ```
   Type:Event EventLog:"Skype Room System" EventLevelName:Error EventID:3001 TimeGenerated>NOW-10MINUTES|measure count() by SRSDisplayName_CF
   ```

6. List query:
    
   ```
   Type:Event EventLog:"Skype Room System" EventLevelName:Error EventID:3001 TimeGenerated>NOW-10MINUTES|measure max(TimeGenerated) by SRSDisplayName_CF
   ```

7. Column titles Name: 
    
   ```
   Display Name
   ```

8. Column titles Value: 
    
   ```
   Last Error
   ```

9. Navigation query: 
    
   ```
   {selected item}  EventLevelName:Error EventID:3001|Dedup SRSDisplayName_CF|Select TimeGenerated, Computer, SRSOperationName_CF, SRSOperationResult_CF,SRSEventDescription_CF, SRSAppVersion_CF, SRSDisplayName_CF, SRSAlias_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF
   ```

### List devices with an App error

1. Define the case: 
    
   This tile displays all SRS devices that report 1 or more app component errors within the last 10 minutes
    
2. Assign Group Title 
    
   ```
   SRS v2
   ```

3. Do not check the new group box. You already did this when creating tile 1, and don't need to do it again.
    
4. Tile legend: 
   ``` 
    Device with App Errors (in prior 10 minutes)
   ``` 
5. Tile Query: 
    
   ```
   Type:Event EventLog:"Skype Room System" EventLevelName:Error EventID:2001 TimeGenerated>NOW-10MINUTES|measure count() by Computer
   ```

6. List query: 
    
   ```
   Type:Event EventLog:"Skype Room System" EventLevelName:Error EventID:2001 TimeGenerated>NOW-10MINUTES|measure max(TimeGenerated) by Computer
   ```

7. Column titles Name: 
    
   ```
   Device Name
   ```

8. Column titles Value: 
    
   ```
   Last Error
   ```

9. Navigation query:
    
   ```
   {selected item} EventLevelName:Error|Dedup SRSDisplayName_CF|Select TimeGenerated, Computer, SRSOperationName_CF, SRSOperationResult_CF,SRSEventDescription_CF, SRSAppVersion_CF, SRSDisplayName_CF, SRSAlias_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF
   ```

### List devices requiring a restart

1. Define the case: 
    
   This tile displays all SRS devices that have been restarted in the past 24 hours and number of restarts
    
2. Assign Group Title 
    
  ```
  SRS v2
  ```

3. Do not check the new group box. You already did this when creating tile 1, and don't need to do it again.
    
4. Tile legend: 
    
   ```
   Devices with App restarted (past 24 hours)
   ```

5. Tile Query: 
    
   ```
   Type:Event EventLog:"Skype Room System" EventID:4000 TimeGenerated>NOW-24HOURS|measure count() by Computer
   ```

6. List query: 
    
   ```
   Type:Event EventLog:"Skype Room System" EventID:4000 TimeGenerated>NOW-24HOURS|measure count(EventID) by SRSDisplayName_CF
   ```

7. Column titles Name: 
    
   ```
   Display Name
   ```

8. Column titles Value: 
    
   ```
   Number of restarts
   ```

9. Navigation query: 
    
   ```
   {selected item} EventID:4000 TimeGenerated >NOW-24HOURS|Select TimeGenerated, Computer, SRSOperationName_CF, SRSOperationResult_CF,SRSEventDescription_CF, SRSAppVersion_CF, SRSDisplayName_CF, SRSAlias_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF
   ```

That completes view creation. The alerts currently available are all reflected in one or more of these tiles.
## See also
<a name="Views"> </a>

#### 

[Plan Skype Room Systems v2 management with OMS](../../plan-your-deployment/clients-and-devices/oms-management.md)
  
[Manage Skype Room Systems v2 devices with OMS](../../manage/skype-room-systems-v2/oms.md)

