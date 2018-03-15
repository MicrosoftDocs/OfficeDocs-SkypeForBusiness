---
title: "Debug-CsLisConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8cc718d6-52ec-4ff3-a77e-8d6df1725fb0
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Debug-CsLisConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Displays the Enhanced 9-1-1 (E9-1-1) Location Information service (LIS) configuration in XML format. This cmdlet was introduced in Lync Server 2010.
  
```
Debug-CsLisConfiguration [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Running this command will display the entire LIS configuration to the Lync Server Management Shell window in XML format. By default, the output of the **Debug-CsLisConfiguration** cmdlet is displayed on one line, with an ellipsis (…) at the end of the line indicating that there's more than one line of data. Therefore, in this example we pipe the output to the **Format-Table** cmdlet, specifying the Wrap parameter, to display the full output wrapped to fit in the display window. 
  
```
Debug-CsLisConfiguration | Format-Table -Wrap
```

## Detailed Description
<a name="sectionSection1"> </a>

The LIS configuration for an Enterprise Voice E9-1-1 implementation is stored in compressed format. This cmdlet un-compresses the configuration and displays it in XML format. This can make it quicker to debug issues with a configuration.
  
This cmdlet retrieves the location information from the Central Management store. When this information is created, it is stored in the location database; it does not move to the Central Management store until it is published with the **Publish-CsLisConfiguration** cmdlet. If the location information has not been published (or has been un-published with the **Unpublish-CsLisConfiguration** cmdlet), the **Debug-CsLisConfiguration** cmdlet will not return anything. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Debug-CsLisConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Debug-CsLisConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Returns an object of type System.Management.Automation.PSCustomObject.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Publish-CsLisConfiguration](publish-cslisconfiguration.md)
  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)
  
[Import-CsLisConfiguration](import-cslisconfiguration.md)
  
[Export-CsLisConfiguration](export-cslisconfiguration.md)
  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

