---
title: "Get-CsKerberosAccountAssignment"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6eaba274-1693-42a7-841d-513bc1153647
description: "Returns information about the Kerberos account assignments configured for use in the organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsKerberosAccountAssignment
 
Returns information about the Kerberos account assignments configured for use in the organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsKerberosAccountAssignment [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns information about all the Kerberos account assignments currently in use in the organization.
  
```
Get-CsKerberosAccountAssignment
```

### EXAMPLE 2

Example 2 returns information about a single Kerberos account assignment: the account assignment for the Redmond site.
  
```
Get-CsKerberosAccountAssignment -Identity "site:Redmond"
```

### EXAMPLE 3

In Example 3, information is returned for all the Kerberos accounts that have been assigned to sites that have the string value "Redmond" somewhere in their site Identity. To do this, the Filter parameter is included along with the filter value "\*Redmond".
  
```
Get-CsKerberosAccountAssignment -Filter "*Redmond*"
```

### EXAMPLE 4

Example 4 returns information about all the Kerberos account assignments where the identity of the assigned account includes the string value "litwareinc". To carry out this task, the command first calls the **Get-CsKerberosAccountAssignment** cmdlet without any parameters; that returns a collection of all the Kerberos accounts assignments currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those account assignments where the identity of the account includes the string value "litwareinc". (Note that, despite the parameter name UserAccount, the account in question is actually a computer account.)
  
```
Get-CsKerberosAccountAssignment | Where-Object {$_.UserAccount -match "litwareinc"}
```

## Detailed Description

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Skype for Business Server 2015 enables you to create a computer account (for a computer that doesn't actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.
  
To run your servers under this new authentication principal, you must first create a computer account by using the **New-CsKerberosAccount** cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association between the account and the Skype for Business Server 2015 site is enabled by running the **Enable-CsTopology** cmdlet. Among other things, this creates the required service principal name (SPN) in Active Directory Domain Services. SPNs provide a way for client applications to locate a particular service.
  
The **Get-CsKerberosAccountAssignment** cmdlet provides a way for you to return information about the Kerberos account assignments currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when specifying the Kerberos account assignment (or assignments) to be returned. For example, this syntax returns all the account assignments that include the string value "Europe":  `-Filter "*Europe*"`.  <br/> You cannot use both the Identity and the Filter parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the site where the Kerberos account was assigned; for example:  `-Identity "site:Redmond"`. (Note that this is the Identity of the site, not of the computer account.) You cannot use wildcards when specifying the site identity. To employ wildcards, use the Filter parameter instead.  <br/> If neither the Identity nor the Filter parameter is included, then the **Get-CsKerberosAccountAssignment** cmdlet returns all the Kerberos account assignments configured for use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Kerberos assignment data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsKerberosAccountAssignment** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsKerberosAccountAssignment** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment object.
  
## See also

#### 

[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)
  
[Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)
  
[Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

