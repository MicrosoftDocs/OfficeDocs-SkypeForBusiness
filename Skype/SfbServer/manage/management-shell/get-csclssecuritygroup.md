---
title: "Get-CsClsSecurityGroup"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ce7aa87a-2355-4025-bba8-d4debf2137d2
description: "Returns information about the centralized logging configuration security groups in use in the organization. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. Security groups are intended for use with Skype for Business Online."
---

# Get-CsClsSecurityGroup
 
Returns information about the centralized logging configuration security groups in use in the organization. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. Security groups are intended for use with Skype for Business Online.
  
This cmdlet was introduced in Lync Server 2013. 
  
```
Get-CsClsSecurityGroup [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the centralized logging security groups configured for use in the organization.
  
```
Get-CsClsSecurityGroup
```

### Example 2

In Example 2, information is returned for a single centralized logging security group: the group with the Identity global/helpdesk.
  
```
Get-CsClsSecurityGroup -Identity "global/HelpDesk"
```

### Example 3

Example 3 returns information for all the centralized logging security groups configured at the global scope. To do this, the Filter parameter is included along with the filter value "global/\*"; that filter value limits the returned data to groups configured at the global scope.
  
```
Get-CsClsSecurityGroup -Filter "global/*"
```

### Example 4

The command shown in Example 4 returns all the centralized logging security groups where the access level has been set to RedmondSupport. To carry out this task, the command first calls the **Get-CsClsSecurityGroup** cmdlet without any parameters; that returns a collection of all the available centralized logging security groups. That collection is then piped to the **Where-Object** cmdlet, which picks out only those groups where the AccessLevel property is equal to RedmondSupport.
  
```
Get-CsClsSecurityGroup | Where-Object {$_.AccessLevel -eq "RedmondSupport"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
With Skype for Business Online, security groups are used to determine which users have access to the personally-identifiable information that is written to the log files. Security groups are created by using the [New-CsClsSecurityGroup](new-csclssecuritygroup.md) cmdlet and then are added to a collection of centralized logging configuration settings. You can return information about your centralized logging security groups by using the **Get-CsClsSecurityGroup** cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsClsSecurityGroup** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a centralized logging security group (or groups). For example, to return a collection of all the groups configured at the global scope, use this syntax:  <br/>  `-Filter "global/*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the centralized logging security group to be returned. A security group identity consists of the scope where the group was created followed by the group name. For example, to return a group named HelpDesk created at the global scope, use the following syntax:  <br/>  `-Identity "global/HelpDesk"` <br/> If this parameter is not specified then the **Get-CsClsSecurityGroup** cmdlet returns information about all your centralized logging security groups. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the centralized logging configuration data from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsClsSecurityGroup** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsClsSecurityGroup** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsClsSecurityGroup](new-csclssecuritygroup.md)
  
[Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md)
  
[Set-CsClsSecurityGroup](set-csclssecuritygroup.md)

