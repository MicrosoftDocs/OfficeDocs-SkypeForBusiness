---
title: Set-CsDialInConferencingConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 3300343f-c075-4b4f-aaa4-091dbf1fcd90
---


# Set-CsDialInConferencingConfiguration
[]
Modifies settings that determine how Skype for Business Server 2015 responds when users join or leave a dial-in conference. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsDialInConferencingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 modifies the EntryExitAnnoucements property for the dial-in configuration settings for the Redmond site. In this case, the EntryExitAnnouncementsType property is set to ToneOnly.
  
    
    

```

Set-CsDialInConferencingConfiguration -Identity site:Redmond -EntryExitAnnouncementsType "ToneOnly"
```


### EXAMPLE 2

Example 2 modifies all the dial-in conferencing configurations settings in use in the organization. To do this, the command first uses the **Get-CsDialInConferencingConfiguration** cmdlet to return a collection of all dial-in conferencing settings. That collection is then piped to the **Set-CsDialInConferencingConfiguration** cmdlet, which sets the EnableNameRecording property for each item in the collection to True ($True).
  
    
    

```
Get-CsDialInConferencingConfiguration | Set-CsDialInConferencingConfiguration -EnableNameRecording $True
```


### EXAMPLE 3

Example 3 modifies all the dial-in conferencing settings that have been configured at the site scope. To carry out this task, the command first uses the **Get-CsDialInConferencingConfiguration** cmdlet and the Filter parameter to return a collection of all the settings configured at the site scope; the filter value "site:*" restricts returned data to settings that have an Identity beginning with the string value "site:". That filtered collection is then piped to the **Set-CsDialInConferencingConfiguration** cmdlet, which modifies the EnableNameRecording property and the EntryExitAnnouncementsType property for each item in the collection. When the command finishes running, all the dial-in conferencing settings configured at the site scope will have their EnableNameRecording property set to True and their EntryExitAnnoucements property set to "UseNames".
  
    
    

```
Get-CsDialInConferencingConfiguration -Filter "site:*" | Set-CsDialInConferencingConfiguration -EnableNameRecording $True -EntryExitAnnouncementsType "UseNames"
```


## Detailed Description

When users join (or leave) a dial-in conference Skype for Business Server 2015 can respond in different ways. For example, participants might be asked to record their name before they can enter the conference itself. Likewise, administrators can decide whether they want to have Skype for Business Server 2015 announce that dial-in participants have either left or joined a conference.
  
    
    
These conference "join behaviors" are managed using dial-in conferencing configuration settings; these settings can be configured at the global scope or at the site scope. When you first install Skype for Business Server 2015, the only dial-in conferencing configuration settings you will have are the ones at the global scope; however, you can create new settings at the site scope by using the **New-CsDialInConferencingConfiguration** cmdlet. In addition, you can modify any of these configuration settings (at either the global or site scopes) by using the **Set-CsDialInConferencingConfiguration** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowAnonymousPstnActivation_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableNameRecording_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether or not users are asked to record their name before entering the conference. Set to True to enable name recording; set to False to bypass name recording. The default value is True.  <br/> |
| _EntryExitAnnouncementsEnabledByDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True announcements will be played each time a participant enters or exits a conference. If set to False (the default value), entry and exit announcements will not be played.  <br/> |
| _EntryExitAnnouncementsType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.EntryExitAnnouncementsType  <br/> |Indicates the action taken by the system any time a participant enters or leaves a conference. (Announcements are made only if the EntryExitAnnouncementsEnabledByDefault is set to True.) Valid values are:  <br/> UseNames. The person's name is announced any time her or she enters or leaves a conference (for example, "Ken Myer is exiting the conference").  <br/> ToneOnly. A tone is played any time a participant enters or leaves a conference.  <br/> The default value is UseNames.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the dial-in conferencing configuration settings to be modified. To refer to the global settings, use this syntax:  `-Identity global`. To refer to site settings, use syntax similar to this:  `-Identity site:Redmond`. Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _PinAuthType_ <br/> |Optional  <br/> |System.String  <br/> |Specifies which users are allowed to use PIN authentication. Allowed values are:  <br/> Everyone  <br/> OrganizerOnly  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BatchToneAnnouncements_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableAccessibilityOptions_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration object. The **Set-CSDialInConferencingConfiguration** cmdlet accepts pipelined instances of the dial-in conferencing configuration object.
  
    
    

## Return Types

The **Set-CSDialInConferencingConfiguration** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)
  
    
    
 [New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)
  
    
    
 [Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)
