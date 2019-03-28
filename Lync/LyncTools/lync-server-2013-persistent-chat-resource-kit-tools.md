---
title: Lync Server 2013 Persistent Chat Resource Kit Tools
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Lync Server 2013 Persistent Chat Resource Kit Tools
ms:assetid: 7a34d2ba-eb25-4e22-92d1-b9baf81b102c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945599(v=OCS.15)
ms:contentKeyID: 51541423
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync Server 2013 Persistent Chat Resource Kit Tools

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-24_

The Lync Server 2013 Persistent Chat Resource Kit tools help to make routine tasks easier for IT administrators who deploy and manage Lync Server 2013 Persistent Chat Server. In addition to installation instructions, this topic describes the purpose of each tool, and examples of its use.

<div>

## Installation of the Resource Kit Tools

To install the Lync Server 2013, Resource Kit Tools, download **PersistentChatReskit.msi**. Run **PersistentChatReskit.msi** to do a simple installation. The .msi installs all the tools in the following path: \\**Program Files\\ Microsoft Lync Server 2013\\Persistent Chat Server Resource Kit**. Tools that are self-contained executables are in this folder. Tools that also have files are in their own subfolders.

<div>


> [!IMPORTANT]  
> After installing the Lync Server 2013, Resource Kit Tools, you must install <STRONG>PsExec.exe</STRONG> and copy <STRONG>PsExec.exe</STRONG> to the following path: \\<STRONG>Program Files\ Microsoft Lync Server 2013\Persistent Chat Server Resource Kit\ChatStressTool</STRONG>. If you do not copy <STRONG>PsExec.exe</STRONG>, the Persistent Chat Stress Tool will throw an error exception, and not perform correctly. Make sure that you meet this prerequisite requirement prior to running the tool. For details about installing <STRONG>PsExec.exe</STRONG>, see <A href="http://go.microsoft.com/fwlink/p/?linkid=282246">http://go.microsoft.com/fwlink/p/?LinkId=282246</A>.



</div>

</div>

<div>

## Supported Environments

For optimal performance, the Lync Server 2013, Resource Kit Tools should be installed in the same environment and with the same specifications that are required for Lync Server 2013.

</div>

<div>

## Resource Kit Tools Overview

Here are the tools that are provided in the Lync Server 2013 Persistent Chat Resource Kit. The following section provides a description of each tool, including requirements and example usage.

  - AffCheck

  - ChatMonitoringSummary

  - ChatStress Tool

  - ChatUpgradeVerifier

  - ChatUsageReport

  - ScheduleADSyncforPrincipal

</div>

<div>

## AffCheck

<div>

## Description

The AffCheck tool confirms that the Persistent Chat back-end database user and group affiliation records match that of Active Directory Domain Services.

</div>

<div>

## Requirements

The tool is installed with the PersistentChatResKit installer on a domain joined machine.

The user account under which the tool is run must have Read access to the Persistent Chat back-end database and Active Directory Domain Services.

</div>

<div>

## Usage

Configure the AffCheck.exe.config file according to the instructions in the config file and run the AffCheck tool without command-line parameters. Following are the contents of the default AffCheck.exe.config.

**AffCheck.exe.config:**

```XML
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <appSettings>
        <!--Domain Controller IP Address-->
        <add key="LDAP" value="LDAP://0.0.0.0/"/>
        
        <!-- Domain DN  This is case sensitive, it must match exactly-->
        <add key="DomainComponent" value ="DC=DOMAIN,DC=COM"/>
        
        <!--Domain Administrator Login and Password-->
        <add key="DomainLogin" value="DOMAIN\Administrator"/>
        <add key="DomainPassword" value ="password"/>
        
        <!-- Connection string to Group Chat Database-->
        <add key="ConnectionString" value="data source=SQL_SERVER\INSTANCE;initial catalog=DATABASE_NAME;integrated security=SSPI"/>
        
        <!--Check group affiliations-->
        <add key="CheckGroups" value="true"/>
        
        <!--Check user affilations-->
        <add key="CheckUsers" value="true"/>
        
        <!--List all affiliations if there is a mismatch between database and active directory-->
        <add key="ListAffiliations" value="true"/>
    
        <!--If you need to offset the results of the number of affilations in AD(can be negative to add to AD parent count)-->
        <add key="Offset" value ="0"/>
    
        <!--If you need to ignore certain parents, provide a semi colon delimitted list.-->
        <add key="Ignore" value ="DC=uatest,DC=test,DC=contoso,DC=com;DC=test,DC=contoso,DC=com"/>
      </appSettings>
    </configuration>
  ```
