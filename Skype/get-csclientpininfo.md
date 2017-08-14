---
title: Get-CsClientPinInfo
ms.prod: SKYPEFORBUSINESS
ms.assetid: 45feaa2c-f284-4374-a8a6-d3ff3c87d660
---


# Get-CsClientPinInfo
[]
Retrieves information about the personal identification number (PIN) assigned to a user. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsClientPinInfo -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 returns PIN information for all the users who have been enabled for Skype for Business Server 2015. To do this, the command first calls the **Get-CsUser** cmdlet to return all users who have been enabled for Skype for Business Server 2015. That collection is piped to the **Get-CsClientPinInfo** cmdlet, which displays PIN information for each user in the collection.
  
    
    

```

Get-CsUser | Get-CsClientPinInfo
```


### EXAMPLE 2

In Example 2, the **Get-CsClientPinInfo** cmdlet is used to display PIN information for a single user: the user with the Identity litwareinc\\kenmyer.
  
    
    

```
Get-CsClientPinInfo -Identity "litwareinc\\kenmyer"
```


### EXAMPLE 3

Example 3 returns PIN information for all the users with accounts in the Finance organizational unit (OU). To do this, the **Get-CsUser** cmdlet and the OU parameter are used to return a collection of all the users in the Finance OU. That collection is then piped to the **Get-CsClientPinInfo** cmdlet, which displays PIN information for each user in the collection.
  
    
    

```
Get-CsUser -OU "OU=Finance,DC=litwareinc,DC=com" | Get-CsClientPinInfo
```


### EXAMPLE 4

The command shown in Example 4 displays PIN information for all the Managers in the organization. To retrieve a collection of all the Managers, the command uses the **Get-CsUser** cmdlet and the LdapFilter parameter; the filter value "Title=Manager" limits the returned collection to users who have "Manager" as their job title. The **Get-CsClientPinInfo** cmdlet is then used to display PIN information for each of these users.
  
    
    

```
Get-CsUser -LdapFilter "Title=Manager" | Get-CsClientPinInfo
```


## Detailed Description

Skype for Business Server 2015 enables users to connect to the system or to join public switched telephone network (PSTN) conferences by using a telephone. Typically, logging on to the system or joining a conference requires the user to enter a user name or password. However, entering a user name and password can be an issue if you are using a phone that does not have an alphanumeric keypad. Because of that, Skype for Business Server 2015 enables you to supply users with numeric-only PINs; when prompted, users can then log on to the system or join a conference by entering the PIN instead of a user name and password.
  
    
    
Administrators can retrieve the PIN settings for a user, or a group of users, by running the **Get-CsClientPinInfo** cmdlet. Note that there is no way for an administrator to retrieve the PIN that has been assigned to a user. If a user forgets his or her PIN, that user will not be able to use PIN authentication to access the system until an administrator has assigned them a new PIN or the user has obtained a new PIN from the Dial-In Conferencing webpage.
  
    
    
Note that, by default, the firewall exceptions for SQL Server Express are not enabled when you install the Standard Edition of Skype for Business Server 2015. That means that you will not be able to run the **Get-CsClientPinInfo** cmdlet from a remote instance of Windows PowerShell; that's because your command will not be able to traverse the firewall and access the SQL Server Express database. (However, you can still run the cmdlet locally on Standard Edition server.) To run the **Get-CsClientPinInfo** cmdlet remotely against a Standard Edition server you will need to manually enable the firewall exceptions for SQL Server Express.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account for which the PIN should be locked. User Identities can be specified by using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). You can also reference a user account by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Get-CsClientPinInfo** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
    
    

## Return Types

The **Get-CsClientPinInfo** cmdlet returns one or more instances of the Microsoft.Rtc.Management.UserPinService.PinInfoDetails object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsPinPolicy](get-cspinpolicy.md)
  
    
    
 [Lock-CsClientPin](lock-csclientpin.md)
  
    
    
 [Set-CsClientPin](set-csclientpin.md)
  
    
    
 [Unlock-CsClientPin](unlock-csclientpin.md)
