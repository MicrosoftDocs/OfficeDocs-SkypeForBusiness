---
title: "Export-CsConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7da7e133-e405-466c-a852-06a4fb678c59
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Export-CsConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Exports your Lync Server topology, policies, and configuration settings to a file. Among other things, this file can then be used to restore this information to the Central Management store after an upgrade, a hardware failure, or some other issue has resulted in data loss. This cmdlet was introduced in Lync Server 2010.
  
```
Export-CsConfiguration [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 exports Lync Server data from the Central Management store to a file named C:\Config.zip. 
  
```
Export-CsConfiguration -FileName "C:\Config.zip"
```

## Detailed Description
<a name="sectionSection1"> </a>

Computers that run Lync Server services or server roles must have a copy of the current topology, current configuration settings, and current policies before they can function in their appointed role. Lync Server is responsible for ensuring that this information is passed along to each computer that needs it. 
  
The **Export-CsConfiguration** cmdlet and the **Import-CsConfiguration** cmdlet are used to backup and restore your Lync Server topology, configuration settings, and policies during a Central Management store upgrade. The **Export-CsConfiguration** cmdlet enables you to export data to a .ZIP file; you can then use the **Import-CsConfiguration** cmdlet to read that .ZIP file and restore the topology, configuration settings, and policies to the Central Management store. After that, the replication services of Lync Server will replicate the restored information to other computers running Lync Server services. 
  
The ability to export and import configuration data is also used when initially configuring computers located in your perimeter network (for example, Edge Servers). When configuring a computer in the perimeter network, you must first perform a manual replication using the CsConfiguration cmdlets: you will need to export the configuration data using the **Export-CsConfiguration** cmdlet and then copy the .ZIP file to the computer in the perimeter network. After that, you can use the **Import-CsConfiguration** cmdlet and the LocalStore parameter to import the data. You only need to do this once; after that, replication will take place automatically. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Export-CsConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Export-CsConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Path to the .ZIP file to be created when you run the **Export-CsConfiguration** cmdlet. For example: -FileName "C:\Config.zip". Note that you must include either the FileName or the AsBytes parameters, but not both, when calling the **Export-CsConfiguration** cmdlet.  <br/> |
| _AsBytes_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns topology information as a byte array; the returned data must then be stored in a variable in order to be used by the **Import-CsConfiguration** cmdlet. You cannot use both AsBytes and FileName in the same command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command. To set the Force parameter to True use this syntax:  <br/> -Force:$True  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the configuration data from the local computer rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Export-CsConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

If called along with the AsBytes parameter, the **Export-CsConfiguration** cmdlet returns configuration information in the form of a byte array. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Import-CsConfiguration](import-csconfiguration.md)