</div>

</div>

<div>

## ChatMonitoringSummary

<div>

## Description

The PersistentChatMonitoringSummary tool moves Persistent Chat monitoring information from the monitoring database into a specified CSV log file.

The CSV file will contain a breakdown of Persistent Chat sessions by number of total sessions, successful sessions, unexpected failures, expected failures, and a breakdown of the unexpected failures by diagnostic ID, number of failures, and failure description.

</div>

<div>

## Requirements

Install the Persistent Chat Resource Kit tools on a domain-joined machine that has access to the Monitoring database.

The user account under which the tool runs must have Read access to the Monitoring database.

The file, PersistentChatMonitoringSummary.exe.config, must contain a \<connectionStrings\> section that defines the connection string to the Monitoring database. It must also contain a key for the PersistentChatEndpointUri that the monitoring data will be gathered for, and a file path to a location for the CSV file that will be generated. Refer to the installed config file for examples. The file must be located in the same directory as the tool.

</div>

<div>

## Usage

```Batch
    PersistentChatMonitoringSummary [-StartDateTime <date>] [-EndDateTime <date>]
```

These parameters define the selection of data:

**StartDateTime:** Optionally specifies the start date of the selection period. Default: 1/1/1753 12:00:00 AM

**EndDateTime:** Optionally specifies the last date of the selection period. Default: Now

</div>

<div>

## Example

```Batch
    C:\Users\Administrator.VDOMAIN>Desktop\PersistentChatMonitoringSummary.exe
    Reading database connection information, Persistent Chat endpoint uri, and csv output path information from the application config file...
    Connecting to Monitoring database with connection string specified in the application config file...
    Gathering Persistent Chat Session Summary information between "1/1/1753 12:00:00 AM" and "11/19/2012 10:11:25 AM" for Persistent Chat Endpoint Uri "persistentChatEndpointUri@domain.com"...
    Press enter to continue or hit ctr-c if these settings are incorrect...
    
    The summary information about Persistent Chat sessions from the Monitoring database has been output to C:\PersistentChatMonitoring_dd4ace24-4c8a-4a3d-8fd4-591bdfacf47b.csv
    Press enter to exit...
```

</div>

</div>

<div>

## Persistent Chat Stress Tool

<div>

## Description

The Persistent Chat Stress tool provides an easy way to simulate usage of Persistent Chat to test real-world performance, including varied user models to better fit your expected usage scenarios.

</div>

<div>

## Requirements

Install the Persistent Chat Resource Kit tools onto a domain-joined machine that has access to the Persistent Chat back-end database.

In addition to this *controller* machine, you will need several *loader* machines. For every 10K users in your user model, you will need at least 4GB of free RAM on a loader machine. For example, a run with 80K users will require about 32GB of RAM spread across all loader machines. We recommend that you have at least three loader machines, regardless of expected load.

Loader machines must have the .NET 4.5 Framework as well as the Visual C++ 2012 Redistributable installed.

</div>

<div>

## Configuration

Copy ChatStressTool files into a shared folder accessible from all loader machines.

Create users and channels for use in the stress run:

  - Create as many users as your user model calls for, enable them for Lync, and set their Persistent Chat policy to Enabled.

  - Create a category for your stress channels, and then create as many rooms as are needed under that category. The category should have all stress users in its **Allowed** list (by way of adding their OU), and stress rooms should have a privacy setting of **Open**.

  - We recommend creating extra stress rooms. You can create 50,000 rooms with the following Windows PowerShell command-line interface command:
    ```Powershell
        for ($i = 0; $i -le 50000; $i++) { New-CsPersistentChatRoom -Category <parent category> -Name "StressChan_$i" -Privacy Open }
    ```    

Edit the configuration files to fit your topology:

