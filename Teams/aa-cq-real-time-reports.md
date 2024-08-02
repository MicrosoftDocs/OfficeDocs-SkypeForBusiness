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
> Only some of the metrics outlined below are currently available to Queues app users.
>
> Please see {insert Queues app link} for information on how and where these metrics are shown within Queues app.

## Feeds

describe feeds here

## Auto attendant metrics
All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                                               |
|:---------------------------------------|:-----------------|:------------------------|:-------------------------------------------------------------------------|
|tot_callers                             |Current & Summary |Authorized Users Only    |Total number of all accepted callers<br>A caller may pass through an Auto Attendant multiple times in a single call – they will only be counted once |
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
|avg_call_time (Decimal – single digit)  |Current & Summary	|Authorized	Users Only    |Average amount of time calls spent in the auto attendant                  |
|avg_caller_actions (Decimal – single digit)	|Current & Summary |Authorized Users Only |Average number of caller actions in the auto attendant                  |

### Notes

- calls pegging more than once
- explain decimal numbers (if needed here)

## Call queue metrics
All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                           |
|:---------------------------------------|:-----------------|:------------------------|:-----------------------------------------------------|
|abandoned_% (Decimal – 3 digits)	       |Current	          |Authorized Users & Agents|Abandoned percentage<br>|tot_abandoned_calls / tot_offered_calls  |
|calls_waiting	                         |Current	          |Authorized Users & Agents|Number of calls currently waiting                                 |
|calls_waiting_longest	                 |Current	          |Authorized Users & Agents|Longest wait time, in seconds, of oldest call in queue<br>Note: To be deprecated |
|longest_waiting_call_enqueue_time       |Current	          |Authorized Users & Agents|Timestamp of arrival time for longest waiting call<br>Offset by UTC offset if supplied during registration.<br>Format: "2024-03-19T11:55:09.9887885+00:00” |
|tot_offered_calls                       |Current & Summary	|Authorized Users & Agents|Total number of accepted calls |
|tot_answered_calls	                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls answered by agents |
|tot_timeout_calls	                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that received the timeout treatment |
|tot_overflowed_calls                    |Current & Summary	|Authorized Users & Agents|	Total number of rejected calls that received the overflow treatment |
|tot_noagent_calls                       |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that received the no-agents treatment |
|tot_abandoned_calls                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that abandoned  |
|avg_speed_answer                        |Current & Summary	|Authorized Users & Agents|	Average speed of answer<br>total wait time of answered calls / total answered calls |
|tot_agent_presents                      |Current & Summary	|Authorized Users & Agents|Total number of presented but not answered calls |
|sl_target (null if not set)             |Current & Summary	|Authorized Users & Agents|Service level target number of seconds<br>See Service Level Notes below |
|sl_tot_answered_calls (null if sl_target is null)	|Current & Summary |Authorized Users & Agents|Total number of calls answered within the service level target |
|sl_tot_abandoned_calls (null if sl_target is null)	|Current & Summary |Authorized Users & Agents|Total number of calls that abandoned within the service level target |
|sl_met_handled (Decimal- two digits) (null if sl_target is null)	|Current & Summary |Authorized Users & Agents|Percentage of answered  calls answered that met the service level target<br>(sl_tot_answered_calls / tot_answered_calls) |
|sl_met_no_abandon (Decimal – two digits) (null if sl_target is null)	|Current & Summary |Authorized Users & Agents|Percentage of answered/abandoned calls that met the service level target - abandoned calls within service level target do not impact service level percentage<br>(sl_tot_answered_calls / [tot_offered_calls – sl_tot_abandoned_calls  ]) |
|sl_met_positive_abandon (Decimal – two digits) (null if sl_target is null) | Current & Summary |Authorized Users & Agents|Percentage of calls answered/abandoned that met service level target - abandoned calls within service level target positively impact service level percentage<br>([sl_tot_answered_calls + sl_tot_abandoned_calls] / tot_offered_calls) |
|sl_met_negative_abandon (Decimal – two digits) (null if sl_target is null)	|Current & Summary |Authorized Users & Agents|Percentage of calls answered/abandoned that met service level target - abandoned calls within service level target negatively impact service level percentage<br>(sl_tot_answered_calls / tot_offered_calls) |

### Service Level Notes

Changes to the service level target threshold are processed as follows:

Current Feed:
- Changes will be reflected in the current feed with the next call answered / call abandoned event
- Previous calls that have have been answered by an agent or abandoned will not be re-evaluated against the new service level target

Summary Feed (non-aggregated):
- The last service level target of the current interval will be used as the value for that interval in the summary feed
- Previous calls in earlier intervals that have been answered by an agent or abandoned will not be re-evaluated against the new service level target

Summary Feed (aggregated):
- The service level target of the most recent summary interval will be sent.
- Previous calls in earlier intervals that have been answered by an agent or abandoned will not be re-evaluated agent the new service level target

## Agent metrics
All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                           |
|:---------------------------------------|:-----------------|:------------------------|:-----------------------------------------------------|
