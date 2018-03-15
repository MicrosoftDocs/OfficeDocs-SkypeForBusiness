---
title: "Get-CsBackupServiceStatus"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7f56cc81-534c-48e8-9f74-5741d4534a83
description: "Returns information about the current state of the backup service for a specified pool. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsBackupServiceStatus
 
Returns information about the current state of the backup service for a specified pool. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsBackupServiceStatus -PoolFqdn <Fqdn> [-Category <UserData | CMS>] [-Force <SwitchParameter>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The preceding command returns the backup service status for the pool atl-cs-001.litwareinc.com.
  
```
Get-CsBackupServiceStatus -PoolFqdn "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsBackupServiceStatus** cmdlet enables administrators to verify that the backup service for a specified Registrar pool has been configured and is working properly. Note that, by default, only users who belong to the RTCUniversalServerAdmins group are allowed to run this cmdlet and check the backup status for a pool. To provide additional groups with permission to run the cmdlet, use the **Set-CsBackupServiceConfiguration** cmdlet to add those groups to the AuthorizedUniversalGroups property.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsBackupServiceStatus** cmdlet are not available in the Skype for Business Server 2015.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool whose backup service status is being checked. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _Category_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Hadr.BackupService.BackupCategory  <br/> |Type of backup whose status is being checked. Allowed values are:  <br/> \* CMS  <br/> \* UserData  <br/> If this parameter is not specified then both backup types will be checked.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsBackupServiceStatus** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

Returns information about the backup service.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)

