---
title: "New-CsCallParkOrbit"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d65a000f-905d-4512-b082-066748719f4c
description: "Creates a new, named range of numbers assigned for parking calls within an organization. This cmdlet was introduced in Lync Server 2010."
---

# New-CsCallParkOrbit
 
Creates a new, named range of numbers assigned for parking calls within an organization. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsCallParkOrbit -Identity <XdsGlobalRelativeIdentity> -CallParkService <String> -NumberRangeEnd <String> -NumberRangeStart <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Type <CallPark | GroupPickup>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example creates a new call park orbit named "Redmond CPO 1" on the Application Server with the service ID ApplicationServer:pool0.litwareinc.com. The available number range for this call park orbit is 100 through 199.
  
```
New-CsCallParkOrbit -Identity "Redmond CPO 1" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService ApplicationServer:pool0.litwareinc.com
```

### EXAMPLE 2

This example creates a new call park orbit named "Redmond CPO 2" on the Call Park application server with the FQDN pool0.litwareinc.com. The available range for this call park orbit is \*1000 through \*1999.
  
```
New-CsCallParkOrbit -Identity "Redmond CPO 2" -NumberRangeStart "*1000" -NumberRangeEnd "*1999" -CallParkService pool0.litwareinc.com
```

### EXAMPLE 3

This example creates a new call park orbit range named "Redmond CPO 3" on the Call Park application server with the service ID ApplicationServer:redmond.litwareinc.com. The available range for this call park orbit is #1000 through #1999.
  
```
New-CsCallParkOrbit -Identity "Redmond CPO 3" -NumberRangeStart "#1000" -NumberRangeEnd "#1999"  -CallParkService ApplicationServer:redmond.litwareinc.com
```

## Detailed Description

Parking a call assigns a received phone call to a specific number for later retrieval. A call park orbit range is the set of call park locations assigned to a specific Call Park service for this purpose. The **New-CsCallParkOrbit** cmdlet defines the numbers for a call park orbit range and applies them to a specific service. Calls parked within the given range will be parked on the specified Call Park service. You can create multiple call park orbits; each must have a globally unique name and a unique range of numbers.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CallParkService_ <br/> |Required  <br/> |System.String  <br/> |The fully qualified domain name (FQDN) or service ID of the Application service that hosts the Call Park application. All calls parked to numbers within the range specified by the NumberRangeStart and NumberRangeEnd parameters will be routed to this server or pool.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The name of the call park orbit range. This name must be unique within the Skype for Business Server 2015 deployment. This string can be any value, but should be something that allows for easy identification of the particular call park orbit range. All call park orbit ranges are created with a global scope.  <br/> |
| _NumberRangeEnd_ <br/> |Required  <br/> |System.String  <br/> |The last number in the range for this call park orbit. The value must be greater than or equal to the NumberRangeStart. The value must also be the same length as the value of the NumberRangeStart. For example, if NumberRangeStart is set to 100, NumberRangeEnd cannot be set to 1001. In addition, if the NumberRangeStart begins with a \* or #, then NumberRangeEnd must begin with the same character.  <br/> Valid values: Must match the regular expression string ([\\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8}). This means that the value must be a string beginning with either the character \* or # or a number 1 through 9 (the first character cannot be a zero). If the first character is \* or # the following character must be a number 1 through 9 (it cannot be a zero). Subsequent characters can be any number 0 through 9 up to seven additional characters. (For example, #6000, \*92000, and \*95551212.) If the first character is not \* or #, the first character must be a number 1 through 9 (it cannot be zero), followed by up to eight characters, each a number 0 through 9. (For example: 915551212;41212;300)  <br/> |
| _NumberRangeStart_ <br/> |Required  <br/> |System.String  <br/> |The first number in the range for this call park orbit. The value must be less than or equal to the NumberRangeEnd. The value must also be the same length as the value of the NumberRangeEnd.  <br/> Valid values: Must match the regular expression string ([\\*|#]?[1-9]\d{0,7})|([1-9]\d{0,8}). This means that the value must be a string beginning with either the character \* or # or a number 1 through 9 (the first character cannot be a zero). If the first character is \* or # the following character must be a number 1 through 9 (it cannot be a zero). Subsequent characters can be any number 0 through 9 up to seven additional characters. (For example, #6000, \*92000, and \*95551212.) The number following the \* or # must be greater than 100. If the first character is not \* or #, the first character must be a number 1 through 9 (it cannot be zero), followed by up to eight characters, each a number 0 through 9. (For example, 915551212;41212;300)  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _Type_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Core.OrbitType  <br/> |Specifies the type of call park orbit being created. Skype for Business Server 2015 allows for two different types of call park orbits:  <br/> CallPark. This is the standard call park orbit, in which a user places a call on hold and then can retrieve that call from any phone by dialing the specified call park number. CallPark is the default orbit type and will be used if the Type parameter is not specified.  <br/> GroupPickup. With group pickup, users can answer any incoming call that is made to any member of their call pickup group. Call pickup groups are configured by administrators.  <br/> To specify a call park orbit type, use syntax similar to this:  <br/>  `-Type GroupPickup` <br/> This parameter was introduced in the February 2013 release of Lync Server 2013.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet creates an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit.
  
## See also

#### 

[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)
  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)
  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)

