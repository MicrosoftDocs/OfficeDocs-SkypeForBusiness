---
title: "Get-CsBackupServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8e81a76c-4019-490d-9cd5-895cc2cc0863
description: "Retrieves the backup service configuration settings for Skype for Business Server 2015. These settings include information about the maximum number of simultaneous Windows Communication Framework calls that can be made to the backup service, as well as the backup service synchronization interval. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsBackupServiceConfiguration
[]
Retrieves the backup service configuration settings for Skype for Business Server 2015. These settings include information about the maximum number of simultaneous Windows Communication Framework calls that can be made to the backup service, as well as the backup service synchronization interval. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsBackupServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 retrieves the backup service configuration information for Skype for Business Server 2015. Because there is only a single, global set of backup service configuration settings you do not need to include the Identity parameter when running this command.
  
```
Get-CsBackupServiceConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

The backup service configuration settings are used to manage pool backups in Skype for Business Server 2015. Note that Skype for Business Server 2015 allows only for a single, global collection of backup configuration settings. Among other things, that means that all your pools must be backed up using the same synchronization schedule, and that users and groups authorized to backup Pool A are also allowed to backup Pools B, C, D, and E.
  
Get-CsBackupServiceConfiguration can be run from any computer running a Skype for Business Server 2015 server role or from a remote instance of Windows PowerShell.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsBackupServiceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values when referencing a collection of backup service configuration settings. Because you can only have a single, global instance of these settings there is no reason to use the Filter parameter. However, if you prefer you can use the following syntax to reference the global settings:  <br/>  `-Filter "g*"` <br/> The preceding syntax returns all the conference backup service configuration settings that have an Identity that begins with the letter "g".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the backup service configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the **Get-CsBackupServiceConfiguration** cmdlet. You can, however, use the following syntax to reference the global settings: <br/>  `-Identity global` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the backup service configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsBackupServiceConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsBackupServiceConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)
  
[Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

