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

|Key                                     |Feed              |Available To             |Description                                           |
|:---------------------------------------|:-----------------|:------------------------|:-----------------------------------------------------|
|tot_callers                             |Current & Summary |Authorized Users Only    |Total number of all accepted callers<br>A caller may pass through an Auto Attendant multiple times in a single call – they will only be counted once |
|tot_callers_int                         |Current & Summary |Authorized Users Only    |Total number of accepted internal callers             |
|tot_callers_ext                         |Current & Summary |Authorized Users Only    |Total number of accepted external callers             |
|tot_calls                               |Current & Summary	|Authorized	Users Only    |Total number of all accepted calls<br>A caller may pass through an Auto Attendant multiple times in a single call – each pass is counted |
|tot_calls_int                           |Current & Summary |Authorized	Users Only    |Total number of accepted internal calls               |
|tot_calls_ext                           |Current & Summary	|Authorized	Users Only    |Total number of accepted external calls               |
|tot_0_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 0 key menu option was selected by callers |
|tot_1_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 1 key menu option was selected by callers |
|tot_2_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 2 key menu option was selected by callers |
|tot_3_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 3 key menu option was selected by callers |
|tot_4_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 4 key menu option was selected by callers |
|tot_5_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 5 key menu option was selected by callers |
|tot_6_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 6 key menu option was selected by callers |
|tot_7_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 7 key menu option was selected by callers |
|tot_8_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 8 key menu option was selected by callers |
|tot_9_calls                             |Current & Summary	|Authorized	Users Only    |Total number of times the 9 key menu option was selected by callers |
|tot_star_calls                          |Current & Summary	|Authorized	Users Only    |Total number of times the * key menu option was selected by callers |
|tot_hash_calls                          |Current & Summary	|Authorized	Users Only    |Total number of times the # key menu option was selected by callers |
|tot_op_calls                            |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to the auto attendant operator |
|tot_app_calls                           |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to another voice application (auto attendant or call queue) |
|tot_extn_calls                          |Current & Summary |Authorized Users Only    |Total number of caller-initiated transfers to an external phone number |
|tot_psrn_calls                          |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to a Teams user |
|tot_vm_calls                            |Current & Summary	|Authorized	Users Only    |Total number of caller-initiated transfers to shared voicemail |
|tot_abandoned_calls                     |Current & Summary	|Authorized	Users Only    |Total number of user abandoned calls – caller doesn't select anything |
|tot_sysxfer_op_calls                    |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to the auto attendant operator |
|tot_sysxfer_app_calls                   |Current & Summary |Authorized	Users Only    |Total number of system-initiated transfers to another voice application (auto attendant or call queue) |
|tot_sysxfer_extn_calls                  |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to an external phone number |
|tot_sysxfer_psrn_calls                  |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to a Teams user |
|tot_sysxfer_vm_calls                    |Current & Summary	|Authorized	Users Only    |Total number of system-initiated transfers to shared voicemail |
|tot_sysdisconnected_calls               |Current & Summary	|Authorized	Users Only    |Total number of system-initiated disconnects |
|avg_call_time (Decimal – single digit)  |Current & Summary	|Authorized	Users Only    |Average amount of time calls spent in the auto attendant |
|avg_caller_actions (Decimal – single digit)	|Current & Summary |Authorized Users Only |Average number of caller actions in the auto attendant |

### Notes

- calls pegging more than once
- explain decimal numbers (if needed here)

## Call queue metrics
All metrics are whole numbers unless otherwise stated.

|Key                                     |Feed              |Available To             |Description                                           |
|:---------------------------------------|:-----------------|:------------------------|:-----------------------------------------------------|

