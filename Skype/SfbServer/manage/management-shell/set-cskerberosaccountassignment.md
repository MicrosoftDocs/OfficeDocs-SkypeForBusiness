---
title: "Set-CsKerberosAccountAssignment"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 16a964d2-2515-4a37-9686-3e377de58b14
description: "Associates a Kerberos account, which is used for IIS Internet Information Services (IIS) authentication, with a site. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsKerberosAccountAssignment
[]
Associates a Kerberos account, which is used for IIS Internet Information Services (IIS) authentication, with a site. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsKerberosAccountAssignment [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The commands shown in Example 1 associate an existing Kerberos account (litwareinc\keberostest) with the Redmond site, then use the **Enable-CsTopology** cmdlet to enable the new association. To do this, the first command in the example uses the **Set-CsKerberosAccountAssignment** cmdlet to associate the account litwareinc\keberostest with the Redmond site; the second command then calls the **Enable-CsTopology** cmdlet in order to create the required service principal name in Active Directory and to enable the modified account assignment.
  
```
Set-CsKerberosAccountAssignment -UserAccount "litwareinc\keberostest" -Identity "site:Redmond"
Enable-CsTopology
```

## Detailed Description

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Skype for Business Server 2015 enables you to create a computer account (for a computer that doesn't actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.
  
To run your servers under this new authentication principal, you must first create a computer account by using the **New-CsKerberosAccount** cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association between the account and the Skype for Business Server 2015 site is enabled by running the **Enable-CsTopology** cmdlet. Among other things, this creates the required service principal name (SPN) in Active Directory Domain Services. SPNs provide a way for client applications to locate a particular service.
  
The **Set-CsKerberosAccountAssignment** cmdlet enables you to change the Kerberos account assigned to a given site. This cmdlet is used for sites that are already associated with an account. To assign an account to a site that currently is not associated with a Kerberos account, use the **New-CsKerberosAccountAssignment** cmdlet instead.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the site where the Kerberos account was assigned. (This is the Identity of the site, not of the computer account.) For example:  `-Identity "site:Redmond"`.  <br/> |
| _Instance_ <br/> |Optional  <br/> |KerberosAccountAssignment object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _UserAccount_ <br/> |Optional  <br/> |System.String  <br/> |Account name for the account to be assigned, using the format domain_name\user_name. For example:  `-UserAccount "litwareinc\kerberostest"`. The user name portion of the account (kerberostest) is a NETBIOS name and can contain a maximum of 15 characters.  <br/> Note that, despite the name UserAccount, the account is actually a computer account, not a user account.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment object. The **Set-CsKerberosAccountAssignment** cmdlet accepts pipelined instances of the Kerberos account assignment object.
  
## Return Types

The **Set-CsKerberosAccountAssignment** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment object.
  
## See also

#### 

[Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)
  
[New-CsKerberosAccount](new-cskerberosaccount.md)
  
[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)
  
[Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

