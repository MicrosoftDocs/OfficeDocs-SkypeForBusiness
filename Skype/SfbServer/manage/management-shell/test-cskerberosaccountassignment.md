---
title: "Test-CsKerberosAccountAssignment"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 442bbb32-7ad1-40c4-bf17-42ecde0a7286
description: "Verifies the configuration of the Kerberos account assigned to a site. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsKerberosAccountAssignment
[]
Verifies the configuration of the Kerberos account assigned to a site. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsKerberosAccountAssignment -Identity <XdsIdentity> [-Report <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 verifies that the Kerberos account assigned to the Redmond site is configured correctly and is working as expected.
  
```
Test-CsKerberosAccountAssignment -Identity site:Redmond
```

## Detailed Description

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Skype for Business Server 2015 enables you to create a computer account (for a computer that doesn't actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.
  
The **Test-CsKerberosAccountAssignment** cmdlet provides a way for you to verify that a Kerberos account has been associated with a given site, that this account has been configured correctly, and that the account is working as expected.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Name of the site where the Kerberos account was assigned. For example:  `-Identity "site:Redmond"`.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\TestKerberos.html"`.  <br/> |
   
## Input Types

None. The **Test-CsKerberosAccountAssignment** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsKerberosAccountAssignment** cmdlet does not return any objects or values.
  
## See also

#### 

[Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)
  
[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)
  
[Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)
  
[Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

