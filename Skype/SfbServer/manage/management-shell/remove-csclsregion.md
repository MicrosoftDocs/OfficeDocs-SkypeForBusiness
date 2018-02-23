---
title: "Remove-CsClsRegion"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6ab1596e-0e27-44e7-8cbc-efd4064ba58b
description: "Removes one or more centralized logging configuration regions. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. Centralized logging regions are intended for use with Skype for Business Online."
---

# Remove-CsClsRegion
[]
Removes one or more centralized logging configuration regions. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. Centralized logging regions are intended for use with Skype for Business Online.
  
This cmdlet was introduced in Lync Server 2013. 
  
```
Remove-CsClsRegion -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the centralized logging region that has the Identity global/US.
  
```
Remove-CsClsRegion -Identity "global/US"
```

### Example 2

In Example 2, all the centralized logging regions configured at the global scope are removed. To do this, the command first calls the **Get-CsClsRegion** cmdlet along with the Filter parameter; the filter value "global/*" limits the returned data to regions configured at the global scope. These regions are then piped to, and deleted by, the **Remove-CsClsRegion** cmdlet.
  
```
Get-CsClsRegion -Filter "global/*" | Remove-CsClsRegion 
```

### Example 3

Example 3 deletes all the centralized logging regions that have the security group suffix EMEA. To carry out this task, the command first calls the **Get-CsClsRegion** cmdlet without any parameters; this returns a collection of all the centralized logging regions configured for use in the organization. This collection is then piped to the Where-Object cmdlet, which picks out only those regions where the SecurityGroupSuffix property is equal to (-eq) EMEA. That subcollection of regions is then piped to the **Remove-CsClsRegion** cmdlet, which deletes each region in the subcollection.
  
```
Get-CsClsRegion | Where-Object {$_.SecurityGroupSuffix -eq "EMEA" | Remove-CsClsRegion
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
With Skype for Business Online, regions are used to determine which users have access to the personally-identifiable information that is written to the log files. Regions are created by using the [New-CsClsRegion](new-csclsregion.md) cmdlet and then are added to a collection of centralized logging configuration settings. Regions added to one of these collections can later be removed by using the **Remove-CsClsRegion** cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsClsRegion** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the centralized logging region to be removed. A region identity consists of the scope where the region was created followed by the region name. For example, to delete a region named US created at the global scope, use the following syntax:  <br/>  `-Identity "global/US"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsClsRegion** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsClsRegion** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsClsRegion](get-csclsregion.md)
  
[New-CsClsRegion](new-csclsregion.md)
  
[Set-CsClsRegion](set-csclsregion.md)

