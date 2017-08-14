---
title: Disable-CsUser
ms.prod: SKYPEFORBUSINESS
ms.assetid: 92e7e29e-2620-4852-9e4a-2fd3569bb095
---


# Disable-CsUser
[]
Modifies the Active Directory account of the specified user or users; this modification prevents users from using Skype for Business Server 2015 clients such as Skype for Business. The **Disable-CsUser** cmdlet only restricts activity related to Skype for Business Server 2015; it does not disable or remove a user's Active Directory account. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Disable-CsUser -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 disables the Skype for Business Server 2015 account for the user Ken Myer. In this example, the user's display name is used to indicate his Identity.
  
    
    

```

Disable-CsUser -Identity "Ken Myer"
```


### EXAMPLE 2

In Example 2, all the users in the Finance department have their Skype for Business Server 2015 accounts disabled. To carry out this task, the command first uses the **Get-CsUser** cmdlet and the LdapFilter parameter to return a collection of all the users who belong to the Finance department. That collection is then piped to the **Disable-CsUser** cmdlet, which disables each account in the collection.
  
    
    

```
Get-CsUser -LdapFilter "Department=Finance" | Disable-CsUser
```


### EXAMPLE 3

In this example, all the user accounts not currently assigned to a Registrar pool are disabled. To do this, the **Get-CsUser** cmdlet is called, along with the UnassignedUser parameter. This parameter restricts the returned data to users who have valid user accounts but are not assigned to a Registrar pool. That collection is then piped to the Disable-CsUser cmdlet, which disables each account in the collection.
  
    
    

```
Get-CsUser -UnassignedUser | Disable-CsUser
```


## Detailed Description

The **Disable-CsUser** cmdlet deletes all the attribute information related to Skype for Business Server 2015 from an Active Directory user account; this prevents the user from logging on to Skype for Business Server 2015. When you run the **Disable-CsUser** cmdlet all the Skype for Business Server 2015-related attributes are removed from an account, including the Identities of any per-user policies that have been assigned to that account. You can later re-enable the account by using the **Enable-CsUser** cmdlet. However, all the Skype for Business Server 2015-related information (such as policy assignments) previously associated with that account will have to be re-created. If you want to prevent a user from logging on to Skype for Business Server 2015, but do not want to lose all of their account information, use the **Set-CsUser** cmdlet instead. For details, see the [Set-CsUser](set-csuser.md) cmdlet help topic.
  
    
    
After an account has been disabled with the **Disable-CsUser** cmdlet, the affected user will no longer be returned by the **Get-CsUser** cmdlet; that's because that user no longer has a valid Skype for Business Server 2015 account. To retrieve information for the disabled user account, use the **Get-CsAdUser** cmdlet.
  
    
    
In addition, user data belonging to the deleted user account will be removed from the backend databases; for example, the user will be removed from Contacts lists in the organization, and any conferences scheduled by that user will be deleted.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be disabled. User Identities can be specified by using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). You can also reference a user account by using the Active Directory distinguished name.  <br/> You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to disable a user account. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-cs-001) or its fully qualified domain name (FQDN) (for example, atl-cs-001.litwareinc.com).  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user account being disabled. By default, the **Disable-CsUser** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

String or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Disable-CsUser** cmdlet accepts a pipelined string value representing the Identity of a user account that has been enabled for Skype for Business Server 2015. The cmdlet also accepts pipelined instances of the Active Directory user object.
  
    
    

## Return Types

The **Disable-CsUser** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.ADConnect.Schema.ADUser object.
  
    
    

## See also


#### 


  
    
    
 [Enable-CsUser](enable-csuser.md)
  
    
    
 [Get-CsUser](get-csuser.md)
