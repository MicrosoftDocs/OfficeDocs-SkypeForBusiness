---
title: "New-CsVoicemailReroutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 37750c6d-9b75-4dde-aa52-79210afe34c2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsVoicemailReroutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates settings that, when enabled, provide phone numbers that Lync Server routes to over public switched telephone network (PSTN) if IP connectivity from Lync Server in the branch site to the Exchange UM Server located in the data center is not available. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsVoicemailReroutingConfiguration -Identity <XdsIdentity> [-AutoAttendantNumber <String>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-SubscriberAccessNumber <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example creates new voice mail rerouting settings that apply to the site Redmond1. The Enabled parameter is set to True to turn on this configuration, and a phone number (+14255551212) is supplied to specify the Auto-Attendant to which calls will be rerouted.
  
```
New-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -Enabled $True -AutoAttendantNumber "+14255551212"
```

### EXAMPLE 2

This example creates new voice mail rerouting settings that apply to the site Redmond1. A phone number (+14255551213) is supplied to specify the Subscriber Access number to which calls will be rerouted. Notice that the Enabled parameter has not been set. Enabled is set to False by default, so Subscriber Access calls will not be rerouted to this number until the Enabled property is set to True.
  
```
New-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -SubscriberAccessNumber "+14255551213"
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet allows you to create settings that are applied at either the global or site level that determine where Auto-Attendant and Subscriber Access calls are rerouted to over PSTN when IP connectivity is lost.
  
Auto-Attendant and Subscriber Access are features of Exchange UM. The Auto-Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) for outside callers to navigate a company's phone system to reach the department or employee that they want or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Lync Server deployment at a remote site to Exchange UM in the data center is unavailable (the SubscriberAccessNumber setting).
  
Note that these settings are not available unless the Enabled property has been set to True.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsVoicemailReroutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsVoicemailReroutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |This parameter contains a unique identifier specifying the scope at which this configuration is applied. New voice mail rerouting configurations can be created only at the site level, so the Identity would be in the format Site:<site name>, where <site name> is the name of the site to which the settings are applied. A global voice mail rerouting configuration exists by default and cannot be re-created by calling the **New-CsVoicemailReroutingConfiguration** cmdlet.  <br/> |
| _AutoAttendantNumber_ <br/> |Optional  <br/> |System.String  <br/> |Phone number of the Auto-Attendant to which the voice mail deposit attempts should be re-routed.  <br/> The number supplied to this parameter must be a LineUri of an existing contact object.  <br/> Value must be a number beginning with a digit 1 through 9, optionally preceded by a plus (+), followed by any number of digits.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether attempts to access voice mail should be re-routed through PSTN when IP connectivity is down.  <br/> Default: False  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _SubscriberAccessNumber_ <br/> |Optional  <br/> |System.String  <br/> |Subscriber Access number to which the voice mail retrieval attempts should be re-routed.  <br/> The number supplied to this parameter must be a LineUri of an existing contact object.  <br/> Value must be a number beginning with a digit 1 through 9, optionally preceded by a plus (+), followed by any number of digits.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)
  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)
  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

