---
title: "Set-CsClsSecurityGroup"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 14e7d927-8d3e-4b36-867c-d4742101e751
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsClsSecurityGroup
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies a centralized logging configuration security group. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsClsSecurityGroup [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 modifies the centralized logging security group that has the Identity global/HelpDesk. In this example, the AccessLevel property is set to Tier3.
  
```
Set-CsClsSecurityGroup -Identity "global/HelpDesk" -AccessLevel "Tier3"
```

### Example 2

In Example 2, the access level is modified for all the centralized logging security groups configured at the global scope. To do this, the command first calls the **Get-CsClsSecurityGroup** cmdlet along with the Filter parameter; the filter value "global/*" limits the returned data to security groups configured at the global scope. Those groups are then piped to the **Set-CsClsSecurityGroup** cmdlet, which sets the AccessLevel property of each group to Tier3. 
  
```
Get-CsClsSecurityGroup -Filter "global/*" | Set-CsClsSecurityGroup-AccessLevel "Tier3"
```

### Example 3

Example 3 shows how you can use a single command to change the access level for all the centralized logging security groups who share an existing access level. To carry out this task, the command first calls the **Get-CsClsSecurityGroup** cmdlet without any parameters in order to return a collection of all the centralized logging security groups. That collection is then piped to the **Where-Object** cmdlet, which selects only those groups where the AccessLevel is equal to (-eq) GlobalAccess. In turn, those groups are piped to the **Set-CsClsSecurityGroup** cmdlet, which takes each group and changes the AccessLevel to Tier3. 
  
```
Get-CsClsSecurityGroup | Where-Object {$_.AccessLevel -eq "GlobalAccess"} | Set-CsClsSecurityGroup -AccessLevel "Tier3"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet. 
  
With the Office 365 version of Lync Server, security groups are used to determine which users have access to the personally-identifiable information that is written to the log files. Security groups are created by using the [New-CsClsSecurityGroup](new-csclssecuritygroup.md) cmdlet and then are added to a collection of centralized logging configuration settings. After these groups have been created, you can modify their property values by using the **Set-CsClsSecurityGroup** cmdlet. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsSecurityGroup"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsClsSecurityGroup** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AccessLevel_ <br/> |Optional  <br/> |System.String  <br/> |String value specifying the access level assigned to the group. Access levels are assigned by administrators and used to categorize security groups. For example:  <br/> -AccessLevel "Tier3"  <br/> Multiple groups can share the same access level. Currently the only values that have meaning are "Tier3", "Tier2", "Product", "Ops", and "Pii".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the centralized logging security group to be modified. A security group identity consists of the scope where the group was created followed by the group name. For example, to modify a group named HelpDesk created at the global scope, use the following syntax:  <br/> -Identity "global/HelpDesk"  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsClsSecurityGroup** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup#Decorated object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsClsSecurityGroup** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsClsSecurityGroup](get-csclssecuritygroup.md)
  
[New-CsClsSecurityGroup](new-csclssecuritygroup.md)
  
[Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md)

