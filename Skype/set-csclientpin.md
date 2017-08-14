---
title: Set-CsClientPin
ms.prod: SKYPEFORBUSINESS
ms.assetid: d587c69c-9cf7-4cd8-81d4-26869524654b
---


# Set-CsClientPin
[]
Assigns a new personal identification number (PIN) to the specified user. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsClientPin -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Pin <String>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the user litwareinc\\kenmyer is assigned a new auto-generated PIN. To assign an auto-generated PIN, leave off the Pin parameter when calling the **Set-CsClientPin** cmdlet. After the command completes, the new PIN assigned to Ken Myer will be displayed on the screen, and that information can then be relayed to the user.
  
    
    

```

Set-CsClientPin -Identity "litwareinc\\kenmyer"
```


### EXAMPLE 2

The command in Example 2 assigns the PIN 18723834 to the user litwareinc\\kenmyer. You can assign a specific PIN by using the Pin parameter followed by the number to be assigned.
  
    
    

```
Set-CsClientPin -Identity "litwareinc\\kenmyer" -Pin 18723834
```


### EXAMPLE 3

Example 3 shows how you can auto-assign new PINs to all the users in a given Active Directory organizational unit (OU). To do this, the **Get-CsUser** cmdlet is used along with the OU parameter to return a collection of all the users who have accounts in the Finance OU. That collection is then piped to the **Set-CsClientPin** cmdlet, which generates a new PIN for each user in the collection.
  
    
    

```
Get-CsUser -OU "OU=Finance,DC=litwareinc,DC=com" | Set-CsClientPin
```


### EXAMPLE 4

The command shown in Example 4 assigns a new PIN to all the users who do not currently have a PIN assigned to them. To accomplish this task, the **Get-CsUser** cmdlet is used to return a collection of all the users who have been enabled for Skype for Business Server 2015. That collection is then piped to the **Get-CsClientPin** cmdlet and the **Where-Object** cmdlet; these two cmdlets are used to select only those users where the IsPinSet property is equal to False. The resulting collection, which contains only users who do not have a PIN, is then piped to the **Set-CsClientPin** cmdlet, which auto-generates a PIN for each user in the collection.
  
    
    

```
Get-CsUser | Get-CsClientPinInfo | Where-Object {$_.IsPinSet -eq $False} | Set-CsClientPin
```


## Detailed Description

Skype for Business Server 2015 enables users to connect to the system or to join public switched telephone network (PSTN) conferences by using a telephone. Typically, logging on to the system or joining a conference requires the user to enter a user name or password. However, entering a user name and password can be a problem if you are using a phone that does not have an alphanumeric keypad. Because of that, enables you to supply users with numeric-only PINs; when prompted, users can then log on to the system or join a conference by entering the PIN instead of a user name and password.
  
    
    
Users are not assigned a PIN when they are enabled for Skype for Business Server 2015; that means that, by default, users cannot access the system by using PIN authentication. Users can obtain a PIN from the Dial-In Conferencing webpage; alternatively, administrators can assign each user a PIN by using the **Set-CsClientPin** cmdlet. With the **Set-CsClientPin** cmdlet you can either assign a user a specific PIN or you can allow Skype for Business Server 2015 to generate a PIN for you. To auto-generate a PIN, simply omit the PIN parameter when calling the **Set-CsClientPin** cmdlet. If you do that, a new PIN will be generated, and the user's Identity and his or her new PIN will be displayed on the screen when the command completes.
  
    
    
Note that the PINs you explicitly assign must meet the conditions specified in the PIN authentication policy governing the user in question; for example, the PIN must have at least as many digits as specified by the MinPasswordLength property. Also note that PINs can contain only numbers; letters or other non-numeric characters are not allowed. 
  
    
    
When you set a client PIN using the **Set-CsClientPin** cmdlet, the PIN history count is not enforced. For example, suppose a user has a PIN number of 12345 and their client PIN policy prevents them from immediately reusing the same PIN number. If that user tries to renew his or her client PIN using the Dial-In Conferencing Web page, any attempt to reuse the same PIN number (12345) will be rejected. However, by using the **Set-CsClientPin** cmdlet an administrator can issue that user the PIN 12345. That's because the **Set-CsClientPin** cmdlet is not bound by the PIN policy history count.
  
    
    
Note that, by default, the firewall exceptions for SQL Server Express are not enabled when you install the Standard Edition of Skype for Business Server 2015. That means that you will not be able to run the **Set-CsClientPin** cmdlet from a remote instance of Windows PowerShell; that's because your command will not be able to traverse the firewall and access the SQL Server Express database. (However, you can still run the cmdlet locally on the Standard Edition server itself.) To run the **Set-CsClientPin** cmdlet remotely against a Standard Edition server you will need to manually enable the firewall exceptions for SQL Server Express.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Identity of the user account for which the PIN should be set. User Identities can be specified by using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). User Identities can also be referenced by using the user's Active Directory distinguished name.  <br/> In addition, you can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Pin_ <br/> |Optional  <br/> |System.String  <br/> |Optional PIN to be assigned to the user. If you do not include the PIN parameter, then Skype for Business Server 2015 will randomly generate a PIN and assign it to the user in question. Note that the PIN must adhere to the minimum length and common pattern settings found in the client PIN policy assigned to the user.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Set-CsClientPin** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
    
    

## Return Types

The **Set-CsClientPin** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.UserPinService.PinInfoDetails object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsClientPinInfo](get-csclientpininfo.md)
  
    
    
 [Lock-CsClientPin](lock-csclientpin.md)
  
    
    
 [Unlock-CsClientPin](unlock-csclientpin.md)
