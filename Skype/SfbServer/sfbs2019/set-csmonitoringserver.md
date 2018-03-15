---
title: "Set-CsMonitoringServer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2c6d6660-7e41-4c56-9e04-27c3d1ea3b95
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsMonitoringServer
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to configure new locations for the Monitoring Server database and reporting pack. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsMonitoringServer [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MonitoringDatabase <String>] [-ReportingUrl <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 configures a new URL for the Monitoring Server reporting pack.
  
```
Set-CsMonitoringServer -Identity "MonitoringServer:atl-cs-001.litwareinc.com" -ReportingUrl "https://atl-cs-001.litwareinc.com/reports"
```

## Detailed Description
<a name="sectionSection1"> </a>

Monitoring Server provides you with two important capabilities. For one, it enables you to maintain information about how, and how often, Enterprise Voice is used in your organization. This information is tracked by using call detail recording (CDR), which records such things as who made a call, who that person called, and how long the call lasted. (The actual conversation itself is not recorded.) In addition to that, you can also use Monitoring Server to keep track of Quality of Experience (QoE) data for your Enterprise Voice calls. As the name implies, Quality of Experience data provides information about the quality of a call, measuring such items as packet loss, call degradation, network bitrate, and jitter.
  
When you install Monitoring Server you must specify the location of the SQL Server database used to store CDR and QoE data. Optionally, you can also install SQL Server Reporting Services and the Monitoring Server Report Pack; these two items enable you to access a website that generates standard monitoring reports for you. 
  
As a general rule, after Monitoring Server has been installed and configured you will not need to change the location of either the back-end database or the reporting URL. However, if you do need to change the location of one (or both) of these items, you can do so by running the **Set-CsMonitoringServer** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsMonitoringServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsMonitoringServer"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Monitoring Server to be modified. For example: -Identity "MonitoringServer:atl-cs-001.litwareinc.com". You can retrieve the Identity for all of your Monitoring Servers by using this command:  <br/> Get-CsService -MonitoringServer | Select-Object Identity.  <br/> Note that you can leave off the prefix "MonitoringServer:" when specifying a Monitoring Server. For example: -Identity "atl-cs-001.litwareinc.com".  <br/> |
| _MonitoringDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service location for the new Monitoring Server database. For example: -MonitoringDatabase "MonitoringDatabase:atl-sql-001.litwareinc.com". Make sure you use the service location of the database store and not the SQL Server path name.  <br/> |
| _ReportingUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the Monitoring Server reports. Note that these reports will not be available unless you install SQL Server Reporting Services and the Monitoring Server Report Pack.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsMonitoringServer** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsMonitoringServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayMonitoringServer object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsService](get-csservice.md)

