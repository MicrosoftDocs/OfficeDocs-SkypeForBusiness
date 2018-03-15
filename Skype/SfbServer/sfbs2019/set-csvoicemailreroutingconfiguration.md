---
title: "Set-CsVoicemailReroutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c16a0d47-318b-46e4-991c-e4842403dbe3
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsVoicemailReroutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies settings that provide public switched telephone network (PSTN) phone numbers to access Exchange UM Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example enables the voice mail rerouting configuration settings for the site Redmond1.
  
```
Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -Enabled $True
```

### EXAMPLE 2

This example modifies the voice mail rerouting settings that apply to the site Redmond1, setting the phone number for Subscriber Access to +14255551213.
  
```
Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -SubscriberAccessNumber "+14255551213"
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet allows you to modify settings that determine where Auto Attendant and Subscriber Access calls are rerouted to when IP connectivity to an Exchange UM server is lost.
  
Auto Attendant and Subscriber Access are features of Exchange UM. The Auto Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) for outside callers to navigate a company's phone system to reach the desired department or employee or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Lync Server deployment at a remote site to Exchange UM in the data center is unavailable (the SubscriberAccessNumber setting).
  
Note that these settings are not available unless the Enabled property has been set to True.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsVoicemailReroutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the RBAC roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsVoicemailReroutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AutoAttendantNumber_ <br/> |Optional  <br/> |String  <br/> |Phone number of the Auto Attendant to which the voice mail deposit attempts should be re-routed.  <br/> The number supplied to this parameter must be a LineUri of an existing contact object.  <br/> Value must be a number beginning with a digit 1 through 9, optionally preceded by a plus (+), followed by any number of digits.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether attempts to access voice mail should be re-routed through PSTN when IP connectivity is down.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsIdentity  <br/> |The unique identifier of the configuration you want to modify. For this cmdlet the Identity will be either Global or Site:\<site name\>, where \<site name\> is the name of the site to which the settings are applied.  <br/> |
| _Instance_ <br/> |Optional  <br/> |VoicemailReroutingConfiguration  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration (which can be retrieved by calling the **Get-CsVoicemailReroutingConfiguration** cmdlet).  <br/> |
| _SubscriberAccessNumber_ <br/> |Optional  <br/> |String  <br/> |Subscriber Access number to which the voice mail retrieval attempts should be re-routed.  <br/> The number supplied to this parameter must be a LineUri of an existing contact object.  <br/> Value must be a number beginning with a digit 1 through 9, optionally preceded by a plus (+), followed by any number of digits.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration object. Accepts pipelined input of voice mail rerouting configuration objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)
  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)
  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

