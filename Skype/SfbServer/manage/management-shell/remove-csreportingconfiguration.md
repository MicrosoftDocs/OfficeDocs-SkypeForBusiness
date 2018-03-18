---
title: "Remove-CsReportingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 17cc1865-4bd9-4630-9947-2c432d1203b3
description: "Removes an existing collection of reporting configuration settings. Reporting configuration settings are used to specify the URL for installations of Skype for Business Server 2015 Monitoring Reports. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsReportingConfiguration
 
Removes an existing collection of reporting configuration settings. Reporting configuration settings are used to specify the URL for installations of Skype for Business Server 2015 Monitoring Reports. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsReportingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

In Example 1, the reporting configuration settings with the Identity service:MonitoringDatabase:atl-sql-002.litwareinc.com are removed.
  
```
Remove-CsReportingConfiguration -Identity "service:MonitoringDatabase:atl-sql-002.litwareinc.com"
```

### Example 2

In Example 2, all the reporting configuration settings currently in use in the organization are removed. To do this, the command first uses the **Get-CsReportingConfiguration** cmdlet to return a collection of all the reporting configuration settings. This collection is then piped to the **Remove-CsReportingConfiguration** cmdlet, which removes each item in the collection.
  
```
Get-CsReportingConfiguration | Remove-CsReportingConfiguration
```

### Example 3

The command shown in Example 3 deletes any reporting configuration settings where the reporting URL is set to https://atl-sql-002.litwareinc.com/lync_reports. To carry out this task, the command first uses the **Get-CsReportingConfiguration** cmdlet to return all the reporting configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the ReportingURL property is equal to https://atl-sql-002.litwareinc.com/lync_reports. That filtered collection is then piped to the **Remove-CsReportingConfiguration** cmdlet, which removes each item in the collection.
  
```
Get-CsReportingConfiguration | Where-Object {$_.ReportingUrl -eq "https://atl-sql-002.litwareinc.com/lync_reports" | Remove-CsReportingConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

Reporting configuration settings are used to specify the home page for the Skype for Business Server 2015 Monitoring Reports; if you are not using Monitoring Reports then there is no reason for you to modify the reporting configuration settings.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsReportingConfiguration** cmdlet are not available in the Skype for Business Server 2015.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the monitoring database whose reporting configuration settings are to be removed. For example:  <br/>  `-Identity "Service:MonitoringDatabase:atl-sql-001.litwareinc.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsReportingConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsReportingConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsReportingConfiguration](get-csreportingconfiguration.md)
  
[New-CsReportingConfiguration](new-csreportingconfiguration.md)
  
[Set-CsReportingConfiguration](set-csreportingconfiguration.md)

