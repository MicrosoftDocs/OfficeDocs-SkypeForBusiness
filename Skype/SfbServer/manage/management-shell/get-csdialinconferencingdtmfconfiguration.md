---
title: "Get-CsDialInConferencingDtmfConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 764741e4-c1cb-4627-8774-95cf08f6cf98
description: "Returns the dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing. DTMF enables users who dial in to a conference to control conference settings (such as muting and unmuting themselves or locking and unlocking the conference) by using the keypad on their telephone. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsDialInConferencingDtmfConfiguration
 
Returns the dual-tone multifrequency (DTMF) signaling settings used for dial-in conferencing. DTMF enables users who dial in to a conference to control conference settings (such as muting and unmuting themselves or locking and unlocking the conference) by using the keypad on their telephone. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsDialInConferencingDtmfConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command show in Example 1 returns the DTMF settings for the Redmond site. 
  
```
Get-CsDialInConferencingDtmfConfiguration -Identity site:Redmond
```

### EXAMPLE 2

Example 2 returns a collection of all the DTMF settings, and then, for each item in the collection, displays the value of the key to be pressed in order to privately play a description of DTMF commands. To do this, the **Get-CsDialInConferencingDtmfConfiguration** cmdlet is called in order to return a collection of all the property values for all the DTMF settings currently in use in the organization. That collection is then piped to the **Select-Object** cmdlet, which picks two properties (Identity and HelpCommand) to be displayed on the screen.
  
```
Get-CsDialInConferencingDtmfConfiguration | Select-Object Identity, HelpCommand
```

### EXAMPLE 3

The command shown in Example 3 returns all the DTMF settings that have been configured at the site scope. This is done by including the Filter parameter and the filter value "site:\*". That filter value limits the returned data to settings that have an Identity that begins with the characters "site:". By definition, those are settings configured at the site scope.
  
```
Get-CsDialInConferencingDtmfConfiguration -Filter "site:*"
```

### EXAMPLE 4

Example 4 returns all the DTMF configuration settings where the AdmitAll property is not equal to 8 (the default value). To accomplish this task, the **Get-CsDialInConferencingDtmfConfiguration** cmdlet is first called without any parameters in order to return a collection of all the DTMF settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the AdmitAll property is not equal to 8.
  
```
Get-CsDialInConferencingDtmfConfiguration | Where-Object {$_.AdmitAll -ne 8}
```

## Detailed Description

Skype for Business Server 2015 enables users to join conferences by dialing in over the telephone. Dial-in users are not able to view video or exchange instant messages with other conference attendees, but they are able to fully participate in the audio portion of the meeting.
  
In addition to being able to join a conference, users are also able to manage selected portions of that conference by using their telephone keypad. (The specific conference settings users can and cannot manage depend on whether or not the user is a presenter.) For example, by default users can press the 6 key on their keypad to mute or unmute themselves. Participants can privately play the names of all the other people attending the meeting, while presenters can do such things as mute and unmute all the meeting participants and enable/disable the announcement that is played any time someone joins or leaves a conference.
  
The ability to make selections using a telephone keypad is known as dual-tone multifrequency (DTMF) signaling: if you have ever dialed a phone number and been instructed to do something along the order of "Press 1 for English or press 2 for Spanish," then you have used DTMF signaling. The **Get-CsDialInConferencingDtmfConfiguration** cmdlet enables you to retrieve a list of all the available DTMF commands as well as the keys used to carry out those commands.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection (or collections) of DTMF configuration settings. To return a collection of all the settings configured at the site scope, use this syntax:  `-Filter site:*`. To return a collection of all the settings that have the string value "EMEA" somewhere in their Identity (the only property you can filter for), use this syntax:  `-Filter *EMEA*.` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the unique identifier for the collection of DTMF settings you want to return. To refer to the global settings, use this syntax:  `-Identity global`. To refer to a collection configured at the site scope, use syntax similar to this:  `-Identity site:Redmond`. Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, then use the Filter parameter instead.  <br/> If this parameter is not specified, then the **Get-CsDialInConferencingDtmfConfiguration** cmdlet returns a collection of all the DTMF configuration settings in use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the DTMF configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsDialInConferencingDtmfConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsDialInConferencingDtmfConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingDtmfConfiguration object.
  
## See also

#### 

[New-CsDialInConferencingDtmfConfiguration](new-csdialinconferencingdtmfconfiguration.md)
  
[Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)
  
[Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)

