---
title: 'Lync Server 2013: Response Group Usage Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Response Group Usage Report
ms:assetid: 3248b320-a552-400a-8485-6891af4eb0f3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558632(v=OCS.15)
ms:contentKeyID: 48183811
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Response Group Usage Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

The Response Group application provides a way for Microsoft Lync Server 2013 to answer and route phone calls based on the number that was dialed and, optionally, on the caller's responses to a series of questions. Typically, Response Group calls are not routed to an individual person but, instead, are routed to a team of people referred to as an agent group. For example, if someone calls the phone number for your help desk, Lync Server 2013 can automatically route that call to the first available help desk agent. Alternatively, Lync Server could ask a series of questions ("Press 1 if you are having hardware problems. Press 2 if you are having software problems. Press 3 if you are having network problems.") and then route the call to the most appropriate help desk agent based on the answer to those questions.

The Response Group Usage Report provides a detailed look at the number of phone calls received by all your Response Group workflows, then breaks those calls down into more finite categories such as Offered calls, Answered calls, and Abandoned calls.

The key to working with the Response Group Usage Report is to understand the difference between the reported call types:

  - **Received calls**. Total number of calls received by all instances of the Response Group application.

  - **Successful calls**. Total number of calls that were picked up by the Response Group application.

  - **Offered calls**. Total number of calls that were transferred to a Response Group agent.

  - **Answered calls**. Total number of calls that were actually answered by a Response Group agent.

  - **Percentage of abandoned calls**. Percentage of calls that were received by the Response Group application but were never answered by an agent. This value is calculated by subtracting the Answered calls from the Received calls, and then dividing that value by the number of Received calls. For example, if you received 10 calls and 7 were answered, you would subtract 7 from 10, leaving 3 unanswered calls. That value would then be divided by 10, giving you an abandoned call percentage of 30%.

  - **Transferred calls**. Total number of Response Group calls that were transferred because of a queue timeout or queue overflow.

If you are looking at the Response Group Usage Report and can't remember the definition for any of these call types, simply hold your mouse over the appropriate call type label. A tooltip will appear that offers a brief description of the call type.

The Response Group Usage Report allows you to filter on a workflow URI (the SIP address associated with that workflow). However, workflow URIs do not actually appear on the report itself. If you would like to know things such as which workflows are answering the most calls or which workflows are experiencing the most transferred calls, click the appropriate metric to open the Response Group Call List Report for that given time period. That reports does list the workflow URIs.

<div>

## Accessing the Response Group Usage Report

The Response Group Usage Report is accessed from the Monitoring Reports home page. You can drill down to the [Response Group Call List Report in Lync Server 2013](lync-server-2013-response-group-call-list-report.md) by clicking any of the following metrics:

  - Received calls

  - Successful calls

  - Offered calls

  - Answered calls

  - Transferred calls

</div>

<div>

## Making the Best Use of the Response Group Usage Report

One of the more interesting uses of the Response Group Usage Report might not be readily apparent: the ability to retrieve usage information for a single Response Group workflow.

<div>


> [!WARNING]  
> A Response Group workflow is basically a set of instructions that determines what Lync Server does when a user dials a particular phone number. To that end, each workflow is uniquely associated with a phone number. When someone calls that number, the workflow determines how the call will be handled. For example, the workflow might cause the call to be routed to a series of interactive voice response (IVR) questions that prompt the caller to enter additional information ("Press 1 for hardware support. Press 2 for software support."). Alternatively, the workflow might cause the call to be placed in a queue , with the caller put on hold until an agent is available to answer the call. The availability of agents to answer calls is also dictated by the workflow: workflows are used to configure both business hours (the days of the week and the times of day when agents are available to answer calls) and holidays (days when no agents are available to answer calls). Any time you dial a phone number that belongs to the Response Group application you are essentially calling a Response Group workflow.



</div>

Although workflow URIs do not appear in the Response Group Usage Report, it's still possible to view the usage statistics for a single workflow, something that is often extremely useful. For example, suppose you recently unveiled a new ad campaign and are curious to know whether people are calling in to ask about that product. If you have associated a Response Group workflow with the phone number given in the ad campaign, you can easily check to see how many people (if any) are calling that number.

