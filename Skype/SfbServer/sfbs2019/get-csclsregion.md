---
title: "Get-CsClsRegion"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4f38e966-8e92-4549-8124-097c236c0165
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsClsRegion
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about the centralized logging configuration regions in use in the organization. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. Centralized logging regions are intended for use with Skype for Business Online.
  
This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsClsRegion [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information for all the centralized logging regions configured for use in the organization.
  
```
Get-CsClsRegion
```

### Example 2

In Example 2, information is returned only for the centralized logging region that has the Identity global/US.
  
```
Get-CsClsRegion -Identity "global/US"
```

### Example 3

Example 3 returns information about all the centralized logging regions configured at the global scope. This is done by calling the **Get-CsClsRegion** cmdlet along with the Filter parameter; the filter value "global/*" limits the returned data to regions configured at the global scope. 
  
```
Get-CsClsRegion -Filter "global/*"
```

### Example 4

The command shown in Example 4 returns information for all the centralized logging regions that allow access by the Europe region. To carry out this task, the command first uses the **Get-CsClsRegion** cmdlet to return a collection of all the centralized logging regions currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those regions where the OtherRegionAccess property includes the string value "Europe". 
  
```
Get-CsClsRegion | Where-Object {$_.OtherRegionAccess -match "Europe"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet. 
  
With the Office 365 version of Lync Server, regions are used to determine which users have access to the personally-identifiable information that is written to the log files. Regions are created by using the [New-CsClsRegion](new-csclsregion.md) cmdlet and then are added to a collection of centralized logging configuration settings. You can return information about your centralized logging regions by using the **Get-CsClsRegion** cmdlet. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsClsRegion"}
  
 **Lync Server Control Panel:** The functions carried out by the **Get-CsClsRegion** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a centralized logging region (or regions). For example, to return a collection of all the settings configured at the global scope, use this syntax:  <br/> -Filter "global/\*"  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the centralized logging region to be returned. A region identity consists of the scope where the region was created followed by the region name. For example, to return a region named US created at the global scope, use the following syntax:  <br/> -Identity "global/US"  <br/> If this parameter is not specified then the **Get-CsClsRegion** cmdlet returns information about all your centralized logging regions.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the centralized logging configuration data from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsClsRegion** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsClsRegion** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsClsRegion](new-csclsregion.md)
  
[Remove-CsClsRegion](remove-csclsregion.md)
  
[Set-CsClsRegion](set-csclsregion.md)

