---
title: New-CsGroupPickupUserOrbit
ms.prod: SKYPEFORBUSINESS
ms.assetid: 7c0d90cd-0a67-4711-9005-b424d8235c57
---


# New-CsGroupPickupUserOrbit
[]
Use the **New-CsGroupPickupUserOrbit** cmdlet to assign and enable a group pickup orbit number for an Enterprise Voice user.
  
    
    


```

New-CsGroupPickupUserOrbit -Orbit <String> -User <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

This example adds a user specified by the SIP address to the *100 orbit.
  
    
    

```

New-CsGroupPickupUserOrbit -User sip:KenMyers@Contoso.com -Orbit "*100"
```


### Example 2

This example adds a user specified by display name to the 2103 orbit. Because  _User_ is a positional parameter, the `-User` syntax is not required. The first parameter after the cmdlet is assumed to be the _User_ parameter value.
  
    
    

```
New-CsGroupPickupUserOrbit "Ken Myers" -Orbit 2103
```


## Detailed Description
<a name="DetailedDescription"> </a>

The same orbit can be assigned to multiple users. This cmdlet will throw an exception if the user is already assigned a group pickup orbit number, or if the specified orbit does not exist or is of the wrong type.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Orbit_ <br/> |Required  <br/> |System.String  <br/> |Specifies the group pickup orbit number to be assigned to the user. The number must be within an orbit pickup range that was created with a type of  _GroupPickup_. For more information on creating call park orbits, see  [New-CsCallParkOrbit](https://technet.microsoft.com/en-us/library/gg398936.aspx).  <br/> Values for the  _Orbit_ parameter must match the regular expression ([\\*|#]?[1-9]\\d{0,7})|([1-9]\\d{0,8}). <br/> |
| _User_ <br/> |Required  <br/> |System.String  <br/> |Specifies the user whose group pickup orbit number will be assigned. Because  _User_ is a positional parameter, the `-User` syntax is not required. The first parameter after the cmdlet is assumed to be the _User_ parameter value. <br/> User identities can be specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). You can also reference a user account by using the user's Active Directory distinguished name.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

This cmdlet supports pipelined input from the **Get-CsUser** cmdlet.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

This cmdlet returns an instance of the **[Microsoft.Rtc.Management.Voice.Helpers.GroupPickup.DisplayGroupPickupUserOrbit]** object.
  
    
    

