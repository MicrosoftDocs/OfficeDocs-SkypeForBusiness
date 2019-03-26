---
title: "Install Monitoring Reports in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6f417569-b100-442c-ad48-fdd794626cf7

description: "Summary: Learn how to install a service that will generate Monitoring reports in Skype for Business Server."
---

# Install Monitoring Reports in Skype for Business Server
 
**Summary:** Learn how to install a service that will generate Monitoring reports in Skype for Business Server.
  
Skype for Business Server Monitoring Reports provide you with a wealth of information about the quality and quantity of the communication sessions that take place in your organization. 
  
## Install Monitoring Reports

Monitoring Reports are not automatically installed when you install Skype for Business Server; instead, you must install Monitoring Reports separately, and only after Skype for Business Server has been installed on the computer.
  
> [!NOTE]
> It is recommended that you install Monitoring Reports on the same computer where the monitoring database is installed. This simplifies the process of assigning permissions for accessing the reports: installing Monitoring Reports on the computer that hosts the monitoring store means that you will not have to configure permissions that allow a database on one computer to interact with Reporting Services running on a second computer. 
  
Skype for Business Server Monitoring Reports include over 30 reports designed to provide detailed information about conferences, peer-to-peer IM sessions, user registrations, the Response Group application, and much more. For the 2013 version, Skype for Business Server Monitoring Reports include a number of enhancements:
  
- **New voice quality reports**. These new reports include the [Media Quality Comparison Report in Skype for Business Server](../../manage/health-and-monitoring/comparison.md), which compares quality between different types of calls (for example, between wired calls and wireless calls); and the [Conference Join Time Report in Skype for Business Server](../../manage/health-and-monitoring/join-time-report.md), which provides information regarding the amount of time requires for users to join a conference. 
    
- **Improved reports for analyzing and troubleshooting both video and application sharing sessions.** the [Media Quality Summary Report in Skype for Business Server](../../manage/health-and-monitoring/summary.md) provides a way to analyze video and application sharing calls, while the [Server Performance Report in Skype for Business Server](../../manage/health-and-monitoring/server-performance.md) details the performance of servers generating these calls. Video and application sharing metrics are also now reported by the [Peer-to-Peer Session Detail Report in Skype for Business Server](../../manage/health-and-monitoring/peer-to-peer-session-detail-report.md) and the [Conference Detail Report in Skype for Business Server](../../manage/health-and-monitoring/detail-report.md).
    
- **Improved report performance**. This includes faster response and data retrieval time, as well as faster and easier navigation through the reports.
    
More information on the individual reports can be found in the Monitoring Reports documentation.
  
> [!NOTE]
> There is another report - QoE Call Detail Subreport - included in Skype for Business Server. However, this report is primarily for internal use, and is not intended to be directly accessed. 
  
There are two ways to install Skype for Business Server Monitoring Reports: you can use the Skype for Business Server Deployment Wizard or you can use a Windows PowerShell script included with the Skype for Business Server installation files. Regardless of the method you use to install the reports you must first make sure that you:
  
- Have the right to add a database role to a user account in the monitoring database.
    
- Hold the Content Manager role in SQL Server Reporting Services. This role gives you the right to deploy reports to SQL Server Reporting Services.
    
To install the Monitoring Reports by using the Deployment Wizard, complete the following steps:
  
1. Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Deployment Wizard**.
    
2. In the Deployment Wizard, click **Deploy Monitoring Reports** in order to start the Deploy Monitoring Reports wizard.
    
3. In the Deploy Monitoring Reports wizard, on the **Specify Monitoring Database** page, make sure that the fully qualified domain name of the computer hosting your monitoring store appears in the **Monitoring database** dropdown list. (If you have multiple monitoring stores you will need to select the appropriate server from the dropdown list.) Verify that the correct SQL Server instance appears in the **SQL Server Reporting Services (SSRS) instance** box (for example, **atl-sql-001.litwareinc.com/archinst**) and then click **Next**.
    
4. On the **Specify Credentials** page, in the **User name** box, type the domain name and user name of the account to be used when accessing the Monitoring Reports (for example, **litwareinc\kenmyer**). If you do not use this format (domain\user name) an error will occur.
    
    Type the user account password in the **Password** box, and then click **Next**. Note that no special rights are required for this account. The account will automatically be granted the required logon and database permissions when setup completes.
    
