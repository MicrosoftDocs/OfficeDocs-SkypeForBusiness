---
title: "Remove-CsTrunkConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 45546534-1a18-4db2-be61-850bacf55a52
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsTrunkConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an existing trunk configuration that describes the settings for a trunking peer entity such as a public switched telephone network (PSTN) gateway, IP-public branch exchange (PBX), or Session Border Controller (SBC) at the service provider. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsTrunkConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the trunk configuration with the Identity site:Redmond.
  
```
Remove-CsTrunkConfiguration -Identity site:Redmond
```

### EXAMPLE 2

Example 2 removes all trunk configurations defined at the site level. The first part of the command is a call to the **Get-CsTrunkConfiguration** cmdlet that uses the Filter parameter to retrieve all trunk configurations with an Identity beginning with site: (that is, all trunk configurations defined at the site level). This collection of configurations is then piped to the **Remove-CsTrunkConfiguration** cmdlet, which removes each object in the collection. 
  
```
Get-CsTrunkConfiguration -Filter site:* | Remove-CsTrunkConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Use this cmdlet to remove a trunking configuration applicable to PSTN gateway entities. Each configuration contains specific settings for a trunking peer entity such as a PSTN gateway, IP-PBX, or SBC at the service provider. These settings configure such things as whether media bypass is enabled on this trunk, whether real-time transport control protocol (RTCP) packets are sent under certain conditions, and whether to require secure real-time protocol (SRTP) encryption.
  
Note that if you call the **Remove-CsTrunkConfiguration** cmdlet on the Global configuration, that trunk configuration will not be removed. Instead the configuration will be "reset" and all custom settings will be replaced with default values. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsTrunkConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsTrunkConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the trunk configuration you want to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration object. Accepts pipelined input of trunk configuration objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)
  
[Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)
  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)
  
[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)

