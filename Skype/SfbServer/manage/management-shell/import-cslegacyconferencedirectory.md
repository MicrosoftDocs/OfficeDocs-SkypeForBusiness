---
title: "Import-CsLegacyConferenceDirectory"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5ecb9bf9-cbce-48a6-966c-ecbdac59cb3a
description: "The Import-CsLegacyConferenceDirectory cmdlet enables you to import conference directories from Microsoft Office Communications Server 2007 R2 to Skype for Business Server 2015. This helps provide interoperability between Skype for Business Server 2015 and Office Communications Server 2007 R2. This cmdlet was introduced in Lync Server 2010."
---

# Import-CsLegacyConferenceDirectory
[]
The **Import-CsLegacyConferenceDirectory** cmdlet enables you to import conference directories from Microsoft Office Communications Server 2007 R2 to Skype for Business Server 2015. This helps provide interoperability between Skype for Business Server 2015 and Office Communications Server 2007 R2. This cmdlet was introduced in Lync Server 2010.
  
```
Import-CsLegacyConferenceDirectory [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 imports conferencing directories from Communications Server 2007 R2 to Skype for Business Server 2015. 
  
```
Import-CsLegacyConferenceDirectory
```

## Detailed Description

The **Import-CsLegacyConferenceDirectory** cmdlet is used in conjunction with the **Merge-CsLegacyTopology** cmdlet to enable organizations to migrate from Office Communications Server 2007 R2 to Skype for Business Server 2015. The **Import-CsLegacyConfiguration** cmdlet imports conferencing directories from Communications Server 2007 R2 to Skype for Business Server 2015.
  
Before you can run the **Import-CsLegacyConferenceDirectory** cmdlet, you must first install the Windows Management Instrumentation (WMI) Backward Compatibility interfaces package; this application is installed by running OCSWMIBC.msi. (OCSWMIBC.msi can be found on the Skype for Business Server 2015 installation DVD in the Setup folder.) After installing the Backward Compatibility interfaces package, you should next run the **Merge-CsLegacyTopology** cmdlet.
  
When the **Merge-CsLegacyTopology** cmdlet finishes running, you can call the **Import-CsLegacyConferenceDirectory** cmdlet. The **Import-CsLegacyConferenceDirectory** cmdlet first uses WMI to read legacy data from Communications Server 2007 R2, then takes the retrieved data and creates corresponding objects in Skype for Business Server 2015: for each conferencing directory found in your installation of Communications Server 2007 R2, a corresponding directory will be created in your new installation of Skype for Business Server 2015.
  
The **Import-CsLegacyConferenceDirectory** cmdlet should be rerun anytime conferences directories are added, deleted, or moved in the Communications Server 2007 R2 environment. The **Import-CsLegacyConferenceDirectory** cmdlet should also be run anytime the **Merge-CsLegacyTopology** cmdlet is run; this helps to ensure the conference directories and the topology remain in sync.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\ImportDirectories.html"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Import-CsLegacyConferenceDirectory** cmdlet does not accept pipelined input.
  
## Return Types

The **Import-CsLegacyConferenceDirectory** cmdlet does not return any objects or values.
  
## See also

#### 

[Import-CsLegacyConfiguration](import-cslegacyconfiguration.md)
  
[Merge-CsLegacyTopology](merge-cslegacytopology.md)
  
[Move-CsLegacyUser](move-cslegacyuser.md)

