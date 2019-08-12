---
title: "Response Group Call List Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a2d3e08b-511b-4507-abba-8ff71aa27c8e
description: "Summary: Learn about the Response Group application in Skype for Business Server."
---

# Response Group Call List Report in Skype for Business Server

**Summary:** Learn about the Response Group application in Skype for Business Server.

The Response Group application provides a way for Skype for Business Server to answer and route phone calls based on the number that was dialed and, optionally, on the caller's responses to a series of questions. Typically, Response Group calls are not routed to an individual person but, instead, are routed to a team of people referred to as an agent group. For example, if someone calls the phone number for your help desk, Skype for Business Server can automatically route that call to the first available help desk agent. Alternatively, Skype for Business Server could ask a series of questions ("Press 1 if you are having hardware problems. Press 2 if you are having software problems. Press 3 if you are having network problems.") and then route the call to the most appropriate help desk agent based on the answer to those questions.

The Response Group Call List Report represents a collection of calls made for a specified period of time and for a specified type of call. The Response Group Usage Report (which must be opened first before you can open the Response Group Call List Report) recognizes the following call types:

- **Received calls**. Total number of calls received by all instances of the Response Group application.

- **Successful calls**. Total number of calls that were picked up by the Response Group application.

- **Offered calls**. Total number of calls that were transferred to a Response Group agent.

- **Answered calls**. Total number of calls that were actually answered by a Response Group agent.

- **Percentage of abandoned calls.** Percentage of calls that were received by the Response Group application but were never answered by an agent. This value is calculated by subtracting the Answered calls from the Received calls, and then dividing that value by the number of Received calls. For example, if you received 10 calls and 7 were answered, you would subtract 7 from 10, leaving 3 unanswered calls. That value would then be divided by 10, giving you an abandoned call percentage of 30%.

- **Transferred calls**. Total number of Response Group calls that were transferred because of a queue timeout or queue overflow.

## Accessing the Response Group Call List Report

The Response Group Call List Report can only be accessed by clicking one of the following metrics found on the [Response Group Usage Report in Skype for Business Server](response-group-usage-report.md):

- Received calls

- Successful calls

- Offered calls

- Answered calls

- Transferred calls

## Making the Best Use of the Response Group Call List Report

The Response Group Call List Report allows you to limit the displayed data to calls involving a particular Response Group workflow. To do that, you need to enter the workflow URI (the workflow's SIP address) in the Workflow URI box. Before you can do that, however, you must actually be able to see the Workflow URI box. To display the filtering options for the Response Group Call List Report, click the Show/Hide Parameters button in the upper left-hand portion of the report window.

Note that the Response Group Call List does not display information about either the Response code or the Diagnostic ID if you hold the mouse over either of those metrics. If you need more information, you might note the Response code and/or Diagnostic ID, and then search for those values in the [Top Failures Report in Skype for Business Server](top-failures-report.md).

a question like this one: "Which individual workflow received the most calls?", you can do the following:

1. On the Response Group Usage Report, set the desired time period and then click the Received Calls metric. That will open the Response Group Call List Report.

2. Export the data shown on the Response Group Call List Report. For example, you might export the data in Microsoft Excel format, and then use Excel to convert that data to a comma-separated values file.

3. Run your analyses using Windows PowerShell.

For example, if you have saved the data to a file named C:\Data\Response_Group_Call_List_Report.csv, you can then use the following command to return the total number of received calls for each workflow listed in the report:

```
$calls = Import-Csv -Path "C:\ Data\Response_Group_Call_List_Report.csv"
$calls | Group-Object Workflow | Select-Object Count, Name | Sort-Object Count -Descending
```

That will information similar to this:

<pre>
Count    Name
-----    ----
  160    Redmond Help Desk
   47    Dublin Help Desk
   31    North America Customer Support
   16    EMEA Customer Support
   14    Employment Opportunities
</pre>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Response Group Call List Report.

**Response Group Call List Report Filters**


| **Name**               | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **From** <br/>         | Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
| **To** <br/>           | End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/>        |
| **Workflow URI** <br/> | Enables you to limit the returned data to the specified Response Group workflow. To use this filter, enter the Workflow SIP address. For example:  <br/> sip:helpdesk@litwareinc.com  <br/>                                                                                                                                                                                                                                                                                                                                                                            |
| **Calls** <br/>        | You can select one of the following call types: <br/>  Received Calls <br/>  Successful Calls <br/>  Offered Calls <br/>  Answered Calls <br/>  Transferred Calls <br/>                                                                                                                                                                                                                                                                                                                                                                                                |

## Metrics

The following table lists the information provided in the Response Group Call List Report for each call received by the Response Group application.

**Response Group Call List Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Caller** <br/> |No  <br/> |SIP address of the caller.  <br/> |
|**Workflow** <br/> |No  <br/> |SIP address of the Response Group workflow.  <br/> |
|**Start time** <br/> |No  <br/> |Date and time that the call started.  <br/> |
|**End time** <br/> |No  <br/> |Date and time that the call ended.  <br/> |
|**Response code** <br/> |No  <br/> |SIP response code sent when the session failed.  <br/> |
|**Diagnostic ID** <br/> |No  <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.  <br/> |


