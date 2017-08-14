---
title: Get-CsVoiceRoutingPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 60245b7d-4e95-4925-aae5-c0fa1e9f38fc
---


# Get-CsVoiceRoutingPolicy
[]
Returns information about the voice routing policies configured for use in your organization. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Skype for Business Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Get-CsVoiceRoutingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 returns information for all the voice routing policies configured for use in the organization.
  
    
    

```

Get-CsVoiceRoutingPolicy
```


### Example 2

In Example 2, information is returned for a single voice routing policy: the policy with the Identity RedmondVoiceRoutingPolicy.
  
    
    

```
Get-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy"
```


### Example 3

The command shown in Example 3 returns information about all the voice routing policies configured at the per-user scope. To do this, the command uses the Filter parameter and the filter value "tag:*"; that filter value limits the returned data to policies that have an Identity that begins with the string value "tag:".
  
    
    

```
Get-CsVoiceRoutingPolicy -Filter "tag:*"
```


### Example 4

In Example 4, information is returned only for those voice routing policies that include the PSTN usage "Long Distance". To carry out this task, the command first calls the **Get-CsVoiceRoutingPolicy** cmdlet without any parameters; that returns a collection of all the voice routing policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the PstnUsages property includes (-contains) the usage "Long Distance".
  
    
    

```
Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -contains "Long Distance"}
```


### Example 5

Example 5 is a variation on the command shown in Example 4; in this case, however, information is returned only for those voice routing policies that do not include the PSTN usage "Long Distance". In order to do that, the **Where-Object** cmdlet uses the -notcontains operator, which limits returned data to policies that do not include the usage "Long Distance".
  
    
    

```
Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -notcontains "Long Distance"}
```


## Detailed Description
<a name="DetailedDescription"> </a>

Voice routing policies are used in "hybrid" scenarios: when some of your users are homed on the on-premises version of Skype for Business Server 2015 and other users are homed on Skype for Business Online. Assigning your Skype for Business Online users a voice routing policy enables those users to receive and to place phones calls to the public switched telephone network by using your on-premises SIP trunks.
  
    
    
Note that simply assigning a user a voice routing policy will not enable them to make PSTN calls via Skype for Business Online. Among other things, you will also need to enable those users for Enterprise Voice and will need to assign them an appropriate voice policy and dial plan.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the Get-CsVoiceRoutingPolicy cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when retrieving one or more voice routing policies. For example, to return all the policies configured at the per-user scope, use this syntax:  <br/>  `-Filter "tag:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the voice routing policy to be retrieved. To return the global policy, use this syntax:  <br/>  `-Identity global` <br/> To return a policy configured at the per-user scope, use syntax like this:  <br/>  `-Identity "RedmondVoiceRoutingPolicy"` <br/> You cannot use wildcard characters when specifying the Identity.  <br/> If neither the Identity nor the Filter parameters are specified, then the **Get-CsVoiceRoutingPolicy** cmdlet returns all the voice routing policies configured for use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice policy data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsVoiceRoutingPolicy** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsVoiceRoutingPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)
  
    
    
 [New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)
  
    
    
 [Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)
  
    
    
 [Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)
