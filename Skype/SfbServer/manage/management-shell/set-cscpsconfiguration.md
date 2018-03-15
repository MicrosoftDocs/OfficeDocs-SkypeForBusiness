---
title: "Set-CsCpsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9c2c0ad1-12f8-47b6-a7ec-60d91c9685bf
description: "Modifies an existing collection of Call Park service settings. Call parking is a service that allows a user toparkan incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and then immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone simply by entering the correct number. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsCpsConfiguration
 
Modifies an existing collection of Call Park service settings. Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and then immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone simply by entering the correct number. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsCpsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 modifies the Call Park service configuration with the Identity site:Redmond1 by setting the maximum number of times a parked call will ring back to the answering phone to 2. This is done by including the MaxCallPickupAttempts parameter and setting the parameter value to 2.
  
```
Set-CsCpsConfiguration -Identity site:Redmond1 -MaxCallPickupAttempts 2
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, we set all (not just one) Call Park service configurations to have a MaxCallPickupAttempts property value of 2. To do this, the **Get-CsCpsConfiguration** cmdlet is used to retrieve a collection of all the Call Park service settings in use in the organization. This collection is then piped to the **Set-CsCpsConfiguration** cmdlet, which takes each individual item in the collection and sets the value of the MaxCallPickupAttempts property to 2.
  
```
Get-CsCpsConfiguration | Set-CsCpsConfiguration -MaxCallPickupAttempts 2
```

### EXAMPLE 3

This example modifies the call park configuration for site Redmond1 by setting the amount of time that will elapse before a parked call will ring back (contained in the CallPickupTimeoutThreshold property) to 45 seconds.
  
```
Set-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:00:45
```

## Detailed Description

This cmdlet is used to modify an existing Call Park service configuration. A Call Park service configuration specifies what happens to a call once it's parked. For example, if a parked call isn't answered after a period of time, it can be automatically forwarded to someone else, such as an administrator, or to a Response Group. Calls can be configured to ring after a certain period of time to ensure the call isn't forgotten. In addition, Call Park service can be configured to play music on hold to the caller while the call is parked.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CallPickupTimeoutThreshold_ <br/> |Optional  <br/> |TimeSpan  <br/> |The amount of time that will elapse after a call has been parked before it will ring back to the phone on which the call was answered.  <br/> This must be entered in the format hh:mm:ss (hh = hours, mm = minutes, ss = seconds)  <br/> Minimum Value: 10 seconds (00:00:10); Maximum Value: 10 minutes (00:10:00)  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableMusicOnHold_ <br/> |Optional  <br/> |Boolean  <br/> |Determines whether music plays for the caller while a call is parked.  <br/> Skype for Business Server 2015 ships with a default Music on Hold file. You can change this file (thereby changing the music the caller hears while parked) with the **Set-CsCallParkServiceMusicOnHoldFile** cmdlet. <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsIdentity  <br/> |A unique identifier of the configuration you want to modify. The Identity specifies the scope at which the configuration is applied, either Global or a specific site (in the format site:\<sitename\>, such as site:Redmond).  <br/> |
| _Instance_ <br/> |Optional  <br/> |CallParkServiceSettings  <br/> |An object reference to a Call Park service configuration object, of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings. This object can be retrieved by calling the **Get-CsCpsConfiguration** cmdlet. The object can then be changed and the changes saved by passing the object back to the **Set-CsCpsConfiguration** cmdlet in this parameter. <br/> |
| _MaxCallPickupAttempts_ <br/> |Optional  <br/> |Int32  <br/> |The number of times a parked call will ring back to the answering phone before giving up and forwarding the call to the fallback Uniform Resource Identifier (URI). The fallback URI is set with the OnTimeoutURI parameter.  <br/> Minimum Value: 1; Maximum Value: 10  <br/> |
| _OnTimeoutURI_ <br/> |Optional  <br/> |String  <br/> |The SIP address of the user or Response Group to which unanswered parked calls will be routed. The parked call will be routed after the number of ringbacks defined with the MaxCallPickupAttempts parameter. If that parameter is set to Null, the OnTimeoutURI will be ignored and the parked call will be disconnected after unsuccessful ringback attempts.  <br/> Values must be SIP URIs, beginning with the string sip:. For example, sip:rgs1@litwareinc.com.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings object. Accepts pipelined input of Call Park service configuration objects.
  
## Return Types

Modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.
  
## See also

#### 

[New-CsCpsConfiguration](new-cscpsconfiguration.md)
  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)
  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)
  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