5. On the **Specify Read-Only Group** page enter the name of a security group that will be granted read-only access to the SQL Server Reporting Services in the User group box. For example, to give read-only administrators access to the reports enter **RTCUniversalReadOnlyAdmins**. Click **Next**.
    
6. On the **Executing Commands** page, click **Finish**.
    
Monitoring Reports can also be installed from the Skype for Business Server Management Shell by running the script DeployReports.ps1; this Windows PowerShell script can be found in the \<install location\>\Skype for Business Server 2015\Deployment\Setup folder. To install Monitoring Reports using DeployReports.ps1, type a command similar to the following at the Management Shell prompt:
  
```
C:\Program Files\Skype for Business Server 2015\Deployment\Setup\DeployReports.ps1 -storedUserName "litwareinc\kenmyer" -storedPassword "p@ssw0rd" -readOnlyGroupName "RTCUniversalReadOnlyAdmins" -reportServerSqlInstance "atl-sql-001.litwareinc.com" -monitoringDatabaseId "MonitoringDatabase:atl-sql-001.litwareinc.com"
```

The parameters used in the preceding command are described in the following table:
  
|**Parameter Name**|**Required**|**Description**|
|:-----|:-----|:-----|
|storedUserName  <br/> |Yes  <br/> |User account (in the format domain\username) used to access the monitoring store; for example:  <br/> ```-storedUserName "litwareinc\kenmyer"``` This account must have the previously-specified SQL Server and SQL Server Reporting Services permissions or the script will fail.  <br/> |
|storedPassword  <br/> |Yes  <br/> |Password for the user account used to access the monitoring store.  <br/> |
|readOnlyGroupName  <br/> |No  <br/> |Domain or local security group whose members will be granted read-only access to the Monitoring Reports. Note that the script will fail if the specified group does not exist. If you later decide to revoke these permissions, or if you decide to grant other users or other groups access permissions, you can do so using the SQL Service Reporting Services Report Manager.  <br/> |
|reportSqlServerInstance  <br/> |No  <br/> |SQL Server instance that hosts the Reporting Service. The Reporting instance must be specified using the fully qualified domain name of the Report Server; for example:  <br/> ```-reportServerSqlInstance atl-sql-001.litwareinc.com``` If this parameter is not included the script will assume that the reporting services are hosted by the same SQL Server instance that hosts the monitoring database.  <br/> |
|monitoringDatabaseId  <br/> |No  <br/> |Service Identity for the monitoring database. You can return the Identities for your monitoring databases by running this command:  <br/> ```Get-CsService -MonitoringDatabase```|
   
After the Monitoring Reports have been installed you must then use the New-CsReportingConfiguration cmdlet to configure the URL used to access these reports. This task can be carried out from the Skype for Business Server Management Shell by running the following Windows PowerShell command. Note that it is recommended, but not required, that you use the HTTPS protocol when configuring the reporting URL:
  
```
New-CsReportingConfiguration -Identity 'service:MonitoringDatabase:atl-sql-001.litwareinc.com' -ReportingURL 'https://atl-sql-001.litwareinc.com:443/Reports_ARCHINST'
```

In the preceding command, the ReportingUrl property should be set to the Report Manager URL used by SQL Server 2008 R2 Reporting Services. You can determine the Report Manager URL by completing the following steps on the computer where SQL Server Reporting Services has been installed:
  
1. Click Start, click All Programs, click Microsoft SQL Server 2008 R2, click Configuration Tools, and then click Reporting Services Configuration Manager.
    
2. In the Reporting Services Configuration Connection dialog box, make sure that the name of the Reporting Services computer appears in the Server Name box. Select the SQL Server instance from the Report Server Instance dropdown list and then click Connect.
    
3. In Reporting Services Configuration Manager, click Report Manager URL. One or more URLs should appear in the Report Manager URL pane. Any of these URLs can be used as the Reporting URL although, again, it is recommended that the ReportingUrl use the HTTPS protocol.
    
If you have set up a mirror database for your monitoring database then you must also associate the Monitoring Reports with the mirror database. See the article [Associate Monitoring Reports with a mirror database in Skype for Business Server](monitoring-reports-with-a-mirror-database.md) for details.
  

