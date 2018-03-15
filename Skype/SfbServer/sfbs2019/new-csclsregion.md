---
title: "New-CsClsRegion"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 09396d6e-e7ec-43b8-9f5b-d9cac30348f6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsClsRegion
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Creates a new centralized logging configuration region. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. Centralized logging regions are intended for use with Skype for Business Online. 
  
This cmdlet was introduced in Lync Server 2013.
  
```
New-CsClsRegion -Name <String> -Parent <String> <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example a creates a new global region named Europe. The new region uses the security group suffix EMEA and also allows access by the global/US region.
  
```
New-CsClsRegion -Identity "global/Europe" -SecurityGroupSuffix "EMEA" -OtherRegionAccess "global/US"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet. 
  
With the Office 365 version of Lync Server, regions are used to determine which users have access to the personally-identifiable information that is written to the log files. Regions are created by using the [New-CsClsRegion](new-csclsregion.md) cmdlet and then are added to a collection of centralized logging configuration settings. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsClsRegion"}
  
 **Lync Server Control Panel:** The functions carried out by the **New-CsClsRegion** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new region. Region Identities consist of the centralized logging configuration scope where the region will be created plus a unique region name. For example, to create a global region named Redmond use this syntax:  <br/> -Identity "global/Redmond"  <br/> If you use the Identity parameter then you cannot use either the name parameter or the Parent parameter in that same command.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Unique name for the new region. For example:  <br/> -Name "Redmond"  <br/> If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.  <br/> |
| _OtherRegionAccess_ <br/> |Required  <br/> |System.String  <br/> |Name of an additional region that can be accessed by authorized users for this region.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Scope of the centralized logging configuration settings where the new region will be located. For example, to add the new region to the global settings, use this syntax:  <br/> -Parent "global"  <br/> You can return identities for all your centralizing logging "parents" by using this command:  <br/> Get-CsCentralizedLoggingConfiguration | Select-Object Identity  <br/> If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.  <br/> |
| _SecurityGroupSuffix_ <br/> |Required  <br/> |System.String  <br/> |Suffix to be added to the end of the name of any security group that will be authorized for this region.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Sites_ <br/> |Optional  <br/> |System.String  <br/> |Sites contained within this region. These correspond to the SideId attribute values in the topology document.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The New-CsClsRegion cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The New-CsClsRegion cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Region#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsClsRegion](get-csclsregion.md)
  
[Remove-CsClsRegion](remove-csclsregion.md)
  
[Set-CsClsRegion](set-csclsregion.md)

