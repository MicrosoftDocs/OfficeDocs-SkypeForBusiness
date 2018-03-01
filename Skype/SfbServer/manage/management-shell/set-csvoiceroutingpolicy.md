---
title: "Set-CsVoiceRoutingPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cff51726-88c6-4cdf-aaad-a7246c4408c5
description: "Modifies an existing voice routing policy. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Skype for Business Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsVoiceRoutingPolicy
 
Modifies an existing voice routing policy. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Skype for Business Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsVoiceRoutingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 adds the PSTN usage "Long Distance" to the per-user voice routing policy RedmondVoiceRoutingPolicy.
  
```
Set-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -PstnUsages @{Add="Long Distance"}
```

### Example 2

In Example 2, the PSTN usage "Local" is removed from the per-user voice routing policy RedmondVoiceRoutingPolicy.
  
```
Set-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -PstnUsages @{Remove="Local"}
```

### Example 3

Example 3 removes the PSTN usage "Local" is removed from all the voice routing policies that include that usage. In order to do this, the command first calls the **Get-CsVoiceRoutingPolicy** cmdlet without any parameters in order to return a collection of all the available voice routing policies. That collection is then piped to the Where-Object cmdlet, which picks out only those policies where the PstnUsages property includes (-contains) the "Local" usage. Those policies are then piped to the **Set-CsVoiceRoutingPolicy** cmdlet, which deletes the Local usage from each policy.
  
```
Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -contains "Local"} | Set-CsVoiceRoutingPolicy -PstnUsages @{Remove="Local"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Voice routing policies are used in "hybrid" scenarios: when some of your users are homed on the on-premises version of Skype for Business Server 2015 and other users are homed on Skype for Business Online. Assigning your Skype for Business Server 2015 users a voice routing policy enables those users to receive and to place phones calls to the public switched telephone network by using your on-premises SIP trunks.
  
Note that simply assigning a user a voice routing policy will not enable them to make PSTN calls via Skype for Business Online. Among other things, you will also need to enable those users for Enterprise Voice and will need to assign them an appropriate voice policy and dial plan.
  
 **Skype for Business Server Control Panel:** The functions carried out by the Set-CsVoiceRoutingPolicy cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide explanatory text to accompany a voice routing policy. For example, the Description might include information about the users the policy should be assigned to.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier assigned to the policy when it was created. Voice routing policies can be assigned at the global scope or the per-user scope. To refer to the global instance, use this syntax:  <br/>  `-Identity global` <br/> To refer to a per-user policy, use syntax similar to this:  <br/>  `-Identity "RedmondVoiceRoutingPolicy"` <br/> If you do not specify an Identity, then the **Set-CsVoiceRoutingPolicy** cmdlet will modify the global policy. <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |A friendly name describing this policy.  <br/> |
| _PstnUsages_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list of PSTN usages (such as Local or Long Distance) that can be applied to this voice routing policy. The PSTN usage must be an existing usage. (PSTN usages can be retrieved by calling the **Get-CsPstnUsage** cmdlet.) <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsVoiceRoutingPolicy** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsVoiceRoutingPolicy** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)
  
[Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)
  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)
  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)

