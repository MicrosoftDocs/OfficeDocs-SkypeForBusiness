---
title: "New-CsDialInConferencingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ac0b6e22-3883-4884-aa94-18f4029c7f1e
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsDialInConferencingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new collection of dial-in conferencing configuration settings. These settings determine how Lync Server responds when users join or leave a dial-in conference. In particular, information is returned regarding whether or not participants are required to record their name when joining a conference, and how (or if) the system announces that someone has joined or left the call. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsDialInConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableNameRecording <$true | $false>] [-EntryExitAnnouncementsEnabledByDefault <$true | $false>] [-EntryExitAnnouncementsType <UseNames | ToneOnly>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 creates a new collection of dial-in conferencing configuration settings that are applied to the Redmond site. In addition, the optional parameter EnableNameRecording is included in order to set the EnableNameRecording property to False.
  
```
New-CSDialInConferencingConfiguration -Identity site:Redmond -EnableNameRecording $False
```

### EXAMPLE 2

In Example 2 the InMemory parameter is used to create a new collection of dial-in conferencing configuration settings that initially exist only in memory. To do this, the example first calls the **New-CSDialInConferencingConfiguration** cmdlet, and the InMemory parameter to create a virtual settings collection that is stored in the variable $x. (Note that this collection is given the Identity site:Redmond.) After creating the virtual collection, line 2 is used to modify the value of the EnableNameRecording property. Finally, line 3 in the example calls the **Set-CSDialInConferencingConfiguration** cmdlet to transform the virtual configuration settings stored in $x into an actual collection of settings applied to the Redmond site. 
  
```
$x = New-CSDialInConferencingConfiguration -Identity site:Redmond -InMemory
$x.EnableNameRecording = $False
Set-CSDialInConferencingConfiguration -Instance $x
```

## Detailed Description
<a name="sectionSection1"> </a>

When users join (or leave) a dial-in conference, Lync Server can respond in different ways. For example, participants might be asked to record their name before they can enter the conference. Likewise, administrators can decide whether they want to have Lync Server announce that dial-in participants have either left or joined a conference.
  
These conference "join behaviors" are managed using dial-in conferencing configuration settings; these settings can be configured at the global scope or at the site scope. (Settings configured at the site scope take precedence over settings configured at the global scope.) When you first install Lync Server, the only dial-in conferencing configuration settings you will have are the ones at the global scope; however, you can create new settings at the site scope by using the **New-CSDialInConferencingConfiguration** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsDialInConferencingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsDialInConferencingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |XdsIdentity  <br/> |Indicates the Identity of the dial-in conferencing configuration settings to be created. Because these settings can only be created at the site scope, use syntax similar to this, with the prefix "site:" followed by the name of the site: -Identity site:Redmond.  <br/> Note that there can only be one set of dial-in conferencing configuration settings per site. The sample command will fail if a collection of settings with the Identity site:Redmond already exists.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableNameRecording_ <br/> |Optional  <br/> |Boolean  <br/> |Determines whether or not users are asked to record their name before entering the conference. Set to True ($True) to require name recording; set to False ($False) to bypass name recording. The default value is True.  <br/> |
| _EntryExitAnnouncementsEnabledByDefault_ <br/> |Optional  <br/> |Boolean  <br/> |If set to True announcements will be played each time a participant enters or exits a conference. If set to False (the default value), entry and exit announcements will not be played.  <br/> |
| _EntryExitAnnouncementsType_ <br/> |Optional  <br/> |EntryExitAnnouncementsType  <br/> |Indicates the action taken by the system any time a participant enters or leaves a conference. Valid values are:  <br/> UseNames. The person's name is announced any time he or she enters or leaves a conference (for example, "Ken Myer is exiting the conference").  <br/> ToneOnly. A tone is played any time a participant enters or leaves a conference.  <br/> The default value is UseNames. Note that announcements are played only if the EntryExitAnnouncementsEnabledByDefault property is set to True.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsDialInConferencingConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)
  
[Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)
  
[Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

