---
title: "Update-CsUserDatabase"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 86ed4291-70cc-4c41-ab2a-e5f7546a0f1f
description: "Forces the back-end user database to clear its replication status with Active Directory. This causes the database to re-read all the user-related information stored in Active Directory Domain Services. This cmdlet was introduced in Lync Server 2010."
---

# Update-CsUserDatabase
 
Forces the back-end user database to clear its replication status with Active Directory. This causes the database to re-read all the user-related information stored in Active Directory Domain Services. This cmdlet was introduced in Lync Server 2010.
  
```
Update-CsUserDatabase [-Force <SwitchParameter>] [-Fqdn <Fqdn>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 locates the user database for the pool where the local computer is located, then forces that database to connect to and return complete user information from Active Directory.
  
```
Update-CsUserDatabase
```

### EXAMPLE 2

Example 2 shows how you can force a specific user database to re-read data from Active Directory. In this case, that's the user database for the pool atl-cs-001.litwareinc.com.
  
```
Update-CsUserDatabase -Fqdn atl-cs-001.litwareinc.com
```

## Detailed Description

The Skype for Business Server 2015 user database holds detailed information about such things as contacts, groups, and access permissions. As such, the database is required to periodically synch its contents with the information stored in Active Directory. 
  
More often than not, the automatic synch between the user database and Active Directory will keep the information in the user database up to date. However, it is possible that a problem might occur that prevents this automatic synchronization from taking place. In a case such as that, you can use the **Update-CsUserDatabase** cmdlet to force the user database to refresh its contents by re-reading all of the user information stored in Active Directory. You might also need to run this cmdlet if a product update ever includes a change to the user replicator service.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Fqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the computer hosting the user database. If this parameter is not specified then the **Update-CsUserDatabase** cmdlet will update the user database for the pool that the local computer belongs to. <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Update-CsUserDatabase** cmdlet does not accept pipelined input.
  
## Return Types

None. Instead, the **Update-CsUserDatabase** cmdlet updates instances of the Microsoft.Rtc.Management.Xds.DisplayUserDatabase object.
  
## See also

#### 

[Get-CsUserDatabaseState](get-csuserdatabasestate.md)
  
[Set-CsUserDatabaseState](set-csuserdatabasestate.md)

