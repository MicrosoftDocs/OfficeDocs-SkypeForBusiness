---
title: Auto attendant and Call queue real-time reports
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 06/10/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
  - ContentFreshnessFY24
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
description: Learn about the real-time metrics that are available
---

# Auto attendant and Call queue real-time metrics

> [!IMPORTANT]
> Only some of the metrics outlined here are currently available to Queues app users.
>
> Please see {insert Queues app link} for information on how and where these metrics are shown within Queues app.

## Feeds & Intervals

### Feeds
When a client registers for real-time data, there are two feeds of metrics that the client immediately receives:

1. Current feeds
   The current feed contains the metrics for the current interval the client is registered for.

   The client receives an updated current feed throughout the interval as calls arrive, are answered, transferred, or abandoned.

   At the end of the current interval, most of the metrics from the current feed are moved to the summary feed and the current feed metrics are reset to zero.
   
1. Summary feeds
   The summary feed contains the metrics for the past 24 hours UTC or since midnight local time of the client, depending on what the client registered for.

   The metrics are broken down by interval or aggregated depending on what the client registered for.

   The client will receive an updated summary feed shortly after each interval ends.

It's the client's responsibility to add the current and summary feeds to get the totals for the time period to be displayed.

### Intervals
- Clients may register for a 15, 30 or 60-minute interval.
- Clients in time zones that are X hours and 0 minutes off of UTC should register for the 60-minute interval.
- Clients in time zones that are X hours and 30 minutes off of UTC should register for the 30-minute interval.
- Clients in time zones that are X hours and 45 minutes off of UTC should register for the 15-minute interval.

## Queues app
Queues app automatically registers for the interval that matches the computer's time zone offset.

Queues app also registers to receive an aggregated summary feed since midnight local time of the client.

