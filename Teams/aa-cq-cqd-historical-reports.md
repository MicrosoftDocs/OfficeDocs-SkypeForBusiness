---
title: Auto attendant and Call queue historical reports
author: DaniEASmith
ms.author: danismith
manager: pamgreen
ms.reviewer: colongma
ms.date: 09/13/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Reporting
  - ms.teamsadmincenter.directrouting.cqd
  - ms.lync.lac.ToolsCallQualityDashboard
description: Learn about how to use the updated Teams Auto Attendant & Call Queue Historical Report Power BI report to view Auto Attendant and Call Queue historical data.
---

# Auto attendant and Call queue historical reports

> [!IMPORTANT]
> GCC High and DoD customers need to use [Auto attendant and call queue historical reports for GCC High and DoD](aa-cq-cqd-historical-reports-v164.md)

This Power BI template provides three reports that allow organizations to report on the number of calls processed by Auto attendants and Call queues.  It also provides agent performance insights.

## V3.1.3 published on September 13, 2023

The Teams Auto Attendant & Call Queue Historical Report Power BI template provides the following three reports:

- The Auto Attendant report shows analytics for calls coming into your Auto attendants.
  - [Original](media/aa-cq-historical-report-sample-aa-v310-orig.png)
  - [New (as of v3.1.0)](media/aa-cq-historical-report-sample-aa-v310-new.png)

- The Call Queue report shows analytics for calls coming into your Call queues.
  - [Original](media/aa-cq-historical-report-sample-cq-v310-orig.png)
  - [New (as of v3.1.0)](media/aa-cq-historical-report-sample-cq-v310-new.png)

- The Agent Timeline report shows a timeline view of agents being active in Call queue calls.
  - [Original](media/aa-cq-historical-report-sample-at-v310-orig.png)
  - [New (as of v3.1.0)](media/aa-cq-historical-report-sample-at-v310-new.png)

These reports use data from the Voice Applications Analytics Collector (VAAC) service.

## V3.x.x prerequisites

### Power BI Desktop

