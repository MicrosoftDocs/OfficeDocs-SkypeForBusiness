---
title: Auto attendant and Call queue real-time reports
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 09/16/2024
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
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
description: Learn about the real-time metrics that are available for Auto attendants and Call queues.
---

# Auto attendant and Call queue real-time metrics

> [!IMPORTANT]
> Only some of the metrics outlined here are currently available to Queues app users.
>
> For more information about Queues app, see [Manage the Queues app](manage-queues-app.md). For user documentation about Queues app, see [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9).

## Auto attendant metrics

The following table contains real-time Auto attendant metrics. All metrics are whole numbers unless otherwise stated.

|Key                         |Feed              |Available To             |Description                                                                                            |
|:---------------------------|:-----------------|:------------------------|:------------------------------------------------------------------------------------------------------|
|tot_callers                 |Current & Summary |Authorized Users Only    |Total number of all accepted callers<br><br>A caller may pass through an Auto attendant multiple times in a single call – this caller is only counted once |
|tot_callers_int             |Current & Summary |Authorized Users Only    |Total number of accepted internal callers                                                              |
|tot_callers_ext             |Current & Summary |Authorized Users Only    |Total number of accepted external callers                                                              |
|tot_calls                   |Current & Summary	|Authorized	Users Only    |Total number of all accepted calls<br><br>A caller may pass through an Auto attendant multiple times in a single call – each individual pass is counted |
|tot_calls_int               |Current & Summary |Authorized	Users Only    |Total number of accepted internal calls                                                                |
|tot_calls_ext               |Current & Summary	|Authorized	Users Only    |Total number of accepted external calls                                                                |
|tot_0_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the zero menu option                                            |
|tot_1_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the one menu option                                             |
|tot_2_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the two menu option                                             |
|tot_3_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the three menu option                                           |
|tot_4_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the four menu option                                            |
|tot_5_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the five menu option                                            |
|tot_6_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the six menu option                                             |
|tot_7_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the seven menu option                                           |
|tot_8_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the eight menu option                                           |
|tot_9_calls                 |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the nine menu option                                            |
|tot_star_calls              |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the star (*) menu option                                        |
|tot_hash_calls              |Current & Summary	|Authorized	Users Only    |Total number of times callers selected the hash (#) menu option                                        |
|tot_op_calls                |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to the auto attendant operator                              |
|tot_app_calls               |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to another voice application (Auto attendant or Call queue) |
|tot_extn_calls              |Current & Summary |Authorized Users Only    |Total number of caller-initiated transfers to an external phone number                                 |
|tot_psrn_calls              |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to a Teams user                                             |
|tot_vm_calls                |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to shared voicemail                                         |
|tot_abandoned_calls         |Current & Summary	|Authorized	Users Only    |Total number of user abandoned calls – caller doesn't select anything                                  |
|tot_sysxfer_op_calls        |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to the auto attendant operator                              |
|tot_sysxfer_app_calls       |Current & Summary |Authorized	Users Only    |Total number of system-initiated transfers to another voice application (Auto attendant or Call queue) |
|tot_sysxfer_extn_calls      |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to an external phone number                                 |
|tot_sysxfer_psrn_calls      |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to a Teams user                                             |
|tot_sysxfer_vm_calls        |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to shared voicemail                                         |
|tot_sysdisconnected_calls   |Current & Summary	|Authorized	Users Only    |Total number of system-initiated disconnects                                                           |
|avg_call_time               |Current & Summary	|Authorized	Users Only    |Average amount of time calls spent in the auto attendant (*Single-digit decimal*)                      |
|avg_caller_actions          |Current & Summary |Authorized Users Only |Average number of caller actions in the auto attendant (*Single-digit decimal*)                           |


## Call queue metrics

The following table contains real-time Call queue metrics. All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                                                                |
|:---------------------------------------|:-----------------|:------------------------|:------------------------------------------------------------------------------------------|
|abandoned_%                             |Current	          |Authorized Users & Agents|Abandoned percentage (*Three-digit decimal*)<br><br>`(tot_abandoned_calls / tot_offered_calls)`   |
|calls_waiting	                         |Current	          |Authorized Users & Agents|Number of calls currently waiting                                                          |
|calls_waiting_longest	                 |Current	          |Authorized Users & Agents|Longest wait time, in seconds, of oldest call in queue<br><br>Note: To be deprecated.        |
|longest_waiting_call_enqueue_time       |Current	          |Authorized Users & Agents|Timestamp of arrival time for longest waiting call<br><br>Offset by UTC offset if supplied during registration.<br><br>Format: `2024-03-19T11:55:09.9887885+00:00` |
|tot_offered_calls                       |Current & Summary	|Authorized Users & Agents|Total number of accepted calls                                                             |
|tot_answered_calls	                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls answered by agents                                          |
|tot_timeout_calls	                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that received the timeout treatment                         |
|tot_overflowed_calls                    |Current & Summary	|Authorized Users & Agents|	Total number of rejected calls that received the overflow treatment                       |
|tot_noagent_calls                       |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that received the no-agents treatment                       |
|tot_abandoned_calls                     |Current & Summary	|Authorized Users & Agents|Total number of accepted calls that abandoned                                              |
|avg_speed_answer                        |Current & Summary	|Authorized Users & Agents|	Average speed of answer<br><br>`(total wait time of answered calls / total answered calls)`       |
|tot_agent_presents                      |Current & Summary	|Authorized Users & Agents|Total number of presented but not answered calls                                           |
|sl_target                               |Current & Summary	|Authorized Users & Agents|Service level target number of seconds<br>See [Service Level Notes](#service-level-notes)<br><br> **null if not set** |
|sl_tot_answered_calls                   |Current & Summary |Authorized Users & Agents|Total number of calls answered within the service level target<br><br>**null if sl_target is null**  |
|sl_tot_abandoned_calls                  |Current & Summary |Authorized Users & Agents|Total number of calls that abandoned within the service level target<br><br>**null if sl_target is null**  |
|sl_met_handled                        	 |Current & Summary |Authorized Users & Agents|Percentage of answered  calls answered that met the service level target (*Two-digit decimal*)<br><br>`(sl_tot_answered_calls / tot_answered_calls)`<br><br>**null if sl_target is null** |
|sl_met_no_abandon                      	|Current & Summary |Authorized Users & Agents|Percentage of answered/abandoned calls that met the service level target (*Two-digit decimal*) - abandoned calls within service level target don't impact service level percentage<br><br>`(sl_tot_answered_calls / [tot_offered_calls – sl_tot_abandoned_calls])`<br><br>**null if sl_target is null** |
|sl_met_positive_abandon                  | Current & Summary |Authorized Users & Agents|Percentage of calls answered/abandoned that met service level target (*Two-digit decimal*) - abandoned calls within service level target positively impact service level percentage<br><br>`([sl_tot_answered_calls + sl_tot_abandoned_calls] / tot_offered_calls`<br><br>**null if sl_target is null** |
|sl_met_negative_abandon                 	|Current & Summary |Authorized Users & Agents|Percentage of calls answered/abandoned that met service level target (*Two-digit decimal*) - abandoned calls within service level target negatively impact service level percentage<br><br>`(sl_tot_answered_calls / tot_offered_calls)`<br><br>**null if sl_target is null** |

## Agent by queue metrics

The following table contains real-time agent metrics. All metrics are whole numbers unless otherwise stated.

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
- [Manage the Queues app](manage-queues-app.md)
- [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9)
- [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)
