---
title: "Remove-CsTestDevice"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 995111e0-2ab2-49a1-83f0-fc873f5b5426
description: "Removes the specified device update management test device. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsTestDevice
[]
Removes the specified device update management test device. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsTestDevice -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 removes all the test devices from the Redmond site. This will remove the device collection as well as the individual test devices.
  
```
Remove-CsTestDevice -Identity site:Redmond
```

### EXAMPLE 2

The command shown in Example 2 removes all the test devices configured for use in the organization; this is done by using the **Get-CsTestDevice** cmdlet to return all the test device collections, and then piping all of those items to the **Remove-CsTestDevice** cmdlet. Note that the global test device collection cannot be removed; however, this command will delete all the individual test devices configured at the global level.
  
```
Get-CsTestDevice | Remove-CsTestDevice
```

### EXAMPLE 3

In Example 3, all the test devices configured at the site scope are removed. To carry out this task, the **Get-CsTestDevice** cmdlet and the Filter parameter are used to return all the test devices that have an Identity that begins with the string value "site:". This filtered collection is then piped to the **Remove-CsTestDevice** cmdlet, which deletes all the items in the collection.
  
```
Get-CsTestDevice -Filter "site:" | Remove-CsTestDevice
```

### EXAMPLE 4

The command shown in Example 4 deletes all the LG-Nortel Phone test devices. To do this, the command first calls the **Get-CsTestDevice** cmdlet to return all the test devices configured for use in the organization. That information is then piped to the **Where-Object** cmdlet, which uses the -match operator to return any devices that have the string value "LG-Nortel" anywhere in the Name property. Any test device meeting that criterion is then deleted by using the **Remove-CsTestDevice** cmdlet.
  
```
Get-CsTestDevice | Where-Object {$_.Name -match "LG-Nortel Phone"} | Remove-CsTestDevice
```

## Detailed Description

By identifying specific Skype for Business-compatible phones or other devices as test devices, administrators can verify and approve firmware updates before those updates are rolled out to all the relevant devices in the organization. When device update rules are imported to Skype for Business Server 2015, they are marked as "pending," which means that the updates corresponding to these rules will not automatically be downloaded and installed by the affected devices. 
  
Instead, these pending rules will be downloaded and installed by any relevant test devices. That's the idea behind test devices: new device update rules are automatically applied to test devices, giving administrators the opportunity to verify that the firmware updates work as expected. If they do, those administrators can then mark the rules as approved; approved rules are then downloaded and installed by all the relevant devices in the organization.
  
Test devices are hardware devices that run Skype for Business. These devices are created by using the **New-CsTestDevice** cmdlet. Once created, the devices can later be removed by running the **Remove-CsTestDevice** cmdlet. Note that removing the device as a test device does not affect the actual device itself; for example, your Skype for Business-compatible phone can still be used to access Skype for Business Server 2015. The only difference is that, because the device is no longer a test device, it will no longer download device update rules that are in the pending state. Instead, the device will wait until the rules have been approved before downloading and installing them.
  
The **Remove-CsTestDevice** cmdlet can be used to remove individual test devices configured at either the global or site scope. You can also use the cmdlet to remove all the test devices configured for a given scope.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the test device to be removed. To remove a specific device, include both the scope (for example, site:Redmond) and the device name; for example:  <br/>  `-Identity "site:Redmond/UCPhoneTest"` <br/> To remove all the devices from a particular site use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> Test devices can also be removed from the global scope. The global test device collection itself cannot be removed; however, the following command will delete all the devices stored in the global collection:  <br/>  `Remove-CsTestDevice -Identity global` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice object. The **Remove-CsTestDevice** cmdlet accepts pipelined input of the test device object.
  
## Return Types

The **Remove-CsTestDevice** cmdlet does not return a value or object. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice object.
  
## See also

#### 

[Get-CsTestDevice](get-cstestdevice.md)
  
[New-CsTestDevice](new-cstestdevice.md)
  
[Set-CsTestDevice](set-cstestdevice.md)

