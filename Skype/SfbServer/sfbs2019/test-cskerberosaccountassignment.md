---
title: "Test-CsKerberosAccountAssignment"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 442bbb32-7ad1-40c4-bf17-42ecde0a7286
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsKerberosAccountAssignment
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Verifies the configuration of the Kerberos account assigned to a site. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsKerberosAccountAssignment -Identity <XdsIdentity> [-Report <String>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 verifies that the Kerberos account assigned to the Redmond site is configured correctly and is working as expected.
  
```
Test-CsKerberosAccountAssignment -Identity site:Redmond
```

## Detailed Description
<a name="sectionSection1"> </a>

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Lync Server enables you to create a computer account (for a computer that doesn't actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.
  
The **Test-CsKerberosAccountAssignment** cmdlet provides a way for you to verify that a Kerberos account has been associated with a given site, that this account has been configured correctly, and that the account is working as expected. 
  
Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsKerberosAccountAssignment"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Name of the site where the Kerberos account was assigned. For example: -Identity "site:Redmond".  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\TestKerberos.html".  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Test-CsKerberosAccountAssignment** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Test-CsKerberosAccountAssignment** cmdlet does not return any objects or values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)
  
[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)
  
[Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)
  
[Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

