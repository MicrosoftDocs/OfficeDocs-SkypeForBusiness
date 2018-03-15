---
title: "New-CsVoiceRoutingPolicy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9e5bd6f6-902f-4911-ab88-9abb581df7fd
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsVoiceRoutingPolicy
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Creates a new voice routing policy. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Skype for Business Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Lync Server 2013. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsVoiceRoutingPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Name <String>] [-PstnUsages <PSListModifier>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new per-user voice routing policy with the Identity RedmondVoiceRoutingPolicy. This policy is assigned a single PSTN usage: Long Distance.
  
```
New-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -Name "RedmondVoiceRoutingPolicy" -PstnUsages "Long Distance"
```

### Example 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the new policy is assigned three PSTN usages: Long Distance; Local; Internal. Multiple usages can be assigned simply by separating each usage using a comma.
  
```
New-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -Name "RedmondVoiceRoutingPolicy" -PstnUsages "Long Distance", "Local", "Internal"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Voice routing policies are used in "hybrid" scenarios: when some of your users are homed on the on-premises version of Lync Server and other users are homed on Skype for Business Online. Assigning your Skype for Business Online users a voice routing policy enables those users to receive and to place phones calls to the public switched telephone network by using your on-premises SIP trunks.
  
Note that simply assigning a user a voice routing policy will not enable them to make PSTN calls via Skype for Business Online. Among other things, you will also need to enable those users for Enterprise Voice and will need to assign them an appropriate voice policy and dial plan.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsVoiceRoutingPolicy"}
  
 **Lync Server Control Panel:** The functions carried out by the New-CsVoiceRoutingPolicy cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier to be assigned to the new voice routing policy. Because you can only create new policies at the per-user scope, the Identity will always be the "name" being assigned to the policy. For example:  <br/> -Identity "RedmondVoiceRoutingPolicy"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide explanatory text to accompany a voice routing policy. For example, the Description might include information about the users the policy should be assigned to.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |A friendly name describing this policy.  <br/> |
| _PstnUsages_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list of PSTN usages (such as Local or Long Distance) that can be applied to this voice routing policy. The PSTN usage must be an existing usage. (PSTN usages can be retrieved by calling the **Get-CsPstnUsage** cmdlet.)  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsVoiceRoutingPolicy** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsVoiceRoutingPolicy** cmdlet creates new instances of Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)
  
[Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)
  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)
  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)

