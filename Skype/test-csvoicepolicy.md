---
title: Test-CsVoicePolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 4d631e36-3a9d-4ca2-913f-8c9f4e93183d
---


# Test-CsVoicePolicy
[]
Tests a telephone number against a voice policy and determines which voice route would be used against that policy for that number. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Test-CsVoicePolicy -TargetNumber <PhoneNumber> -VoicePolicy <VoicePolicy> [-Force <SwitchParameter>] [-RouteSettings <PstnRoutingSettings>]

```


## Examples


  
    
    

### EXAMPLE 1

This example runs a voice policy test against the voice policy with the Identity site:Redmond. First the **Get-CsVoicePolicy** cmdlet is run to retrieve the policy with the Identity site:Redmond. That policy object is then piped to the **Test-CsVoicePolicy** cmdlet, where the policy is tested against the telephone number +14255559999. The output will be the first voice route (based on the Priority property of the route) that has a number pattern matching the TargetNumber value and a phone usage matching a phone usage in the policy. If no matching route is found (for example, if the number pattern matches the pattern for an 11-digit number and you supply a 7-digit number) a null value will be returned.
  
    
    

```

Get-CsVoicePolicy -Identity site:Redmond | Test-CsVoicePolicy -TargetNumber "+14255559999"
```


### EXAMPLE 2

Example 2 is identical to Example 1 except that instead of piping the results of the Get operation directly to the **Test-CsVoicePolicy** cmdlet, the object is first stored in the variable $a and then is passed as the value to the parameter VoicePolicy to be used as the policy against which the test will run.
  
    
    

```
$a = Get-CsVoicePolicy -Identity site:Redmond
Test-CsVoicePolicy -TargetNumber "+14255559999" -VoicePolicy $a
```


### EXAMPLE 3

This example runs a voice policy test against all voice policies defined within the Skype for Business Server 2015 deployment. First the **Get-CsVoicePolicy** cmdlet is run (with no parameters) to retrieve all the voice policies. The collection of policies that is returned is then piped to the **Test-CsVoicePolicy** cmdlet, where each policy in the collection is checked for a matching route based on the target phone number provided (+12065559999) and phone usages. The output will be a list of matching routes along with the phone usages that were matched.
  
    
    

```

Get-CsVoicePolicy | Test-CsVoicePolicy -TargetNumber "+12065559999"
```


## Detailed Description

Voice policies are tied to voice routes through public switched telephone network (PSTN) usages. A call from a user who has been assigned a particular voice policy can only be sent through a route that has a PSTN usage matching a usage on the policy and also a number pattern that matches the number dialed. Call the **Test-CsVoicePolicy** cmdlet to determine which (if any) route will be used to route a call from a user with a particular voice policy, and also what phone usage ties the policy to the route.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetNumber_ <br/> |Required  <br/> |PhoneNumber  <br/> |The phone number against which to run the test. This number should be in E.164 format (such as +14255551212).  <br/> |
| _VoicePolicy_ <br/> |Required  <br/> |VoicePolicy  <br/> |A reference to the voice policy object against which to run the test. Voice policy objects can be retrieved by calling the **Get-CsVoicePolicy** cmdlet. <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts or non-fatal error messages that might occur when you run the cmdlet.  <br/> |
| _RouteSettings_ <br/> |Optional  <br/> |PstnRoutingSettings  <br/> |Route settings against which to run the test. The route settings can be retrieved with a call to the **Get-CsRoutingConfiguration** cmdlet. <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy object. Accepts pipelined input of voice policy objects.
  
    
    

## Return Types

Returns an object of type Microsoft.Rtc.Management.Voice.VoicePolicyTestResult.
  
    
    

## See also


#### 


  
    
    
 [New-CsVoicePolicy](new-csvoicepolicy.md)
  
    
    
 [Remove-CsVoicePolicy](remove-csvoicepolicy.md)
  
    
    
 [Set-CsVoicePolicy](set-csvoicepolicy.md)
  
    
    
 [Get-CsVoicePolicy](get-csvoicepolicy.md)
  
    
    
 [Grant-CsVoicePolicy](grant-csvoicepolicy.md)
