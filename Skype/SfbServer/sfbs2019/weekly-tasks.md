---
title: "Weekly tasks in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d564839b-b49d-4c5d-b67e-dc5abb0f6980
description: "In this articleArchive event logsCreate reportsIncident reportsCheck IIS logs and performanceGenerate database reportsCheck for security and Lync Server updatesRun the Lync Server 2013 Best Practice AnalyzerReview SLA performance figuresReview System Center Operations Manager Management Pack and quality of experience reportsGenerating and viewing database reports for enterprise poolsRunning Bandwidth Utilization Analyzer"
---

# Weekly tasks in Lync Server 2013
[]
 **In this article**
  
[Archive event logs](#sectionSection0)
  
[Create reports](#sectionSection1)
  
[Incident reports](#sectionSection2)
  
[Check IIS logs and performance](#sectionSection3)
  
[Generate database reports](#sectionSection4)
  
[Check for security and Lync Server updates](#sectionSection5)
  
[Run the Lync Server 2013 Best Practice Analyzer](#sectionSection6)
  
[Review SLA performance figures](#sectionSection7)
  
[Review System Center Operations Manager Management Pack and quality of experience reports](#sectionSection8)
  
[Generating and viewing database reports for enterprise pools](#sectionSection9)
  
[Running Bandwidth Utilization Analyzer](#sectionSection10)
  
Weekly tasks are generally related to collecting and analyzing logs and reports. 
  
## Archive event logs
<a name="sectionSection0"> </a>

If event logs are not configured to overwrite events as required, they must be regularly archived and deleted. This action is especially important for security logs, which may be required when investigating attempted security breaches.
  
Your organization will have to define policies and procedures for log archiving.
  
## Create reports
<a name="sectionSection1"> </a>

Create status reports to help with capacity planning, SLA reviews, and performance analysis. Use daily data from event log and System Monitor to create reports on disk, memory, and CPU usage. Use System Center Operations Manager to generate uptime and availability reports.
  
Your organization will have to define policies and procedures for status reports.
  
## Incident reports
<a name="sectionSection2"> </a>

Perform a weekly audit of your organization's incident reports that relate to Lync Server. This audit should include the following: 
  
- The top generated, resolved, and pending incidents.
    
- Solutions for unresolved incidents.
    
- Updating reports to include new trouble tickets.
    
- Updating a document repository for troubleshooting guides and post mortems about outages.
    
Since your organization's incident tracking system is a choice independent of Lync Server, specific instructions or pointers are not available. Consult the documentation for the system your organization chose.
  
## Check IIS logs and performance
<a name="sectionSection3"> </a>

Perform a weekly review of Internet Information Services (IIS) logs and performance. For more information about how to monitor IIS logs and performance, see [Windows Server 2003 Internet Information Services (IIS) Event Logging Overview](https://go.microsoft.com/fwlink/?LinkId=36077). The review should include the following: 
  
- Web Service Cache counters to monitor the WWW service cache.
    
- Active Server Pages (ASPs) counters to monitor applications that run as ASPs.
    
## Generate database reports
<a name="sectionSection4"> </a>

### To generate reports on the SQL Database

1. Open Lync Server 2013.
    
2. In the console tree, expand the forest node, expand **Enterprise pools**, and then click the pool for which you want to generate a database report.
    
3. In the details pane, click the **Database** tab. 
    
4. On the **Database** tab, do the following: 
    
1. To view the name of the database, expand **General Settings**, and view the database name.
    
2. To retrieve current user summary statistics for the pool, expand **User Summary Reports**, click **Go**, and view the results.
    
3. To retrieve current per-user data for a single user of the pool, expand **Per-User Reports**, type the user's SIP URI, click **Go**, and view the results.
    
To retrieve current conference summary statistics for the pool, expand **Conference Summary Reports**, click **Go**, and view the results.
  
## Check for security and Lync Server updates
<a name="sectionSection5"> </a>

Identify any new service packs, hotfixes, or updates. If appropriate, test these in a test lab, and use the change control procedures to arrange for deployment to the production servers. Also, Lync Server component updates are now available as part of Windows update. All Lync Server component updates must be updated at the same time on all of the servers that are running Lync Server for which the updates are applicable.
  
## Run the Lync Server 2013 Best Practice Analyzer
<a name="sectionSection6"> </a>

The Lync Server 2013 Best Practices Analyzer Tool is a diagnostic tool that collects configuration information and determines whether the configuration is set according to Microsoft best practices. Documentation for this tool is at [Lync Server 2013 Best Practices Analyzer](lync-server-2013-best-practices-analyzer.md). 
  
The tool compares your deployment's configuration data against a set of pre-defined rules for Lync Server, and reports potential issues. For every issue reported, the tool provides the current configuration in the Lync Server environment, and the recommended configuration.
  
With the correct network access, the tool can examine your AD DS and servers that are running Lync Server 2013 to do the following:
  
- Proactively perform health checks, verifying that the configuration is set according to recommended best practices
    
- Generate a list of issues, such as suboptimal configuration settings or unsupported or not recommended options
    
- Judge the general health of a system
    
- Help troubleshoot specific issues
    
- Prompt you to download updates if they are available
    
- Provide online and local documentation about reported issues, and include troubleshooting tips
    
- Generate configuration information that can be captured for later review
    
Ensure that the RTCBPA.msi is installed on all Lync Server 2013 servers, and generate a weekly Health Check Report. Note the results and correct, if necessary.
  
## Review SLA performance figures
<a name="sectionSection7"> </a>

Check the key performance data for the previous week. Review performance against the requirements of the SLA. Identify trends and items that have not met their targets.
  
## Review System Center Operations Manager Management Pack and quality of experience reports
<a name="sectionSection8"> </a>

Obtain and review Lync Server 2013 Management Pack and Quality of Experience reports.
  
## Generating and viewing database reports for enterprise pools
<a name="sectionSection9"> </a>

### To generate pool reports

1. Open Lync Server 2013.
    
2. In the console tree, expand the forest node, expand **Enterprise pools**, and then click the pool for which you want to generate a database report.
    
3. In the details pane, click the **Database** tab. 
    
4. On the **Database** tab, do the following: 
    
1. To view the name of the database, expand **General Settings**, and view the database name.
    
2. To retrieve current user summary statistics for the pool, expand **User Summary Reports**, click **Go**, and view the results.
    
3. To retrieve current per-user data for a single user of the pool, expand **Per-User Reports**, type the user's SIP URI, click **Go**, and view the results.
    
To retrieve current conference summary statistics for the pool, expand **Conference Summary Reports**, click **Go**, and view the results.
  
For each Enterprise Pool, administrators can use the **Database** tab to view the database name and retrieve and view reports from the database. 
  
**Database Reports and Descriptions**

|**Section**|**Description**|
|:-----|:-----|
|User Summary Reports  <br/> | Dbanalyze /v /report:diag [/sqlserver:value]  <br/>  This section displays aggregate information about users in a pool, such as the number of enabled users, the average number of contacts per user, and the number of users for specific features.  <br/>  When using these reports, the following information may be helpful:  <br/>  An enabled user is a user who is enabled for Lync Server 2013 by using the Active Directory Users and Computers Snap-in.  <br/>  An active user is a user who has logged on or registered.  <br/>  The summary reports also offer a set of statistical information about contacts. These statistics are only valid for the population of users who have logged on at least one time, and who have at least one contact. Consequently, you'll typically not see a minimum number of contacts of 0. Because of this behavior, if a user has no contacts (but is active, in that the user has registered), you may see: \<empty\> for some statistics fields.  <br/> |
|Per-User Reports  <br/> |Dbanalyze /v /report:disk [/sqlserver:value]  <br/> Unlike the summary reports, which are calculated over a user population, these are reports about a specific user.  <br/> |
|Conference Summary Reports  <br/> |Dbanalyze /v /report:conf [/sqlserver:value]  <br/> This section displays aggregate information about conference summary statistics for the pool, such as the number of active conferences and total number of participants.  <br/> |
   
## Running Bandwidth Utilization Analyzer
<a name="sectionSection10"> </a>

Bandwidth Utilization Analyzer is a tool that creates reports about various views of bandwidth consumption by the UC endpoints across WAN links in the enterprise network. These reports can be used to understand the current bandwidth consumption pattern and to help with bandwidth capacity planning. It also iterates on the bandwidth capacity that is assigned to various links.
  
This tool does the following:
  
- Generates specific reports for audio usage over the network
    
- Helps with more effective capacity planning and iteration on the bandwidth capacity that is assigned to various links
    
Bandwidth Utilization Analyzer can generate graphical plots of bandwidth capacity and usage reports. They are as follows:
  
- All the WAN links in the enterprise network
    
- Filtered by selected WAN links that were chosen
    
- Filtered by WAN links that have exceeded link capacity
    
- Filtered by WAN links that were under-using the provisioned bandwidth
    
- Filter by WAN links that were reaching critical levels (a bandwidth usage that is greater than 90 percent of bandwidth capacity of the WAN link)
    
- Filtered by WAN link type—network-site links, interregional links, and links inside a site
    
- Filtered by network region
    
Documentation for this tool is available at [Lync Server 2013 Resource Kit Tools Documentation](https://go.microsoft.com/fwlink/?LinkId=623245). 
  
## See also
<a name="sectionSection10"> </a>

#### 

[Weekly task checklist](operations-checklists.md#Weekly_task)

