---
title: 'Lync Server 2013: Using Microsoft SQL Server 2008 R2 as your System Center Operations Manager database'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Using Microsoft SQL Server 2008 R2 as your System Center Operations Manager database
ms:assetid: 0efe76da-8854-499e-bdc7-3623244a8e85
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687969(v=OCS.15)
ms:contentKeyID: 49733555
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Microsoft SQL Server 2008 R2 as your System Center Operations Manager database for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-29_

To use SQL Server 2008 R2 as your back-end database, complete the steps detailed in this topic.

<div>

## Configuring SQL Server 2008 R2 and SQL Server Reporting Services

Before you begin installing System Center Operations Manager you must make two changes to your SQL Server 2008 R2 and your SQL Server Reporting Services configuration. (These changes are required only if you are using SQL Server 2008 R2 as your Operations Manager database.) First, do the following on the computer that will host your Operations Manager database:

1.  Click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **C:\\Program Files\\Microsoft SQL Server\\ MSRS10\_50.ARCHINST\\Reporting Services\\ReportServer** and then press ENTER.

3.  In the **ReportServer** folder, open the file **rsreportserver.config** in Notepad or any other text editor.

4.  Near the beginning of the file you will see a series of "Add Key" nodes. Find the entry that begins **\<Add Key="SecureConnectionLevel"** and set the value to **0**:
    
        <Add Key="SecureConnectionLevel" Value="0"/>

5.  Save the file **rsreportserver.config** and then close your text editor.

After updating the Report Server configuration file you must then assign the correct certificate to SQL Server Reporting Services. To do that:

1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Reporting Services Configuration Manager**.

2.  In the **Reporting Services Configuration Connection** dialog box, make sure that the name of your server appears in the **Server Name** box. Select the SQL Server instance that will host your Operations Manager database (for example, **ARCHINST**) from the **Report Server Instance** drop-down list and then click **Connect**.

3.  In Reporting Services Configuration Manager, click **Web Service URL**.

4.  On the **Web Service URL** page, select the certificate to be used for your Reporting Services from the **SSL Certificate** dropdown list and then click **Apply**. After a few seconds, you will see a pair of URLs listed under **Report Server Web Service URLs**.

5.  Click both of the URLs to verify that you can access SQL Server Reporting Services.

6.  Close Reporting Services Configuration Manager.

</div>

<div>

## Creating a System Center Operations Manager database for use with SQL Server 2008 R2

If you want to configure System Center Operations Manager to use a SQL Server 2008 R2 database, you will need to "manually" create the Operations Manager database on the computer running SQL Server 2008 R2. (Again, these steps are not required if you are using SQL Server 2005 or SQL Server 2008 as your back-end database.)

To manually create an Operations Manager database do the following:

1.  On the System Center Operations Manager 2007 R2 setup media, in the SupportTools\\AMD64 folder, double-click **DBCreateWizard.exe**.

2.  In the Database Configuration Wizard, on the **Welcome to the Database Configuration Wizard** page, click **Next**.

3.  On the **Database Information** page leave all the settings as-is and then click **Next**

4.  On the **Management Group Configuration** page type a name for your Management Group (for example, **Lync Server Monitoring**) in the **Management Group name** box and then click **Next**.

5.  On the **Operations Manager Error Reports** page click **Next**.

6.  On the **Summary** page click **Finish**.

</div>

<div>

## Creating a System Center Operations Manager data warehouse for use with SQL Server 2008 R2

Microsoft Lync Server 2013 ships with three new System Center Operations Manager reports:

  - **End to End Scenario Availability Report**   This report details the availability/uptime for key Lync Server services such as registration or presence.

  - **Capacity Report**   Using performance counter information, this report shows trends for system components such as memory availability and processor usage.

  - **Component Report**   This report lists the top alert generators grouped by Lync Server component.

In order to use these new reports you must install a System Center Operations Manager data warehouse. (A data warehouse provides for long-term storage of operations data.) To use a data warehouse with SQL Server 2008 R2 you must carry out the following steps on the computer that hosts your SQL Server database:

1.  On the System Center Operations Manager setup media, in the Setup\\SupportTools\\AMD64 folder, double-click **DBCreateWizard.exe**.

2.  In the Database Configuration Wizard, on the **Welcome to the Database Configuration Wizard** page, click **Next**.

3.  On the **Database Information** page, select **Operations Manager Data Warehouse Database** from the **Database Type** dropdown list and then click **Next**.

4.  On the **Summary** page click **Finish**.

</div>

<div>

## Installing the System Center Operations Manager console

The Operations Manager console is the primary tool used to manage System Center Operations Manager. Before you install the Operations Manager console, make sure that you have installed a supported version of SQL Server along with the SQL Server Reporting Service. It is also recommended that you run SQL Server's Reporting Services Configuration Manager to verify that the Reporting Service has been correctly installed and configured.

To install the System Center Operations Manager console:

1.  On the System Center Operations Manager setup media, double-click **SetupOM.exe**.

2.  In System Center Operations Manager 2007 R2 Setup, click **Check Prerequisites**.

3.  In the System Center Operations Manager Prerequisite Viewer, select the System Center components to be installed: (**Server**; **Console**; and **PowerShell**) and then click **Check**. Verify that no blocking issues have been reported and then click **Close**. If a blocking issue has been reported, correct the problem and then click **Check** to re-run the prerequisite testing.

4.  In System Center Operations Manager Setup, click **Install Operations Manager**.

5.  In the System Center Operations Manager Setup wizard, on the **Welcome to the System Center Operations Manager Setup Wizard** page, click **Next**.

6.  On the **End-User License Agreement** page, select **I accept the terms in the license agreement** and then click **Next**.