In **LoaderProcess.exe.config**, change “controller.contoso.com” to the controller machine’s fully qualified domain name (FQDN).

In **StressLauncher.exe.config:**

1.  Change the “LoaderBinary” setting value to the shared folder’s path.

2.  Change “AdminUser”/”AdminPassword” to credentials that have admin access to loader machines.

3.  Change “ChannelCategory” to the name of the category that stress channels have been created under.

4.  Change “UserNamePattern” and “UserPasswordPattern” to a template that matches your stress user credentials. {0} is replaced with the user’s index number.

5.  Change “Domain” to the SIP domain of your test topology.

6.  Change “ConnectionString” to a connection string for your Persistent Chat back-end database.

7.  Change “UserIndexStart” to the index of the first stress user.

8.  Change “LyncFQDN” to the FQDN of your Front End pool.

9.  Modify the “Machines” list to include machine names for all of your loader machines.

10. Change the baseAddress of the service endpoint (default is “controller.contoso.com”) to the FQDN of your controller machine.

</div>

<div>

## Usage

After configuration is complete, open StressLauncher.exe on the controller machine. You can launch StressLauncher as any user. The credentials under which the loader processes start on the loader machines must be specified in the config file. You also must give a connection string that has Read access to the Persistent Chat back-end database. If this connection string uses integrated Windows authentication, you must launch StressLauncher as a user that has this access.

Alter the user model settings as needed. Click **Start Load** to initiate a run. After a minute or so, users will start being signed in, and the progress bar will begin to fill. At this point, you may can the controller machine working and take performance measurements.

</div>

</div>

<div>

## ChatUpgradeVerifier

<div>

## Description

ChatUpgradeVerifier is a Persistent Chat specific database comparison tool. The tool compares either the Group Chat 2007 R2 or Group Chat 2010 Database (2007/2010Db) to the Persistent Chat 2013 Database (2013Db).

The tool will check, one by one, each category, Persistent Chat room, and add-in in 2007/2010Db to see if it appears in the 2013Db. The comparison includes checking all settings on the category, chat room, or add-in, any principals in scope on the category, and any principal in a role on either the category or the chat room. If a category or a chat room does not appear correctly in the 2013Db, the differences will be output to a conflicts file. If, after the upgrade has occurred, the 2007/2010Db is changed and then this tool is run, there will be a differences output to the conflicts file. Note that this application is a database comparison tool only and does not validate the upgrade process.

</div>

<div>

## Requirements

Install the Persistent Chat Resource Kit tools on a domain-joined machine that has access to the Persistent Chat back-end databases (previous and current versions for Persistent Chat).

The user account under which the tool runs must have Read access to the Persistent Chat databases.

The ChatUpgradeVerifier.exe.config file must contain either the GroupChat2007R2Db parameter or the GroupChat2010Db parameter, with a connection string to the appropriate Group Chat database (either Groupchat 2007R2 or 2010). It must also contain a PersistentChat2013Db parameter, with a connection string to the Persistent Chat 2013 database.

</div>

<div>

## Usage

Run **ChatUpgradeVerifier** without any parameters.

</div>

<div>

## Example

![Running ChatUpgradeVerifier.exe.](images/JJ945599.4c273bc3-7926-47c7-ade7-34522721ebf9(OCS.15).jpg "Running ChatUpgradeVerifier.exe.")

</div>

</div>

<div>

## Persistent Chat Usage Report

<div>

## Description

The ChatUsageReport tool generates an HTML report of Persistent Chat service usage.

</div>

<div>

## Requirements

Install the Persistent Chat Resource Kit tools on a domain-joined machine that has access to the Persistent Chat back-end database.

The user account under which the tool is run must have Read access to the Persistent Chat back-end database.

The file, ChatUsageReport.exe.config, must contain a \<connectionStrings\> section defining the connection string to the Persistent Chat back-end database. The contents of the default config file are included here, for your reference.

</div>

<div>

## Usage

```Powershell
    ChatUsageReport [-StartDate {date}] [-EndDate {date}] [-TopActiveUsers {n}] [-TopActiveRooms {n}] [-LeastActiveRooms {n}] [-RoomsInactiveSince {Date}] [-OutputFolder {path}]
```
These parameters define the selection of data:

