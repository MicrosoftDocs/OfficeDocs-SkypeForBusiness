---
title: "New-CsKerberosAccount"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 67ffa1b1-0ca5-410b-81f7-2375b9dbef3c
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsKerberosAccount
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new Kerberos account used for Internet Information Services (IIS) authentication. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsKerberosAccount -UserAccount <String> [-Confirm [<SwitchParameter>]] [-ContainerDN <String>] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The commands shown in Example 1 create a new Kerberos account (litwareinc\kerberostest), and then assign that account to the Redmond site. To do this, the first command in the example creates an account with the account name "litwareinc\kerberostest". This account will be created in the Computers container in the Litwareinc.com domain. After the account has been created, the second command uses the **New-CsKerberosAccountAssignment** cmdlet to assign that Kerberos account to the Redmond site. 
  
After you make the new account assignment, the final command calls the **Enable-CsTopology** cmdlet in order to enable the changes. 
  
```
New-CsKerberosAccount -UserAccount "litwareinc\kerberostest" -ContainerDN "cn=Computers,dc=litwareinc,dc=com"
New-CsKerberosAccountAssignment -UserAccount "litwareinc\kerberostest" -Identity "site:Redmond"
Enable-CsTopology
```

## Detailed Description
<a name="sectionSection1"> </a>

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Lync Server enables you to create a computer account (for a computer that doesn't actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.
  
To run your servers under this authentication principal, you must first create a computer account by using the **New-CsKerberosAccount** cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association between the account and the Lync Server site is enabled by running the **Enable-CsTopology** cmdlet. Among other things, this creates the required service principal name (SPN) in Active Directory Domain Services. SPNs provide a way for client applications to locate a particular service. 
  
Who can run this cmdlet: You must be a domain administrator in order to run the **New-CsKerberosAccount** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsKerberosAccount\b"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _UserAccount_ <br/> |Required  <br/> |System.String  <br/> |Account name for the new account, using the format domain_name\user_name. For example: -UserAccount "litwareinc\kerberostest". Note that your command will fail if the specified account already exists.  <br/> Note, too that, despite the name UserAccount, the account created by running the **New-CsKerberosAccount** cmdlet is actually a computer account, not a user account.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ContainerDN_ <br/> |Optional  <br/> |System.String  <br/> |Distinguished name of the Active Directory container where the new account is to be created. For example: -ContainerDN "ou=Finance,dc=litwareinc,dc=com". If this parameter is not specified, then the **New-CsKerberosAccount** cmdlet will create the new account in the Computers container in Active Directory.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\KerberosAccount.html".  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsKerberosAccount** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsKerberosAccount** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccount object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)