## Auto attendant metrics
All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                                               |
|:---------------------------------------|:-----------------|:------------------------|:-------------------------------------------------------------------------|
|tot_callers                             |Current & Summary |Authorized Users Only    |Total number of all accepted callers<br>A caller may pass through an Auto Attendant multiple times in a single call – they are only counted once |
|tot_callers_int                         |Current & Summary |Authorized Users Only    |Total number of accepted internal callers                                 |
|tot_callers_ext                         |Current & Summary |Authorized Users Only    |Total number of accepted external callers                                 |
|tot_calls                               |Current & Summary	|Authorized	Users Only    |Total number of all accepted calls<br>A caller may pass through an Auto Attendant multiple times in a single call – each pass is counted |
|tot_calls_int                           |Current & Summary |Authorized	Users Only    |Total number of accepted internal calls                                   |
|tot_calls_ext                           |Current & Summary	|Authorized	Users Only    |Total number of accepted external calls                                   |
|tot_0_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the zero menu option               |
|tot_1_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the one menu option                |
|tot_2_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the two menu option                |
|tot_3_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the three menu option              |
|tot_4_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the four menu option               |
|tot_5_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the five menu option               |
|tot_6_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the six menu option                |
|tot_7_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the seven menu option              |
|tot_8_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the eight menu option              |
|tot_9_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the nine menu option               |
|tot_star_calls                          |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the star (*) menu option           |
|tot_hash_calls                          |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the hash (#) menu option           |
|tot_op_calls                            |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to the auto attendant operator |
|tot_app_calls                           |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to another voice application (auto attendant or call queue) |
|tot_extn_calls                          |Current & Summary |Authorized Users Only    |Total number of caller-initiated transfers to an external phone number    |
|tot_psrn_calls                          |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to a Teams user                |
|tot_vm_calls                            |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to shared voicemail            |
|tot_abandoned_calls                     |Current & Summary	|Authorized	Users Only    |Total number of user abandoned calls – caller doesn't select anything     |
|tot_sysxfer_op_calls                    |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to the auto attendant operator |
|tot_sysxfer_app_calls                   |Current & Summary |Authorized	Users Only    |Total number of system-initiated transfers to another voice application (auto attendant or call queue) |
|tot_sysxfer_extn_calls                  |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to an external phone number    |
|tot_sysxfer_psrn_calls                  |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to a Teams user                |
|tot_sysxfer_vm_calls                    |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to shared voicemail            |
|tot_sysdisconnected_calls               |Current & Summary	|Authorized	Users Only    |Total number of system-initiated disconnects                              |
|avg_call_time<br>Decimal–single digit   |Current & Summary	|Authorized	Users Only    |Average amount of time calls spent in the auto attendant                  |
|avg_caller_actions<br>Decimal–single digit	|Current & Summary |Authorized Users Only |Average number of caller actions in the auto attendant                    |


## Call queue metrics
All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                                                                |
|:---------------------------------------|:-----------------|:------------------------|:------------------------------------------------------------------------------------------|
|abandoned_%<br>Decimal–3 digits         |Current	          |Authorized Users & Agents|Abandoned percentage<br>tot_abandoned_calls / tot_offered_calls                            |
|calls_waiting	                         |Current	          |Authorized Users & Agents|Number of calls currently waiting                                                          |
|calls_waiting_longest	                 |Current	          |Authorized Users & Agents|Longest wait time, in seconds, of oldest call in queue<br>Note: To be deprecated           |
|longest_waiting_call_enqueue_time       |Current	          |Authorized Users & Agents|Timestamp of arrival time for longest waiting call<br>Offset by UTC offset if supplied during registration.<br>Format: "2024-03-19T11:55:09.9887885+00:00” |
|tot_offered_calls                       |Current & Summary	|Authorized Users & Agents|Total number of accepted calls                                                             |
|tot_answered_calls	                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls answered by agents                                          |
|tot_timeout_calls	                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that received the timeout treatment                         |
|tot_overflowed_calls                    |Current & Summary	|Authorized Users & Agents|	Total number of rejected calls that received the overflow treatment                       |
|tot_noagent_calls                       |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that received the no-agents treatment                       |
|tot_abandoned_calls                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that abandoned                                              |
|avg_speed_answer                        |Current & Summary	|Authorized Users & Agents|	Average speed of answer<br>total wait time of answered calls / total answered calls       |
|tot_agent_presents                      |Current & Summary	|Authorized Users & Agents|Total number of presented but not answered calls                                           |
|sl_target<br>null if not set            |Current & Summary	|Authorized Users & Agents|Service level target number of seconds<br>See [Service Level Notes](#service-level-notes)  |
|sl_tot_answered_calls<br>null if sl_target is null	|Current & Summary |Authorized Users & Agents|Total number of calls answered within the service level target                  |
|sl_tot_abandoned_calls<br>null if sl_target is null|Current & Summary |Authorized Users & Agents|Total number of calls that abandoned within the service level target            |
|sl_met_handled<br>Decimal-two digits<br>null if sl_target is null	|Current & Summary |Authorized Users & Agents|Percentage of answered  calls answered that met the service level target<br>(sl_tot_answered_calls / tot_answered_calls) |
|sl_met_no_abandon<br>Decimal-two digits<br>null if sl_target is null	|Current & Summary |Authorized Users & Agents|Percentage of answered/abandoned calls that met the service level target - abandoned calls within service level target don't impact service level percentage<br>(sl_tot_answered_calls / [tot_offered_calls – sl_tot_abandoned_calls]) |
|sl_met_positive_abandon<br>Decimal-two digits<br>null if sl_target is null | Current & Summary |Authorized Users & Agents|Percentage of calls answered/abandoned that met service level target - abandoned calls within service level target positively impact service level percentage<br>([sl_tot_answered_calls + sl_tot_abandoned_calls] / tot_offered_calls) |
|sl_met_negative_abandon<br>Decimal-two digits<br>null if sl_target is null)	|Current & Summary |Authorized Users & Agents|Percentage of calls answered/abandoned that met service level target - abandoned calls within service level target negatively impact service level percentage<br>(sl_tot_answered_calls / tot_offered_calls) |

### Service Level Notes

Changes to the service level target threshold are processed as follows:

Current Feed:
- Changes will be reflected in the current feed with the next call answered or call abandoned event.
- Previous call results and service level calculations in the current feed aren't reevaluated against the new service level target.

Summary Feed (nonaggregated):
- The last service level target of the current interval is used as the value for that interval in the summary feed.
- Previous call results and service level calculations in the summary feed intervals aren't reevaluated against the new service level target.

Summary Feed (aggregated):
- The service level target of the most recent summary interval is sent.
- The service level target of the most recent summary interval is used to calculate the service level for the aggregated totals.
- Previous call results and service level calculations in the summary feed aren't reevaluated agent the new service level target.

## Agent by queue metrics
All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                                       |
|:---------------------------------------|:-----------------|:------------------------|:-----------------------------------------------------------------|
|tot_calls_offered                       |Current & Summary |Authorized Users<sup>1</sup> & Agents<sup>2</sup>|Total number of calls offered to the agent.                       |
|tot_calls_answered                      |Current & Summary |Authorized Users<sup>1</sup> & Agents<sup>2</sup>|Total number of calls answered by the agent.                      |

### Notes
1. Authorized Users: for all agents in the queue
1. Agents: for self only – not for all other agents in the queue

## Related articles
- [Auto attendant and Call queue historical reports](aa-cq-cqd-historical-reports.md).
- [Plan for authorized users](aa-cq-authorized-users-plan.md)

