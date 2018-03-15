---
title: "Update-CsUserDatabase"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 86ed4291-70cc-4c41-ab2a-e5f7546a0f1f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Update-CsUserDatabase
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Forces the back-end user database to clear its replication status with Active Directory. This causes the database to re-read all the user-related information stored in Active Directory Domain Services. This cmdlet was introduced in Lync Server 2010.
  
```
Update-CsUserDatabase [-Force <SwitchParameter>] [-Fqdn <Fqdn>]
```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

The Lync Server user database holds detailed information about such things as contacts, groups, and access permissions. As such, the database is required to periodically synch its contents with the information stored in Active Directory. 
  
More often than not, the automatic synch between the user database and Active Directory will keep the information in the user database up to date. However, it is possible that a problem might occur that prevents this automatic synchronization from taking place. In a case such as that, you can use the **Update-CsUserDatabase** cmdlet to force the user database to refresh its contents by re-reading all of the user information stored in Active Directory. You might also need to run this cmdlet if a product update ever includes a change to the user replicator service. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Update-CsUserDatabase** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Update-CsUserDatabase"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Fqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the computer hosting the user database. If this parameter is not specified then the **Update-CsUserDatabase** cmdlet will update the user database for the pool that the local computer belongs to.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Update-CsUserDatabase** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Update-CsUserDatabase** cmdlet updates instances of the Microsoft.Rtc.Management.Xds.DisplayuserDatabase object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsUserDatabaseState](get-csuserdatabasestate.md)
  
[Set-CsUserDatabaseState](set-csuserdatabasestate.md)

