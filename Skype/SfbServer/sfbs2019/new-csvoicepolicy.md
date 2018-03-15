---
title: "New-CsVoicePolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3852de89-a604-437a-9fdf-3597b88ce13d
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsVoicePolicy
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new voice policy. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsVoicePolicy -Identity <XdsIdentity> [-AllowCallForwarding <$true | $false>] [-AllowPSTNReRouting <$true | $false>] [-AllowSimulRing <$true | $false>] [-CallForwardingSimulRingUsageType <VoicePolicyUsage | InternalOnly | CustomUsage>] [-Confirm [<SwitchParameter>]] [-CustomCallForwardingSimulRingUsages <PSListModifier>] [-Description <String>] [-EnableBWPolicyOverride <$true | $false>] [-EnableCallPark <$true | $false>] [-EnableCallTransfer <$true | $false>] [-EnableDelegation <$true | $false>] [-EnableMaliciousCallTracing <$true | $false>] [-EnableTeamCall <$true | $false>] [-EnableVoicemailEscapeTimer <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Name <String>] [-PreventPSTNTollBypass <$true | $false>] [-PstnUsages <PSListModifier>] [-PSTNVoicemailEscapeTimer <Int64>] [-Tenant <Guid>] [-VoiceDeploymentMode <OnPrem | Online | OnlineBasic | OnPremOnlineHybrid>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example creates a new per-user voice policy (with default settings) that has an Identity of UserVoicePolicy1.
  
```
New-CsVoicePolicy -Identity UserVoicePolicy1
```

### EXAMPLE 2

This example creates a new per-user voice policy with an Identity of UserVoicePolicy2 and sets the AllowSimulRing property to False, meaning that any users to which this policy is assigned are not enabled for simultaneous ring, a feature that determines whether a second phone (such as a mobile phone) can be set to ring every time the user's office phone rings. This command also adds "Local" to the list of PSTN usages, which associates this voice policy with a voice route that also uses the Local PSTN usage. (Note that the Identity parameter is not explicitly specified. The Identity parameter is a positional parameter and therefore if you put the identity value first in the list of parameters you don't need to explicitly state that it's the Identity.)
  
```
New-CsVoicePolicy UserVoicePolicy2 -AllowSimulRing $false -PstnUsages @{add = "Local"}
```

### EXAMPLE 3

This example creates a new voice policy for site Redmond and applies all the PSTN usages defined for the organization to this policy. The first line in this example calls the **Get-CsPstnUsage** cmdlet to retrieve the global set of PSTN usages for the organization and save it in the variable $a. The second line calls the **New-CsVoicePolicy** cmdlet to create the new voice policy for site Redmond. A value is passed to the PstnUsages parameter to add the list contained in the global set of PSTN usages to this policy. Note the syntax of the add value: $a.Usage. This refers to the Usage property of the PSTN usage settings, which contains the list of PSTN usages. 
  
```
$a = Get-CsPstnUsage
New-CsVoicePolicy site:Redmond -PstnUsages @{add = $a.Usage}
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet creates a new voice policy. Voice policies are used to manage such Enterprise Voice-related features as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding. The policy created by this cmdlet determines whether many of these features are enabled or disabled.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsVoicePolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsVoicePolicy"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |XdsIdentity  <br/> |A unique identifier specifying the scope or the name of the policy. Valid values for this cmdlet are site:\<site name\> (where \<site name\> is the name of the Lync Server site to which this policy applies, such as site:Redmond), and a string designating a per-user policy, such as RedmondVoicePolicy. A global policy exists by default.  <br/> |
| _AllowCallForwarding_ <br/> |Optional  <br/> |Boolean  <br/> |If this parameter is set to True, calls can be forwarded. If this parameter is set to False, calls cannot be forwarded.  <br/> Default: True  <br/> |
| _AllowPSTNReRouting_ <br/> |Optional  <br/> |Boolean  <br/> |When this parameter is set to True, calls made to internal numbers homed on another pool will be routed through the public switched telephone network (PSTN) when the pool or WAN is unavailable.  <br/> Default: True  <br/> |
| _AllowSimulRing_ <br/> |Optional  <br/> |Boolean  <br/> |Simultaneous ring is a feature that allows multiple phones to ring when a single number is dialed. Setting this parameter to True enables this feature. If this parameter is set to False, simultaneous ring cannot be configured for any user to which this policy is assigned.  <br/> Default: True  <br/> |
| _CallForwardingSimulRingUsageType_ <br/> |Optional  <br/> |CallForwardingSimulRingUsageType  <br/> |Provides a way for administrators to manage call forwarding and simultaneous ringing. Allowed values are:  <br/> \* VoicePolicyUsage - The default voice policy usage is used to manage call forwarding and simultaneous ringing on all calls. This is the default value.  <br/> \* InternalOnly - Call forwarding and simultaneous ringing are limited to calls made from one Lync user to another.  <br/> \* CustomUsage. A custom PSTN usage will be used to manage call forwarding and simultaneous ringing. This usage must be specified using the CustomCallForwardingSimulRingUsages parameter.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CustomCallForwardingSimulRingUsages_ <br/> |Optional  <br/> |PSListModifier  <br/> |Custom PSTN usage used to manage call forwarding and simultaneous ringing. To add a custom usage to voice policy use syntax similar to this:  <br/> -CustomCallForwardingSimulRingUsages @{Add="RedmondPstnUsage"}  <br/> To remove a custom usage, use this syntax:  <br/> -CustomCallForwardingSimulRingUsages @{Remove="RedmondPstnUsage"}  <br/> Note that the usage must exist before it can be used with the CustomCallForwardingSimulRingUsages parameter.  <br/> |
| _Description_ <br/> |Optional  <br/> |String  <br/> |A description of the voice policy.  <br/> Maximum length: 1040 characters.  <br/> |
| _EnableBWPolicyOverride_ <br/> |Optional  <br/> |Boolean  <br/> |Policies can be set to manage network configuration, including limiting bandwidth. Setting this parameter to True will allow override of these policies. In other words, if this parameter is set to True, no bandwidth checks will be made and calls will go through regardless of the call admission control (CAC) settings.  <br/> Default: False  <br/> |
| _EnableCallPark_ <br/> |Optional  <br/> |Boolean  <br/> |The Call Park application allows a call to be held, or parked, at a certain number within a range of numbers for later retrieval. Setting this parameter to True enables the application. If this parameter is set to False, users assigned to this policy cannot park calls that have been dialed to their phone number.  <br/> Default: False  <br/> |
| _EnableCallTransfer_ <br/> |Optional  <br/> |Boolean  <br/> |Determines whether calls can be transferred to another number. If this parameter is set to True, calls can be transferred; if the parameter is set to False, calls cannot be transferred.  <br/> Default: True  <br/> |
| _EnableDelegation_ <br/> |Optional  <br/> |Boolean  <br/> |Call delegation allows a user to answer calls for another user or make calls on the other user's behalf. For example, a manager can set up call delegation so that all incoming calls ring both the manager's phone and the phone of an administrator. Setting this parameter to True allows users with this policy to set up call delegation. Setting this parameter to False disables call delegation.  <br/> Default: True  <br/> |
| _EnableMaliciousCallTracing_ <br/> |Optional  <br/> |Boolean  <br/> |Malicious call tracing is a standard that is in place to trace calls that a user designates as malicious. These calls can be traced even if caller ID is blocked. The trace is available only to the proper authorities, not the user. Setting this property to True enables the ability to set a trace on malicious calls.  <br/> Default: False  <br/> |
| _EnableTeamCall_ <br/> |Optional  <br/> |Boolean  <br/> |Team Call allows a user to designate a group of other users whose phones will ring when that user's number is called. This feature is useful in teams where, for example, anyone from a team can answer incoming calls from customers. Setting this parameter to True enables this feature.  <br/> Default: True  <br/> |
| _EnableVoicemailEscapeTimer_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, calls to an unanswered mobile device will be routed to the organization voicemail instead of the mobile device provider's voicemail. If a call is answered "too soon" (that is, before the value configured for the PSTNVoicemailEscapeTimer property has elapsed) it will be assumed that the mobile device is not available and the call will be routed to the organization voicemail.  <br/> The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Name_ <br/> |Optional  <br/> |String  <br/> |A displayable name describing this policy.  <br/> Default: DefaultPolicy  <br/> |
| _PreventPSTNTollBypass_ <br/> |Optional  <br/> |Boolean  <br/> |PSTN tolls are more commonly known as long-distance charges. Organizations can sometimes bypass these tolls by implementing a Voice over Internet Protocol (VoIP) solution that enables branch offices to connect by using network calls. Setting this parameter to True will send calls through the PSTN and incur charges rather than going through the network and bypassing the tolls.  <br/> Default: False  <br/> |
| _PstnUsages_ <br/> |Optional  <br/> |PSListModifier  <br/> |A list of PSTN usages available to this policy. The PSTN usage ties a voice policy to a phone route.  <br/> Any string value can be placed into this list, as long as the value exists in the current global list of PSTN usages. (Duplicate strings are not allowed; all strings must be unique.) The list of PSTN usages can be retrieved by calling the **Get-CsPstnUsage** cmdlet.  <br/> By default this list is empty. If you don't supply a value for this parameter, you'll receive a warning message stating that users granted this policy will not be able to make outbound PSTN calls.  <br/> |
| _PSTNVoicemailEscapeTimer_ <br/> |Optional  <br/> |Int64  <br/> |Amount of time (in milliseconds) used to determine whether or not a call has been answered "too soon." If a response is received within this time interval Lync Server will assume that the mobile device is not available and automatically switch the call to the organization's voicemail. If no response is received before the time interval is reached then the call will be allowed to proceed. The default value is 1500 milliseconds.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the new voice policy is being created. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> |
| _VoiceDeploymentMode_ <br/> |Optional  <br/> |VoiceDeploymentMode  <br/> |Allowed values are:  <br/> \* OnPrem  <br/> \* Online  <br/> \* OnlineBasic  <br/> \* OnPremOnlineHybrid  <br/> The default value is OnPrem.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet creates an instance of the Microsoft.Rtc.Management.WritableConfig.Voice.VoicePolicy object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsVoicePolicy](remove-csvoicepolicy.md)
  
[Set-CsVoicePolicy](set-csvoicepolicy.md)
  
[Get-CsVoicePolicy](get-csvoicepolicy.md)
  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)
  
[Test-CsVoicePolicy](test-csvoicepolicy.md)
  
[Get-CsPstnUsage](get-cspstnusage.md)

