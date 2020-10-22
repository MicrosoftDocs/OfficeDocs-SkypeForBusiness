---
title: Using CQD Power BI report to view Auto Attendant & Call Queue Historical Report
ms.author: colongma
author: ColinLongman
manager: roykuntz
ms.reviewer: 
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
  - seo-marvel-apr2020
description: Learn about how to use Call Quality Dashboard Power BI report to view Auto Attendant & Call Queue Historical data.
---

# What are the Requirements? 
You need to have Power BI Desktop installed. You can install it from the [Microsoft Windows Store](https://aka.ms/pbidesktopstore)

You can use the free version of Power BI Desktop. Minimum compatible version is 2.85.681.0 (September 2020)

## Permissions to access the CQD pipeline
The account you use to view the AA & CQ Analytics historical report needs to have permissions to access the CQD data pipeline. Please refer to [CQD access role](https://docs.microsoft.com/microsoftteams/turning-on-and-using-call-quality-dashboard#assign-roles-for-accessing-cqd) for more information.

## Installation 
The following steps assume you have already installed Power BI Desktop on the computer and that your account has the necessary permissions to access the CQD data pipeline.

Please perform these steps:
- Download the [CQD Teams Auto Attendant & Call Queue Historical Report Template](https://aka.ms/TAPAACQAnalytics) and save it to a directory on your computer
- Double-click on the template and Power BI Desktop should launch
- You will be prompted to select the CQD data pipeline region. Select the region where your tenant is located.

:::image type="content" source="media/XXX.png" alt-text="Screenshot of the Call quality dashboard button in Teams admin center":::

 - You can see the region using the Skype for Business Online PS cmdlet (Get-CsTenant).ServiceInstance output. 
 The region will be displayed after the / like in this example microsoftcommunicationsonline/noam-4a-s7 where the region is noam
 - The report will launch with sample data
 - To see your own data please click Refresh in the Home tab under Queries in Power BI Desktop

:::image type="content" source="media/XXX.png" alt-text="Screenshot of the Call quality dashboard button in Teams admin center":::

- You will then be prompted to sign in. Select Organization account and click Sign in

:::image type="content" source="media/XXX.png" alt-text="Screenshot of the Call quality dashboard button in Teams admin center":::

- Click Connect and watch the data refresh

## Data latency Any AA & CQ analytics
Data will be available in the CQD data pipeline within 30 minutes.

You will have to refresh the data to see the new analytics data. 

## Customization 
You are able to customize certain visualization aspects of the reports, i.e. adding or removing fields to be shown in the various visualizations, changing chart type etc.

You cannot add additional data fields other than the ones provided in the report.

### Change color schema 
The following steps assume you have already completed Installation steps.

Please perform these steps:
- Select on ribbon View tab

:::image type="content" source="media/XXX.png" alt-text="Screenshot of the Call quality dashboard button in Teams admin center":::

- Select color schema from drop down list

:::image type="content" source="media/XXX.png" alt-text="Screenshot of the Call quality dashboard button in Teams admin center":::


## CQD Fields Description

|Name                                    |Data Type                |Description                            |
|----------------------------------------|:-------:                |:-------:                              |
|Auto Attendant Identity                 |string                   |Name of resource account attached to AA<br>Example: aa_test@microsoft.com|
|Auto Attendant Chain Start Time         |datetime                 |AA chain start time                    |
|Auto Attendant Directory Search Method  |string                   |Last Address book search method        |
|Auto Attendant Transfer Action          |string                   |Call transfer target type<br>Possible values:<br>§  unknown - entity type was not specified<br>§  user - user entity<br>§  orgaa - Organizational Auto Attendant entity<br>§  hunt_group - Call Queue entity<br>§  application - voice application entity<br>§  external_pstn - external PSTN entity<br>§  shared_voicemail - shared voicemail entity|
|Auto Attendant Call Result              |string                   |Call result:<br>§  unknown<br>§  transferred_to_user<br>§  transferred_to_operator<br>§  failover_to_operator<br>§  user_terminated<br>§  service_declined<br>§  service_terminated<br>§  failed_to_establish_media<br>§  terminated_no_operator<br>§  terminated_transfer_failed<br>§  terminated_automatic_selection<br>§  transferred_to_shared_voicemail<br>§  oaa_chain_too_long<br>§  oaa_session_too_long|
|Auto Attendant Call Flow                |string                   |Encapsulates the different states of Auto Attendant Call<br>§  abs_search<br>§  call_termination<br>§  call_transfer<br>§  main_menu<br>§  user_selection<br>§  speech_input_confirmation<br>§  first_level_menu<br>§  automatic_menu<br>§  announcement|
|Is Auto Attendant Involved              |Boolean                  |Indicated if AA involved into the call |
|Auto Attendant Caller Action Count      |Int                      |Count of used action by caller         |
|Auto Attendant Chain Duration Seconds   |Int                      |Duration of call in AA                 |
|Call Queue Call Result                  |String                   |Call queue call final state<br>possible values:<br>§  error<br>§  declined<br>§  overflown<br>§  failed<br>§  timed_out<br>§  transferred_to_agent<br>§  agent_joined_conference|
|Call Queue Final State Action           |String                   |Call queue final action<br>possible values:<br>§  forward<br>§  disconnect<br>§  voicemail<br>§  disconnect_with_busy<br>§  shared_voicemail<br>§  failed_to_accept_call<br>§  other|
|Call Queue Identity                     |String                   |Name of resource account attached to CQ<br>Example: aa_test@microsoft.com|
|Call Queue Is Conference Mode           |Boolean                  |Set to 1 if conference mode enabled on CQ |
|Call Queue Target Type                  |String                   |Expected call redirection target type     |
|Transferred From Call Queue Identity    |Boolean                  |Name of resource account attached to CQ from which this call was transferred<br>Example: aa_test@microsoft.com|
|Call Queue Agent Opt In Count           |Int                      |Count of agents available to this queue at the moment of call |
|Call Queue Agent Count                  |Int                      |count of agents assigned to this queue at the moment of call |
|Is Call Queue Involved                  |Boolean                  |If call queue is involved into to this call equal 1 |


### PowerBI data model Dimensions

### Measures

### PowerBI graph description Auto Attendant

### Call Queue

### Agent Timeline

## Known Issues
- Currently CQ and AA shows Resource accounts Id instead of CQ/AA names.  To show all the traffic for an Auto Attendant or Call Queue you must select all the Resource Accounts assigned to the Auto Attendant or Call Queue.
- Currently only 28 days of history are available in the dashboard as CQ/AA data is considered End User Identifiable Information and is subject to data privacy retention policies
