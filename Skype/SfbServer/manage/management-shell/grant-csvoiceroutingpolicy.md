---
title: "Grant-CsVoiceRoutingPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a7c7b6c4-925a-464c-a3ee-8373f4eb46b2
description: "Assigns a per-user voice routing policy to one or more users. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Skype for Business Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013."
---

# Grant-CsVoiceRoutingPolicy
 
Assigns a per-user voice routing policy to one or more users. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Skype for Business Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013.
  
```
Grant-CsVoiceRoutingPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 assigns the per-user voice routing policy RedmondVoiceRoutingPolicy to the user with the Active Directory display name "Ken Myer".
  
```
Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName "RedmondVoiceRoutingPolicy"
```

### Example 2

In Example 2, any per-user voice routing policy previously assigned to the user Ken Myer is unassigned from that user; as a result, Ken Myer will be managed by the global voice routing policy. To unassign a per-user policy, set the PolicyName to a null value ($Null).
  
```
Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName $Null
```

### Example 3

Example 3 assigns the per-user voice routing policy RedmondVoiceRoutingPolicy to all the users in the Redmond OU in Active Directory. To do this, the command first calls the **Get-CsUser** cmdlet long with the OU parameter; the parameter value "OU=Redmond,dc=litwareinc,dc=com" limits the returned data to user accounts in the Redmond OU. Those user accounts are then piped to the **Grant-CsVoiceRoutingPolicy** cmdlet, which assigns each user the voice routing policy RedmondVoiceRoutingPolicy.
  
```
Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | Grant-CsVoiceRoutingPolicy -PolicyName "RedmondVoiceRoutingPolicy"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Voice routing policies are used in "hybrid" scenarios: when some of your users are homed on the on-premises version of Skype for Business Server 2015 and other users are homed on Skype for Business Online. Assigning your Skype for Business Online users a voice routing policy enables those users to receive and to place phones calls to the public switched telephone network by using your on-premises SIP trunks.
  
Note that simply assigning a user a voice routing policy will not enable them to make PSTN calls via Skype for Business Online. Among other things, you will also need to enable those users for Enterprise Voice and will need to assign them an appropriate voice policy and dial plan.
  
 **Skype for Business Server Control Panel:** The functions carried out by the Grant-CsVoiceRoutingPolicy cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be assigned the per-user voice routing policy. User Identities are typically specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).  <br/> User Identities can also be specified by using the user's Active Directory distinguished name.  <br/> In addition, you can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" returns all the users who have a display name that ends with the string value " Smith".  <br/> |
| _PolicyName_ <br/> |Required  <br/> |System.String  <br/> |"Name" of the policy to be assigned. The PolicyName is simply the policy Identity minus the policy scope (the "tag:" prefix). For example, a policy with the Identity tag:Redmond has a PolicyName equal to Redmond; likewise, a policy with the Identity tag:RedmondVoiceRoutingPolicy has a PolicyName equal to RedmondVoiceRoutingPolicy.  <br/> To unassign a per-user policy previously assigned to a user, set the PolicyName to a null value ($Null).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve user information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user account being assigned the voice routing policy. By default, the **Grant-CsVoiceRoutingPolicy** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Grant-CsVoiceRoutingPolicy** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
## Return Types
<a name="ReturnTypes"> </a>

By default, the **Grant-CsVoiceRoutingPolicy** cmdlet does not return a value or object. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)
  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)
  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)
  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)

