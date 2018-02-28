---
title: "Remove-CsBackupServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 56bbf0a2-20cf-4f1e-b305-3521659eb909
description: "Resets the properties in the backup service configuration settings for Skype for Business Server 2015 to their default values. These settings include information about the maximum number of simultaneous Windows Communication Framework calls that can be made to the backup service as well as the backup service synchronization interval. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsBackupServiceConfiguration
[]
Resets the properties in the backup service configuration settings for Skype for Business Server 2015 to their default values. These settings include information about the maximum number of simultaneous Windows Communication Framework calls that can be made to the backup service as well as the backup service synchronization interval. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsBackupServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 resets the backup service configuration settings for Skype for Business Server 2015. Note that even though Skype for Business Server 2015 only uses a single, global collection of backup settings you must still include the Identity parameter: if you do not, the **Remove-CsBackupServiceConfiguration** cmdlet will prompt you for the Identity before continuing.
  
```
Remove-CsBackupServiceConfiguration -Identity "global"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The backup service configuration settings are used to manage pool backups in Skype for Business Server 2015. Note that Skype for Business Server 2015 allows only for a single, global collection of backup configuration settings. Among other things, that means that all your pools must be backed up using the same synchronization schedule, and that users and groups authorized to backup Pool A are also allowed to backup Pools B, C, D, and E.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsBackupServiceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the backup service configuration settings. Although you can only have a single, global instance of these settings, you still need to specify an Identity when calling the **Remove-CsBackupServiceConfiguration** cmdlet: <br/>  `-Identity global` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsBackupServiceConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsBackupServiceConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)
  
[Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

