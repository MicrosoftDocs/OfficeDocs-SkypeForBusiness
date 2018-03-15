---
title: "Get-CsReportingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e777a154-354a-49da-8140-79f80416bc49
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsReportingConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about the reporting configuration settings in use in the organization. Reporting configuration settings are used to specify the URL used for accessing Lync Server 2013 Monitoring Reports. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsReportingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information for all the reporting configuration settings currently in use in the organization.
  
```
Get-CsReportingConfiguration
```

### Example 2

In Example 2, information is returned for a single collection of reporting configuration settings: the settings with the Identity "Service:MonitoringDatabase:atl-sql-001.litwareinc.com".
  
```
Get-CsReportingConfiguration -Identity "Service:MonitoringDatabase:atl-sql-001.litwareinc.com"
```

### Example 3

In Example 3, information is returned for all the reporting configuration settings that have an Identity that ends in ".litwareinc.com". To do this, the command uses the Filter parameter and the filter value "\*.litwareinc.com".
  
```
Get-CsReportingConfiguration -Filter "*.litwareinc.com"
```

### Example 4

Example 4 returns information for all the reporting configuration settings that include the string value "_ARCHINST" somewhere in their reporting URL. To do this the command first uses the **Get-CsReportingConfiguration** cmdlet to return a collection of all the reporting configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the ReportingUrl includes (-like) the string value "_ARCHINST". 
  
```
Get-CsReportingConfiguration | Where-Object {$_.ReportingUrl -like "*_ARCHINST*"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Reporting configuration settings are used to specify the home page for the Lync Server Monitoring Reports; if you are not using Monitoring Reports then there is no reason for you to modify the reporting configuration settings.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsReportingConfiguration
  
 **Lync Server Control Panel:** The functions carried out by the **Get-CsReportingConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when specifying the reporting configuration settings to be returned. For example, this syntax returns all the settings configured at the service scope:  <br/> -Filter "service:\*"  <br/> Note that you cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the monitoring database associated with the reporting configuration settings. For example:  <br/> -Identity "Service:MonitoringDatabase:atl-sql-001.litwareinc.com"  <br/> If you do not include either the Identity parameter or the Filter parameter in your command, then the **Get-CsReportingConfiguration** cmdlet will return all the reporting configuration settings in use in your organization.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the reporting configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsReportingConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsReportingConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsReportingConfiguration](new-csreportingconfiguration.md)
  
[Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)
  
[Set-CsReportingConfiguration](set-csreportingconfiguration.md)

