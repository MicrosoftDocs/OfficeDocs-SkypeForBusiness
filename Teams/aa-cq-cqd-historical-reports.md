---
title: Auto Attendant & Call Queue Historical Report
ms.author: mikeplum
author: MikePlumleyMSFT
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
localization_priority: Normal
f1.keywords: 
  - CSH
ms.custom: 
  - Reporting
  - ms.teamsadmincenter.directrouting.cqd
  - ms.lync.lac.ToolsCallQualityDashboard
description: Learn about how to use Call Quality Dashboard Power BI report to view Auto Attendant and Call Queue historical data.
---
# Auto Attendant & Call Queue Historical Report

The CQD Teams Auto Attendant & Call Queue Historical Report Power BI Template provides the following three reports:

- Auto Attendant – showing analytics for calls coming into your Auto Attendants.
- Call Queue – showing analytics for calls coming into your Call Queues.
- Agent Timeline – showing a timeline view of agents being active in Call Queue calls.

These reports use data from the [Call Quality Dashboard](CQD-Power-BI-query-templates.md) data store and allow organizations
to report on the number of calls being processed by auto attendants and call queues as well agent performance in the call queues.

## What are the requirements? 

You need to have Power BI Desktop installed. You can install it from the [Microsoft Windows Store](https://aka.ms/pbidesktopstore).

You can use the free version of Power BI Desktop. The minimum compatible version is 2.85.681.0 (September 2020).

## Permissions to access the CQD pipeline

The account you use to view the AA & CQ Analytics historical report needs to have permissions to access the CQD data pipeline. Refer to the [CQD access role](./turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd) for more information.

## Installation 

The following steps assume you have already installed Power BI Desktop on the computer and that your account has the necessary permissions to access the CQD data pipeline.

Perform the following steps:

- Download the [CQD Power BI Query Templates](https://www.microsoft.com/download/details.aspx?id=102291) and save the zip file to a directory on your computer.

- Double-click on the zip file to open it.

- Double-click on the "CQ and AA combined Analytics 20201105.pbit" template file and Power BI Desktop should launch.

- You will be prompted to select the CQD data pipeline region. Select the region where your tenant is located.

  :::image type="content" source="media/cqd-teams-aa-cq-historical-report-01.png" alt-text="Screenshot selecting the CQD data pipeline region":::

- The region where your tenant is located can be obtained by using the [Get-CsTenant](/powershell/module/skype/get-cstenant.md) cmdlet.

    ```PowerShell
    (Get-CsTenant).ServiceInstance


    microsoftcommunicationsonline/noam-4a-s7
    ```

    - The region will be displayed after the **/** as in the above example where there region is: noam

 - The report will launch with sample data.
 
 - To see your own data, click **Refresh** in the Home tab under Queries in Power BI Desktop.

   :::image type="content" source="media/cqd-teams-aa-cq-historical-report-02.png" alt-text="Screenshot selecting the refresh option":::

- You will then be prompted to sign in. Select **Organization account** and then select **Sign in**.

  :::image type="content" source="media/cqd-teams-aa-cq-historical-report-03.png" alt-text="Screenshot showing login":::

- Select **Connect** and watch the data refresh.

## Data latency and AA & CQ analytics

Data will be available in the CQD data pipeline within 30 minutes.

You will have to refresh the data to see the new analytics data. 

## Customization 

You can customize certain visualization aspects of the reports, such as adding or removing fields to be shown in the various visualizations, changing chart type, etc.

You cannot add additional data fields other than the ones provided in the report.

### Change color schema 

The following steps assume you have already completed the Installation steps.

Perform the following steps:
- Select **View tab** on the ribbon.

  :::image type="content" source="media/cqd-teams-aa-cq-historical-report-04.png" alt-text="Screenshot selecting view tab to change color scheme":::

- Select the color schema from the drop-down list.

  :::image type="content" source="media/cqd-teams-aa-cq-historical-report-05.png" alt-text="Screenshot showing various color schemes":::
  
## Auto Attendant and Call Queue Historical Reports Definitions

### Cloud Auto Attendant Analytics

#### Report description

|Report Section                          |Description                                                       |
|:---------------------------------------|:-----------------------------------------------------------------|
|Incoming call source<sup>1</sup>        |Distribution of calls by Internal/External call source             |
|Directory search method totals          |Distribution of calls by search type                               |
|Caller action                           |Distribution of calls by call receiver                             |
|Call result                             |Distribution of calls by final call state                          |
|Caller action count                     |Distribution of calls by number action used during the call        |


#### Report to CQD table and field mapping

|Report Tab            |Report Table Name     |Global Filter                          |
|:---------------------|:---------------------|:--------------------------------------|
|Auto Attendant        |fAutoAttendant        |AAStartTime is within the last 28 days |


|Report Table Name            |Source Table Name            |Processing       |
|:----------------------------|:----------------------------|:----------------|
|fAutoAttedant                |AutoAttendant                |Source = AutoAttendant, <br>#"Filtered Rows" = Table.SelectRows(Source, each true), <br>#"Auto Attendant" = Table.AddColumn(#"Filtered Rows", "AA Name", each List.First(Text.Split([AAIdentity], "@"))), <br>#"Changed Type" = Table.TransformColumnTypes(#"Auto Attendant",{{"AAStartTime", type datetime}}), <br>#"Removed Columns" = Table.RemoveColumns(#"Changed Type",{"AAIdentity"}) |


|Report Section                                  |Field(s) Used                              |Filters Applied     |
|:-----------------------------------------------|:------------------------------------------|:-------------------|
|Auto Attedant (drop down - top right)           |AA Name                                    |None                |
|Incoming call source<sup>1</sup>                |Call Type<br>TotalCallCount                |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal |
|Directory search method totals                  |AADirectorySearchMethod<br>TotalCallCount  |AADirectorySearchMethod is abs_search_dtmf or abs_search_name    |
|Caller actions                                  |AATransferAction<br>TotalCallCount         |None                                                             |
|Average Seconds in AA<br>Average Caller Actions |AAChainDuration<br>AACallerActionCount     |None                                                             |
|Call results                                    |AACallResult<br>TotalCallCount             |None                                                             |
|Caller actions count                            |AACallerActionCount<br>TotalCallCount      |None                                                             |
|Lower section of report                         |AA Name<br>AACallFlow<br>AACallResult<br>AAChainDuration<br>Call Type<br>TotalCallCount |None                |

#### fAutoAttendant CQD fields description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|AA Name                                 |string                   |Name of resource account attached to Auto Attendant<br><br>If the full Resource Account name is **aa_test@microsoft.com** then the value for AA Name will be **aa_test** |
|AACallerActionCount                     |int	                     |Count of actions selected by caller in Auto Attendant during the call  |
|AACallFlow                              |string                   |Encapsulates the different states of Auto Attendant Call -- possible values:<br><br>§ abs_search<br>§ announcement<br>§ automatic_menu<br>§ call_termination<br>§ call_transfer<br>§ first_level_menu<br>§ main_menu<br>§ speech_input_confirmation<br>§ user_selection |
|AACallResult                            |string                   |Final call result -- possible values:<br><br>§ failed_to_establish_media<br>§ failover_to_operator<br>§ oaa_chain_too_long<br>§ oaa_session_too_long<br>§ service_declined<br>§ service_terminated<br>§ terminated_automatic_selection<br>§ terminated_no_operator<br>§ terminated_transfer_failed<br>§ transferred_to_operator<br>§ transferred_to_shared_voicemail<br>§ transferred_to_user<br>§ unknown<br>§ user_terminated |
|AAChainDuration                         |int                      |Duration of call in Auto Attendant     |
|AAChainIndex                            |string                   |                                       |
|AAConnectivityType                      |string                   |                                       |
|AACount                                 |int                      |Number of Auto Attendants involved in call    |
|AADirectorySearchMethod                 |string                   |Last address book search method -- possible values:<br><br>§ abs_search_dtmf<br>§ abs_search_extension<br>§ abs_search_name |
|AAStartTime                             |datetime                 |Auto Attendant call start time (UTC)   |
|AATransferAction                        |string                   |Call transfer target type -- possible values:<br><br>§ application - voice application entity<br>§ external_pstn - external PSTN entity<br>§ hunt_group - Call Queue entity<br>§ orgaa - Organizational Auto Attendant entity<br>§ shared_voicemail - shared voicemail entity<br>§ unknown - entity type was not specified<br>§ user - user entity |
|Call Type<sup>1</sup>                   |string                   |Type of call -- possible values:<br><br>§ External<br>§ Internal |
|IsAAInvolved                            |boolean                  |True if Auto Attendant involved        |
|PSTNMinutes                             |int                      |Total minute usage                     |
|TotalCallCount                          |int                      |Total number of calls                  |


### Cloud Call Queue Analytics

#### Report description

|Report Section                          |Description                                                        |
|:---------------------------------------|:------------------------------------------------------------------|
|Incoming call source<sup>1</sup>        |Distribution of call by Internal/External call source              |
|Call volume                             |Distribution of call by call queues                                |
|Caller result                           |Distribution of call by call result                                |
|Timeout/Overflow call total action      |Distribution of NOT forwarded(abandoned) call by call result       |
|Transfer/Forward target totals          |Distribution of call forwarded by call result                      |
|Abandoned calls ratio                   |Ratio of successful to abandoned call count                        |
|Average session length (seconds)        |Call length in seconds grouped by abandoned/successful calls       |

#### Report to CQD table and field mapping

|Report Tab         |Report Table Names                                                          |Global Filter |
|:------------------|:---------------------------------------------------------------------------|:-------------|
|Call Queue         |Dates<br>dCQ-CQIdenity<br>fCallQueueAnalytics<br>fCallQueueFinalStateAction |None          |
 
|Report Table Name            |Source Table Name            |Processing       |
|:----------------------------|:----------------------------|:----------------|
|Dates                        |Dates                        |None             |
|dCQ-CQIdentity               |CallQueueAnalytics           |Source = CallQueueAnalytics, <br>#"Removed Columns" = Table.RemoveColumns(Source,{"Call Count", "Call Queue Call Result", "Date", "PSTN Connectivity Type", "Call Queue Target Type", "PSTN Total Minutes"}),<br>Distinct = Table.Distinct(#"Removed Columns") |
|fCallQueueAnalytics          |CallQueueAnalytics           |None             |
|fCallQueueFinalStateAction   |CallQueueFinalStateAction    |None             |

|Report Section                      |Table -> Field(s) Used                |Filters Applied       |
|:-----------------------------------|:-------------------------------------|:---------------------|
|Date selector                       |Dates -> DateTime                     |None                  |
|Call Queue Identity                 |dCQ-CQIdentity -> Call Queue Identity |None                  |
|Incoming call source<sup>1</sup>    |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Type    |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal |
|Avg Waiting Time                    |fCallQueueFinalStateAction -> Average Call Duration (Seconds) |Before Transfer: Call Queue Call Result is agent_joined_conference or transferred_to_agent<br>Before Hang Up: Call Queue Call Result is not agent_joined_conference or transferred_to_agent |
|Call Result                         |fCallQueueAnalytics ->Call Count<br>fCallQueueAnalytics -> Call Queue Call Result | None |
|Timeout/Overflow calls total action |fCallQueueFinalStateAction -> Call Count<br>fCallQueueFinalStateAction -> Call Queue Final State Action |Call Queue Final State Action is not forward |
|Transfer/Forard target totals       |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Target Type |None |
|Call volumes                        |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Identify<br>fCallQueueAnalytics -> Date |None |
|Abandoned Calls                     |fCallQueueAnalytics -> %Abandoned Calls<br>fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Date<br>fCallQueueAnalytics -> IsAbandoned |IsAbandoned is True |
|Average Session Length (seconds)    |fCallQueueFinalStateAction -> Average Call Duration<br>fCallQueueFinalStateAction -> Date<br>fCallQueueFinalStateAction -> IsAbandoned |None |

#### dCQ-CQIdenity CQD fields description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|Call Queue Identity                     |string                   |Name of resource account attached to CQ<br>Example: aa_test@microsoft.com |

#### fCallQueueAnalytics CQD fields description

|Name                                    |Data Type                |Description                              |
|:---------------------------------------|:------------------------|:----------------------------------------|
|Call Count                              |int                      |                                         |
|Call Queue Call Result                  |string                   |Call queue call final state -- possible values:<br><br>§ agent_joined_conference<br>§ declined<br>§ error<br>§ failed<br>§ overflown<br>§ timed_out<br>§ transferred_to_agent |
|Call Queue Identity                     |string                   |Name of resource account attached to CQ<br>Example: aa_test@microsoft.com |
|Call Queue Target Type                  |string                   |Expected call redirection target type    |
|Call Type<sup>1</sup>                   |string                   |Type of call -- possible values:<br><br>§ External<br>§ Internal |
|Date                                    |datetime                 |Call Queue call start time (UTC)         | 
|IsAbandoned                             |boolean                  |True if call is not answered by an agent |
|PSTN Connectivity Type                  |string                   |                                         |
|PSTN Total Minutes                      |int                      |Total minute usage                       |

#### fCallQueueAnalytics measures description

|Name                                    |Data Type                |Description                              |
|:---------------------------------------|:------------------------|:----------------------------------------|
|% Abandoned Calls                       |percentage               |Measure: TotalCallCount / Total Calls    |
|Total Calls                             |int                      |Measure:                                 |
|TotalCallCount                          |int                      |Measure: Sum(Call Count)                 |

#### fCallQueueFinalStateAction  CQD fields description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|Average Call Duration (Seconds)         |int                      |                                       |
|Call Count                              |int                      |                                       |
|Call Queue Call Result                  |string                   |Call queue call final state -- possible values:<br><br>§ agent_joined_conference<br>§ declined<br>§ error<br>§ failed<br>§ overflown<br>§ timed_out<br>§ transferred_to_agent |
|Call Queue Final State Action           |string                   |Call queue final action -- possible values:<br><br>§ disconnect<br>§ disconnect_with_busy<br>§ failed_to_accept_call<br>§ forward<br>§ shared_voicemail<br>§ other<br>§ voicemail |
|Call Queue Identity                     |string                   |Name of resource account attached to CQ<br>Example: aa_test@microsoft.com|
|Date                                    |datetime                 |                                       |
|IsAbandoned                             |boolean                  |True if call is abandoned while in queue |


### Cloud Call Queue Agent Timeline

#### Report description

|Report Section                                          |Description                                                  |
|:-------------------------------------------------------|:------------------------------------------------------------|
|# calls by agent                                        |Distribution of call by call queue and agent                 |
|Total call duration (seconds) by agent and Call Queue   |Total duration (seconds) of call by agent and call queue     |
|Average call duration (seconds) by agent name           |Average duration (seconds) of call by agent                  |

#### Report to CQD table and field mapping

|Report Tab         |Report Table Names        |Global Filter |
|:------------------|:-------------------------|:-------------|
|Agent Timeline     |fAgentTimelineAnalytics   |None          |
 
|Report Table Name            |Source Table Name            |Processing       |
|:----------------------------|:----------------------------|:----------------|
|fAgentTimelineAnalytics      |AgentTimelineAnalytics       |Source = AgentTimelineAnalytics, <br>#"Changed Type" = Table.TransformColumnTypes(Source,{{"Call Count", Int64.Type}, {"Call Duration (Minute)", Int64.Type}, {"Average Call Duration (Second)", type number}, {"Date", type date}})|

|Report Section                                |Field(s) Used                         |Filters Applied       |
|:---------------------------------------------|:-------------------------------------|:---------------------|
|Agent Name                                    |Agent Name                            |None                  |
|Call Queue Name                               |Call Queue Name                       |None                  |
|#Calls By Agent                               |Agent Name<br>Call Count<br>Date      |None                  |
|Distribution by Agent and Call Queue          |Agent Name<br>Call Count<br>Call Duration (Minutes)<br>Call Queue Name |None                      |
|Bottom Left                                   |Agent Name<br>Average Call Duration (Second)<br>Call Count<br>Call Duration (Minute)<br>Call Queue Name | None |
|Average Call Duration (Seconds) by Agent Name |Agent Name<br>Average Call Duration (Second)<br>Call Count<br>Call Duration (Minute)<br>Call Queue Name | None |

#### fAgentTimelineAnalytics CQD fields description

|Name                                    |Data Type                |Description                                         |
|:---------------------------------------|:------------------------|:---------------------------------------------------|
|Agent Name                              |string                   |User UPN                                            |
|Average Call Duration (Second)          |int                      |The average duration of call queue calls in seconds |
|Call Count                              |int                      |                                                    |
|Call Duration (Minute)                  |int                      |                                                    |
|Call Queue Name                         |string                   |                                                    |
|Date                                    |datetime                 |                                                    |


## Known Issues

- Call queue and auto attendants are shown by resource account's ID instead of call queue/auto attendant names.  To show all the traffic for an auto attendant or call queue you must select all the resource accounts assigned to the auto attendant or call queue.

- Only 28 days of history is available in the dashboard as call queue/auto attendant data is considered personal data and is subject to data privacy retention policies.

- <sup>1</sup> **Incoming call source** in the auto attendant and call queue graphs show the final call leg source rather than the initial call leg source. For example, if an auto attendant receives an external call and transfers the call to another auto attendant or call queue, the **Incoming call source** will be reported as Internal.
