---
title: "Associate Monitoring Reports with a mirror database in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 42b797c6-8db8-4ad7-886e-8ddf8deb06f9
description: "Summary: Learn how to associate Monitoring Reports with a mirror database used by Skype for Business Server."
---

# Associate Monitoring Reports with a mirror database in Skype for Business Server 
 
**Summary:** Learn how to associate Monitoring Reports with a mirror database used by Skype for Business Server.
  
## Monitor reports with a mirror database

If you configure a mirror for your monitoring database, that mirror database will take over as the primary database if a failover occurs. However, if you use Skype for Business Server Monitoring Reports and a failover occurs, you might find that your Monitoring Reports are not connecting to the mirror database. This is because, when you install Monitoring Reports, you specify only the location of the primary database; you do not specify the location of the mirror database.
  
To get Monitoring Reports to automatically failover to the mirror database, you must add the mirror database as a "failover partner" to the two databases that are used by Monitoring Reports (one database for Call Detail Record data, and the other for Quality of Experience (QoE) data). (Note that this step should be performed after you have installed Monitoring Reports.) You can add the failover partner information by manually editing the connection string values used by these two databases. To do that, complete the following procedure:
  
1. Use Internet Explorer to open the **SQL Server Reporting Services** home page. The Reporting Services home page URL includes:
    
   - The **http:** prefix.
    
   - The fully qualified domain name (FQDN) of the computer where the Reporting Services are installed (for example, **atl-sql-001.litwareinc.com**).
    
   - The character string **/Reports_**.
    
   - The name of the database instance where the Monitoring Reports are installed (for example, **archinst**).
    
     For example, if SQL Server Reporting Services was installed on the computer atl-sql-001.litwareinc.com and the Monitoring Reports use the database instance archinst, the home page URL would look like this:
    
     **http://atl-sql-001.litwareinc.com/Reports_archinst**
    
2. After you have accessed the Reporting Services home page, click **ServerReports**, and then click **Reports_Content**. That will take you to the **Reports_Content** page for the Skype for Business Server Monitoring Reports.
    
3. On the **Reports_Content** page, click the **CDRDB** data source.
    
4. On the **CDRDB** page, on the **Properties** tab, look for the text box labeled **Connection string**. The current connection string will look similar to this:
    
    Data source=(local)\archinst;initial catalog=LcsCDR
    
5. Edit the connection string to include the server name and database instance for the mirror database. For example, if the server is named atl-mirror-001 and the mirror database is in the archinst instance, you will need to add to specify the mirror database using this syntax:
    
    Failover Partner=atl-mirror-001\archinst
    
    Your edited connection string will look like this:
    
    Data source=(local)\archinst;Failover Partner=atl-mirror-001\archinst;initial catalog=LcsCDR
    
6. After updating the connection string, click **Apply**.
    
7. On the **CDRDB** page, click the **Reports_Content** link. Click the **QMSDB** data source, and then edit the connection string for the QoE database. For example:
    
    Data source=(local)\archinst;Failover Partner=atl-mirror-001\archinst;initial catalog=QoEMetrics
    
8. Click **Apply**.
    
## See also

[Install Monitoring Reports in Skype for Business Server](install-monitoring-reports.md)
  
[Using Monitoring Reports in Skype for Business Server](../../manage/health-and-monitoring/monitoring-reports.md)
