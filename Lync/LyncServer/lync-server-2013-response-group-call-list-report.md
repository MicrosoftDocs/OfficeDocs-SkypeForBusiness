---
title: 'Lync Server 2013: Response Group Call List Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Response Group Call List Report
ms:assetid: a2d3e08b-511b-4507-abba-8ff71aa27c8e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615443(v=OCS.15)
ms:contentKeyID: 48184954
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Response Group Call List Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

The Response Group application provides a way for Microsoft Lync Server 2013 to answer and route phone calls based on the number that was dialed and, optionally, on the caller's responses to a series of questions. Typically, Response Group calls are not routed to an individual person but, instead, are routed to a team of people referred to as an agent group. For example, if someone calls the phone number for your help desk, Lync Server 2013 can automatically route that call to the first available help desk agent. Alternatively, Lync Server could ask a series of questions ("Press 1 if you are having hardware problems. Press 2 if you are having software problems. Press 3 if you are having network problems.") and then route the call to the most appropriate help desk agent based on the answer to those questions.

The Response Group Call List Report represents a collection of calls made for a specified period of time and for a specified type of call. The Response Group Usage Report (which must be opened first before you can open the Response Group Call List Report) recognizes the following call types:

  - **Received calls**. Total number of calls received by all instances of the Response Group application.

  - **Successful calls**. Total number of calls that were picked up by the Response Group application.

  - **Offered calls**. Total number of calls that were transferred to a Response Group agent.

  - **Answered calls**. Total number of calls that were actually answered by a Response Group agent.

  - Percentage of abandoned calls. Percentage of calls that were received by the Response Group application but were never answered by an agent. This value is calculated by subtracting the Answered calls from the Received calls, and then dividing that value by the number of Received calls. For example, if you received 10 calls and 7 were answered, you would subtract 7 from 10, leaving 3 unanswered calls. That value would then be divided by 10, giving you an abandoned call percentage of 30%.

  - **Transferred calls**. Total number of Response Group calls that were transferred because of a queue timeout or queue overflow.

<div>

## Accessing the Response Group Call List Report

The Response Group Call List Report can only be accessed by clicking one of the following metrics found on the [Response Group Usage Report in Lync Server 2013](lync-server-2013-response-group-usage-report.md):

  - Received calls

  - Successful calls

  - Offered calls

  - Answered calls

  - Transferred calls

</div>

<div>

## Making the Best Use of the Response Group Call List Report

The Response Group Call List Report allows you to limit the displayed data to calls involving a particular Response Group workflow. To do that, you need to enter the workflow URI (the workflow's SIP address) in the Workflow URI box. Before you can do that, however, you must actually be able to see the Workflow URI box. To display the filtering options for the Response Group Call List Report, click the Show/Hide Parameters button in the upper left-hand portion of the report window.

Note that the Response Group Call List does not display information about either the Response code or the Diagnostic ID if you hold the mouse over either of those metrics. If you need more information, you might note the Response code and/or Diagnostic ID, and then search for those values in the [Top Failures Report in Lync Server 2013](lync-server-2013-top-failures-report.md).

a question like this one: "Which individual workflow received the most calls?", you can do the following:

1.  On the Response Group Usage Report, set the desired time period and then click the Received Calls metric. That will open the Response Group Call List Report.

2.  Export the data shown on the Response Group Call List Report. For example, you might export the data in Microsoft Excel format, and then use Excel to convert that data to a comma-separated values file.

3.  Run your analyses using Windows PowerShell.

For example, if you have saved the data to a file named C:\\Data\\Response\_Group\_Call\_List\_Report.csv, you can then use the following command to return the total number of received calls for each workflow listed in the report:

    $calls = Import-Csv -Path "C:\ Data\Response_Group_Call_List_Report.csv"
    $calls | Group-Object Workflow | Select-Object Count, Name | Sort-Object Count -Descending

That will information similar to this:

    Count    Name
    -----    ----
      160    Redmond Help Desk
       47    Dublin Help Desk
       31    North America Customer Support
       16    EMEA Customer Support
       14    Employment Opportunities

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Response Group Call List Report.

### Response Group Call List Report Filters

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
<td><p><strong>Workflow URI</strong></p></td>
<td><p>Enables you to limit the returned data to the specified Response Group workflow. To use this filter, enter the Workflow SIP address. For example:</p>
<p>sip:helpdesk@litwareinc.com</p></td>
</tr>
<tr class="even">
<td><p><strong>Calls</strong></p></td>
<td><p>You can select one of the following call types:</p>
<ul>
<li><p>Received Calls</p></li>
<li><p>Successful Calls</p></li>
<li><p>Offered Calls</p></li>
<li><p>Answered Calls</p></li>
<li><p>Transferred Calls</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Response Group Call List Report for each call received by the Response Group application.

### Response Group Call List Report Metrics

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
<td><p><strong>Caller</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the caller.</p></td>
</tr>
<tr class="even">
<td><p><strong>Workflow</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the Response Group workflow.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Start time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time that the call started.</p></td>
</tr>
<tr class="even">
<td><p><strong>End time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time that the call ended.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Response code</strong></p></td>
<td><p>No</p></td>
<td><p>SIP response code sent when the session failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>No</p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

