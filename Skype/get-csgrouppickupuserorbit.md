---
title: Get-CsGroupPickupUserOrbit
ms.prod: SKYPEFORBUSINESS
ms.assetid: 4590555b-d578-4990-8a2f-f030e1c31929
---


# Get-CsGroupPickupUserOrbit
[]
Use the **Get-CsGroupPickupUserOrbit** cmdlet to get the group pickup orbit number for an Enterprise Voice user.
  
    
    


```

Get-CsGroupPickupUserOrbit -User <String> [-Force <SwitchParameter>]

```


## Examples
<a name="Examples"> </a>


### Example 1

The following example gets the group pickup orbit number of a user specified by SIP address.
  
    
    

```

Get-CsGroupPickupUserOrbit -User sip:ken.myer@contoso.com
```


### Example 2

The following example gets the group pickup orbit number by using the display name.  _User_ is a positional parameter. The first parameter after the cmdlet is assumed to be the _User_ parameter value.
  
    
    

```
Get-CsGroupPickupUserOrbit "Ken Myer"
```


### Example 3

The following example gets the group pickup orbit numbers by piping the output of **Get-CsUser** to the **Get-CsGroupPickupUserOrbit**.
  
    
    

```
Get-CsUser "Ken Myer" | Get-CsGroupPickupUserOrbit
```


## Parameters
<a name="Examples"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _User_ <br/> |Required  <br/> |System.String  <br/> |Specifies the user whose group pickup orbit number will be retrieved. Because  _User_ is a positional parameter, the `-User` syntax is not required. The first parameter after the cmdlet is assumed to be the _User_ parameter value. <br/> User identities can be specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). You can also reference a user account by using the user's Active Directory distinguished name.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

This cmdlet supports pipelined input from the **Get-CsUser** cmdlet.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

This cmdlet return an instance of the **[Microsoft.Rtc.Management.Voice.Helpers.GroupPickup.DisplayGroupPickupUserOrbit]** object.
  
    
    

