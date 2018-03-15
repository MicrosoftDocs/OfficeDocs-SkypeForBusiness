---
title: "Set-CsReportingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8e7c8e8c-ab68-4f95-a58e-b04a9b2110ea
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsReportingConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies the reporting URL for an existing collection of reporting configuration settings. Reporting configuration settings are used to specify the URL used to access Lync Server 2013 Monitoring Reports. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsReportingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 modifies the reporting URL for the reporting configuration settings with the Identity service:MonitoringDatabase:atl-sql-002.litwareinc.com. In this example, the reporting URL is changed to "https://atl-sql-002.litwareinc.com/lync_reports".
  
```
Set-CsReportingConfiguration -Identity "service:MonitoringDatabase:atl-sql-002.litwareinc.com" -ReportingURL "https://atl-sql-002.litwareinc.com/lync_reports"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Reporting configuration settings are used to specify the home page for the Lync Server Monitoring Reports; if you are not using Monitoring Reports then there is no reason for you to modify the reporting configuration settings.
  
If you do not know the URL for the Monitoring Reports home page you can determine that URL by doing the following:
  
1. Open the SQL Server Reporting Services Configuration Manager for the SQL Server instance that contains your monitoring database.
    
2. In the Configuration Manager, click **Report Manager URL** and then click the URL for your Monitoring Reports. If you see two URLs, click the one that uses the https protocol. 
    
3. In SQL Server Reporting Services, click **LyncServerReports**.
    
4. On the LyncServerReports page, click **Reports Home Page**. That will take you to the home page for the Monitoring Reports. You can then copy the URL and use that URL in conjunction with the CsReportingConfiguration cmdlets.
    
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsReportingConfiguration"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsReportingConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the monitoring database whose reporting configuration settings are being modified. For example:  <br/> -Identity "Service:MonitoringDatabase:atl-sql-001.litwareinc.com"  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _ReportingUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the Lync Server 2013 Monitoring Reports.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsReportingConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsReportingConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsReportingConfiguration](get-csreportingconfiguration.md)
  
[New-CsReportingConfiguration](new-csreportingconfiguration.md)
  
[Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)

