---
title: Invoke-CsUcsRollback
ms.prod: SKYPEFORBUSINESS
ms.assetid: 0aed0286-e552-4d47-93bc-3375cab48a03
---


# Invoke-CsUcsRollback
[]
Removes a user's contacts from the Unified Contact Store and, instead, stores that contact information in Skype for Business Server 2015. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Skype for Business, Microsoft Outlook, and/or Microsoft Outlook Web Access. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Invoke-CsUcsRollback -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 removes the user Ken Myer from the unified contact store.
  
    
    

```

Invoke-CsUcsRollback -Identity "Ken Myer"
```


### Example 2

In Example 2, all the users homed on the Registrar pool atl-cs-001.litwareinc.com are removed from the unified contact store. To do this, the command first calls the **Get-CsUser** cmdlet along with the Filter parameter; the filter value {RegistrarPool -eq "atl-cs-001.litwareinc.com"} limits the returned data to users homed on the pool atl-cs-001.litwareinc.com. Those user accounts are then piped to the **Invoke-CsUcsRollback** cmdlet, which removes each user from the unified contact store. In order to suppress the confirmation prompt that would otherwise occur each time the cmdlet rolls back a user account, the Confirm parameter is included using this syntax: `-Confirm:$False`
  
    
    

```
Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Invoke-CsUcsRollback -Confirm:$False
```


## Detailed Description
<a name="DetailedDescription"> </a>

The unified contact store introduced in Skype for Business Server 2015 gives administrators the option of storing a user's contacts in Exchange instead of in Skype for Business Server 2015; in turn that allows the user to access the same set of contacts in Microsoft Outlook and Outlook Web Access as well as in Skype for Business. (Alternatively, you can continue to store contacts in Skype for Business Server 2015. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web Access, and one for use with Skype for Business Server 2015.)
  
    
    
In order to take advantage of the unified contact store you must (among other things) assign the user a user services policy that enables the use of the unified contact store; if all the other prerequisites have been met, then the next time the user logs on using Skype for Business Server 2015 his or her contacts will automatically be moved from Skype for Business Server 2015 to the unified contact store. See the help topic for the Set-CsUserServicesPolicy cmdlet for more information.
  
    
    
If later decide to move those contacts back to Skype for Business Server 2015 (and out of the unified contact store) then you need to do two things. First, you must assign the user a new user services policy, one that prohibits the use of the unified contact store. Second, you must use the **Invoke-CsUcsRollback** cmdlet to "manually" migrate the contacts from the unified contact store back to Skype for Business Server 2015. Simply changing the user services policy will not remove the user's contacts from the unified contact store; that can only be done by calling the **Invoke-CsUcsRollback** cmdlet.
  
    
    
Note. Technically, calling the **Invoke-CsUcsRollback** cmdlet by itself, without modifying the user services policy, will remove a user's contacts from the unified contact store. However, this change will only be temporary: if you do not change the user services policy then, after a 7-day waiting period, the user's contacts will automatically be moved back into the unified contact store.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Invoke-CsUcsRollback** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be rolled back. User Identities are typically specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).  <br/> You can also reference a user account by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. To prevent a confirmation prompt from appearing each time you roll back a user account use this syntax:  <br/>  `-Confirm:$False` <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve user information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user account being removed from the Unified Contact Store. By default, the **Invoke-CsUcsRollback** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Invoke-CsUcsRollback** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [New-CsUserServicesPolicy](new-csuserservicespolicy.md)
  
    
    
 [Set-CsUserServicesPolicy](set-csuserservicespolicy.md)
  
    
    
 [Test-CsUnifiedContactStore](test-csunifiedcontactstore.md)
