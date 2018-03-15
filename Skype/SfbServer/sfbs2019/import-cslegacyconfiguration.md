---
title: "Import-CsLegacyConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bd688c08-abb8-4c78-8e1b-b330412d4422
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Import-CsLegacyConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
The **Import-CsLegacyConfiguration** cmdlet enables you to import a number of configuration settings from Microsoft Office Communications Server 2007 R2 or Microsoft Office Communications Server 2007 to Lync Server. This helps provide interoperability between Lync Server and your earlier installation of Office Communications Server 2007 R2 or Office Communications Server 2007. This cmdlet was introduced in Lync Server 2010. 
  
```
Import-CsLegacyConfiguration [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplaceExisting <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 merges voice policies and other settings from Communications Server 2007 or Communications Server 2007 R2 with an installation of Lync Server.
  
```
Import-CsLegacyConfiguration
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the ReplaceExisting parameter is included. This parameter instructs the cmdlet to use the imported data to resolve name collisions. For example, suppose you try to import a voice route named LocalRoute, and a voice route by that name already exists in your Lync Server installation. Because you included the ReplaceExisting parameter, the Lync Server route will be replaced by the voice route being imported.
  
```
Import-CsLegacyConfiguration -ReplaceExisting
```

## Detailed Description
<a name="sectionSection1"> </a>

The **Import-CsLegacyConfiguration** cmdlet is used in conjunction with the **Merge-CsLegacyTopology** cmdlet to enable organizations to migrate from a previous version of Office Communications Server (either Office Communications Server 2007 R2 or Office Communications Server 2007) to Lync Server. The **Import-CsLegacyConfiguration** cmdlet is used to import voice policies; location profiles (for instance, dial plans); voice routes; voice normalization rules; meeting policies; external access policies; archiving policies; presence policies; Communicator Web Access URL settings; and dial-in conferencing access numbers. 
  
Before you can run the **Import-CsLegacyConfiguration** cmdlet, you must first install the Windows Management Instrumentation (WMI) Backward Compatibility interfaces package; this application is installed by running OCSWMIBC.msi. After installing the Compatibility interfaces package, you should next run the **Merge-CsLegacyTopology** cmdlet. When the **Merge-CsLegacyTopology** cmdlet finishes, you should publish the merged topology by using Topology Builder. After publishing the merged topology, you can then call the **Import-CsLegacyConfiguration** cmdlet. The **Import-CsLegacyConfiguration** cmdlet uses WMI to read legacy data from the earlier version of Office Communications Server. The **Import-CsLegacyConfiguration** cmdlet then takes the retrieved data and creates corresponding objects in Lync Server. For example, for each voice policy found in your installation of Office Communications Server, a corresponding voice policy will be created in your new installation of Lync Server. 
  
The **Import-CsLegacyConfiguration** cmdlet should be re-run whenever you make changes to any of the following Office Communications Server items: voice policies; location profiles; voice routes; voice normalization rules; meeting policies; external access policies; archiving policies; presence policies; Communicator Web Access URL settings; and dial-in conferencing access numbers. By default, only new items added to your Office Communications Server topology will be imported when you re-run the **Import-CsLegacyConfiguration** cmdlet. To import modified objects you must do two things. First, confirm that no changes have been made to the corresponding item (for example, a voice policy) in the Lync Server copy of the configuration. Second, run the **Import-CsLegacyConfiguration** cmdlet along with the ReplaceExisting parameter; this causes the **Import-CsLegacyConfiguration** cmdlet to import modified objects and to overwrite the corresponding object currently in Lync Server. Note that objects deleted from the Communications Server 2007 R2 topology do not result in corresponding deletions in Lync Server. You will need to manually remove those in Lync Server. 
  
It's important to know that the **Move-CsLegacyUser** cmdlet relies on information imported by the **Import-CsLegacyConfiguration** cmdlet. That means that, when running the **Move-CsLegacyUser** cmdlet, you might receive an error message telling you that you must run the **Import-CsLegacyConfiguration** cmdlet before proceeding. If that happens you must re-run the **Import-CsLegacyConfiguration** cmdlet before you will be able to move the legacy user. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Import-CsLegacyConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Import-CsLegacyConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _ReplaceExisting_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, this parameter instructs the **Import-CsLegacyConfiguration** cmdlet to overwrite any previously imported policies or settings that have changed since the last time the cmdlet was run.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\ImportConfiguration.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Import-CsLegacyConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Import-CsLegacyConfiguration** cmdlet does not return any objects or values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Import-CsLegacyConferenceDirectory](import-cslegacyconferencedirectory.md)
  
[Merge-CsLegacyTopology](merge-cslegacytopology.md)
  
[Move-CsLegacyUser](move-cslegacyuser.md)

