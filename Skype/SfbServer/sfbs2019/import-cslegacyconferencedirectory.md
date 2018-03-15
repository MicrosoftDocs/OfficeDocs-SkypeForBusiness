---
title: "Import-CsLegacyConferenceDirectory"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5ecb9bf9-cbce-48a6-966c-ecbdac59cb3a
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Import-CsLegacyConferenceDirectory
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
The **Import-CsLegacyConferenceDirectory** cmdlet enables you to import conference directories from Microsoft Office Communications Server 2007 R2 to Lync Server. This helps provide interoperability between Lync Server and Office Communications Server 2007 R2. This cmdlet was introduced in Lync Server 2010. 
  
```
Import-CsLegacyConferenceDirectory [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 imports conferencing directories from Communications Server 2007 R2 to Lync Server. 
  
```
Import-CsLegacyConferenceDirectory
```

## Detailed Description
<a name="sectionSection1"> </a>

The **Import-CsLegacyConferenceDirectory** cmdlet is used in conjunction with the **Merge-CsLegacyTopology** cmdlet to enable organizations to migrate from Office Communications Server 2007 R2 to Lync Server. The **Import-CsLegacyConfiguration** cmdlet imports conferencing directories from Communications Server 2007 R2 to Lync Server. 
  
Before you can run the **Import-CsLegacyConferenceDirectory** cmdlet, you must first install the Windows Management Instrumentation (WMI) Backward Compatibility interfaces package; this application is installed by running OCSWMIBC.msi. (OCSWMIBC.msi can be found on the Lync Server installation DVD in the Setup folder.) After installing the Backward Compatibility interfaces package, you should next run the **Merge-CsLegacyTopology** cmdlet. 
  
When the **Merge-CsLegacyTopology** cmdlet finishes running, you can call the **Import-CsLegacyConferenceDirectory** cmdlet. The **Import-CsLegacyConferenceDirectory** cmdlet first uses WMI to read legacy data from Communications Server 2007 R2, then takes the retrieved data and creates corresponding objects in Lync Server: for each conferencing directory found in your installation of Communications Server 2007 R2, a corresponding directory will be created in your new installation of Lync Server. 
  
The **Import-CsLegacyConferenceDirectory** cmdlet should be rerun anytime conferences directories are added, deleted, or moved in the Communications Server 2007 R2 environment. The **Import-CsLegacyConferenceDirectory** cmdlet should also be run anytime the **Merge-CsLegacyTopology** cmdlet is run; this helps to ensure the conference directories and the topology remain in sync. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Import-CsLegacyConferenceDirectory** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Import-CsLegacyConferenceDirectory"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\ImportDirectories.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Import-CsLegacyConferenceDirectory** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Import-CsLegacyConferenceDirectory** cmdlet does not return any objects or values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Import-CsLegacyConfiguration](import-cslegacyconfiguration.md)
  
[Merge-CsLegacyTopology](merge-cslegacytopology.md)
  
[Move-CsLegacyUser](move-cslegacyuser.md)

