---
title: Updated auto attendant and call queue historical reports
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
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

# Updated auto attendant and call queue historical reports

>[!NOTE]
> GCC HIgh and DOD customers should continue to use V1.63 of [Auto Attendant & Call Queue Historical Reports (CQD)](aa-cq-cqd-historical-reports-v163.md).

This Power BI template provides three reports that allow organizations to report on the number of calls being processed by auto attendants and call queues.  It also provides agent performance insights.

## V3.0.4 published on November 18, 2022

The Teams Auto Attendant & Call Queue Historical Report Power BI template provides the following three reports:

- The [Auto Attendant](media/aa-cq-historical-report-sample-aa-v304.png) report shows analytics for calls coming into your auto attendants.
- The [Call Queue](media/aa-cq-historical-report-sample-cq-v304.png) report shows analytics for calls coming into your call queues.
- The [Agent Timeline](media/aa-cq-historical-report-sample-at-v304.png) report shows a timeline view of agents being active in call queue calls.

These reports use data from the Voice Applications Analytics Collector (VAAC) service.

## V3.x.x prerequisites

### Power BI Desktop

You need to have Power BI Desktop installed. You can install and use the free version from the [Microsoft Windows Store](https://aka.ms/pbidesktopstore).

The minimum compatible version is 2.85.681.0 (September 2020).

### Permissions to access the CQD pipeline

While this version of the reports doesn't use the Call Quality Dashboard (CQD) data pipeline, the account used to view the historical data still requires access to the Call Quality Dashboard. For more information, see [CQD access role](./turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd).

- This requirement will be removed in a future release.

## V3.x.x installation 

The following steps assume you've already installed Power BI Desktop on your computer and that your account has the necessary permissions to access the CQD data pipeline.

Perform the following steps:

1. Download and save the [Teams Auto Attendant & Call Queue Historical Reports V3.0.4.zip](https://www.microsoft.com/download/details.aspx?id=104623) file on your computer.

2. Open the zip file.

3. Open the `Teams Auto Attendant & Call Queue Historical Reports V3.0.4.pbit` template file. Power BI Desktop should launch.

4. You'll be prompted to select the **Data Source**.  Select the `api.interfaces.records.teams.microsoft.com` entry.

  :::image type="content" source="media/aa-cq-historical-report-01-v304.png" alt-text="Screenshot selecting the api.interfaces.records.teams.microsoft.com Data Soure":::

5. You'll be prompted to sign in with an account. Select **Organizational account**, and then select **Sign in**.

  :::image type="content" source="media/aa-cq-historical-report-03-v300.png" alt-text="Screenshot showing login for V3.0.0.":::

6. Select **Connect**, and the data will refresh.

> [!NOTE]
> If you were using v1.63 or earlier, you may encounter an error when v3.x.x tries to retrieve the data from VAAC.  To resolve this error, it's necessary to clear any previous credentials from Power BI.
> 
> 1. Open the v3.x.x template to clear the error. 
> 1. Select **File** > **Options & Settings** > **Data source settings**.
> 1. Select the drop down for **Clear Permissions**, and then select **Clear All Permissions**.
> 1. Close the template after they're cleared, and restart Power BI. You'll be asked to authorize again. 

## Data latency for auto attendant and call queue analytics

Data is typically available within 30 minutes of the call completing; however, there are occasions where it may take several hours for data to appear. 

You'll have to refresh the data to see any new data.

## Customization 

You can customize certain visualization aspects of the reports, such as adding or removing fields to be shown in the various visualizations, changing chart type, and more.

The report contains all the data metrics currently available.

### Change color schema 

The following steps assume you've already completed the installation steps.

Perform the following steps:

1. Select **View tab** on the ribbon.

  :::image type="content" source="media/aa-cq-historical-report-04.png" alt-text="Screenshot selecting view tab to change color scheme.":::

2. Select the color schema from the drop-down list.

  :::image type="content" source="media/aa-cq-historical-report-05.png" alt-text="Screenshot showing various color schemes.":::
  
## Dimensions and measurements

### Common dimensions

These dimensions are common to both auto attendants and call queues:

|Name (Type)                                            |Possible Values                |Description                                                       |
|:------------------------------------------------------|:------------------------------|:-----------------------------------------------------------------|
|ConferenceId<br>(Text)                                 |GUID                           |Call identifier                                                   |
|Date<br>(DateTime)                                     |                               |Date of call (UTC)                                                |
|DialogId<br>(Text)                                     |GUID                           |Call identifier                                                   |
|DocumentId<br>(Text)                                   |GUID                           |Call identifier                                                   |
|Duration<br>(Whole Number)                             |                               |Duration of call, in seconds                                      |
|EndTime<br>(DateTime)                                  |                               |Time call ended (UTC)                                             |
|FirstIsCaller<br>(Boolean)                             |                               |                                                                  |
|FirstUPN<br>(Text)                                     |                               |                                                                  |
|Hour<br>(Text)                                         |                               |Hour call started (UTC)                                           |
|Minute<br>(Text)                                       |                               |Minute call started (UTC)                                         |
|PSTNCallDuration<br>(Whole Number)                     |                               |                                                                  |
|PSTNCallType<br>(Text)                                 |                               |                                                                  |
|                                                       |External                       |                                                                  |
|                                                       |Internal                       |                                                                  |
|PSTNConnectivityType<sup>1</sup><br>(Text)             |                               |                                                                  |
|                                                       |CallingPlan                    |                                                                  |
|                                                       |DirectRouting                  |                                                                  |
|Second<br>(Text)                                       |                               |Second call started (UTC)                                         |
|SecondUPN<br>(Text)                                    |                               |                                                                  |
|TenantId<br>(Text)                                     |                               |Tenant ID                                                         |
|Timestamp<br>(DateTime)                                |                               |Time record was written (UTC)                                     |
|UserStartTimeUTC<br>(DateTime)                         |                               |Time call started (UTC)                                           |

- <sup>1</sup> **PSTNConnectivityType** will show the final call leg source rather than the initial call leg source. For example, if an auto attendant receives an external call and transfers the call to another auto attendant or call queue, the **Incoming call source** will be reported as **Internal**.


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
|                                                       |transferred_to_cq              |Call was transferred to call queue                                |
|                                                       |transferred_to_receptionist    |Same as transferred_to_operator                                   |
|                                                       |transferred_to_self            |Call was returned to the start of the AA                          |
|                                                       |transferred_to_shared_voicemail |Call was transferred to shared voicemail                         |
|                                                       |transferred_to_user            |Call was transferred to a user                                    |
|                                                       |unknown                        |An unknown condition has occurred                                 |
|                                                       |user_terminated                |Caller hung up                                                    |
|AutoAttendantCallerActionCounts<br>(Whole Number)      |                               |                                                                  |
|AutoAttendantChairDurationInSecs<br>(Real Number)      |                               |                                                                  |
|AutoAttendantChainIndex<br>(Whole Number)              |                               |                                                                  |
|AutoAttendantChainStartTime<br>(DateTime)              |                               |                                                                  |
|AutoAttendantCount<br>(Whole Number)                   |                               |                                                                  |
|AutoAttendantDirectorySearchMethod<br>(Text)           |                               |Directory search method                                           |
|                                                       |abs_search_dtmf                |Touch tone                                                        |
|                                                       |abs_search_voice               |Voice                                                             |
|AutoAttendantIdentity<br>(Text)                        |                               |Resource account URI call arrived on                              |
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
|CallQueueAgentCount<br>(Whole Number)                  |                               |Number of agents in call queue                                    |
|CallQueueAgentOptInCount<br>(Whole Number)             |                               |Number of agents opted-in to call queue                           |
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
|CallQueueDurationSeconds<br>(Real Number)              |                               |                                                                  |
|CallQueueFinaleStateAction<br>(Text)                   |                               |Call queue final action                                           |
|                                                       |disconnect                     |time_out calls                                                    |
|                                                       |disconnect_with_busy           |overflown calls                                                   |
|                                                       |failed_to_accept_call          |                                                                  |
|                                                       |forward                        |                                                                  |
|                                                       |shared_voicemail               |                                                                  |
|                                                       |other                          |                                                                  |
|                                                       |voicemail                      |                                                                  |
|CallQueueIdentity<br>(Text)                            |                               |Resource account URI call arrived on                              |
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

## Auto attendant and call queue historical reports definitions

### Cloud Auto Attendant Analytics report

#### Report description

|Report Section                          |Description                                                       |
|:---------------------------------------|:-----------------------------------------------------------------|
|Incoming Call Source                    |Distribution of calls by Internal/External call source            |
|Directory Search Method                 |Distribution of calls by search type                              |
|Caller Action Count                     |Distribution of calls by number action used during the call       |
|Average Seconds in AA                   |Average number of seconds callers spend in the AA                 |
|Average Caller Actions                  |Average number of actions callers perform in the AA               |
|Call Results                            |Distribution of calls by final call state                         |
|Lower section of report                 |Call flow breakdown                                               |

#### Report visual and field mapping

|Report Tab            |Report Table Name     |Global Filter                          |
|:---------------------|:---------------------|:--------------------------------------|
|Auto Attendant        |fAutoAttendant        |None                                   |

|Report Section                               |Field(s) Used                                                                                    |Filters Applied |
|:--------------------------------------------|:------------------------------------------------------------------------------------------------|:----------|
|Date selector                                |AAStartTime                                                                                      |None       |
|Time Range selector                          |AAStartHour                                                                                      |None       |
|Auto Attendant Resource Accounts             |AA Name                                                                                          |None       |
|Incoming Call Source                         |Call Type<br>Sum of TotalCallCount         |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal |
|Directory Search Method                      |AADirectorySearchMethod<br>AADirectorySearchMethodLegend<br>TotalCallCount  |AADirectorySearchMethod is abs_search_dtmf or abs_search_name    |
|Caller Action Count                          |AACallerActionCount<br>TotalCallCount                                                            |None       |
|Average Seconds in AA                        |AAChainDuration                                                                                  |None       |
|Average Caller Actions                       |AACallerActionCount                                                                              |None       |
|Call Results                                 |AACallResult<br>AACallResultLegend<br>TotalCallCount                                             |None       |
|Lower section of report                      |MM-DD<br>AA Name<br>AACallFlow<br>Call Type<br>AACallResult<br>TotalCallCount<br>AAChainDuration |None       |

#### fAutoAttendant field description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|AA Name                                 |Text                     |Name of resource account attached to Auto Attendant<br><br>If the full Resource Account name is **aa_test@microsoft.com**, then this value will be: **aa_test** |
|AACallerActionCount                     |Whole number             |Summarize: Sum<br>Count of actions selected by caller in Auto Attendant during the call  |
|AACallerActionCount (Measure)           |Whole number             |Same as above except will be 0 if no calls instead of blank                              |
|AACallFlow                              |Text                     |See Auto Attendant dimensions -> AutoAttendantCallFlow                                   |
|AACallResult                            |Text                     |See Auto Attendant dimensions -> AutoAttendantCallResult                                 |
|AACallResultLegend                      |Text                     |Sets up legend items based on AACallResult                                               |
|AAChainDuration                         |Decimal number           |Summarize: Sum<br>Duration of call in Auto Attendant                                     |
|AAChainDuration (Measure)               |Decimal number           |Same as above except will be 0 if no calls instead of blank                              |
|AAChainIndex                            |Text                     |                                                                                         |
|AAConnectivityType                      |Text                     |                                                                                         |
|AACount                                 |Text                     |Number of Auto Attendants involved in call                                               |
|AADirectorySearchMethod                 |Text                     |See Auto Attendant dimensions -> AutoAttendantDirectorySearchMethod                      |
|AADirectorySearchMethodLegend           |Text                     |Sets up legend items based on AADirectorySearchMethod                                    |
|AAStartHour                             |Decimal number           |Auto Attendant call start hour                                                           |
|AAStartTime                             |Date/time                |Auto Attendant call start time                                                           |
|AATransferAction                        |Text                     |See Auto Attendant Dimensions -> AutoAttendantTransferAction                             |
|Call Type<sup>1</sup>                   |Text                     |See Common Dimensions -> PSTNCallType                                                    |
|MM-DD                                   |Text                     |Auto Attendant call month-day                                                            |
|PSTNMinutes                             |Whole number             |Summarize: Sum<br>Total minute usage                                                     |
|TotalCallCount                          |Whole number             |Summarize: Sum<br>Always 1 - used to provide sum of all calls                            |
|Sum of TotalCallCount (Measure)         |Whole number             |Same as above except will be 0 if no calls instead of blank                              |


### Cloud Call Queue Analytics report

#### Report description

|Report Section                          |Description                                                        |
|:---------------------------------------|:------------------------------------------------------------------|
|Incoming Call Source                    |Distribution of calls by Internal/External call source             |
|Average Wait Time (seconds)             |Wait time for answered and abandoned calls                          |
|Call Volume and Agent Opt-in Count      |Distribution of calls by call queues / Maximum agent opt-in count  |
|Call Results                            |Distribution of calls by call result                               |
|Abandoned Calls                         |Distribution of abandoned calls by call queues                     |
|Average Session Length (seconds)        |Call length in seconds grouped by call result                      |
|Call Overflow/Timeout Destinations      |Distribution of calls that timed out or overflowed                 |


#### Report visual and field mapping

|Report Tab            |Report Table Name                                   |Global Filter       |
|:---------------------|:---------------------------------------------------|:-------------------|
|Call Queue            |fCallQueueAnalytics<br>fCallQueueFinalStateAction   |None                |

|Report Section                      |Table -> Field(s) Used                |Filters Applied       |
|:-----------------------------------|:-------------------------------------|:---------------------|
|Date selector                       |fCallQueueAnalytics -> Date           |None                  |
|Time Range selector                 |fCallQueueAnalytics -> CQHour         |None                  |
|Call Queue Resource Account         |fCallQueueAnalytics -> CQ Name        |None                  |
|Incoming call source                |fCallQueueAnalytics -> Sum of Call Count (Measure)  |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal |
|Avg Wait Time (seconds)-Before Answered |fCallQueueFinalStateAction -> Avg of Average CQ Duration (Measure) |Call Queue Call Result is agent_joined_conference or transferred_to_agent|
|Avg Wait Time (seconds)-Before Abandoned |fCallQueueFinalStateAction -> Avg of Average Call Duration (Measure) |Call Queue Call Result isn't agent_joined_conference, transferred_to_agent, overflown, timed_out |
|Call Volume and Agent Opt-In Count   |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Agent Opt In Count<br>fCallQueueAnalytics -> CQ Name<br>fCallQueueAnalytics -> Date |None |
|Abandoned Calls                     |fCallQueueAnalytics -> Date<br>fCallQueueAnalytics -> TotalCallCount | Call Queue Call Result Legend is Abandoned |
|Average Session Length (seconds)    |fCallQueueFinalStateAction -> Average Call Queue Duration (Sec)<br>Call Queue Call Result Legend |Average Call Queue Duration (Sec) > 0 |
|Call Overflow/Timeout Destinations  |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Target Type<br>fCallQueue Target Type Legend |Call Queue Target Type Legend doesn't contain Abandoned and Agent Answered |


#### fCallQueueAnalytics field description

|Name                                    |Data Type                |Description                                                                |
|:---------------------------------------|:------------------------|:--------------------------------------------------------------------------|
|Call Count                              |Whole number             |Summarize: Sum<br>Number of calls                                          |
|Call Queue Agent Count                  |Whole number             |Summarize: Sum<br>Number of agents configured in the call queue            |
|Call Queue Agent Opt In Count           |Whole number             |Summarize: Sum<br>Number of agents opted-in to the call queue              |
|Call Queue Call Result                  |Text                     |See Call Queue Dimensions -> CallQueueCallResult                           |
|Call Queue Call Result Legend           |Text                     |Sets up legend items based on Call Queue Result                            |
|Call Queue Target Type                  |Text                     |See Call Queue Dimensions -> CallQueueTargetType                           |
|Call Queue Target Type Legend           |Text                     |Sets up legend items based on Call Queue Target Type                       |
|Call Type                               |Text                     |See Common Dimensions -> PSTNCallType                              |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value will be: **cq_test** |
|CQ Hour                                 |Whole Number             |Call queue call start hour                                                 |
|Date                                    |Date/time                |Call queue call start date and time (hour)                                 | 
|DateTimeCQName                          |Text                     |Unique key for filtering on fCallQueueFinalStateAction                     |
|PSTN Connectivity Type                  |Text                     |See Common Dimensions -> PSTNConnectivityType                              |
|PSTN Total Minutes                      |Whole number             |Summarize: Sum<br>Total minutes usage for PSTN calls                       |
|Sum of Call Count (Measure)             |Whole number             |Same as Call Count however will be 0 when no call                          |
|TotalCallCount (Measure)                |Whole Number             |Summarize: Sum<br>Call Count                                               |


#### fCallQueueFinalStateAction field description

|Name                                    |Data Type                |Description                                                                |
|:---------------------------------------|:------------------------|:--------------------------------------------------------------------------|
|Average Call Duration (Seconds)         |Decimal number           |Summarize: Sum<br>Average call duration in seconds for abandoned calls     |
|Average Call Queue Duration (Sec)       |Decimal number           |Summarize: Sum<br>Average waiting time in seconds for answered calls       |
|Avg of Average Call Duration (Measure)  |Whole number             |Same as Average Call Duration (Seconds) however will be 0 when no calls    |
|Avg of Average CQ Duration (Measure)    |Whole number             |Same as Average Call Queue Duration (Sec) however will be 0 when no calls  |
|Call Count                              |Whole number             |Summarize: Sum<br>Number of calls                                          |
|Call Queue Call Result                  |Text                     |See Call Queue Dimensions -> CallQueueCallResult                           |
|Call Queue Call Result Legend           |Text                     |Sets up legend items based on Call Queue Call Result                       |
|Call Queue Final State Action           |Text                     |See Call Queue Dimensions -> CallQueueFinaleStateAction                    |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value will be: **cq_test** |
|CQ Hour                                 |Number                   |Hour that the call took place in
|Date                                    |Date/time                |Call Queue call start date and time (hour)                                 |
|DateTimeCQName                          |Text                     |Unique key for filtering on fCallQueueFinalStateAction                     |
|IsAbandoned                             |True/false               |True if call isn't answered by an agent                                    |


### Cloud Call Queue Agent Timeline report

#### Report description

|Report Section                                          |Description                                                         |
|:-------------------------------------------------------|:-------------------------------------------------------------------|
|Number of Calls by Agent                                |Distribution of calls by call queue and agent                       |
|Distribution by Agent and all Queue                     |Distribution of calls by agent and call queue                       |
|Table (bottom left)                                     |Distribution of calls by agent with average and total call duration |
|Average Call Duration (seconds) by Agent (bottom right) |Average duration (seconds) of call by agent                         |

#### Report visual field mapping

|Report Tab            |Report Table Name           |Global Filter       |
|:---------------------|:---------------------------|:-------------------|
|Agent Timeline        |fAgentTimelineAnalytics     |None                |


|Report Section                                |Field(s) Used                         |Filters Applied       |
|:---------------------------------------------|:-------------------------------------|:---------------------|
|Date selector                                 |DateTime                              |None                  |
|Agent Username selector                       |Agent Name                            |None                  |
|Call Queue Resource Accounts selector         |CQ Name                               |None                  |
|Number of Calls by Agent                      |Call Count<br>Agent Name<br>Date<br>Hour      |None                  |
|Distribution by Agent and Call Queue          |Agent Name<br>Average Calls Duration (Seconds)<br>Call Count<br>CQ Name |None                      |
|Bottom Left                                   |Agent Name<br>Average Call Duration (Seconds)<br>Call Count<br>Call Duration (Minute)<br>CQ Name<br>Hour<br>MM-DD | None |
|Average Call Duration (Seconds) by Agent      |Agent Name<br>Average Call Duration (Seconds) | None |

#### fAgentTimelineAnalytics field description

|Name                                    |Data Type                |Description                                         |
|:---------------------------------------|:------------------------|:---------------------------------------------------|
|Agent Name                              |Text                     |User UPN<br>If the full username is **user@microsoft.com**, then this value will be: **user** |
|Average Call Duration (Seconds)         |Decimal number           |Summarize: Sum<br>The average duration of answered call queue calls in seconds |
|Call Count                              |Whole number             |Summarize: Sum<br>Number of calls answered by the agent     |
|Call Duration (Minutes)                 |Whole number             |Summarize: Sum<br>Total call duration of answered call queue calls in minutes (rounded down to nearest minute)  |
|CQ Name                                 |Text                     |Name of resource account attached to Call Queue<br><br>If the full Resource Account name is **cq_test@microsoft.com**, then this value will be: **cq_test** |
|Date                                    |Date                     |Date of call                                             |
|DateTime                                |DateTime                 |Date of call                                             |
|Hour                                    |Whole number             |Hour of call                                             |
|MM-DD                                   |Text                     |Month and day of call                                    |


> [!NOTE]
> When a call arrives at the first call queue, if the number of calls already waiting in that queue has reached the **Call overflow handling** limit and if the redirect option sends new calls to a second call queue, then the agents in the second call queue will be shown as being in the first call queue on this report. 

## Known issues

- Call queues and auto attendants are shown by the resource account's ID instead of call queue/auto attendant names.  To show all the traffic for an auto attendant or call queue, you must select all the resource accounts assigned to the auto attendant or call queue.

- Only 28 days of history are available in the dashboard as call queue/auto attendant data is considered personal data and is subject to data privacy retention policies.

- In some scenarios, the agent answered call count on the **Cloud Call Queue Agent Timeline** report may be different than the number of calls shown in the Teams client call history. The Teams client call history is correct. Support is investigating, but there's no estimated time to repair available at this time.

## Version 3.x.x history

Refer to: Teams Auto Attendant & Call Queue Historical Reports - Change Log.docx in the downloaded zip file for a detailed list of changes 

|Version  |Date Published     |Filename                                                           |Description                                         |
|:--------|:------------------|:------------------------------------------------------------------|:---------------------------------------------------|
|3.0.4    |November 18, 2022  |Teams Auto Attendant & Call Queue Historical Reports V3.0.4        |Corrected error, improved call classification, added legend |
|3.0.3    |November 8, 2022   |Teams Auto Attendant & Call Queue Historical Reports V3.0.3        |Corrected error, added documentation link, optimized queries |
|3.0.1    |October 26, 2022   |Teams Auto Attendant & Call Queue Historical Reports V3.0.1        |Removed testing data source entry                   |
|3.0.0    |October 25, 2022   |Teams Auto Attendant & Call Queue Historical Reports V3.0.0        |New backend data source                             |
