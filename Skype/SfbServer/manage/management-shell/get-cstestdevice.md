---
title: "Get-CsTestDevice"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4c88d448-4130-40de-b7e9-7389922322f4
description: "Retrieves information about the device update management test devices that have been configured for use in your organization. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsTestDevice
 
Retrieves information about the device update management test devices that have been configured for use in your organization. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTestDevice [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns all the test devices in the organization. Calling the **Get-CsTestDevice** cmdlet without any additional parameters will return all the test devices currently in use.
  
```
Get-CsTestDevice
```

### EXAMPLE 2

This example returns the test device named UCPhone that was assigned to the Redmond site.
  
```
Get-CsTestDevice -Identity site:Redmond/UCPhone
```

### EXAMPLE 3

In Example 3, the command returns all the test devices configured for the Redmond site.
  
```
Get-CsTestDevice -Identity site:Redmond  
```

### EXAMPLE 4

Example 4 returns all the test devices that have been configured at the site scope. To do this, the command uses the Filter parameter; the filter value "site:\*" limits the returned data to test devices that have an Identity that begins with the string value "site:".
  
```
Get-CsTestDevice -Filter site:*
```

## Detailed Description

By identifying specific phones compatible with Skype for Business or other devices as test devices, administrators can verify and approve firmware updates before those updates are rolled out to all the relevant devices in the organization. When device update rules are imported to Skype for Business Server 2015, they are marked as "pending," which means that the updates corresponding to these rules will not automatically be downloaded and installed by the affected devices.
  
 Instead, these pending rules will be downloaded and installed by any relevant test devices. That's what test devices are for: new device update rules are automatically applied to test devices, giving administrators the opportunity to verify that the firmware updates work as expected. If they do, those administrators can then mark the rules as approved; approved rules are then downloaded and installed by all the relevant devices in the organization.
  
Test devices can be assigned to either the global or the site scope. You can use the **Get-CsTestDevice** cmdlet to retrieve information about the test devices currently configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Provides a way for you to use wildcard characters when specifying the test device (or devices) to be returned. For example, to return all the test device collections that have been configured at the site scope, use this syntax:  <br/>  `-Filter "site:*"` <br/> To return all the devices that have the term "EMEA" in their Identity, use this syntax:  <br/>  `-Filter "*EMEA*"` <br/> Note that Filter acts only on the Identity of the test device collection; you cannot filter on other collection properties.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the test device to be returned. To refer to an individual device named UCPhone (stored in the global collection), use this syntax:  <br/>  `-Identity global/UCPhone` <br/> To refer to a device found in a site collection, use syntax similar to this:  <br/>  `-Identity site:Redmond/UCPhone` <br/> To refer to an entire collection, leave off the device name. For example, this syntax returns all the test devices configured for the Redmond site:  <br/>  `-Identity site:Redmond` <br/> Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the test device data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsTestDevice** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsTestDevice** cmdlet returns one or more instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice object.
  
## See also

#### 

[New-CsTestDevice](new-cstestdevice.md)
  
[Remove-CsTestDevice](remove-cstestdevice.md)
  
[Set-CsTestDevice](set-cstestdevice.md)

