---
title: "New-CsReportingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2f033456-5c1c-4313-ab17-37038a412189
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsReportingConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Creates a new collection of reporting configuration settings at the service scope. Reporting configuration settings are used to specify the URL used to access Lync Server 2013 Monitoring Reports. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsReportingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-ReportingUrl <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new collection of reporting configuration settings assigned to the monitoring database with the identity service:MonitoringDatabase:atl-sql-001.litwareinc.com. In this example, the value of the ReportingUrl property is set to "https://atl-sql-001.litwareinc.com/lync_reports".
  
```
New-CsReportingConfiguration -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -ReportingUrl "https://atl-sql-001.litwareinc.com/lync_reports"
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
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsReportingConfiguration"}
  
 **Lync Server Control Panel:** The functions carried out by the **New-CsReportingConfiguration** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the monitoring database to be associated with the new reporting configuration settings. For example:  <br/> -Identity "Service:MonitoringDatabase:atl-sql-001.litwareinc.com"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _ReportingUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the Lync Server 2013 Monitoring Reports.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsReportingConfiguration** cmdlet does not accept pipelined data. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsReportingConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsReportingConfiguration](get-csreportingconfiguration.md)
  
[Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)
  
[Set-CsReportingConfiguration](set-csreportingconfiguration.md)

