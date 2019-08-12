---
title: "Set-CcCredential"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 8/8/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 784ff94a-4b33-4dbd-ba74-27acc3eb6954
description: "The Set-CcCredential cmdlet sets the credential of the current Skype for Business Cloud Connector Edition deployment."
---

# Set-CcCredential
 
The Set-CcCredential cmdlet sets the credential of the current Skype for Business Cloud Connector Edition deployment. 
  
With Cloud Connector version 2.0 and later, this cmdlet can also set the account information for the virtual machine administrator and for the domain administrator.
  
```
Set-CcCredential [[-AccountType] <string> {TenantAdmin}]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example specifies the account name and password for the tenant administrator:
  
```
Set-CcCredential -AccountType "TenantAdmin"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Set-CcCredential cmdlet sets the account name and password for the tenant administrator. For releases prior to 2.0, this administrator must be an Office 365 Global Administrator. Cloud Connector uses this account to get configuration information, set configuration parameters, and update appliance status to the Office 365 tenant configuration. With release 2.0 and later, you can also use this cmdlet to update the passwords for the VmAdmin and DomainAdmin accounts.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| AccountType <br/> | Required <br/> |System.String  <br/> | Parameter value must be "TenantAdmin", "VmAdmin", or "DomainAdmin". <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Set-CcCredential cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Get-CcCredential](get-cccredential.md)
  