**StartDate:** Optionally specifies the UTC start date of the selection period. Default: Earliest Date

**EndDate:** Optionally specifies the UTC end date of the selection period. Default: Now

These parameters define how and what data is displayed:

**TopActiveUsers:** If this is specified, the report will include the n most active users in terms of the number of messages the user has posted in the chat room for the selected period. Default: 10

**TopActiveRooms:** If this is specified, the report will include the n most active chat rooms in terms of the number of messages posted in the room for the selected period. Default: 10

**LeastActiveRooms:** If this is specified, the report will include the n least active chat rooms in terms of the number of messages posted in the chat room for the selected period. Rooms will have at least one message posted. Default: 10

**RoomsInactiveSince:** If this is specified, the report will include a list of chat rooms that have been inactive since the specified date. Default: Entire Time

**OutputFolder:** The folder where the ChatUsageReport.html and the graph images will be placed. This must be defined in the config file or on the command line.

All of the command line parameter values can also be specified in the ChatUsageReport.exe.config file that is located in the same directory as the tool. If any value is specified in both the config file and the command line, the command line value will override the config file value.

</div>

<div>

## Output

The report will always include the following output:

  - Top n most active chat rooms by number of message posts for selected period.

  - Top n most active users by number of message posts for selected period.

  - Top n least active chat rooms by number of message posts for selected period.

  - Chat rooms that are inactive for the entire life of the database, or since the specified date.

  - Daily message post trend for selected period.

  - Weekly message post trend for selected period.

  - Monthly message post trend for selected period.

  - Total message posts for selected period.

  - Total number of enabled rooms.

</div>

<div>

## Example

The following example generates a usage report for the entire year 2001 and places the report in the OutputFolder specified in the ChatUsageReport.exe.config.

```Powershell
    ChatUsageReport -RoomsInactiveSince 06-20-2010
```
ChatUsageReport.exe.config:

```XML
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <connectionStrings>
        <!-- The PersistentChat connection string must be defined in this file. -->
        <add name="PersistentChat" connectionString="Data Source=contoso.com\RTC;Initial Catalog=mgc;Integrated Security=SSPI"/>
      </connectionStrings>
      <appSettings>
        <!-- The OutputFolder must be defined here or on the command line. -->
        <add key="OutputFolder" value="."/>
        <!-- The values below are the same as the application defaults. -->
        <add key="StartDate" value="01/01/0001"/>
        <add key="EndDate" value="12/31/9999"/>
        <add key="TopActiveUsers" value="10"/>
        <add key="TopActiveRooms" value="10"/>
        <add key="LeastActiveRooms" value="10"/>
        <add key="RoomsInactiveSince" value="01/01/0001"/>
      </appSettings>
    </configuration></configuration>
```
</div>

</div>

<div>

## ScheduleADSyncForPrincipal

<div>

## Description

ScheduleADSyncForPrincipal is a Microsoft SQL Server 2012 script that must be run directly from within SQL Server Management Studio when connected to the Persistent Chat back-end database. This script enables you to force Persistent Chat to synchronize its records of a user with those of Active Directory Domain Services, rather than waiting for the scheduled synchronization time.

</div>

<div>

## Requirements

The user account under which the script is run must have owner access to the Persistent Chat back-end database.

</div>

<div>

## Usage

Following are the contents of the default script:

```Powershell
    /*
    This script will schedule a principal for a forced AD synchronization cycle
    
    If you're using Sql Server Management Studio, pressing Ctrl+Shift+M will 
    allow you to specify values for the template parameter.
    */
    
        insert into
          tblPrincipalMeta
          (
           prinID
          ,prinAffiliationsDirty
          ,prinAttributesDirty
          ,prinDeleted
          )
          select
            prinID
           ,1
           ,1
           ,0
          from
            tblPrincipal
          where
            prinID not in (select prinID from tblPrincipalMeta) and
            prinID = <PrinID,int,0>
     
        update
          tblPrincipalMeta
        set
          prinAffiliationsDirty = 1
         ,prinAttributesDirty = 1
         ,tryCount = 0
         ,nextTry = null
        where
         prinID = <PrinID,int,0>
```

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

