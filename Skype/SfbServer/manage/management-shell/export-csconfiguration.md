---
title: "Export-CsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7da7e133-e405-466c-a852-06a4fb678c59
description: "Exports your Skype for Business Server 2015 topology, policies, and configuration settings to a file. Among other things, this file can then be used to restore this information to the Central Management store after an upgrade, a hardware failure, or some other issue has resulted in data loss. This cmdlet was introduced in Lync Server 2010."
---

# Export-CsConfiguration
 
Exports your Skype for Business Server 2015 topology, policies, and configuration settings to a file. Among other things, this file can then be used to restore this information to the Central Management store after an upgrade, a hardware failure, or some other issue has resulted in data loss. This cmdlet was introduced in Lync Server 2010.
  
```
Export-CsConfiguration [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 exports Skype for Business Server 2015 data from the Central Management store to a file named C:\Config.zip. 
  
```
Export-CsConfiguration -FileName "C:\Config.zip"
```

## Detailed Description

Computers that run Skype for Business Server 2015 services or server roles must have a copy of the current topology, current configuration settings, and current policies before they can function in their appointed role. Skype for Business Server 2015 is responsible for ensuring that this information is passed along to each computer that needs it. 
  
The **Export-CsConfiguration** cmdlet and the **Import-CsConfiguration** cmdlet are used to backup and restore your Skype for Business Server 2015 topology, configuration settings, and policies during a Central Management store upgrade. The **Export-CsConfiguration** cmdlet enables you to export data to a .ZIP file; you can then use the **Import-CsConfiguration** cmdlet to read that .ZIP file and restore the topology, configuration settings, and policies to the Central Management store. After that, the replication services of Skype for Business Server 2015 will replicate the restored information to other computers running Skype for Business Server 2015 services.
  
The ability to export and import configuration data is also used when initially configuring computers located in your perimeter network (for example, Edge Servers). When configuring a computer in the perimeter network, you must first perform a manual replication using the CsConfiguration cmdlets: you will need to export the configuration data using the **Export-CsConfiguration** cmdlet and then copy the .ZIP file to the computer in the perimeter network. After that, you can use the **Import-CsConfiguration** cmdlet and the LocalStore parameter to import the data. You only need to do this once; after that, replication will take place automatically.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Path to the .ZIP file to be created when you run the **Export-CsConfiguration** cmdlet. For example: `-FileName "C:\Config.zip"`. Note that you must include either the FileName or the AsBytes parameters, but not both, when calling the **Export-CsConfiguration** cmdlet. <br/> |
| _AsBytes_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns topology information as a byte array; the returned data must then be stored in a variable in order to be used by the **Import-CsConfiguration** cmdlet. You cannot use both AsBytes and FileName in the same command. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command. To set the Force parameter to True use this syntax:  <br/>  `-Force:$True` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the configuration data from the local computer rather than from the Central Management store itself.  <br/> |
   
## Input Types

None. The **Export-CsConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

If called along with the AsBytes parameter, the **Export-CsConfiguration** cmdlet returns configuration information in the form of a byte array.
  
## See also

#### 

[Import-CsConfiguration](import-csconfiguration.md)

