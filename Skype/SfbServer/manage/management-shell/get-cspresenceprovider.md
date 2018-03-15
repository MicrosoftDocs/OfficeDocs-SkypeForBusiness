---
title: "Get-CsPresenceProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15f7a7d0-d6d6-491e-a2e3-04fd2d6528d5
description: "Returns information about the presence providers configured for use in the organization. Presence providers represent the PresenceProviders property of a collection of user services configuration settings. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsPresenceProvider
 
Returns information about the presence providers configured for use in the organization. Presence providers represent the PresenceProviders property of a collection of user services configuration settings. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPresenceProvider [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the presence providers configured for use in your organization.
  
```
Get-CsPresenceProvider
```

### Example 2

Example 2 returns information about a single presence provider: the provider with the Identity global/fabrikam.com.
  
```
Get-CsPresenceProvider -Identity "global/fabrikam.com"
```

### Example 3

In Example 3, information is returned for all the presence providers configured at the site scope. To do this, the Filter parameter is used along with the filter value "site:\*". That filter value limits returned data to presence providers that have an Identity that begins with the string value "site:".
  
```
Get-CsPresenceProvider -Filter "site:*"
```

### Example 4

Example 4 returns all the presence providers that have the string value "fabrikam.com" somewhere in their Fqdn property. To carry out this task, the command first uses the **Get-CsPresenceProvider** cmdlet to return a collection of all the presence providers configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those providers where the Fqdn property includes (-match) the string value "fabrikam.com".
  
```
Get-CsPresenceProvider | Where-Object {$_.Fqdn -match "fabrikam.com"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **CsPresenceProvider** cmdlets are used to manage the PresenceProviders property found in the User Services configuration settings. Among other things, these settings are used to maintain presence information, including a collection of authorized presence providers. That collection is stored in the PresenceProviders property. The Get-CsPresenceProvider cmdlet provides a way for you to return information about the presence providers that have been authorized for use in your organization.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsPresenceProvider** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Identity of the presence provider (or providers) to be returned. For example, to return all the presence providers configured at the service scope use this filter value:  <br/>  `-Filter "service:*"` <br/> You cannot use both the Filter parameter and the Identity parameter in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the presence provider. The Identity of a presence provider is composed of two parts: the scope (Parent) where the provider has been applied (for example, service:UserServer:atl-cs-001.litwareinc.com) and the provider's fully qualified domain name. For example, to retrieve a single presence provider use syntax similar to this:  <br/>  `-Identity "global/fabrikam.com"` <br/> To return all the presence providers for a specific parent, simply specify the scope. For example, this syntax returns all the presence providers configured for the global scope:  <br/>  `-Identity "global"` <br/> If neither the Identity nor the Filter parameters are included, then the **Get-CsPresenceProvider** cmdlet returns information about all your providers. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the allowed domains from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPresenceProvider** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPresenceProvider** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
  
[New-CsPresenceProvider](new-cspresenceprovider.md)
  
[Remove-CsPresenceProvider](remove-cspresenceprovider.md)
  
[Set-CsPresenceProvider](set-cspresenceprovider.md)

