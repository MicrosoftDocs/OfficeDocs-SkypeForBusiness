---
title: "Get-CsWebServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 28582668-839c-4b04-8211-928c91634672
description: "Returns information about all the Web Services configuration settings in use in your organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsWebServiceConfiguration
[]
Returns information about all the Web Services configuration settings in use in your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsWebServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns information about all the Web Services configuration settings currently in use in the organization.
  
```
Get-CsWebServiceConfiguration
```

### EXAMPLE 2

The command shown in Example 2 returns information about the Web Services configuration settings that have the Identity site:Redmond.
  
```
Get-CsWebServiceConfiguration -Identity site:Redmond
```

### EXAMPLE 3

Example 3 returns all the Web Services configuration settings that have been assigned at the site scope. To do this, the Filter parameter is included when calling the **Get-CsWebServiceConfiguration** cmdlet; the filter value "site:*" ensures that only those settings that have an Identity that begins with the string value "site:" are returned.
  
```
Get-CsWebServiceConfiguration -Filter "site:*"
```

### EXAMPLE 4

In Example 4, the command returns all the Web Services configuration settings that do not allow personal identification number (PIN) authentication. This is done by first calling the **Get-CsWebServiceConfiguration** cmdlet to return all the Web Services configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the UsePinAuth property is equal to False.
  
```
Get-CsWebServiceConfiguration | Where-Object {$_.UsePinAuth -eq $False}
```

### EXAMPLE 5

Example 5 returns all the Web Services configuration settings where the maximum group expansion size is greater than 100. To do this, the command first uses the **Get-CsWebServiceConfiguration** cmdlet to return all the Web Services configuration settings currently in use. This information is then piped to the **Where-Object** cmdlet, which selects only those settings where the MaxGroupSizeToExpand property is greater than 100.
  
```
Get-CsWebServiceConfiguration | Where-Object {$_.MaxGroupSizeToExpand -gt 100}
```

## Detailed Description

Many Skype for Business Server 2015 components are web-based: these components either use web services or webpages to carry out their tasks. For example, users employ a web service when searching for new contacts in the Address Book or when using group expansion to view the individual members of a distribution group. Likewise, components ranging from dial-in conferencing to Skype for Business Server Control Panel use webpages as the interface between Skype for Business Server 2015 and users.
  
The **CsWebServiceConfiguration** cmdlets enable administrators to manage Web Services configuration settings throughout the organization; this includes managing group expansion, certificate settings, and allowed authentication methods. Because you can configure different settings at the global, site, and service scope (albeit for the only the Web Services service), you can customize Web Services capabilities for different users and different locations.
  
The **Get-CsWebServiceConfiguration** cmdlet enables you to return detailed information about the Web Services configuration settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Web Services configuration settings collection (or collections) to be returned. For example, this syntax returns all the settings configured at the site scope:  <br/>  `-Filter "site:*"` <br/> You cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Web Services configuration settings to be returned. To return the global settings, use this syntax:  <br/>  `-Identity global` <br/> To return settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> Service-scope settings can be returned using syntax like this:  <br/>  `-Identity "service:WebServer:atl-cs-001.litwareinc.com"` <br/> You cannot use both the Filter and the Identity parameters in the same command. If you do not specify either parameter, the **Get-CsWebServiceConfiguration** cmdlet will return all the Web Services settings collections currently in use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Web Services configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsWebServiceConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsWebServiceConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Web.WebServiceSettings object.
  
## See also

#### 

[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)
  
[Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)
  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