You need to have Power BI Desktop installed. You can install and use the free version from the [Microsoft Windows Store](https://aka.ms/pbidesktopstore).

The minimum compatible version is 2.85.681.0 (September 2020).

### Power BI Service

These reports may be [published to the Power BI service](/power-bi/create-reports/desktop-upload-desktop-files).

Once the report is published:

1. Go to the dataset **Settings**.
2. Expand the **Data source credentials** section.
3. Select **Edit credentials**.
4. Set the **Authentication method** to `OAuth2`.
5. Ensure **Skip test connection** is enabled.
6. Select **Sign in** and provide your credentials.

When completed, you're able to [configure a scheduled refresh](/power-bi/connect-data/refresh-scheduled-refresh) of the dataset.

### Permissions to access the CQD pipeline

While this version of the reports doesn't use the Call Quality Dashboard (CQD) data pipeline, the account used to view the historical data still requires access to the Call Quality Dashboard. For more information, see [CQD access role](./turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd).

Any CQD role with both **View Reports** and **View EUII fields** set to **Yes** will work.

This requirement will be removed in a future release.

## V3.x.x desktop installation

The following steps assume you have already installed Power BI Desktop on your computer and that your account has the necessary permissions to access the CQD data pipeline.

Perform the following steps:

1. Download and save the [Teams Auto Attendant & Call Queue Historical Reports V3.1.3.zip](https://www.microsoft.com/download/details.aspx?id=104623) file on your computer.

2. Open the zip file.

3. Open the `Teams Auto Attendant & Call Queue Historical Reports V3.1.3.pbit` template file. Power BI Desktop should launch.

4. You're prompted to select the **DataSource** and **UTC Offset**.  

   :::image type="content" source="media/aa-cq-historical-report-01-v312.png" alt-text="Screenshot showing the DataSource and UTC Offset selections.":::

    - **DataSource**: Select the `api.interfaces.records.teams.microsoft.com` entry.
    - **UTC Offset**: Select the UTC offset that represents the time zone the reports are presented in.

5. You're prompted to sign in with an account. Select **Organizational account**, and then select **Sign in**.

   :::image type="content" source="media/aa-cq-historical-report-03-v300.png" alt-text="Screenshot showing sign-in for V3.0.0.":::

6. Select **Connect**, and the data refreshes.

> [!NOTE]
> If you were using v1.63 or earlier, you may encounter an error when v3.x.x tries to retrieve the data from VAAC.  To resolve this error, it's necessary to clear any previous credentials from Power BI.
>
> 1. Open the v3.x.x template to clear the error.
> 1. Select **File** > **Options & Settings** > **Data source settings**.
> 1. Select the dropdown menu for **Clear Permissions**, and then select **Clear All Permissions**.
> 1. Close the template after they're cleared, and restart Power BI. You'll be asked to authorize again.

## Data latency for Auto attendant and Call queue analytics

The data is available within 30 minutes of the call being completed, but there are cases where it can take several hours for the data to appear.

You have to refresh the data to see any new data.

## Auto attendant and Call queue historical reports definitions

### Cloud Auto Attendant Analytics report

#### Report description

|Report Section                                                    |Description                                                       |
|:-----------------------------------------------------------------|:-----------------------------------------------------------------|
|Original: Incoming Call Source<br>New: Incoming Calls             |Distribution of calls by Internal/External call source            |
|Directory Search Method                                           |Distribution of calls by search type                              |
|Caller Action Count                                               |Distribution of calls by number action used during the call       |
|Original: Average Seconds in AA<br>New: AA Stats Duration [secs]  |Average number of seconds callers spend in the AA                 |
|Original: Average Caller Actions<br>New: AA Stats Caller Actions  |Average number of actions callers perform in the AA               |
|Call Results                                                      |Distribution of calls by final call state                         |
|Lower section of report                                           |Call flow breakdown                                               |

#### Report visual and field mapping

|Report Tab                                  |Report Table Name     |Global Filter                          |
|:-------------------------------------------|:---------------------|:--------------------------------------|
|Auto Attendant<br>Auto Attendant - New      |fAutoAttendant        |None                                   |

|Report Section                               |Field(s) Used                                                                                    |Filters Applied |
|:--------------------------------------------|:------------------------------------------------------------------------------------------------|:----------|
|Date selector                                |AA Start Time Local                                                                              |None       |
|Time Range selector                          |AAStartHour                                                                                      |None       |
|Auto Attendant Resource Accounts             |AA Name                                                                                          |None       |
|Incoming Call Source                         |Call Type<br>Sum of TotalCallCount         |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal |
|Directory Search Method                      |AADirectorySearchMethod<br>AADirectorySearchMethodLegend<br>TotalCallCount  |AADirectorySearchMethod is abs_search_dtmf or abs_search_name    |
|Caller Action Count                          |AACallerActionCount<br>TotalCallCount                                                            |None       |
|Average Seconds in AA                        |AAChainDuration                                                                                  |None       |
|Average Caller Actions                       |AACallerActionCount                                                                              |None       |
|Call Results                                 |AACallResult<br>AACallResultLegend<br>TotalCallCount                                             |None       |
|Lower section of report                      |MM-DD<br>AA Name<br>AACallFlow<br>Call Type<br>AACallResult<br>TotalCallCount<br>AAChainDuration |None       |

#### fAutoAttendant table field description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|AA Name                                 |Text                     |Name of resource account attached to Auto Attendant<br><br>If the full Resource Account name is **aa_test@microsoft.com**, then this value is: **aa_test** |
|AA Start Time Local                     |Date/time                |Auto Attendant call start time - Local (based on selected UTC Offset)                    |
|AA Start Time UTC                       |Date/time                |Auto Attendant call start time - UTC                                                     |
|AACallerActionCount                     |Whole number             |Summarize: Sum<br>Count of actions selected by caller in Auto Attendant during the call  |
|AACallerActionCount (Measure)           |Whole number             |Same as AACallerActionCount except will be 0 if no calls instead of blank                |
|AACallFlow                              |Text                     |See Auto Attendant dimensions -> AutoAttendantCallFlow                                   |
|AACallResult                            |Text                     |See Auto Attendant dimensions -> AutoAttendantCallResult                                 |
|AACallResultLegend                      |Text                     |Sets up legend items based on AACallResult                                               |
|AAChainDuration                         |Decimal number           |Summarize: Sum<br>Duration of call in Auto Attendant                                     |
|AAChainDuration (Measure)               |Decimal number           |Same as AAChainDuration except will be 0 if no calls instead of blank                    |
|AAChainIndex                            |Whole Number             |                                                                                         |
|AAConnectivityType                      |Text                     |See Common dimensions -> PSTNConnectivityType                                            |
|AACount                                 |Whole Number             |Number of Auto Attendants involved in call                                               |
|AADirectorySearchMethod                 |Text                     |See Auto Attendant dimensions -> AutoAttendantDirectorySearchMethod                      |
|AADirectorySearchMethodLegend           |Text                     |Sets up legend items based on AADirectorySearchMethod                                    |
|AAStartHour                             |Whole number             |Auto Attendant call start hour                                                           |
|AATransferAction                        |Text                     |See Auto Attendant Dimensions -> AutoAttendantTransferAction                             |
|Call Duration Seconds                   |Whole number             |Call duration                                                                            |
|Call End Time Local                     |Date/time                |Call end time - Local (based on selected UTC Offset)                                     |
|Call End Time UTC                       |Date/time                |Call end time - UTC                                                                      |
|Call Start Time Local                   |Date/time                |Call start time - Local (based on selected UTC Offset)                                   |
|Call Start Time UTC                     |Date/time                |Call start time - UTC                                                                    |
|ConferenceID                            |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|Count of AADirectorySearchMethod for DTMF |Whole number           |Count of calls that used DTMF to search the directory                                    |
|Count of AADirectorySearchMethod for Voice |Whole number           |Count of calls that used Voice to search the directory                                    |
|DialogID                                |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|DocumentID                              |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|MM-DD                                   |Text                     |Auto Attendant call month-day                                                            |
|PSTNMinutes                             |Whole number             |Summarize: Sum<br>Total minute usage                                                     |
|Sum of TotalCallCount (Measure)         |Whole number             |Same as TotalCallCount except will be 0 if no calls instead of blank                     |
|TotalCallCount                          |Whole number             |Summarize: Sum<br>Always 1 - used to provide sum of all calls                            |

### Cloud Call Queue Analytics report

#### Report description

|Report Section                                        |Description                                                        |
|:-----------------------------------------------------|:------------------------------------------------------------------|
|Original: Incoming Call Source<br>New: Incoming Calls |Distribution of calls by Internal/External call source             |
|Average Wait Time (seconds)                           |Wait time for answered and abandoned calls                         |
|Call Volume and Agent Opt-in Count                    |Distribution of calls by Call queues / Maximum agent opt-in count  |
|Call Results                                          |Distribution of calls by call result                               |
|Abandoned Calls                                       |Distribution of abandoned calls by Call queues                     |
|Average Session Length (seconds)                      |Call length in seconds grouped by call result                      |
|Call Overflow/Timeout Destinations                    |Distribution of calls that timed out or overflowed                 |

#### Report visual and field mapping

|Report Tab            |Report Table Name                                   |Global Filter       |
|:---------------------|:---------------------------------------------------|:-------------------|
|Call Queue            |fCallQueueAnalytics<br>fCallQueueFinalStateAction   |None                |

|Report Section                      |Table -> Field(s) Used                |Filters Applied       |
|:-----------------------------------|:-------------------------------------|:---------------------|
|Date selector                       |fCallQueueAnalytics -> Call Start Time Local |None           |
|Time Range selector                 |fCallQueueAnalytics -> CQHour         |None                  |
|Call Queue Resource Account         |fCallQueueAnalytics -> CQ Name        |None                  |
|Incoming call source                |fCallQueueAnalytics -> Sum of Call Count (Measure)  |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal |
|Avg Wait Time (seconds)-Before Answered |fCallQueueFinalStateAction -> Avg of Average CQ Duration (Measure) |Call Queue Call Result is agent_joined_conference or transferred_to_agent|
|Avg Wait Time (seconds)-Before Abandoned |fCallQueueFinalStateAction -> Avg of Average Call Duration (Measure) |Call Queue Call Result isn't agent_joined_conference, transferred_to_agent, overflown, timed_out |
|Call Volume and Agent Opt-In Count   |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Agent Opt In Count<br>fCallQueueAnalytics -> CQ Name<br>fCallQueueAnalytics -> Date |None |
|Call Results                        |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Call Result<br>fCallQueueAnalytics ->Call Queue Call Result Legend | None|
|Abandoned Calls                     |fCallQueueAnalytics -> Date<br>fCallQueueAnalytics -> TotalCallCount | Call Queue Call Result Legend is Abandoned |
|Average Session Length (seconds)    |fCallQueueFinalStateAction -> Average Call Queue Duration (Sec)<br>Call Queue Call Result Legend |Average Call Queue Duration (Sec) > 0 |
|Call Overflow/Timeout/No Agents Destinations  |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Target Type<br>fCallQueue Target Type Legend |Call Queue Target Type Legend doesn't contain Abandoned and Agent Answered |

#### fCallQueueAnalytics table field description

|Name                                    |Data Type                |Description                                                                              |
|:---------------------------------------|:------------------------|:----------------------------------------------------------------------------------------|
|Call Count                              |Whole number             |Summarize: Sum<br>Number of calls                                                        |
|Call Duration Seconds                   |Whole number             |Call duration                                                                            |
|Call End Time Local                     |Date/time                |Call end time - Local (based on selected UTC Offset)                                     |
|Call End Time UTC                       |Date/time                |Call end time - UTC                                                                      |
|Call Queue Agent Count                  |Whole number             |Summarize: Sum<br>Number of agents configured in the Call queue                          |
|Call Queue Agent Opt In Count           |Whole number             |Summarize: Sum<br>Number of agents opted-in to the Call queue                            |
|Call Queue Call Result                  |Text                     |See Call Queue Dimensions -> CallQueueCallResult                                         |
|Call Queue Call Result Legend           |Text                     |Sets up legend items based on Call Queue Result                                          |
|Call Queue Target Type                  |Text                     |See Call Queue Dimensions -> CallQueueTargetType                                         |
|Call Queue Target Type Legend           |Text                     |Sets up legend items based on Call Queue Target Type                                     |
|Call Start Time Local                   |Date/time                |Call start time - Local (based on selected UTC Offset)                                   |
|Call Start Time UTC                     |Date/time                |Call start time - UTC                                                                    |
|ConferenceID                            |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|CQ Hour                                 |Whole Number             |Call queue call start hour                                                               |
|Date                                    |Date/time                |Call queue call start date and time (hour)                                               | 
|DateTimeCQName                          |Text                     |Unique key for filtering on fCallQueueFinalStateAction                                   |
|DialogID                                |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|DocumentID                              |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|PSTN Connectivity Type                  |Text                     |See Common Dimensions -> PSTNConnectivityType                                            |
|PSTN Total Minutes                      |Whole number             |Summarize: Sum<br>Total minutes usage for PSTN calls                                     |
|Sum of Call Count (Measure)             |Whole number             |Same as Call Count however will be 0 when no call                                        |
|TotalCallCount (Measure)                |Whole Number             |Summarize: Sum<br>Call Count                                                             |

#### fCallQueueFinalStateAction table field description

|Name                                    |Data Type                |Description                                                                |
|:---------------------------------------|:------------------------|:--------------------------------------------------------------------------|
|Average Call Duration (Seconds)         |Decimal number           |Summarize: Sum<br>Average call duration in seconds for abandoned calls     |
|Average Call Queue Duration (Sec)       |Decimal number           |Summarize: Sum<br>Average waiting time in seconds for answered calls       |
|Avg of Average Call Duration (Measure)  |Whole number             |Same as Average Call Duration (Seconds) however will be 0 when no calls    |
|Avg of Average CQ Duration (Measure)    |Whole number             |Same as Average Call Queue Duration (Sec) however will be 0 when no calls  |
|Call Count                              |Whole number             |Summarize: Sum<br>Number of calls                                          |
|Call Queue Call Result                  |Text                     |See Call Queue Dimensions -> CallQueueCallResult                           |
|Call Queue Call Result Legend           |Text                     |Sets up legend items based on Call Queue Call Result                       |
|Call Queue Final State Action           |Text                     |See Call Queue Dimensions -> CallQueueFinalStateAction                     |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|CQ Hour                                 |Number                   |Hour that the call took place in
|Date                                    |Date/time                |Call Queue call start date and time (hour)                                 |
|DateTimeCQName                          |Text                     |Unique key for filtering on fCallQueueFinalStateAction                     |
|IsAbandoned                             |True/false               |True if caller hangs up before being answered by an agent                  |
|Local Date                              |Date/time                |Local date/time (based on selected UTC Offset)                             |
|UTC Date                                |Date/time                |UTC  date/time                                                             |

### Cloud Call Queue Agent Timeline report

#### Report description

|Report Section                                          |Description                                                         |
|:-------------------------------------------------------|:-------------------------------------------------------------------|
|Number of Calls Answered by Agent                       |Distribution of calls by Call queue and agent                       |
|Distribution of Calls Answered by Agent and Call Queue  |Distribution of calls by agent and Call queue                       |
|Table (bottom left)                                     |Distribution of calls by agent with average and total call duration |
|Average Answered Call Duration (seconds) by Agent (bottom right) |Average duration (seconds) of call by agent                |

#### Report visual field mapping

|Report Tab            |Report Table Name                  |Global Filter       |
|:---------------------|:----------------------------------|:-------------------|
|Agent Timeline        |fAgentTimelineAnalyticsSummary     |None                |

|Report Section                                |Field(s) Used                         |Filters Applied       |
|:---------------------------------------------|:-------------------------------------|:---------------------|
|Date selector                                 |Date                                  |None                  |
|Agent Username selector                       |Agent Name                            |None                  |
|Call Queue Resource Accounts selector         |CQ Name                               |None                  |
|Number of Calls Answered by Agent             |Total Call Count<br>Agent Name<br>Date<br>Hour      |None                  |
|Distribution of Calls Answer by Agent and Call Queue          |Agent Name<br>Average Calls Duration (Seconds)<br>CQ Name<br>Total Call Count |None               |
|Bottom Left                                   |Agent Name<br>Average Call Duration (Seconds)<br>CQ Name<br>Hour<br>MM-DD<br>Total Call Count<br>Total Call Duration (HH:MM:SS)<br>Total Call Duration (Minutes) | None |
|Average Answered Call Duration (Seconds) by Agent      |Agent Name<br>Average Call Duration (Seconds) | None |

#### fAgentTimelineAnalytics table field description

|Name                                    |Data Type                |Description                                         |
|:---------------------------------------|:------------------------|:---------------------------------------------------|
|Agent Name                              |Text                     |User UPN<br>If the full username is **user@microsoft.com**, then this value is: **user** |
|AgentTimelineAnalyticsSummaryLink       |Text                     |Used to link with fAgentTimelineAnalyticsSummary for the pop-up tooltip |
|Call Duration (HH:MM:SS)                |Text                     |Call Duration (Minutes) converted to HH:MM:SS            |
|Call Duration (Minutes)                 |Whole number             |Total call duration of answered Call queue calls in minutes  |
|Call Duration (Second)                  |Whole number             |Total call duration of answered Call queue calls in seconds  |
|Call End Time Local                     |Date/time                |Call end time - Local (based on selected UTC Offset)                                     |
|Call End Time UTC                       |Date/time                |Call end time - UTC                                                                      |
|Call Start Time Local                   |Date/time                |Call start time - Local (based on selected UTC Offset)                                   |
|Call Start Time UTC                     |Date/time                |Call start time - UTC                                                                    |
|ConferenceID                            |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|DateTime                                |DateTime                 |Date of call                                             |
|DialogID                                |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|DocumentID                              |Text                     |Used for troubleshooting purposes - provide this information when opening a ticket       |
|Hour                                    |Whole number             |Hour of call                                             |
|Total Call Count                        |Whole number             |Summarize: Sum<br>Number of calls presented to agent     |

#### fAgentTimelineAnalyticsSummary table field description

|Name                                    |Data Type                |Description                                         |
|:---------------------------------------|:------------------------|:---------------------------------------------------|
|Agent Name                              |Text                     |User UPN<br>If the full username is **user@microsoft.com**, then this value is: **user** |
|AgentTimelineAnalyticsLink              |Text                     |Used to link with fAgentTimelineAnalytics for the pop-up tooltip |
|Average Call Duration (Seconds)         |Decimal number           |Summarize: Sum<br>The average duration of answered Call queue calls in seconds |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value is: **cq_test** |
|Date                                    |Date                     |Date of call                                             |
|Hour                                    |Whole number             |Hour of call                                             |
|MM-DD                                   |Text                     |Month and day of call                                    |
|Total Call Count                        |Whole number             |Summarize: Sum<br>Number of calls presented to agent     |
|Total Call Duration (HH:MM:SS)          |Text                     |Call Duration (Minutes) converted to HH:MM:SS            |
|Total Call Duration (Minutes)           |Whole number             |Summarize: Sum<br>Total call duration of answered Call queue calls in minutes  |

> [!NOTE]
> When a call arrives at the first Call queue, if the number of calls already waiting in that queue has reached the **Call overflow handling** limit and if the redirect option sends new calls to a second Call queue, then the agents in the second Call queue will be shown as being in the first Call queue on this report. 

## Data Limits

Each report tab is restricted to retrieving 90,000 rows. If there's a large number of calls being processed each day, it's possible that the report won't show all calls for all days within the selected date range.  There is no notification when this occurs.  Try shortening the date range to avoid this issue.

If shortening the date range is not sufficient, it is possible to increase the number of rows that can be retrieved by modifying the report as follows:

1. Right click on the "fAutoAttendant" field on the right, click "Edit Query".
2. Right click on "CommonQueryParameters" and click "Advanced Editor".
3. Change the "LimitedResultRowsCount" to a larger number.
4. Save the report.

The maximum number of rows that can be retuned is 200,000.  Setting the value to a number higher than this will have no effect as this is a hard-coded limit.

Increasing the limit will result in longer response times.

## Known issues

- Only the calls and caller actions in the first Auto attendant or Call queue that answers the call are reported on.  Calls and caller actions in chained Auto attendants (when one Auto attendant transfers to another Auto attendant) or chained Call queues (when one Call queue transfers to another Call queue) aren't reported on. 

- Call queues and Auto attendants are shown by the resource account's ID instead of Call queue or Auto attendant names.  To show all the traffic for an Auto attendant or Call queue, you must select all the resource accounts assigned to the Auto attendant or Call queue.

- Only 28 days of call history are available. Call queue and Auto attendant data is considered personal data and is subject to data privacy retention policies.

- In some scenarios, the agent answered call count on the **Cloud Call Queue Agent Timeline** report may be different than the number of calls shown in the Teams client call history. The Teams client call history is correct. Support is investigating, but there's no estimated time to repair available at this time.

## Customization

You can customize certain visualization aspects of the reports, such as adding or removing fields to be shown in the various visualizations, changing chart type, and more.

### Change color schema

The following steps assume you have already completed the installation steps.

Perform the following steps:

1. Select **View tab** on the ribbon.

   :::image type="content" source="media/aa-cq-historical-report-04.png" alt-text="Screenshot selecting view tab to change color scheme.":::

2. Select the color schema from the drop-down list.

   :::image type="content" source="media/aa-cq-historical-report-05.png" alt-text="Screenshot showing various color schemes.":::
  
## Dimensions and measurements

The following dimensions and measurements are available to be used.

### Common dimensions

These dimensions are common to both Auto attendants and Call queues:

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|ConferenceId<br>(Text)                                 |GUID                           |Call identifier                                                   |
|Date<br>(DateTime)                                     |                               |Date of call (UTC)                                                |
|DialogId<br>(Text)                                     |GUID                           |Call identifier                                                   |
|DocumentId<br>(Text)                                   |GUID                           |Call identifier                                                   |
|Duration<br>(Whole Number)                             |                               |Duration of call, in seconds                                      |
|EndTime<br>(DateTime)                                  |                               |Time call ended (UTC)                                             |
|FirstIsCaller<br>(Boolean)                             |                               |[First and Second endpoint classification](dimensions-and-measures-available-in-call-quality-dashboard.md)     |
|FirstUPN<br>(Text)                                     |                               |The user principal name (UPN) of the first endpoint's user        |
|Hour<br>(Text)                                         |                               |Hour call started (UTC)                                           |
|Minute<br>(Text)                                       |                               |Minute call started (UTC)                                         |
|PSTNCallDuration<br>(Whole Number)                     |                               |Duration of the call                                              |
|PSTNCallType<br>(Text)                                 |                               |                                                                  |
|                                                       |External                       |Call is coming from outside the tenant                            |
|                                                       |Internal                       |Call is coming from within the tenant                             |
|PSTNConnectivityType<sup>1</sup><br>(Text)             |                               |                                                                  |
|                                                       |CallingPlan                    |                                                                  |
|                                                       |DirectRouting                  |                                                                  |
|Second<br>(Text)                                       |                               |Second call started (UTC)                                         |
|SecondUPN<br>(Text)                                    |                               |The user principal name (UPN) of the second endpoint's user       |
|TenantId<br>(Text)                                     |                               |Tenant ID                                                         |
|Timestamp<br>(DateTime)                                |                               |Time record was written (UTC)                                     |
|UserStartTimeUTC<br>(DateTime)                         |                               |Time call started (UTC)                                           |

- <sup>1</sup> **PSTNConnectivityType** shows the final call leg source rather than the initial call leg source. For example, if an Auto attendant receives an external call and transfers the call to another Auto attendant or Call queue, the **Incoming call source** is reported as **Internal**.

### Auto attendant dimensions

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|AutoAttendantCallFlow<br>(Text)                        |                               |Encapsulates the different states of Auto Attendant call          |
|                                                       |abs_search                     |                                                                  |
|                                                       |announcement                   |                                                                  |
|                                                       |automatic_menu                 |                                                                  |
|                                                       |call_termination               |                                                                  |
|                                                       |call_transfer                  |                                                                  |
|                                                       |first_level_menu               |                                                                  |
|                                                       |main_menu                      |                                                                  |
|                                                       |speech_input_confirmation      |                                                                  |
|                                                       |user_selection                 |                                                                  |
|AutoAttendantCallResult<br>(Text)                      |                               |Final call result                                                 |
|                                                       |failed_to_establish_media      |The media portion of the call couldn't be established             |
|                                                       |failover_to_operator           |Call transferred to operator typically due to a system error      |
|                                                       |oaa_chain_too_long             |Too many legs in the AA                                           |
|                                                       |oaa_session_too_long           |AA session has lasted too long                                    |
|                                                       |service_declined               |AA didn't accept the call                                         |
|                                                       |service_terminated             |AA configuration disconnects the call or call hung up             |
|                                                       |terminated_automatic_selection |AA configuration disconnects the calls                           |
|                                                       |terminated_no_operator         |All terminated due to error no operator defined                   |
|                                                       |terminated_transfer_failed     |Call terminated as transfer failed - typically to external number |
|                                                       |transfer_in_progress           |AA->AA transfer                                                   |
|                                                       |transferred_to_operator        |Call was transferred to operator                                  |
|                                                       |transferred_to_cq              |Call was transferred to Call queue                                |
|                                                       |transferred_to_receptionist    |Same as transferred_to_operator                                   |
|                                                       |transferred_to_self            |Call was returned to the start of the AA                          |
|                                                       |transferred_to_shared_voicemail |Call was transferred to shared voicemail                         |
|                                                       |transferred_to_user            |Call was transferred to a user                                    |
|                                                       |unknown                        |An unknown condition has occurred                                 |
|                                                       |user_terminated                |Caller hung up                                                    |
|AutoAttendantCallerActionCounts<br>(Whole Number)      |                               |                                                                  |
|AutoAttendantChainDurationInSecs<br>(Real Number)      |                               |                                                                  |
|AutoAttendantChainIndex<br>(Whole Number)              |                               |                                                                  |
|AutoAttendantChainStartTime<br>(DateTime)              |                               |                                                                  |
|AutoAttendantCount<br>(Whole Number)                   |                               |                                                                  |
|AutoAttendantDirectorySearchMethod<br>(Text)           |                               |Directory search method                                           |
|                                                       |abs_search_dtmf                |Touch tone                                                        |
|                                                       |abs_search_voice               |Voice                                                             |
|AutoAttendantIdentity<br>(Text)                        |                               |Resource account URI the call arrived on                         |
|AutoAttendantTransferAction<br>(Text)                  |                               |Call transfer target type                                         |
|                                                       |AA                             |Transferred to an AA                                              |
|                                                       |CQ                             |Transferred to a CQ                                               |
|                                                       |external_pstn                  |Transferred to an external number                                 |
|                                                       |shared voicemail               |Transferred to shared voicemail                                   |
|                                                       |Unknown                        |Unknown action                                                    |
|HasAA<br>(Boolean)                                     |                               |Is AA involved in call                                            |

### Call queue dimensions

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|CallQueueAgentCount<br>(Whole Number)                  |                               |Number of agents in Call queue                                    |
|CallQueueAgentOptInCount<br>(Whole Number)             |                               |Number of agents opted-in to Call queue                           |
|CallQueueCallResult<br>(Text)                          |                               |Call queue call final state                                       |
|                                                       |agent_joined_conference        |Call answered - conference mode CQ                                |
|                                                       |declined                       |                                                                  |
|                                                       |disconnected                   |                                                                  |
|                                                       |error                          |                                                                  |
|                                                       |failed                         |                                                                  |
|                                                       |invalid                        |                                                                  |
|                                                       |overflown                      |Overflow condition met                                            |
|                                                       |timed_out                      |Timeout condition met                                             |
|                                                       |transferred_to_agent           |Call answered - transfer mode CQ                                  |
|CallQueueDurationSeconds<br>(Real Number)              |                               |Call duration in the Call queue                                   |
|CallQueueFinalStateAction<br>(Text)                    |                               |Call queue final action                                           |
|                                                       |disconnect                     |time_out calls                                                    |
|                                                       |disconnect_with_busy           |overflown calls                                                   |
|                                                       |failed_to_accept_call          |                                                                  |
|                                                       |forward                        |Call was forwarded to a user or externally                        |
|                                                       |shared_voicemail               |Call was sent to shared voicemail                                 |
|                                                       |other                          |                                                                  |
|                                                       |voicemail                      |                                                                  |
|CallQueueIdentity<br>(Text)                            |                               |Resource account URI the call arrived on                         |
|CallQueueTargetType<br>(Text)                          |                               |Call redirection target                                           |
|                                                       |ApplicationEndpoint            |                                                                  |
|                                                       |Mailbox                        |                                                                  |
|                                                       |Other                          |                                                                  |
|                                                       |Phone                          |                                                                  |
|                                                       |User                           |                                                                  |
|HasCQ<br>(Boolean)                                     |                               |Is CQ involved in call                                            |
|TransferredFromCallQueueIdentity<br>(Text)             |                               |                                                                  |

### Measurements

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|AvgAutoAttendantChainDurationSeconds<br>(Real Number)  |                               |                                                                  |
|AvgCallDuration<br>(Real Number)                       |                               |                                                                  |
|AvgCallQueueDurationSeconds<br>(Real Number)           |                               |                                                                  |
|PSTNTotalMinutes<br>(Real Number)                      |                               |                                                                  |
|TotalAudioStreamDuration<br>(Real Number)              |                               |                                                                  |
|TotalCallCount<br>(Whole Number)                       |                               |                                                                  |

### Constructing a valid query

A valid query consists of several attributes in a JSON object:

```json
{
   "Filters":[
      {
         "DataModelName":"Date",
         "Value":"2022-04-01",
         "Operand":4
      },
      {
         "DataModelName":"Date",
         "Value":"2022-04-30",
         "Operand":6
      }
   ],
   "Dimensions":[
      {
         "DataModelName":"AutoAttendantIdentity"
      },
      {
         "DataModelName":"AutoAttendantDirectorySearchMethod"
      }
   ],
   "Measurements":[
      {
         "DataModelName":"PSTNTotalMinutes"
      },
      {
         "DataModelName":"TotalCallCount"
      }
   ],
   "Parameters":{
      "UserAgent":"Power BI Desktop"
   },
   "LimitResultRowsCount":100000
}
```

#### Required fields

- Filters: used to filter data returned by VAAC
  - DataModelName should be one of the supported dimensions
  - Value should be in the correct format (datetime, string, number etc.)
  - Operands:
    - 0 - Equals
    - 1 - Not Equals
    - 2 - Contains
    - 3 - Begins With
    - 4 - Greater Than
    - 5 - Greater Than or Equal To
    - 6 - Less Than
    - 7 - Less Than or Equal To
    - 8 - Does Not Contain
    - 9 - Does Not Begin With

- Dimensions:
  - DataModelName should be one of the supported dimensions

- Measurements:
  - DataModelName should be one of the supported measurements

- Parameters: Currently only UserAgent is supported.

- LimitResultRowsCount: the max count of rows returned by VAAC

## Accessing VAAC outside of Power BI

Any application that can access RESTful web services can use the VAAC API to retrieve historical data. In the following example, [Postman](https://www.postman.com/) is used.
  
### Preparation

1. Download [Postman](https://www.postman.com/).
1. Import the folder `postman` in the [downloaded zip file](#v3xx-desktop-installation) instructions into Postman. 

:::image type="content" source="media/aa-cq-historical-report-postman-01.png" alt-text="Screenshot showing import completed" lightbox="media/aa-cq-historical-report-postman-01.png":::

### Accessing VAAC using Postman

1. Select **VAAC - msit** on the top right ***No Environment*** drop-down.
2. Select **Environments** on the left hand rail menu.
3. Select **VAAC - msit** under **Globals**.
4. Replace **userName**, **password** and **tenantId** with the applicable credentials.
5. Select **Reset All** in the top right corner.
6. Select **Save**.

   :::image type="content" source="media/aa-cq-historical-report-postman-02.png" alt-text="Screenshot showing username, password and tenant ID fields configured" lightbox="media/aa-cq-historical-report-postman-02.png":::

7. Select **Collections** on the left hand rail menu.
8. Select **Config API Access Token - Prod** and navigate to the **Body** tab.
9. Select **Send**.

   An access token is returned.

   :::image type="content" source="media/aa-cq-historical-report-postman-03.png" alt-text="Screenshot showing result with access token returned" lightbox="media/aa-cq-historical-report-postman-03.png":::

   If an access token isn't returned, check your credentials to make they have [sufficient permissions](#permissions-to-access-the-cqd-pipeline).

10. Select **VAAC ConfigAPI Prod** and navigate to the **Params** tab.

    - [Compress](#compress-the-json-query) the query as outlined
    - [URL encode](#url-encode-the-compressed-json-query) the compressed result as outlined

11. Fill in your [query](#constructing-a-valid-query) string.
12. Select **Send**.

### Reading the result

After you submit your input, there will be a couple of possible results:

- If the input is invalid, an error message with the actual reason is returned
- If the input is valid, the result looks like this:

   :::image type="content" source="media/aa-cq-historical-report-postman-04.png" alt-text="Screenshot showing query result with dataResult field" lightbox="media/aa-cq-historical-report-postman-04.png" :::

   In this case, the data is in the "dataResult" field in the same order requested in the query dimension and measurements attributes.

### Compress the JSON query

The VAAC API only accepts GZip-compressed or Base64-encoded strings as input.

Find any website to compress the JSON blob using GZIP or Base64.

- GZIP: (https://www.multiutil.com/text-to-gzip-compress/)
- Base64: (https://www.multiutil.com/text-to-base64-converter/)

GZIP output should look like this:
````
H4sIAAAAAAAACq2SQWsCMRCF7/6KkLNC3EoPe9u6FISuFbW9lB4GM9TQbEaSCSLif+9mV4uCBwXnMkze5L0vkH1PCCFfjWX0QeZfaWxqf+xJLIGhIo12CjXKPM0o+2cLn2BjEjKVZQM1Gqjhhfy+QQ9Oy3x0PDz0H5HypK6nPJ9SUv9uV2RpanTBkLvxiUVkKpjRaXA80ejY8E7eg3/hUBqPKya/WyD41bpCXpP+tzvjrBBC9NjA8o2ks8VyuiQGWxkXGcNdkO3FMVg7puj4GtAMfLPa/Y2Tk/wI6IufhjHl0xa9eJmIEsMv06Y16cLlm6kNzzFEy3Pahi4kH6pUvcMfrAhUU3oCAAA=
````

Base64 output should look like this:
````
ew==
IkZpbHRlcnMiOls=
ew==
IkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw=
IlZhbHVlIjoiMjAyMi0wNC0wMSIs
Ik9wZXJhbmQiOjQ=
fSw=
ew==
IkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw=
IlZhbHVlIjoiMjAyMi0wNC0zMCIs
Ik9wZXJhbmQiOjY=
fQ==
XSw=
IkRpbWVuc2lvbnMiOls=
ew==
IkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50SWRlbnRpdHki
fSw=
ew==
IkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50RGlyZWN0b3J5U2VhcmNoTWV0aG9kIg==
fQ==
XSw=
Ik1lYXN1cmVtZW50cyI6Ww==
ew==
IkRhdGFNb2RlbE5hbWUiOiJQU1ROVG90YWxNaW51dGVzIg==
fSw=
ew==
IkRhdGFNb2RlbE5hbWUiOiJUb3RhbENhbGxDb3VudCI=
fQ==
XSw=
IlBhcmFtZXRlcnMiOns=
IlVzZXJBZ2VudCI6IlBvd2VyIEJJIERlc2t0b3Ai
fSw=
IkxpbWl0UmVzdWx0Um93c0NvdW50IjoxMDAwMDA=
fQ==
````

### URL-Encode the compressed JSON query

The GZIP or Base64 compressed JSON query must be [URL encoded](https://meyerweb.com/eric/tools/dencoder/).

GZIP URL encoded output looks like this:
````
H4sIAAAAAAAACq2SQWsCMRCF7%2F6KkLNC3EoPe9u6FISuFbW9lB4GM9TQbEaSCSLif%2B9mV4uCBwXnMkze5L0vkH1PCCFfjWX0QeZfaWxqf%2BxJLIGhIo12CjXKPM0o%2B2cLn2BjEjKVZQM1Gqjhhfy%2BQQ9Oy3x0PDz0H5HypK6nPJ9SUv9uV2RpanTBkLvxiUVkKpjRaXA80ejY8E7eg3%2FhUBqPKya%2FWyD41bpCXpP%2BtzvjrBBC9NjA8o2ks8VyuiQGWxkXGcNdkO3FMVg7puj4GtAMfLPa%2FY2Tk%2FwI6IufhjHl0xa9eJmIEsMv06Y16cLlm6kNzzFEy3Pahi4kH6pUvcMfrAhUU3oCAAA%3D
````

Base64 URL encoded output looks like this:
````
%0Aew%3D%3D%0AIkZpbHRlcnMiOls%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw%3D%0AIlZhbHVlIjoiMjAyMi0wNC0wMSIs%0AIk9wZXJhbmQiOjQ%3D%0AfSw%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJEYXRlIiw%3D%0AIlZhbHVlIjoiMjAyMi0wNC0zMCIs%0AIk9wZXJhbmQiOjY%3D%0AfQ%3D%3D%0AXSw%3D%0AIkRpbWVuc2lvbnMiOls%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50SWRlbnRpdHki%0AfSw%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJBdXRvQXR0ZW5kYW50RGlyZWN0b3J5U2VhcmNoTWV0aG9kIg%3D%3D%0AfQ%3D%3D%0AXSw%3D%0AIk1lYXN1cmVtZW50cyI6Ww%3D%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJQU1ROVG90YWxNaW51dGVzIg%3D%3D%0AfSw%3D%0Aew%3D%3D%0AIkRhdGFNb2RlbE5hbWUiOiJUb3RhbENhbGxDb3VudCI%3D%0AfQ%3D%3D%0AXSw%3D%0AIlBhcmFtZXRlcnMiOns%3D%0AIlVzZXJBZ2VudCI6IlBvd2VyIEJJIERlc2t0b3Ai%0AfSw%3D%0AIkxpbWl0UmVzdWx0Um93c0NvdW50IjoxMDAwMDA%3D%0AfQ%3D%3D
````

> [!IMPORTANT]
> The VAAC API is limited to returning a maximum of 200,000 rows per query.
>
> Requests into the system are throttled based on the IP address making the call, the recognized tenant identity in the auth header, as well as the calling service in order to prevent a single client, tenant, or service from monopolizing the resources.

## Version 3.x.x history

Refer to: Teams Auto Attendant & Call Queue Historical Reports - Change Log.docx in the downloaded zip file for a detailed list of changes.

|Version  |Date Published     |Filename                                                    |Description                                                             |
|:--------|:------------------|:-----------------------------------------------------------|:-----------------------------------------------------------------------|
|3.1.3    |September 13, 2023      |Teams Auto Attendant & Call Queue Historical Reports V3.1.2 |Accessibility improvements for screen readers   |
|3.1.2    |July 21, 2023      |Teams Auto Attendant & Call Queue Historical Reports V3.1.2 |Support any time zone offset, added detail call pop-up on Auto Attendant & Call Queue, No Agents support    |
|3.1.1    |May 11, 2023       |Teams Auto Attendant & Call Queue Historical Reports V3.1.1 |Corrected an error with the Date, Agent and Call Queue slicers          |
|3.1.0    |May 1, 2023        |Teams Auto Attendant & Call Queue Historical Reports V3.1.0 |New templates, added detail call pop-up on Agent Timeline, Power BI Service support   |
|3.0.7    |February 16, 2023  |Teams Auto Attendant & Call Queue Historical Reports V3.0.7 |Corrected error on Agent Timeline when call minutes were greater than 9 |
|3.0.6    |February 14, 2023  |Teams Auto Attendant & Call Queue Historical Reports V3.0.6 |Corrected error, improved call classification and Agent timeline visuals|
|3.0.5    |January 9, 2023    |Teams Auto Attendant & Call Queue Historical Reports V3.0.5 |Improved Call Overflow/Timeout Destinations and Agent timeline visuals  |
|3.0.4    |November 18, 2022  |Teams Auto Attendant & Call Queue Historical Reports V3.0.4 |Corrected error, improved call classification, added legend             |
|3.0.3    |November 8, 2022   |Teams Auto Attendant & Call Queue Historical Reports V3.0.3 |Corrected error, added documentation link, optimized queries            |
|3.0.1    |October 26, 2022   |Teams Auto Attendant & Call Queue Historical Reports V3.0.1 |Removed testing data source entry                                       |
|3.0.0    |October 25, 2022   |Teams Auto Attendant & Call Queue Historical Reports V3.0.0 |New backend data source                                                 |
