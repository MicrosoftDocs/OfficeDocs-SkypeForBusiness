---
title: "Get-CsTestDevice"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4c88d448-4130-40de-b7e9-7389922322f4
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsTestDevice
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves information about the device update management test devices that have been configured for use in your organization. Test devices provide a way for administrators to test firmware updates before those updates are distributed to all the devices in an organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTestDevice [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

By identifying specific phones compatible with Lync Phone Edition or other devices as test devices, administrators can verify and approve firmware updates before those updates are rolled out to all the relevant devices in the organization. When device update rules are imported to Lync Server, they are marked as "pending," which means that the updates corresponding to these rules will not automatically be downloaded and installed by the affected devices.
  
 Instead, these pending rules will be downloaded and installed by any relevant test devices. That's what test devices are for: new device update rules are automatically applied to test devices, giving administrators the opportunity to verify that the firmware updates work as expected. If they do, those administrators can then mark the rules as approved; approved rules are then downloaded and installed by all the relevant devices in the organization. 
  
Test devices can be assigned to either the global or the site scope. You can use the **Get-CsTestDevice** cmdlet to retrieve information about the test devices currently configured for use in your organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsTestDevice** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsTestDevice"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Provides a way for you to use wildcard characters when specifying the test device (or devices) to be returned. For example, to return all the test device collections that have been configured at the site scope, use this syntax: -Filter "site:\*". To return all the devices that have the term "EMEA" in their Identity, use this syntax: -Filter "\*EMEA\*". Note that Filter acts only on the Identity of the test device collection; you cannot filter on other collection properties.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the test device to be returned. To refer to an individual device named UCPhone (stored in the global collection), use this syntax: -Identity global/UCPhone. To refer to a device found in a site collection, use syntax similar to this: -Identity site:Redmond/UCPhone. To refer to an entire collection, leave off the device name. For example, this syntax returns all the test devices configured for the Redmond site: -Identity site:Redmond.  <br/> Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the test device data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsTestDevice** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsTestDevice** cmdlet returns one or more instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.TestDevice object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTestDevice](new-cstestdevice.md)
  
[Remove-CsTestDevice](remove-cstestdevice.md)
  
[Set-CsTestDevice](set-cstestdevice.md)