You might also use a similar approach to gauge the number of calls being handled by your internal help desk or your customer service department.

To review usage statistics for a particular workflow, enter the workflow URI in the Workflow URI box. Of course, as noted, workflow URIs (the SIP address associated with a workflow) do not appear on the report. That means you need to find some other way to determine the URI of a workflow. One way to do this is to use Windows PowerShell and the Lync Server Management Shell. For example, this command returns the URIs for all your Response Group workflows:

    Get-CsRgsWorkflow | Select-Object Name, PrimaryUri

That will return data similar to this:

    Name                            PrimaryUri
    ----                            ----------
    Customer Support                sip:support@litwareinc.com
    Help Desk                       sip:helpdesk@litwareinc.com
    New Ad Campaign                 sip:newads@litwareinc.com

This command returns information for a single workflow, the one with the name New Ad Campaign:

    Get-CsRgsWorkflow -Name "New Ad Campaign" | Select-Object Name, PrimaryUri

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Response Group Usage Report enables you to view data for all your Response Group workflows or to view data for an individual workflow. You can also choose how data should be grouped. In this case, usages are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Response Group Usage Report.

### Response Group Usage Report Filters

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>From</strong></p></td>
<td><p>Start date/time for the time range. To view data by hours, enter both the start date and time as follows:</p>
<p>7/7/2012 1:00 PM</p>
<p>If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/7/2012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/3/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong></p></td>
<td><p>End date/time for the time range. To view data by hours, enter both the end date and time as follows:</p>
<p>7/7/2012 1:00 PM</p>
<p>If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/7/2012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/3/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Interval</strong></p></td>
<td><p>Time interval. Select one of the following:</p>
<ul>
<li><p>Hourly (a maximum of 25 hours can be displayed)</p></li>
<li><p>Daily (a maximum of 31 days can be displayed)</p></li>
<li><p>Weekly (a maximum of 12 weeks can be displayed)</p></li>
<li><p>Monthly (a maximum of 12 months can be displayed)</p></li>
</ul>
<p>If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2012 and an end date of 2/28/2012, data is displayed for the days 8/7/2012 12:00 AM to 9/7/2012 12:00 AM (that is, a total of 31 days' worth of data).</p></td>
</tr>
<tr class="even">
<td><p><strong>Workflow URI</strong></p></td>
<td><p>Enables you to limit the returned data to the specified Response Group workflow. To use this filter, enter the Workflow SIP address. For example:</p>
<p>sip:helpdesk@litwareinc.com</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Response Group Usage Report.

### Response Group Usage Report Metrics

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Can you sort on this item?</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Hourly</strong></p>
<p><strong>Daily</strong></p>
<p><strong>Weekly</strong></p>
<p><strong>Monthly</strong></p></td>
<td><p>No</p></td>
<td><p>Indicates the selected time interval. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/7/2012, you see an hourly breakdown of user registration activity for that date.</p></td>
</tr>
<tr class="even">
<td><p><strong>Received calls</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls received by all instances of the Response Group application. When you click this item, the report shows you the Response Group Call List report for the selected time period.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Successful calls</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that were picked up the Response Group application. When you click this item, the report shows you the Response Group Call List report for the selected time period.</p></td>
</tr>
<tr class="even">
<td><p><strong>Offered calls</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that were transferred to a Response Group agent. When you click this item, the report shows you the Response Group Call List report for the selected time period.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Answered calls</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that were actually answered by a Response Group agent. When you click this item, the report shows you the Response Group Call List report for the selected time period.</p></td>
</tr>
<tr class="even">
<td><p><strong>Percentage of abandoned calls</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that were received by the Response Group application but were never answered by an agent. This is calculated by subtracting the Answered calls from the Received calls, and then dividing that value by the number of received calls. For example, if you have 10 received calls and seven were answered, you would subtract seven from 10, leaving three unanswered calls. That value would then be divided by 10, giving you an abandoned call percentage of 30%.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Average call minutes by agent</strong></p></td>
<td><p>No</p></td>
<td><p>Average amount of time a Response Group agent spent on a call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Transferred calls</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of Response Group calls that were transferred because of a queue timeout or queue overflow. When you click this item, the report shows you the Response Group Call List report for the selected time period.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

