---
title: 'Lync Server 2013: Weekly tasks'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Weekly tasks
ms:assetid: d564839b-b49d-4c5d-b67e-dc5abb0f6980
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn722432(v=OCS.15)
ms:contentKeyID: 63969650
ms.date: 08/20/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Weekly tasks in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-08-17_

Weekly tasks are generally related to collecting and analyzing logs and reports.

<div>

## Archive event logs

If event logs are not configured to overwrite events as required, they must be regularly archived and deleted. This action is especially important for security logs, which may be required when investigating attempted security breaches.

Your organization will have to define policies and procedures for log archiving.

</div>

<div>

## Create reports

Create status reports to help with capacity planning, SLA reviews, and performance analysis. Use daily data from event log and System Monitor to create reports on disk, memory, and CPU usage. Use System Center Operations Manager to generate uptime and availability reports.

Your organization will have to define policies and procedures for status reports.

</div>

<div>

## Incident reports

Perform a weekly audit of your organization’s incident reports that relate to Lync Server. This audit should include the following:

  - The top generated, resolved, and pending incidents.

  - Solutions for unresolved incidents.

  - Updating reports to include new trouble tickets.

  - Updating a document repository for troubleshooting guides and post mortems about outages.

Since your organization’s incident tracking system is a choice independent of Lync Server, specific instructions or pointers are not available. Consult the documentation for the system your organization chose.

</div>

<div>

## Check IIS logs and performance

Perform a weekly review of Internet Information Services (IIS) logs and performance. For more information about how to monitor IIS logs and performance, see [Windows Server 2003 Internet Information Services (IIS) Event Logging Overview](http://go.microsoft.com/fwlink/?linkid=36077). The review should include the following:

  - Web Service Cache counters to monitor the WWW service cache.

  - Active Server Pages (ASPs) counters to monitor applications that run as ASPs.

</div>

<div>

## Generate database reports

**To generate reports on the SQL Database**

1.  Open Lync Server 2013.

2.  In the console tree, expand the forest node, expand **Enterprise pools**, and then click the pool for which you want to generate a database report.

3.  In the details pane, click the **Database** tab.

4.  On the **Database** tab, do the following:
    
    1.  To view the name of the database, expand **General Settings**, and view the database name.
    
    2.  To retrieve current user summary statistics for the pool, expand **User Summary Reports**, click **Go**, and view the results.
    
    3.  To retrieve current per-user data for a single user of the pool, expand **Per-User Reports**, type the user’s SIP URI, click **Go**, and view the results.

To retrieve current conference summary statistics for the pool, expand **Conference Summary Reports**, click **Go**, and view the results.

</div>

<div>

## Check for security and Lync Server updates

Identify any new service packs, hotfixes, or updates. If appropriate, test these in a test lab, and use the change control procedures to arrange for deployment to the production servers. Also, Lync Server component updates are now available as part of Windows update. All Lync Server component updates must be updated at the same time on all of the servers that are running Lync Server for which the updates are applicable.

</div>

<div>

## Run the Lync Server 2013 Best Practice Analyzer

The Lync Server 2013 Best Practices Analyzer Tool is a diagnostic tool that collects configuration information and determines whether the configuration is set according to Microsoft best practices. Documentation for this tool is at [Lync Server 2013 Best Practices Analyzer](lync-server-2013-lync-server-best-practices-analyzer.md).

The tool compares your deployment’s configuration data against a set of pre-defined rules for Lync Server, and reports potential issues. For every issue reported, the tool provides the current configuration in the Lync Server environment, and the recommended configuration.

With the correct network access, the tool can examine your AD DS and servers that are running Lync Server 2013 to do the following:

  - Proactively perform health checks, verifying that the configuration is set according to recommended best practices

  - Generate a list of issues, such as suboptimal configuration settings or unsupported or not recommended options

  - Judge the general health of a system

  - Help troubleshoot specific issues

  - Prompt you to download updates if they are available

  - Provide online and local documentation about reported issues, and include troubleshooting tips

  - Generate configuration information that can be captured for later review

Ensure that the RTCBPA.msi is installed on all Lync Server 2013 servers, and generate a weekly Health Check Report. Note the results and correct, if necessary.

</div>

<div>

## Review SLA performance figures

Check the key performance data for the previous week. Review performance against the requirements of the SLA. Identify trends and items that have not met their targets.

</div>

<div>

## Review System Center Operations Manager Management Pack and quality of experience reports

Obtain and review Lync Server 2013 Management Pack and Quality of Experience reports.

</div>

<div>

## Generating and viewing database reports for enterprise pools

**To generate pool reports**

1.  Open Lync Server 2013.

2.  In the console tree, expand the forest node, expand **Enterprise pools**, and then click the pool for which you want to generate a database report.

3.  In the details pane, click the **Database** tab.

4.  On the **Database** tab, do the following:
    
    1.  To view the name of the database, expand **General Settings**, and view the database name.
    
    2.  To retrieve current user summary statistics for the pool, expand **User Summary Reports**, click **Go**, and view the results.
    
    3.  To retrieve current per-user data for a single user of the pool, expand **Per-User Reports**, type the user’s SIP URI, click **Go**, and view the results.

To retrieve current conference summary statistics for the pool, expand **Conference Summary Reports**, click **Go**, and view the results.

For each Enterprise Pool, administrators can use the **Database** tab to view the database name and retrieve and view reports from the database.

### Database Reports and Descriptions

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Section</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>User Summary Reports</p></td>
<td><p>Dbanalyze /v /report:diag [/sqlserver:value]</p>
<p>This section displays aggregate information about users in a pool, such as the number of enabled users, the average number of contacts per user, and the number of users for specific features.</p>
<p>When using these reports, the following information may be helpful:</p>
<ul>
<li><p>An enabled user is a user who is enabled for Lync Server 2013 by using the Active Directory Users and Computers Snap-in.</p></li>
<li><p>An active user is a user who has logged on or registered.</p></li>
<li><p>The summary reports also offer a set of statistical information about contacts. These statistics are only valid for the population of users who have logged on at least one time, and who have at least one contact. Consequently, you'll typically not see a minimum number of contacts of 0. Because of this behavior, if a user has no contacts (but is active, in that the user has registered), you may see: &lt;empty&gt; for some statistics fields.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Per-User Reports</p></td>
<td><p>Dbanalyze /v /report:disk [/sqlserver:value]</p>
<p>Unlike the summary reports, which are calculated over a user population, these are reports about a specific user.</p></td>
</tr>
<tr class="odd">
<td><p>Conference Summary Reports</p></td>
<td><p>Dbanalyze /v /report:conf [/sqlserver:value]</p>
<p>This section displays aggregate information about conference summary statistics for the pool, such as the number of active conferences and total number of participants.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Running Bandwidth Utilization Analyzer

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

Documentation for this tool is available at [Lync Server 2013 Resource Kit Tools Documentation](http://go.microsoft.com/fwlink/?linkid=623245).

</div>

<div>

## See Also


[Weekly task checklist](lync-server-2013-operations-checklists.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

