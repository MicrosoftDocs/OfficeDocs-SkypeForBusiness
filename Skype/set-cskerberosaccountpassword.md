---
title: Set-CsKerberosAccountPassword
ms.prod: SKYPEFORBUSINESS
ms.assetid: 837292b9-3c08-4c3c-a49d-3f9492518ddd
---


# Set-CsKerberosAccountPassword
[]
Locates each server running Web Services in a site that has been assigned a Kerberos account, and then updates the Internet Information Services (IIS) configuration settings on each of those servers. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsKerberosAccountPassword -UserAccount <String> <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 sets the password for the Kerberos account litwareinc\\kerberostest.
  
    
    

```

Set-CsKerberosAccountPassword -UserAccount "litwareinc\\kerberostest"
```


### EXAMPLE 2

In Example 2, the Kerberos account password is copied from the computer atl-cs-001.litwareinc.com to the computer dublin-cs-001.litwareinc.com.
  
    
    

```
Set-CsKerberosAccountPassword -FromComputer "atl-cs-001.litwareinc.com" -ToComputer "dublin-cs-001.litwareinc.com"
```


## Detailed Description

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Skype for Business Server 2015 enables you to create a computer account (for a computer that doesn't actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.
  
    
    
To run your servers under this new authentication principal, you must first create a computer account by using the **New-CsKerberosAccount** cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association between the account and the Skype for Business Server 2015 site is enabled by running the **Enable-CsTopology** cmdlet. Among other things, this creates the required service principal name (SPN) in Active Directory Domain Services. SPNs provide a way for client applications to locate a particular service.
  
    
    
After a new association has been made, the **Set-CsKerberosAccountPassword** cmdlet provides a way to modify the password assigned to the account and, equally important, update the password on every computer that uses the specified Kerberos test account for Kerberos web authentication.
  
    
    
In addition, the cmdlet can also use the ToComputer and FromComputer parameters to copy this configuration information from one computer to another.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FromComputer_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the computer containing the Kerberos account's password that will be copied to another computer. This parameter cannot be used if you use the UserAccount parameter.  <br/> |
| _ToComputer_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of the computer where the Kerberos account password will be copied. This parameter cannot be used if you use the UserAccount parameter.  <br/> |
| _UserAccount_ <br/> |Required  <br/> |System.String  <br/> |Account name for the account whose password should be changed. This account name must use the format domain_name\\user_name; for example:  `-UserAccount "litwareinc\\kerberostest"`.  <br/> Note that, despite the name UserAccount, the account is actually a computer account, not a user account.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\\Logs\\SetKerberosPassword.html"`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

The **Set-CsKerberosAccountPassword** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccount object.
  
    
    

