---
title: "Remove-CsVoicemailReroutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 758cea84-5979-417c-a0cd-c76748e0da79
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsVoicemailReroutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes settings that provide public switched telephone network (PSTN) phone numbers to access Exchange UM Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoicemailReroutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the voice mail rerouting configuration settings for the site Redmond1.
  
```
Remove-CsVoicemailReroutingConfiguration -Identity site:Redmond1
```

### EXAMPLE 2

This example removes all the voice mail rerouting settings for this deployment of Lync Server. The command first retrieves all the voice mail rerouting configuration settings by calling the **Get-CsVoicemailReroutingConfiguration** cmdlet. The settings retrieved by this call are then passed to the **Remove-CsVoicemailReroutingConfiguration** cmdlet to delete each one. 
  
```
Get-CsVoicemailReroutingConfiguration | Remove-CsVoicemailReroutingConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet allows you to remove settings that determine where Auto Attendant and Subscriber Access calls are rerouted to over PSTN when IP connectivity is lost.
  
Auto Attendant and Subscriber Access are features of Exchange UM. The Auto Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) for outside callers to navigate a company's phone system to reach the desired department or employee or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Lync Server deployment at a remote site to Exchange UM in the data center is unavailable (the SubscriberAccessNumber setting).
  
Note that if you call this cmdlet to remove the Global settings, those settings will simply be reset to their defaults.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoicemailReroutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsVoicemailReroutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the configuration you want to remove. For this cmdlet the Identity will be either Global or Site:\<site name\>, where \<site name\> is the name of the site to which the settings are applied.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration object. Accepts pipelined input of voice mail rerouting configuration objects.
  
## Return Types
<a name="sectionSection3"> </a>

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)
  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)
  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

