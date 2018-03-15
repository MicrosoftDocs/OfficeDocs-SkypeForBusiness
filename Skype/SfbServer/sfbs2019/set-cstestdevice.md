---
title: "Set-CsTestDevice"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0a9fabfc-b0d3-4c94-ae04-0a87f0886db8
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsTestDevice
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies one or more of the device update management test devices that have been configured for use in your organization. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsTestDevice [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 modifies the Identifier property for the test device named UCPhone assigned to the Redmond site. 
  
```
Set-CsTestDevice -Identity site:Redmond/UCPhone -Identifier "09768-ABDR-83295"
```

### EXAMPLE 2

The command shown in Example 2 also modifies the test device named UCPhone assigned to the Redmond site. In this case, however, the command not only specifies a new Identifier but also assigns a new IdentifierType: SerialNumber. 
  
```
Set-CsTestDevice -Identity site:Redmond/UCPhone -IdentifierType SerialNumber -Identifier "09768-ABDR-83295"
```

## Detailed Description
<a name="sectionSection1"> </a>

By identifying specific phones running Lync Phone Edition or other devices as test devices, administrators can verify and approve firmware updates before those updates are rolled out to all the relevant devices in the organization. When device update rules are imported to Lync Server, they are marked as "pending," which means that the updates corresponding to these rules will not automatically be downloaded and installed by the affected devices.
  
Instead, these pending rules will be downloaded and installed by any relevant test devices. That's the idea behind test devices: new device update rules are automatically applied to test devices, giving administrators the opportunity to verify that the firmware updates work as expected. If they do, those administrators can then mark the rules as approved; approved rules are then downloaded and installed by all the relevant devices in the organization. 
  
Test devices are created by using the **New-CsTestDevice** cmdlet. After a test device has been created, you can then use the **Set-CsTestDevice** cmdlet to change the Identifier and the IdentifierType of that device, or any other test device. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsTestDevice** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsTestDevice"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identifier_ <br/> |Optional  <br/> |System.String  <br/> |Based on the IdentifierType, indicates the Media Access Control (MAC) address or serial number of the new test device. Serial numbers can be specified using numbers, letters, hyphens and underscores; for example:  <br/> -Identifier "AB37_679e"  <br/> MAC addresses must be specified as six or more two-character pairs; depending on the MAC address, these pairs can be a single string value or they can be separated using hyphens or colons. (Note that MAC addresses can include both letters and/or numbers.) Each of the following are valid MAC addresses:  <br/> 010203040506  <br/> 01-02-03-04-05-06  <br/> 01:02:03:04:05:06  <br/> A MAC address such as 01-02-03-04-05 will not be accepted because it does not have at least six two-character pairs.  <br/> |
| _IdentifierType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.IdentifierType  <br/> |Indicates whether the test device will be uniquely identified by its MAC address or by its serial number. To identify a device by its MAC address, set the IdentifierType to MACAddress. To identify a device by its serial number, set the IdentifierType to SerialNumber. MACAddress and SerialNumber are the only allowed values.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the test device to be modified. For example: -Identity site:Redmond/UCPhoneTestDevice. Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _Instance_ <br/> |Optional  <br/> |Test device object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice object. The **Set-CsTestDevice** cmdlet accepts pipelined input of the test device object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsTestDevice** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsTestDevice](get-cstestdevice.md)
  
[New-CsTestDevice](new-cstestdevice.md)
  
[Remove-CsTestDevice](remove-cstestdevice.md)

