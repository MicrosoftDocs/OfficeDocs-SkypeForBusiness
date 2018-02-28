---
title: "Remove-CsClsSecurityGroup"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 67778239-9338-4717-abeb-8b87e8cb7a9a
description: "Removes a centralized logging configuration security group. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsClsSecurityGroup
[]
Removes a centralized logging configuration security group. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsClsSecurityGroup -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes the centralized logging security group with the Identity Global/HelpDesk.
  
```
Remove-CsClsSecurityGroup -Identity "global/HelpDesk"
```

### Example 2

In Example 2, all the centralized logging security groups currently in use in the organization are deleted. To do this, the command first calls the **Get-CsClsSecurityGroup** cmdlet without any parameters; this returns a collection of all the centralized logging security groups. That collection is then piped to the **Remove-CsClsSecurityGroup** cmdlet, which deletes each group in the collection.
  
```
Get-CsClsSecurityGroup | Remove-CsClsSecurityGroup
```

### Example 3

Example 3 shows how you can delete all the centralized logging security groups that have the access level RedmondSupport. To carry out this task, the command first uses the **Get-CsClsSecurityGroup** cmdlet to return a collection of all the available centralized logging security groups. That collection is then piped to the **Where-Object** cmdlet, which selects only those groups where the AccessLevel property is set to Tier3. In turn, those groups are piped to, and removed by, the **Remove-CsClsSecurityGroup** cmdlet.
  
```
Get-CsClsSecurityGroup | Where-Object {$_.AccessLevel -eq "Tier3"} | Remove-CsClsSecurityGroup
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
With Skype for Business Online, security groups are used to determine which users have access to the personally-identifiable information that is written to the log files. Security groups are created by using the [New-CsClsSecurityGroup](new-csclssecuritygroup.md) cmdlet and then are added to a collection of centralized logging configuration settings. These groups can later be removed by using the **Remove-CsClsSecurityGroup** cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsClsSecurityGroup** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the centralized logging security group to be removed. A security group identity consists of the scope where the group was created followed by the group name. For example, to remove a group named HelpDesk created at the global scope, use the following syntax:  <br/>  `-Identity "global/HelpDesk"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsClsSecurityGroup** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsClsSecurityGroup** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsClsSecurityGroup](get-csclssecuritygroup.md)
  
[New-CsClsSecurityGroup](new-csclssecuritygroup.md)
  
[Set-CsClsSecurityGroup](set-csclssecuritygroup.md)

