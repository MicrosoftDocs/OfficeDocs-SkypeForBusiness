---
title: "Remove-CsTrustedApplicationPool"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 93aa3381-e3fc-45df-840e-3d6d61a52fb3
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsTrustedApplicationPool
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a pool that contains the computers that host trusted applications. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsTrustedApplicationPool -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the pool with the FQDN TrustPool.litwareinc.com. We use the Identity parameter to specify the FQDN of the pool we want to remove. Because identities are unique, this command will remove, at most, one pool.
  
```
Remove-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com
```

### EXAMPLE 2

This example removes all trusted pools where the FQDN of the pool begins with the string "trust". The first part of the command is a call to the **Get-CsTrustedApplicationPool** cmdlet, which retrieves a collection of all trusted application pools in your Lync Server infrastructure. This collection is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet checks each item in the collection to see whether the PoolFqdn matches the wildcard string trust*. This will result in a collection of all trusted application pools with a PoolFqdn that begins with the string trust followed by any character or characters. Finally, this collection is piped to the **Remove-CsTrustedApplicationPool** cmdlet, which removes every item in the collection. 
  
```
Get-CsTrustedApplicationPool | Where-Object {$_.PoolFqdn -match "trust*"} | Remove-CsTrustedApplicationPool
```

## Detailed Description
<a name="sectionSection1"> </a>

It is recommended that the computers that are running trusted applications within a Lync Server deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. This cmdlet removes an existing trusted application pool. However, you cannot remove a trusted application pool that does not have a Registrar value. If the trusted application pool has not been assigned a Registrar, you must add a Registrar value with the **Set-CsTrustedApplicationPool** cmdlet, and then remove the pool. 
  
Keep in mind that removing the pool also removes all computers, applications, and application endpoints associated with that pool.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsTrustedApplicationPool** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsTrustedApplicationPool"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The fully qualified domain name (FQDN) or service ID of the pool you want to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.Xds.DisplayExternalServer object. Accepts pipelined input of trusted application pool objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Xds.DisplayExternalServer.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)
  
[Set-CsTrustedApplicationPool](set-cstrustedapplicationpool.md)
  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)

