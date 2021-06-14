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

The account you use to view the AA & CQ Analytics historical report needs to have permissions to access the CQD data pipeline. Please refer to the [CQD access role](./turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd) for more information.

## Installation 

The following steps assume you have already installed Power BI Desktop on the computer and that your account has the necessary permissions to access the CQD data pipeline.

Please perform these steps:

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

    - The region will be displayed after the **/** like in the above example where there region is noam.

 - The report will launch with sample data.
 
 - To see your own data, please click **Refresh** in the Home tab under Queries in Power BI Desktop.

   :::image type="content" source="media/cqd-teams-aa-cq-historical-report-02.png" alt-text="Screenshot selecting the refresh option":::

- You will then be prompted to sign in. Select **Organization account** and then select **Sign in**.

  :::image type="content" source="media/cqd-teams-aa-cq-historical-report-03.png" alt-text="Screenshot showing login":::

- Select **Connect** and watch the data refresh.

## Data latency and AA & CQ analytics

Data will be available in the CQD data pipeline within 30 minutes.

You will have to refresh the data to see the new analytics data. 

## Customization 

You are able to customize certain visualization aspects of the reports, such as adding or removing fields to be shown in the various visualizations, changing chart type, etc.

You cannot add additional data fields other than the ones provided in the report.

### Change color schema 

The following steps assume you have already completed the Installation steps.

Please perform these steps:
- Select **View tab** on the ribbon.

  :::image type="content" source="media/cqd-teams-aa-cq-historical-report-04.png" alt-text="Screenshot selecting view tab to change color scheme":::

- Select the color schema from the drop-down list.

  :::image type="content" source="media/cqd-teams-aa-cq-historical-report-05.png" alt-text="Screenshot showing various color schemes":::
  
## Report name to CQD table and field mapping

### Cloud Auto Attendant Analytics

|Power BI Report Tab   |Report Table Name     |Global Filter                          |
|:---------------------|:---------------------|:--------------------------------------|
|Auto Attendant        |fAutoAttendant        |AAStartTime is within the last 28 days |
 
|Report Table Name            |Source Table Name            |Processing       |
|:----------------------------|:----------------------------|:----------------|
|fAutoAttedant                |AutoAttendant                |Source = AutoAttendant, <br>#"Filtered Rows" = Table.SelectRows(Source, each true), <br>#"Auto Attendant" = Table.AddColumn(#"Filtered Rows", "AA Name", each List.First(Text.Split([AAIdentity], "@"))), <br>#"Changed Type" = Table.TransformColumnTypes(#"Auto Attendant",{{"AAStartTime", type datetime}}), <br>#"Removed Columns" = Table.RemoveColumns(#"Changed Type",{"AAIdentity"}) |

|Report Section                                  |Field(s) Used                              |Filters Applied     |
|:-----------------------------------------------|:------------------------------------------|:-------------------|
|Auto Attedant (drop down - top right)           |AA Name         |                          |None                |
|Incoming call source                            |Call Type<br>TotalCallCount                |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal |
|Directory search method totals                  |AADirectorySearchMethod<br>TotalCallCount  |AADirectorySearchMethod is abs_search_dtmf or abs_search_name    |
|Caller actions                                  |AATransferAction<br>TotalCallCount         |None                                                             |
|Average Seconds in AA<br>Average Caller Actions |AAChainDuration<br>AACallerActionCount     |None                                                             |
|Call results                                    |AACallResult<br>TotalCallCount             |None                                                             |
|Caller actions count                            |AACallerActionCount<br>TotalCallCount      |None                                                             |
|Lower section of report                         |AA Name<br>AACallFlow<br>AACallResult<br>AAChainDuration<br>Call Type<br>TotalCallCount |None                |

#### CQD fields description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|AA Name                                 |string                   |Name of resource account attached to Auto Attendant<br><br>If the full Resource Account name is **aa_test@microsoft.com** then the value for AA Name will be **aa_test** |
|AACallerActionCount                     |int                      |Count of used action by caller         |
|AACallFlow                              |string                   |Encapsulates the different states of Auto Attendant Call<br><br>possible values:<br>§ abs_search<br>§ call_termination<br>§ call_transfer<br>§ main_menu<br>§ user_selection<br>§ speech_input_confirmation<br>§ first_level_menu<br>§ automatic_menu<br>§ announcement|
|AACallResult                            |string                   |Final call result<br><br>possible values:<br>§ unknown<br>§ transferred_to_user<br>§  transferred_to_operator<br>§ failover_to_operator<br>§ user_terminated<br>§ service_declined<br>§ service_terminated<br>§ failed_to_establish_media<br>§ terminated_no_operator<br>§ terminated_transfer_failed<br>§ terminated_automatic_selection<br>§ transferred_to_shared_voicemail<br>§ oaa_chain_too_long<br>§ oaa_session_too_long|
|AAChainDuration                         |int                      |Duration of call in AA                 |
|AAChainIndex                            |                         |                                       |
|AAConnectivityType                      |                         |                                       |
|AACount                                 |                         |                                       |
|AADirectorySearchMethod                 |string                   |Last Address book search method<br><br>possible values:<br>§ abs_search_dtmf<br>§  abs_search_name       |
|AAStartTime                             |datetime                 |AA chain start time                    |
|AATransferAction                        |string                   |Call transfer target type<br><br>possible values:<br>§ unknown - entity type was not specified<br>§ user - user entity<br>§ orgaa - Organizational Auto Attendant entity<br>§ hunt_group - Call Queue entity<br>§ application - voice application entity<br>§ external_pstn - external PSTN entity<br>§ shared_voicemail - shared voicemail entity|
|Call Type                               |                         |Type of call<br><br>possible values:<br>§ External<br>§ Internal                                       |
|IsAAInvolved                            |boolean                  |Indicated if AA involved into the call |
|PSTNMinutes                             |int                      |                                       |
|TotalCallCount                          |int                      |                                       |


### Cloud Call Queue Analytics

|Report Tab         |Report Table Names        |Global Filter                          |
|:------------------|:-------------------------|:--------------------------------------|
|Call Queue         |Dates<br>dCQ-CQIdenity<br>fCallQueueAnalytics<br>fCallQueueFinalStateAction |None |
 
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
|Incoming call soure                 |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Type    |External Calls: Call Type is External<br>Internal Calls: Call Type is Internal  |
|Avg Waiting Time|fCallQueueFinalStateAction -> Average Call Duration (Seconds) |Before Transfer: Call Queue Call Result is agent_joined_conference or transferred_to_agent<br>Before Hang Up: Call Queue Call Result is not agent_joined_conference or transferred_to_agent |
|Call Result                         |fCallQueueAnalytics ->Call Count<br>fCallQueueAnalytics -> Call Qeueue Call Result | None |
|Timeout/Overflow calls total action |fCallQueueFinalStateAction -> Call Count<br>fCallQueueFinalStateAction -> Call Queue Final State Action |Call Queue Final State Action is not forward |
|Transfer/Forard target totals       |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Target Type |None |
|Call volumes                        |fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Call Queue Identify<br>fCallQueueAnalytics -> Date |None |
|Abandoned Calls                     |fCallQueueAnalytics -> %Abandoned Calls<br>fCallQueueAnalytics -> Call Count<br>fCallQueueAnalytics -> Date<br>fCallQueueAnalytics -> IsAbandoned |IsAbandoned is True |
|Average Session Length (seconds)    |fCallQueueFinalStateAction -> Average Call Duration<br>fCallQueueFinalStateAction -> Date<br>fCallQueueFinalStateAction -> IsAbandoned |None |


### CQD fields description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|Call Queue Call Result                  |String                   |Call queue call final state<br>possible values:<br>§ error<br>§ declined<br>§ overflown<br>§ failed<br>§ timed_out<br>§ transferred_to_agent<br>§ agent_joined_conference|
|Call Queue Final State Action           |String                   |Call queue final action<br>possible values:<br>§ forward<br>§ disconnect<br>§ voicemail<br>§ disconnect_with_busy<br>§ shared_voicemail<br>§ failed_to_accept_call<br>§ other|
|Call Queue Identity                     |String                   |Name of resource account attached to CQ<br>Example: aa_test@microsoft.com|
|Call Queue Is Conference Mode           |Boolean                  |Set to 1 if conference mode enabled on CQ |
|Call Queue Target Type                  |String                   |Expected call redirection target type     |
|Transferred From Call Queue Identity    |Boolean                  |Name of resource account attached to CQ from which this call was transferred<br>Example: aa_test@microsoft.com|
|Call Queue Agent Opt In Count           |int                      |Count of agents available to this queue at the moment of call |
|Call Queue Agent Count                  |int                      |Count of agents assigned to this queue at the moment of call |
|Is Call Queue Involved                  |Boolean                  |If call queue is involved into to this call equal 1 |



## CQD fields description

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|Auto Attendant Identity                 |string                   |Name of resource account attached to AA<br>Example: aa_test@microsoft.com|
|Auto Attendant Chain Start Time         |datetime                 |AA chain start time                    |
|Auto Attendant Directory Search Method  |string                   |Last Address book search method        |
|Auto Attendant Transfer Action          |string                   |Call transfer target type<br>possible values:<br>§ unknown - entity type was not specified<br>§ user - user entity<br>§ orgaa - Organizational Auto Attendant entity<br>§ hunt_group - Call Queue entity<br>§ application - voice application entity<br>§ external_pstn - external PSTN entity<br>§ shared_voicemail - shared voicemail entity|
|Auto Attendant Call Result              |string                   |Call result:<br>§ unknown<br>§ transferred_to_user<br>§  transferred_to_operator<br>§ failover_to_operator<br>§ user_terminated<br>§ service_declined<br>§ service_terminated<br>§ failed_to_establish_media<br>§ terminated_no_operator<br>§ terminated_transfer_failed<br>§ terminated_automatic_selection<br>§ transferred_to_shared_voicemail<br>§ oaa_chain_too_long<br>§ oaa_session_too_long|
|Auto Attendant Call Flow                |string                   |Encapsulates the different states of Auto Attendant Call<br>§ abs_search<br>§ call_termination<br>§ call_transfer<br>§ main_menu<br>§ user_selection<br>§ speech_input_confirmation<br>§ first_level_menu<br>§ automatic_menu<br>§ announcement|
|Is Auto Attendant Involved              |Boolean                  |Indicated if AA involved into the call |
|Auto Attendant Caller Action Count      |int                      |Count of used action by caller         |
|Auto Attendant Chain Duration Seconds   |int                      |Duration of call in AA                 |
|Call Queue Call Result                  |String                   |Call queue call final state<br>possible values:<br>§ error<br>§ declined<br>§ overflown<br>§ failed<br>§ timed_out<br>§ transferred_to_agent<br>§ agent_joined_conference|
|Call Queue Final State Action           |String                   |Call queue final action<br>possible values:<br>§ forward<br>§ disconnect<br>§ voicemail<br>§ disconnect_with_busy<br>§ shared_voicemail<br>§ failed_to_accept_call<br>§ other|
|Call Queue Identity                     |String                   |Name of resource account attached to CQ<br>Example: aa_test@microsoft.com|
|Call Queue Is Conference Mode           |Boolean                  |Set to 1 if conference mode enabled on CQ |
|Call Queue Target Type                  |String                   |Expected call redirection target type     |
|Transferred From Call Queue Identity    |Boolean                  |Name of resource account attached to CQ from which this call was transferred<br>Example: aa_test@microsoft.com|
|Call Queue Agent Opt In Count           |int                      |Count of agents available to this queue at the moment of call |
|Call Queue Agent Count                  |int                      |Count of agents assigned to this queue at the moment of call |
|Is Call Queue Involved                  |Boolean                  |If call queue is involved into to this call equal 1 |


### Power BI data model dimensions

|Name                                    |Data Type                |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|AA Name	                               |string                   |Auto Attendant ID (resource account ID) |
|AACallFlow                              |string                   |Encapsulates the different states of Auto Attendant Call<br>§	abs_search<br>§	call_termination<br>§	call_transfer<br>§ main_menu<br>§	user_selection<br>§	speech_input_confirmation<br>§ first_level_menu<br>§ automatic_menu<br>§ announcement |
|AACallResult                            |string                   |Result of Auto Attendant Call:<br>§	unknown<br>§ transferred_to_user<br>§ transferred_to_operator<br>§ failover_to_operator<br>§ user_terminated<br>§ service_declined – error of AA configuration<br>§	service_terminated – internal AA errors<br>§ failed_to_establish_media<br>§ terminated_no_operator<br>§	terminated_transfer_failed<br>§	terminated_automatic_selection<br>§	transferred_to_shared_voicemail<br>§ oaa_chain_too_long<br>§ oaa_session_too_long          |
|AAChainDuration                         |string                   |Duration of Auto Attendant call in seconds  |
|AACount                                 |string                   |# of Auto Attendant involve in call         |
|AADirectorySearchMethod                 |string                   |Search method used in call:<br>§ abs_search_dtmf<br>§ abs_search_extension<br>§ abs_search_name<br>
|AAStartTime                             |string                   |Call time in UTC      |
|AATransferAction                        |string                   |Receiver of call:<br>§ unknown - entity type was not specified<br>§ user - user entity<br>§ AA - Organizational Auto Attendant entity<br>§ CQ - Call Queue entity<br>§ application - voice application entity<br>§ external_pstn - external PSTN entity<br>§ shared_voicemail - shared voicemail entity      |
|PSTNMinutes                             |int                      |Total minute usage                          |
|Call Queue Call Result                  |string                   |Call queue call final state<br>possible values:<br>§ error<br>§ declined<br>§ overflown<br>§ failed<br>§ timed_out<br>§ transferred_to_agent<br>§ agent_joined_conference    |
|Call Queue Identity                     |string                   |Name of resource account attached to CQ     |
|Call Queue Target Type                  |string                   |Expected call redirection target type:<br>§ User<br>§ Application Endpoint<br>§ Other     |
|Call Queue Call Result                  |string                   |Call queue call final state<br>possible values:<br>§ error<br>§ declined<br>§ overflown<br>§ failed<br>§ timed_out<br>§ transferred_to_agent<br>§ agent_joined_conference           |
|Call Queue Final State Action           |string                   |Call queue final action<br>possible values:<br>§ forward<br>§ disconnect<br>§ voicemail<br>§ disconnect_with_busy<br>§ shared_voicemail<br>§ failed_to_accept_call<br>§ other             |
|Agent Name                              |string                   |User UPN               |


### Measures

|Name	                                   |Type	                   |Description                            |
|:---------------------------------------|:------------------------|:--------------------------------------|
|AACallerActionCount                     |int	                     |# of action selected by user in AA during the call  |
|PSTNMinutes                             |int                      |Total minute usage                                  |
|TotalCallCount                          |int                      |# of calls                                          |
|Average Call Duration( Seconds)         |int                      |Total duration of call queue calls in seconds     |


### Power BI graph description Auto Attendant

|Name	                                   |Description                            |
|:---------------------------------------|:--------------------------------------|
|Incoming call source                    |Distribution of call by Internal/External call source<sup>1</sup>|
|Directory search method totals          |Distribution of call by search type                         |
|Caller action                           |Distribution of call by call receiver                       |
|Call result                             |Distribution of call by final call state                    |
|Caller action count                     |Distribution of call by number action used during the call  |


### Call Queue

|Name	                                   |Description                            |
|:---------------------------------------|:--------------------------------------|
|Incoming call source                    |Distribution of call by Internal/External call source<sup>1</sup>   |
|Call volume                             |Distribution of call by call queues                            |
|Caller result                           |Distribution of call by call result                            |
|Timeout/Overflow call total action      |Distribution of NOT forwarded(abandoned) call by call result   |
|Transfer/Forward target totals          |Distribution of call forwarded by call result                  |
|Abandoned calls ratio                   |Ratio of successful to abandoned call count                    |
|Average session length (seconds)        |Call length in seconds grouped by abandoned/successful calls   |



### Agent timeline

|Name	                                                   |Description                            |
|:-------------------------------------------------------|:--------------------------------------|
|# calls by agent                                        |Distribution of call by call queue and agent                 |
|Total call duration (seconds) by agent and Call Queue   |Total duration (seconds) of call by agent and call queue     |
|Average call duration (seconds) by agent name            |Average duration (seconds) of call by agent                  |



## Known Issues

- Call Queue and auto attendants are shown by resource account's ID instead of Call Queue/auto attendant names.  To show all the traffic for an auto attendant or Call Queue you must select all the resource accounts assigned to the auto attendant or Call Queue.

- Only 28 days of history is available in the dashboard as Call Queue/auto attendant data is considered end user identifiable information and is subject to data privacy retention policies.

- <sup>1</sup> **Incoming call source** in the auto attendant and Call Queue graphs show the final call leg source rather than the initial call leg source. For example, if an auto attendant receives an external call and transfers the call to another auto attendant or Call Queue, the **Incoming call source** will be reported as Internal.
