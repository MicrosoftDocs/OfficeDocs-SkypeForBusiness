---
title: "Remove-CsVoicemailReroutingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 758cea84-5979-417c-a0cd-c76748e0da79
description: "Removes settings that provide public switched telephone network (PSTN) phone numbers to access Exchange Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsVoicemailReroutingConfiguration
 
Removes settings that provide public switched telephone network (PSTN) phone numbers to access Exchange Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoicemailReroutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example removes the voice mail rerouting configuration settings for the site Redmond1.
  
```
Remove-CsVoicemailReroutingConfiguration -Identity site:Redmond1
```

### EXAMPLE 2

This example removes all the voice mail rerouting settings for this deployment of Skype for Business Server 2015. The command first retrieves all the voice mail rerouting configuration settings by calling the **Get-CsVoicemailReroutingConfiguration** cmdlet. The settings retrieved by this call are then passed to the **Remove-CsVoicemailReroutingConfiguration** cmdlet to delete each one.
  
```
Get-CsVoicemailReroutingConfiguration | Remove-CsVoicemailReroutingConfiguration
```

## Detailed Description

This cmdlet allows you to remove settings that determine where Auto Attendant and Subscriber Access calls are rerouted to over PSTN when IP connectivity is lost.
  
Auto Attendant and Subscriber Access are features of Exchange. The Auto Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) for outside callers to navigate a company's phone system to reach the desired department or employee or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Skype for Business Server 2015 deployment at a remote site to Exchange in the data center is unavailable (the SubscriberAccessNumber setting).
  
Note that if you call this cmdlet to remove the Global settings, those settings will simply be reset to their defaults.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the configuration you want to remove. For this cmdlet the Identity will be either Global or Site:\<site name\>, where \<site name\> is the name of the site to which the settings are applied.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration object. Accepts pipelined input of voice mail rerouting configuration objects.
  
## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.
  
## See also

#### 

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)
  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)
  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

