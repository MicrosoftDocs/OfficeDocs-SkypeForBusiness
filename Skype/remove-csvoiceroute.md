---
title: Remove-CsVoiceRoute
ms.prod: SKYPEFORBUSINESS
ms.assetid: 6687e538-e8f6-4bf0-b393-2c7b4a3f2f06
---


# Remove-CsVoiceRoute
[]
Removes a voice route. Voice routes contain instructions that tell Skype for Business Server 2015 how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Remove-CsVoiceRoute -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

Removes the settings for the voice route with the identity Route1.
  
    
    

```

Remove-CsVoiceRoute -Identity Route1
```


### EXAMPLE 2

This command removes all voice routes from the organization. First all voice routes are retrieved by the **Get-CsVoiceRoute** cmdlet. These voice routes are then piped to the **Remove-CsVoiceRoute** cmdlet, which removes each one.
  
    
    

```
Get-CsVoiceRoute | Remove-CsVoiceRoute
```


### EXAMPLE 3

This command removes all voice routes with an identity that includes the string "Redmond." First the **Get-CsVoiceRoute** cmdlet is called with the Filter parameter. The value of the Filter parameter is the string Redmond surrounded by wildcard characters (*), which specifies that the string can be anywhere within the Identity. After all of the voice routes with identities that include the string Redmond are retrieved, these voice routes are piped to the **Remove-CsVoiceRoute** cmdlet, which removes each one.
  
    
    

```
Get-CsVoiceRoute -Filter *Redmond* | Remove-CsVoiceRoute
```


## Detailed Description

Use this cmdlet to remove an existing voice route. Voice routes are associated with voice policies through PSTN usages, so removing a voice route does not change any values relating to a voice policy, it simply changes the routing for the numbers that had matched the pattern for the deleted voice route.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string that uniquely identifies the voice route you want to delete. (If the route name contains a space, such as Test Route, you must enclose the full string in double quotes.)  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route object. Accepts pipelined input of voice route objects.
  
    
    

## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route.
  
    
    

## See also


#### 


  
    
    
 [New-CsVoiceRoute](new-csvoiceroute.md)
  
    
    
 [Set-CsVoiceRoute](set-csvoiceroute.md)
  
    
    
 [Get-CsVoiceRoute](get-csvoiceroute.md)
  
    
    
 [Test-CsVoiceRoute](test-csvoiceroute.md)
