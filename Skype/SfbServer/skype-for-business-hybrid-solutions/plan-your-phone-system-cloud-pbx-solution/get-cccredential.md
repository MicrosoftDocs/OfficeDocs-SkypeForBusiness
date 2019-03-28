---
title: "Get-CcCredential"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 8/8/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b2b5aefb-a08d-4bec-9204-76597d413849
description: "The Get-CcCredential cmdlet returns the credential of the current Skype for Business Cloud Connector Edition deployment."
---

# Get-CcCredential
 
The Get-CcCredential cmdlet returns the credential of the current Skype for Business Cloud Connector Edition deployment. 
  
With Version 2.0 and later, you can also use the -DisplayPassword parameter to show the passwords for TenantAdmin, DomainAdmin, and VMAdmin.
  
```
Get-CcCredential [[-AccountType] <string> {VmAdmin | DomainAdmin | SafeModeAdmin | ExternalCert | TenantAdmin}]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example returns the credential of the domain administrator of the Cloud Connector virtual machine domain:
  
```
Get-CcCredential -AccountType DomainAdmin
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Get-CcCredential cmdlet returns the credential information about the specified account type. These credentials are specified by the administrator who runs the Register-CcAppliance and Install-CcAppliance cmdlets when deploying the current appliance. 
  
The Get-CcCredential cmdlet returns an instance of the System.Management.Automation.PSCredential object. The password property of the return object is System.Security.SecureString.
  
If you want to get the clear text of the domain administrator password, be sure the password is input by your current logon account on the host server, and then open a PowerShell console as administrator and run the below script:
  
```
$cred = Get-CcCredential -AccountType DomainAdmin
$password =  $cred.Password
$bstr = [System.Runtime.InteropServices.Marshal]::SecureStringToBSTR($password);
$text = [System.Runtime.InteropServices.Marshal]::PtrToStringAuto($bstr);
[System.Runtime.InteropServices.Marshal]::ZeroFreeBSTR($bstr);
Write-Host $text
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| AccountType <br/> |Required  <br/> | System.String <br/> | AccountType value can be one of the following: <br/>  VmAdmin: the local administrator of Cloud Connector virtual machines. <br/>  DomainAdmin: Domain administrator of Cloud Connector virtual machine domain. <br/>  SafeModeAdmin: SafeModeAdmin of Cloud Connector virtual machine domain controller. <br/>  ExternalCert: Account of external certificate installed on the Edge Server. <br/>  TenantAdmin: Administrator of the O365 tenant. <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Get-CcCredential cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The Get-CcCredential cmdlet returns an instance of the System.Management.Automation.PSCredential object.
  
## See also
<a name="ReturnTypes"> </a>

[Set-CcCredential](set-cccredential.md)
  

