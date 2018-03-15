---
title: "Get-CsTrunkConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15951113-5f96-4f44-8cad-9ff97fb5dfd6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsTrunkConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves one or more trunk configurations, which describe the settings for a trunking peer entity such as a public switched telephone network (PSTN) gateway, IP-private branch exchange (PBX), or Session Border Controller (SBC) at the service provider. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTrunkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example retrieves all trunk configurations for the Lync Server deployment.
  
```
Get-CsTrunkConfiguration
```

### EXAMPLE 2

This example retrieves the trunk configuration with the Identity site:Redmond. Because identities are unique, this command will return at most one object.
  
```
Get-CsTrunkConfiguration -Identity site:Redmond
```

### EXAMPLE 3

Example 3 retrieves all trunk configurations defined at the site level. The **Get-CsTrunkConfiguration** cmdlet uses the Filter parameter to retrieve all trunk configurations with an Identity beginning with site:, meaning all trunk configurations defined at the site level. 
  
```
Get-CsTrunkConfiguration -Filter site:*
```

## Detailed Description
<a name="sectionSection1"> </a>

Use this cmdlet to retrieve one or more trunking configurations applicable to PSTN gateway entities. Each configuration contains specific settings for a trunking peer entity such as a PSTN gateway, IP-PBX, or SBC at the service provider. These settings configure such things as whether media bypass is enabled on this trunk, whether real-time transport control protocol (RTCP) packets are sent under certain conditions, and whether to require secure real-time protocol (SRTP) encryption.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsTrunkConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsTrunkConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter accepts a wildcard string and returns all trunk configurations with identities matching that string. For example, a Filter value of site:\* will return all trunk configurations defined at the site level.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the trunk configuration you want to retrieve. Trunk configurations can be defined at the Global scope, the Site scope, or at the Service scope for a PSTN Gateway service. For example, site:Redmond (for site) or PstnGateway:Redmond.litwareinc.com (for service).  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the trunk configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet returns an object of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)
  
[Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)
  
[Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)
  
[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)

