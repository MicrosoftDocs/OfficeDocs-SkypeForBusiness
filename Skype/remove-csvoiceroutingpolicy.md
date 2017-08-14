---
title: Remove-CsVoiceRoutingPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 3729e908-5c0d-4970-bdff-5869ba2082c9
---


# Remove-CsVoiceRoutingPolicy
[]
Deletes an existing voice routing policy. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Skype for Business Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Remove-CsVoiceRoutingPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 deletes the voice routing policy RedmondVoiceRoutingPolicy
  
    
    

```

Remove-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy"
```


### Example 2

In Example 2, all the voice routing policies configured at the per-user scope are removed. To do this, the command first calls the **Get-CsVoiceRoutingPolicy** cmdlet along with the Filter parameter; the filter value "tag:*" limits the returned data to voice routing policies configured at the per-user scope. Those per-user policies are then piped to, and removed by, the **Remove-CsVoiceRoutingPolicy** cmdlet.
  
    
    

```
Get-CsVoiceRoutingPolicy -Filter "tag:*" | Remove-CsVoiceRoutingPolicy
```


### Example 3

In Example 3, all the voice routing polices that include the PSTN usage "Long Distance" are removed. To carry out this task, the **Get-CsVoiceRoutingPolicy** cmdlet is first called without any parameters in order to return a collection of all the available voice routing policies. That collection is then piped to the Where-Object cmdlet, which picks out only those policies where the PstnUsages property includes (-contains) the usage "Long Distance." Policies that meet that criterion are then piped to the **Remove-CsVoiceRoutingPolicy**, which removes each voice routing policy that includes the PSTN usage "Long Distance".
  
    
    

```
Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -contains "Long Distance"} | Remove-CsVoiceRoutingPolicy
```


## Detailed Description
<a name="DetailedDescription"> </a>

Voice routing policies are used in "hybrid" scenarios: when some of your users are homed on the on-premises version of Skype for Business Server 2015 and other users are homed on Skype for Business Online. Assigning your Skype for Business Online users a voice routing policy enables those users to receive and to place phones calls to the public switched telephone network by using your on-premises SIP trunks.
  
    
    
Note that simply assigning a user a voice routing policy will not enable them to make PSTN calls via Skype for Business Online. Among other things, you will also need to enable those users for Enterprise Voice and will need to assign them an appropriate voice policy and dial plan.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsVoiceRoutingPolicy** cmdlet are not available in the Skype for Business Server 2015.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the voice routing policy to be removed. To "remove" the global policy, use the following syntax:  <br/>  `-Identity global` <br/> Note that the global policy cannot actually be removed. Instead, all the properties in that policy will be reset to their default values.  <br/> To remove a per-user policy, use syntax similar to this:  <br/>  `-Identity "RedmondVoiceRoutingPolicy"` <br/> You cannot use wildcards when specifying a policy Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If this parameter is present, the policy will automatically be removed even if it is currently assigned to at least one user.  <br/> If this parameter is not present, then the **Remove-CsVoiceRoutingPolicy** cmdlet will not automatically remove a per-user policy that is assigned to at least one user. Instead, a confirmation prompt will appear asking if you are sure that you want to remove the policy. You must answer yes (by pressing the Y key) before the command will continue and the policy will be removed. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Remove-CsVoiceRoutingPolicy** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsVoiceRoutingPolicy** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)
  
    
    
 [Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)
  
    
    
 [New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)
  
    
    
 [Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)
