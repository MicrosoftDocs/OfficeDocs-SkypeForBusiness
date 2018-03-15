---
title: "New-CsClsSecurityGroup"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e42f2d5f-7720-4b69-8563-48172120d8d9
description: "Creates a new centralized logging configuration security group. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013."
---

# New-CsClsSecurityGroup
 
Creates a new centralized logging configuration security group. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsClsSecurityGroup -Identity <XdsIdentity> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new centralized logging security group with the Identity global/HelpDesk. In this example, the AccessLevel property is set to Tier3.
  
```
New-CsClsSecurityGroup -Identity "global/HelpDesk" -AccessLevel "Tier3"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
With Skype for Business Online, security groups are used to determine which users have access to the personally-identifiable information that is written to the log files. Security groups are created by using the New-CsClsSecurityGroup cmdlet and then are added to a collection of centralized logging configuration settings. 
  
 **Skype for Business Server Control Panel:** The functions carried out by the **New-CsClsSecurityGroup** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AccessLevel_ <br/> |Required  <br/> |System.String  <br/> |String value specifying the access level assigned to the group. Access levels are arbitrary string values assigned by administrators and used to categorize security groups. For example:  <br/>  `-AccessLevel "Tier3"` <br/> Multiple groups can share the same access level. Currently the only values that have meaning are "Tier3", "Tier2", "Product", "Ops", and "Pii".  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new security group. Security group Identities consist of the centralized logging configuration scope where the group will be created plus a unique security group name. For example, to create a global security group named HelpDesk use this syntax:  <br/>  `-Identity "global/HelpDesk"` <br/> If you use the Identity parameter then you cannot use either the name parameter or the Parent parameter in that same command.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Unique name for the new security group. For example:  <br/>  `-Name "HelpDesk"` <br/> If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Scope of the centralized logging configuration settings where the new security group will be located. For example, to add the new security group to the global settings, use this syntax:  <br/>  `-Parent "global"` <br/> You can return identities for all your centralizing logging "parents" by using this command:  <br/>  `Get-CsCentralizedLoggingConfiguration | Select-Object Identity` <br/> If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsClsSecurityGroup** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsClsSecurityGroup** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsClsSecurityGroup](get-csclssecuritygroup.md)
  
[Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md)
  
[Set-CsClsSecurityGroup](set-csclssecuritygroup.md)

