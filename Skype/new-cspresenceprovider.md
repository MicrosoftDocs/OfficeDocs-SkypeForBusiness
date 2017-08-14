---
title: New-CsPresenceProvider
ms.prod: SKYPEFORBUSINESS
ms.assetid: 55110f49-f8d5-4287-89d3-ae069d8090d3
---


# New-CsPresenceProvider
[]
Authorizes a new presence provider for use in the organization. Presence providers represent the PresenceProviders property of a collection of user services configuration settings. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

New-CsPresenceProvider -Identity <XdsIdentity> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 creates a new presence provider (with the fully qualified domain name "fabrikam.com") that will be added to the global collection of user services configuration settings.
  
    
    

```

New-CsPresenceProvider -Parent "global" -Fqdn "fabrikam.com"


```


### Example 2

Example 2 adds a presence provider with the Fqdn "fabrikam.com" to all the user services configuration collections in the organization. To do this, the command first uses the **Get-CsUserServicesConfiguration** cmdlet to return a collection of all the user services settings. Those settings are then piped to the ForEach-Object, which takes each item in the collection and a creates a new presence provider for that collection, using "fabrikam.com" as the presence provider Fqdn and the Identity of the user services collection as the presence provider Parent.
  
    
    

```

Get-CsUserServicesConfiguration | ForEach-Object {New-CsPresenceProvider -Parent $_.Identity -Fqdn "fabrikam.com"}
```


## Detailed Description
<a name="DetailedDescription"> </a>

The **CsPresenceProvider** cmdlets are used to manage the PresenceProviders property found in the User Services configuration settings. Among other things, these settings are used to maintain presence information, including a collection of authorized presence providers. That collection is stored in the PresenceProviders property. You can use the **New-CsPresenceProvider** cmdlet to add an authorized presence provider to a collection of User Services configuration settings.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **New-CsPresenceProvider** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Fqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name for the presence provider. For example:  <br/>  `-Fqdn "fabrikam.com"` <br/> If you use the Fqdn parameter you must also use the Parent parameter. However, the Fqdn parameter cannot be used in the same command as the Identity parameter.  <br/> Note that FQDNs must be unique at a given scope.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new presence provider. The Identity of a presence provider is composed of two parts: the scope (Parent) where the rule has been applied (for example, service:UserServer:atl-cs-001.litwareinc.com) and the provider's fully qualified domain name. To create a new provider at the global scope use syntax similar to this:  <br/>  `-Identity "global/fabrikam.com"` <br/> To create a provider at the site scope, use syntax like this:  <br/>  `-Identity "site:Redmond/fabrikam.com"` <br/> To create a provider at the service scope (for the UserServer service only), use syntax similar to this:  <br/>  `-Parent "UserServer:atl-cs-001.litwareinc.com"` <br/> You cannot use the Identity parameter in the same command as the Fqdn or the Parent parameter.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Scope where the new presence provider will be created. To create a new presence provider at the global scope, use syntax similar to this:  <br/>  `-Parent "global"` <br/> To create a new provider at the site scope use syntax like this:  <br/>  `-Parent "site:Redmond"` <br/> To create a provider at the service scope (for the UserServer service only), use syntax similar to this:  <br/>  `-Parent "UserServer:atl-cs-001.litwareinc.com"` <br/> If you use the Parent parameter you must also include the Fqdn parameter. However, the Parent parameter cannot be used in conjunction with the Identity parameter.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **New-CsPresenceProvider** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **New-CsPresenceProvider** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider#Decorated object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsPresenceProvider](get-cspresenceprovider.md)
  
    
    
 [Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
  
    
    
 [Remove-CsPresenceProvider](remove-cspresenceprovider.md)
  
    
    
 [Set-CsPresenceProvider](set-cspresenceprovider.md)
