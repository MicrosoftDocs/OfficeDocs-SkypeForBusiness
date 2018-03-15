---
title: "Set-CsKerberosAccountPassword"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 837292b9-3c08-4c3c-a49d-3f9492518ddd
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsKerberosAccountPassword
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Locates each server running Web Services in a site that has been assigned a Kerberos account, and then updates the Internet Information Services (IIS) configuration settings on each of those servers. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsKerberosAccountPassword -UserAccount <String> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 sets the password for the Kerberos account litwareinc\kerberostest.
  
```
Set-CsKerberosAccountPassword -UserAccount "litwareinc\kerberostest"
```

### EXAMPLE 2

In Example 2, the Kerberos account password is copied from the computer atl-cs-001.litwareinc.com to the computer dublin-cs-001.litwareinc.com.
  
```
Set-CsKerberosAccountPassword -FromComputer "atl-cs-001.litwareinc.com" -ToComputer "dublin-cs-001.litwareinc.com"
```

## Detailed Description
<a name="sectionSection1"> </a>

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Lync Server enables you to create a computer account (for a computer that doesn't actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.
  
To run your servers under this new authentication principal, you must first create a computer account by using the **New-CsKerberosAccount** cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association between the account and the Lync Server site is enabled by running the **Enable-CsTopology** cmdlet. Among other things, this creates the required service principal name (SPN) in Active Directory Domain Services. SPNs provide a way for client applications to locate a particular service. 
  
After a new association has been made, the **Set-CsKerberosAccountPassword** cmdlet provides a way to modify the password assigned to the account and, equally important, update the password on every computer that uses the specified Kerberos test account for Kerberos web authentication. 
  
In addition, the cmdlet can also use the ToComputer and FromComputer parameters to copy this configuration information from one computer to another.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsKerberosAccountPassword** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsKerberosAccountPassword"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FromComputer_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the computer containing the Kerberos account's password that will be copied to another computer. This parameter cannot be used if you use the UserAccount parameter.  <br/> |
| _ToComputer_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of the computer where the Kerberos account password will be copied. This parameter cannot be used if you use the UserAccount parameter.  <br/> |
| _UserAccount_ <br/> |Required  <br/> |System.String  <br/> |Account name for the account whose password should be changed. This account name must use the format domain_name\user_name; for example: -UserAccount "litwareinc\kerberostest".  <br/> Note that, despite the name UserAccount, the account is actually a computer account, not a user account.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\SetKerberosPassword.html".  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsKerberosAccountPassword** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccount object. 
  

