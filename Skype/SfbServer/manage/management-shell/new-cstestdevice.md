---
title: "New-CsTestDevice"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3d223c5e-b987-4353-9bf7-b247a2bdfa25
description: "Creates a new device update management test device. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010."
---

# New-CsTestDevice
 
Creates a new device update management test device. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsTestDevice -Identity <XdsIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 creates a new test device (named UCPhone) for the Redmond site. Note the syntax used to specify the device Identity: the device scope (site:Redmond) followed by the / character followed by the device Name (UCPhone). This device uses the serial number as the IdentifierType, and has a serial number of 07823-A345.
  
```
New-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "07823-A345"
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In Example 2, however, the Identity parameter is not used. Instead, the Parent parameter is used to specify the scope for the new test device (site:Redmond) and the Name parameter is used to indicate the name for the new device (UCPhone). The **New-CsTestDevice** cmdlet will take those two parameter values and construct the test device Identity (site:Redmond/UCPhone) for you.
  
```
New-CsTestDevice -Parent "site:Redmond" -Name UCPhone -IdentifierType SerialNumber -Identifier "07823-A345"
```

## Detailed Description

By identifying specific phones that are compatible with Skype for Business or other devices as test devices, administrators can verify and approve firmware updates before those updates are rolled out to the relevant devices in the organization. When device update rules are imported to Skype for Business Server 2015, they are marked as "pending," which means that the updates corresponding to these rules will not automatically be downloaded and installed by the affected devices.
  
Instead, these pending rules will be downloaded and installed by any relevant test devices. That's the idea behind test devices: new device update rules are automatically applied to test devices, giving administrators the opportunity to verify that the firmware updates work as expected. If they do, those administrators can then mark the rules as approved; approved rules are then downloaded and installed by all the relevant devices in the organization.
  
Test devices are created by using the **New-CsTestDevice** cmdlet. These devices can be configured at either the global scope or the site scope.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identifier_ <br/> |Required  <br/> |System.String  <br/> |Based on the IdentifierType, indicates the Media Access Control (MAC) address or serial number of the new test device. Serial numbers can be specified using numbers, letters, hyphens and underscores; for example:  <br/>  `-Identifier "AB37_679e"` <br/> MAC addresses must be specified as six or more two-character pairs; depending on the MAC address, these pairs can either be joined together in a single string or can be separated using hyphens or colons. (Note that MAC addresses can include both letters and/or numbers.) Each of the following are valid MAC addresses:  <br/> 010203040506  <br/> 01-02-03-04-05-06  <br/> 01:02:03:04:05:06  <br/> A MAC address such as 01-02-03-04-05 will not be accepted because it does not have at least six two-character pairs.  <br/> |
| _IdentifierType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.IdentifierType  <br/> |Indicates whether the test device will be uniquely identified by its MAC address or by its serial number. To identify a device by its MAC address, set the IdentifierType to MACAddress. To identify a device by its serial number, set the IdentifierType to SerialNumber. MACAddress and SerialNumber are the only allowed values.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity for the new test device. An Identity consists of both the scope where the test device is to be assigned (for example, site:Redmond) and the name for the new device (for example, UCPhone). To assign a test device named UCPhone to the Redmond site, your Identity parameter must look like this:  <br/>  `-Identity "site:Redmond/UCPhone"` <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Name for the new test device (names must be unique within a given scope). The Name parameter should be used only when using the Parent parameter.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Name of the scope (for example, site:Redmond) where the new test device is to be assigned. If you use the Parent parameter then you must also use the Name parameter; for example:  <br/>  `-Parent site:Redmond -Name UCPhone` <br/> If you use the Parent parameter then you should not use the Identity parameter, and vice-versa.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsTestDevice** cmdlet does not accept pipelined input.
  
## Return Types

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice object.
  
## See also

#### 

[Get-CsTestDevice](get-cstestdevice.md)
  
[Remove-CsTestDevice](remove-cstestdevice.md)
  
[Set-CsTestDevice](set-cstestdevice.md)

