---
title: "Get-CsDialInConferencingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 75a959f7-5712-4dbc-b7ac-5a15b9b2f404
description: "Retrieves information about how Skype for Business Server 2015 responds when users join or leave a dial-in conference. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsDialInConferencingConfiguration
[]
Retrieves information about how Skype for Business Server 2015 responds when users join or leave a dial-in conference. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsDialInConferencingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns a collection of all the dial-in conferencing configuration settings currently in use in the organization. Calling the **Get-CsDialInConferencingConfiguration** cmdlet without any additional parameters always returns the complete collection of dial-in conferencing settings.
  
```
Get-CsDialInConferencingConfiguration
```

### EXAMPLE 2

Example 2 returns the dial-in conferencing configuration settings with the Identity site:Redmond. 
  
```
Get-CsDialInConferencingConfiguration -Identity site:Redmond
```

### EXAMPLE 3

In Example 3, the Filter parameter is used to return all the dial-in conferencing settings that have been configured at the site scope. The filter value "site:*" instructs the **Get-CsDialInConferencingConfiguration** cmdlet to return only those settings where the Identity begins with the string value "site:". By design, any dial-conferencing settings that have an Identity beginning with "site:" represent settings configured at the site scope.
  
```
Get-CsDialInConferencingConfiguration -Filter "site:*"
```

### EXAMPLE 4

Example 4 uses the **Get-CsDialInConferencingConfiguration** cmdlet and the **Where-Object** cmdlet to return a collection of all the dial-in conferencing configuration settings where the EnableNameRecording property is set to False. To do this, the **Get-CsDialInConferencingConfiguration** cmdlet is called without any parameters in order to return a collection of all the dial-in conferencing settings. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the EnableNameRecording property is equal to False.
  
```
Get-CsDialInConferencingConfiguration | Where-Object {$_.EnableNameRecording -eq $False}
```

## Detailed Description

When users join (or leave) a dial-in conference, Skype for Business Server 2015 can respond in different ways. For example, participants might be asked to record their name before they can enter the conference itself. Likewise, administrators can decide whether they want to have Skype for Business Server 2015 announce that dial-in participants have either left or joined a conference.
  
These conference "join behaviors" are managed using dial-in conferencing configuration settings; these settings can be configured at the global scope or at the site scope. (Settings configured at the site scope take precedence over settings configured at the global scope.) The **Get-CsDialInConferencingConfiguration** cmdlet enables you to retrieve information about the dial-in conferencing configuration settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Provides a way for you to use wildcard characters when specifying dial-in conferencing configuration settings. For example, to return a collection of all the configuration settings that have been applied at the site scope use this syntax:  `-Filter "site:*"`. To return all the settings that have the term "EMEA" in their Identity use this syntax:  `-Filter "*EMEA*"`. Note that the Filter parameter acts only on the Identity of the settings; you cannot filter on other dial-in conferencing configuration properties.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the dial-in conferencing configuration settings to be retrieved. To refer to the global settings, use this syntax:  `-Identity global`. To refer to site settings, use syntax similar to this:  `-Identity site:Redmond`. You cannot use wildcards when specifying an Identity. To do that, use the Filter parameter instead.  <br/> If called without any parameters the **Get-CsDialInConferencingConfiguration** cmdlet returns information about all the dial-in conferencing configuration settings in use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the dial-in conferencing data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsDialInConferencingConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsDialInConferencingConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration object.
  
## See also

#### 

[New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)
  
[Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)
  
[Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

