---
title: "Set-CsBackupServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 72ed064e-5f67-481f-802a-74846cecb189
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsBackupServiceConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Retrieves the backup service configuration settings for Lync Server 2013. These settings include information about the maximum number of simultaneous Windows Communication Framework calls that can be made to the backup service as well as the backup service synchronization interval. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsBackupServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 assigns the Active Directory security group Schema Admins to the AuthorizedUniversalGroup property for the global collection of backup service settings.
  
```
Set-CsBackupServiceConfiguration -Identity "global" -AuthorizedUniversalGroup "Schema Admins"
```

### Example 2

In Example 2, the MaxConcurrentCalls property of the global collection of backup service settings is set to 12.
  
```
Set-CsBackupServiceConfiguration -Identity "global" -MaxConcurrentCalls 12
```

### Example 3

Example 3 modifies the SyncInterval property of the global collection of backup service settings. In this example, SyncInterval is set to 10 minutes: 00 hours : 10 minutes : 00 seconds.
  
```
Set-CsBackupServiceConfiguration -Identity "global" -SyncInterval "00:10:00"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The backup service configuration settings are used to manage pool backups in Lync Server 2013. Note that Lync Server allows only for a single, global collection of backup configuration settings. Among other things, that means that all your pools must be backed up using the same synchronization schedule, and that users and groups authorized to backup Pool A are also allowed to backup Pools B, C, D, and E.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsBackupServiceConfiguration"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsBackupServiceConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AuthorizedLocalAccounts_ <br/> |Optional  <br/> |System.String  <br/> |Names of the local users/local groups that are authorized to run the backup service. The default value is Network Service.  <br/> |
| _AuthorizedUniversalGroups_ <br/> |Optional  <br/> |System.String  <br/> |Names of the universal groups authorized to run the backup service. The default value is Schema admins.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the backup service configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the **Set-CsBackupServiceConfiguration** cmdlet. If you prefer, however, you can use the following syntax to reference the global settings:  <br/> -Identity global  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MaxBatchesPerCmsSync_ <br/> |Optional  <br/> |System.Int32  <br/> |Maximum number of batches that the CMS backup module will export during each export cycle. The default value is 500.  <br/> |
| _MaxBatchesPerUserStoreSync_ <br/> |Optional  <br/> |System.Int32  <br/> |Maximum number of batches that the User Store backup module will export during each export cycle. The default value is 500.  <br/> |
| _MaxConcurrentCalls_ <br/> |Optional  <br/> |System.Int32  <br/> |The maximum number of Windows Communication Foundation (WCF) calls that can be made to the backup service at the same time. The default value is 10.  <br/> |
| _MaxDataConfPackageSizeKB_ <br/> |Optional  <br/> |System.Int32  <br/> |Maximum size of the data package (in kilobytes) that the Data Conference module will export during each export cycle. The default value is 102400.  <br/> |
| _SyncInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time that the service waits before synchronizing a pool with its backup pool. The default value is 2 minutes (00:02:00, or 00 hours, 02 minutes, 00 seconds). The SyncInterval can be configured to any value between 5 seconds (00:00:05) and 3 hours (03:00:00), inclusive.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsBackupServiceConfiguration** cmdlet accepts piped instances of the Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsBackupServiceConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)
  
[Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)