7.  On the **Product Registration** page, type your name in the **User Name** box and name of your organization in the **Organization** box. Type your System Center Operations Manager product key in the **Enter your 25 digit CD Key** box and then click **Next**.

8.  On the **Custom Setup** page select the System Center options to be installed and then click **Next**. You should select **Management Server**, **User Interfaces**, and **Web Console** to be installed. **Database** should not be selected and should not be installed.

9.  On the **SC Database Server Instance** page, verify that the name of the computer where the Operations Manager databases are installed appears in the **System Center Database Server** box. Click **Next**.

10. On the **Management Server Action Account** page, select **Domain or Local Computer Account** and then enter the appropriate values in the **User Account**, **Password**, and **Domain or local computer** boxes. Click **Next**.

11. On the **SDK and Config Service Account** page, select **Domain or Local Computer Account** and then enter the appropriate values in the **User Account**, **Password**, and **Domain or local computer** boxes. Click **Next**.

12. On the **Operations Manager Error Reports** page click **Next**.

13. On the **Customer Experience Improvement Program** page click **Next**.

14. On the **Ready to Install the Program** page, click **Install**.

15. On the **Completing the System Center Operations Manager Setup** page, clear the **Backup Encryption Key** and **Start the console checkboxes** and then click **Finish**.

16. In System Center Operations Manager Setup click **Exit**.

</div>

<div>

## Installing System Center Reporting Services

After installing and configuring the System Center Operations Manager console you must then install System Center Reporting Services. If you are using SQL Server 2008 R2 as your Operations Manager back-end database, that means that you must first make a temporary change to the security group associated with SQL Server Reporting Services. If you are using SQL Server 2008 R2, you must do the following:

1.  Click **Start**, point to **Administrative Tools**, and then click **Server Manager**.

2.  In Server Manager, expand **Configuration**, expand **Local Users and Groups**, and then click **Groups**.

3.  Locate the following group, where atl-sc-001 represents the name of your computer and ARCHINST represents the SQL Server instance for the System Center database: **SQLServerReportServerUser$atl-sc-001$MSRS10\_50.ARCHINST**.

4.  Right-click the group and then click **Rename**. Rename the group by deleting **\_50** from the group name. For example: **SQLServerReportServerUser$atl-sc-001$MSRS10.ARCHINST**.

5.  Close Server Manager.

At this point you are ready to install System Center Reporting Services. To do this:

1.  On the System Center Operations Manager 2007 R2 Setup media, double-click **SetupOM.exe**.

2.  In System Center Operations Manager 2007 R2 Setup, click **Install Operations Manager Reporting**.

3.  In the System Center Operations Manager 2007 R2 Reporting Setup wizard, on the **Welcome to Operations Manager Reporting Setup** page, click **Next**.

4.  On the **End-user License Agreement** page select **I accept the terms of the license agreement** and then click **Next**.

5.  On the **Product Registration** page, ensure that your name and the name of your organization appear in the **User Name** and **Organization** boxes and then click **Next**.

6.  On the **Custom Setup** page, click **Reporting Server** and select **This component, and all dependent components, will be installed on local disk drive**. Click **Data Warehouse** and select **This component will not be available**, and then click **Next**.

7.  On the **Connect to the Root Management Server** page, type the name of your Operations Manager root management server in the **Root Management Server** box and then click **Next**.

8.  On the **Connect to the Operations Manager Data Warehouse** page, type the SQL Server instance where your data warehouse is located in the **SQL Server Instance** box. (If your data warehouse is located in the Default instance then simply type the server name; for example: atl-sql-001.) Verify that the database name **OperationsManagerDW** appears in the **Name** box, and that port **1433** appears in the **SQL Server port** box. Click **Next**.

9.  On the **SQL Server Reporting Instance** page, select your SQL Server reporting server from the **Enter the SQL Server Reporting Services Server** dropdown list and then click **Next**.

10. On the **Data Warehouse Write Account** page, enter the name and password of the user to be initially assigned write permissions to the data warehouse in the **User Account** and **Password** boxes. Select the user's domain from the **Domain** dropdown list and then click **Next**.

11. On the **Data Reader Account** page, enter the name and password of the user account to be used when SQL Reporting Services queries the data warehouse in the **User Account** and **Password** boxes. Select the account domain from the **Domain** dropdown list and then click **Next**.

12. On the **Operational Data Reports** page, click **Next**.

13. On the **Microsoft Update** page, click **Next**.

14. On the **Ready to Install the Program** page, click **Install**.

15. On the **Completing the Operations Manager Reporting Components Setup Wizard** page, click **Finish**.

16. In System Center Operations Manager 2007 R2 Setup, click **Exit**.

After System Center reporting has been installed you then use the following procedure to reset the name of the security group associated with SQL Server reporting. Again, this procedure is only required if you are using SQL Server:

1.  Click **Start**, point to **Administrative Tools**, and then click **Server Manager**.

2.  In Server Manager, expand **Configuration**, expand **Local Users and Groups**, and then click **Groups**.

3.  Locate the following group, where atl-sc-001 represents the name of your computer and ARCHINST represents the SQL Server instance for the archiving and monitoring databases: **SQLServerReportServerUser$atl-sc-001$MSRS10.ARCHINST**.

4.  Right-click the group and then click **Rename**. Rename the group by adding **\_50** to the end of the group name, right before the SQL Server instance name. For example: **SQLServerReportServerUser$atl-sc-001$MSRS10\_50.ARCHINST**.

5.  Close Server Manager.

If the System Center Operations Console is open you will need to close the application and then restart it; if you do not do this the **Reporting** tab will not appear in the Operations Console user interface. Note that, after restarting the Operations Console the first time, it could take several minutes before all the Monitoring Reports appear on the **Reporting** tab.

</div>

</div>

<span> </span>

</div>

</div>

</div>

