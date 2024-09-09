---
title: Create a Call queue in Microsoft Teams
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 05/20/2024
ms.topic: article
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - tier1
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
description: Learn how to set up Call queues in Microsoft Teams. Call queues provide a greeting message, hold music, call redirecting, and other features.
---

# Create a Call queue in Microsoft Teams

Call queues route callers to people in your organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue, who are known as *agents*.

Call queues provide:

- A greeting message.
- Music while people are waiting on hold in a queue.
- Call routing - in *First In, First Out* (FIFO) order - to agents.
- Handling options for queue overflow and timeout.

Before you follow the procedures in this article, be sure you have read [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md) and followed the [getting started steps](plan-auto-attendant-call-queue.md#getting-started).

## What's new for Call queues in the past six months

- September 16
  - [Callback](#callback) functionality available through PowerShell cmdlets
  - Conference mode is now supported for Skype for Business clients and calls that are routed to the queue from Skype for Business Server
- April 8 - Additional messaging options for call queue Overflow, Timeout, and No Agents exception routing in Teams admin center and [PowerShell cmdlets](#additional-messaging)

## Steps to create a Call queue

The steps to set up a Call queue includes:

1. Set up general information
1. Set the greeting and music
1. Set up call answering
1. Choose and assign agents
1. Set up call exception handling
1. Set up authorized users

The steps outlined in the article create Call queues using the Teams admin center. For instructions to create Call queues using PowerShell, see [Creating Call queues with PowerShell cmdlets](create-a-phone-system-call-queue-via-cmdlets.md).

## Follow these steps to set up your Call queue

## [Step 1: General info](#tab/general-info)

## Step 1: Set up general information

To set up a Call queue, in the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), expand **Voice**, select **Call queues**, and then select **Add**.

Type a name for the Call queue in the box at the top.

### Add an existing resource account

Before you can create and manage resource accounts, you must do the following:

- [Obtain Microsoft Teams Phone Resource Account licenses](manage-resource-accounts.md#obtain-microsoft-teams-phone-resource-account-licenses)
- [Obtain phone numbers](manage-resource-accounts.md#obtain-phone-numbers)
- [Assign permissions for managing a resource account](manage-resource-accounts.md#assign-permissions-for-managing-a-resource-account)

All Call queues must have an associated resource account. All resource accounts must be assigned a [Microsoft Teams Phone Resource Account license](teams-add-on-licensing/virtual-user.md). If you wish, you can assign several resource accounts to a Call queue.

For details on how to create resource accounts and ready them for use with auto attendants, see [Manage Teams resource accounts](manage-resource-accounts.md).

Agents see the resource account name when they receive an incoming call.

### Assign a calling ID (optional)

**Available for Teams channel/collaborative calling desktop users and Teams mobile client users with standard Call queues.**

Assign outbound caller ID numbers for the agents by specifying one or more resource accounts with a phone number. Agents can select which outbound caller ID number to use with each outbound call they make. Within the Calls App, agents can use their Call Queue (CQ) / Auto Attendant (AA) number or their own personal Direct InWard Dial (DID).

> [!NOTE]
> The resource account used for calling ID purposes must have a **Microsoft Teams Phone Resource Account** license and one of the following assigned:
>
> - A Calling Plan license and a phone number assigned
> - An Operator Connect phone number assigned
> - An online voice routing policy (phone number assignment is optional when using Direct Routing)

1. Under **Assign calling ID**, select the **Add** button.
1. On the **Add accounts** pane, search for one or more resource accounts you want to allow agents to use for outbound caller ID purposes.
1. Select the **Add** button next to the resource account with an assigned phone number.
1. Select the **Add** button at the bottom of the pane.

If you don't have a resource account with an assigned phone number, you must create a resource account. For more information, see [Create a Teams resource accounts](manage-resource-accounts.md#create-a-resource-account).

After you create this new resource account for calling ID, you still need to:

- Assign a [Microsoft Teams Phone Resource Account license](manage-resource-accounts.md#assign-a-license).
- Assign a Microsoft Calling Plan license, assign an Operator Connect phone number, or assign an online voice routing policy for Direct Routing.
- Assign the [phone number to the resource account](manage-resource-accounts.md#assign-a-phone-number), if you're using Microsoft Calling Plan.

### Set the Service level threshold

_This feature is in public preview._

Service level measures the efficiency and responsiveness to incoming customer requests within a specific Service level threshold.

You can set the threshold target to any value from 0 to 40 minutes (2,400 seconds).  The value must be less than the value set for [Call timeout](#call-timeout-set-how-to-handle-call-timeouts). Setting the value to blank (empty) disables the service level metric calculation for the call queue.

>[!NOTE]
> Service level metrics are not currently available in Queues app.
> 
> Service level metrics are not currently available in historical reporting.

### Set the Call queue language

Choose a [supported language](create-a-phone-system-call-queue-languages.md).

This language is used for system-generated voice prompts and voicemail transcription, if you enable them.

After you select a language, select the **Next** button at the bottom of the **Add a Call queue** page.

## [Step 2: Greeting and music](#tab/greeting-music)

## Step 2: Add a greeting and on-hold music

Specify if you want to play a *greeting* to callers when they arrive in the queue.

- If you select **Play an audio file**, you must upload an MP3, WAV, or WMA file containing the greeting that you want to play. See [Supported audio file formats](plan-auto-attendant-call-queue.md#supported-audio-file-formats).
- If you select **Type a greeting message**, the system reads the text that you type (up to 1,000 characters) when the Call queue answers a call.

>[!NOTE]
> When using *Text to Speech*, the text must be entered in the selected language as the system doesn't perform translation.
>
> All words will be pronounced in the selected language.

Teams provides default music to callers while they're *on hold in a queue*.

- The default music supplied in Teams Call queues is free of any royalties payable by your organization.
- If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file. See [Supported audio file formats](plan-auto-attendant-call-queue.md#supported-audio-file-formats).

> [!NOTE]
> You are responsible for independently clearing and securing all necessary rights and permissions to use any music or audio file with your Microsoft Teams service, which may include intellectual property and other rights in any music, sound effects, audio, brands, names, and other content in the audio file from all relevant rights holders, which may include artists, actors, performers, musicians, songwriters, composers, record labels, music publishers, unions, guilds, rights societies, collective management organizations and any other parties who own, control or license the music copyrights, sound effects, audio and other intellectual property rights.

After you select a greeting and on-hold music, select the **Next** button at the bottom of the **Add a Call queue** page.

## [Step 3: Call answering](#tab/call-answering)

## Step 3: Set up who answers incoming calls

Review the [prerequisites for adding agents to a Call queue](plan-auto-attendant-call-queue.md#prerequisites).

### Teams channel

You can add up to 200 agents via a Teams channel. You must be a member of the team or the creator or owner of the channel to add a channel to the queue.

[Using a Teams channel to manage the queue](https://support.microsoft.com/office/9f07dabe-91c6-4a9b-a545-8ffdddd2504e):

1. Select the **Choose a team** radio button and select **Add a channel**.
1. Search for the team that you want to use, select it, and select **Add**.
1. Select the channel that you want to use (only standard channels are fully supported) and select **Apply**.

The following clients are supported when using a Teams channel for Call queues:

- Microsoft Teams Windows client
- Microsoft Teams Mac client

> [!NOTE]
> If you use this option, it can take up to 24 hours for the Call queue to be fully operational.
>
> If there are more than 200 members in the team, only the first 200 members, in alphabetical order, will be added as agents to the Call queue.

### Users and groups

You can add up to 20 agents individually and up to 200 agents via groups.

If you want to add individual users or groups to the queue:

1. Select the **Choose users and groups** radio button.

To **add a user** to the queue:

1. Select **Add users**, search for the user, select **Add**, and then select **Add**.

To **add a group** to the queue:

1. Select **Add groups**, search for the group, select **Add**, and then select **Add**.
    1. You can use distribution lists, security groups, and Microsoft 365 groups or Microsoft Teams teams.

> [!NOTE]
> New users added to a group can take up to eight hours for their first call to arrive.
>
> If there are more than 200 members in the group, only the first 200 members, in alphabetical order, will be added as agents to the Call queue.

> [!IMPORTANT]
> Known issue: Assigning private channels to Call queues
>
> When using a private channel calls will be distributed to all members of the team even if the private channel only has a subset of team members.
>
> You may experience this problem when trying to assign a private channel to a Call queue. This problem may occur even if the Call queue previously had a private channel assigned or if the private channel was previously assigned to a Call queue.
>
> If you already have private channels assigned to Call queue they will continue to work. This problem only affects new assignments.
>
> Support continues to work on identifying the root cause of this problem.

### Conference mode

**Conference mode** reduces the amount of time it takes for a caller to be connected to an agent after the agent accepts the call. 
  
Agents' Teams accounts must be set to TeamsOnly mode. Agents who don't meet the requirements aren't included in the call routing list.

> [!TIP]
> Setting **Conference mode** to **On** is the recommended setting.

Once you select your call answering options, select the **Next** button at the bottom of the **Add a Call queue** page.

> [!NOTE]
> Conference mode isn't supported for calls that are routed to the queue from a Direct Routing gateway that's enabled for Location Based Routing.
>
> Conference mode is required if Teams users need to consult/transfer calls with Call queues.
>
> Agents may hear the configured music on hold in queue for up to 2 seconds when first joining the call.

> [!IMPORTANT]
> Transfer mode (when conference mode is disabled) is now in legacy mode.  Support for transfer mode is scheduled to be removed by the end of June 2025.

## [Step 4: Agent selection](#tab/agent-selection)

## Step 4: Select your agent routing options

> [!NOTE]
> When using **Longest idle** and when there are less calls in queue than available agents, only the first two longest idle agents will be presented with calls from the queue.
>
> When using **Longest idle**, there may be times when an agent receives a call from the queue shortly after becoming unavailable, or a short delay in receiving a call from the queue after becoming available.
>
> Call Queue call presentation to agents may conflict with Location Based Routing restrictions. In this case, the agent will receive a call toast but can't answer the call. This condition will continue until another agent is available to answer the call, the caller hangs up, or the Call queue timeout condition occurs.

**Routing method** determines the order in which agents receive calls from the queue.

Choose from these options:

- **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

- **Serial routing** rings all call agents one by one in the order specified in the **Call agents** list. If an agent dismisses or doesn't pick up a call, the call will ring the next agent. This cycle repeats until the call is answered, times out, or the caller hangs up.

- **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue.

- **Longest idle** routes each call to the agent who has been idle the longest. An agent is considered idle if their presence state is *Available*. Agents who aren't available don't receive calls until they change their presence to *Available*.

> [!TIP]
> Setting the **Routing Method** to **Round robin** or **Longest idle** is the recommended setting.

### Presence-based call routing

**Presence-based call routing** uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method.

Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and can't receive calls until their availability status changes back to **Available**.

You can enable **presence-based call routing** with any of the routing methods.

If an agent opts out of getting calls, they can't receive calls regardless of their availability status.

> [!TIP]
> Setting the **Presence-based routing** to **on** is the recommended setting.

> [!NOTE]
> When **Longest idle** is selected as the routing method, presence-based routing is required and automatically enabled even though the Presence-based routing toggle will be **Off** and grayed out.
>
> If presence-based routing isn't enabled and there are multiple calls in the queue, the system will present these calls simultaneously to the agents regardless of their presence status. This action will result in multiple call notifications to agents, particularly if some agents don’t answer the initial call presented to them.
>
> When using **Presence-based routing**, there may be times when an agent receives a call from the queue shortly after becoming unavailable or a short delay in receiving a call from the queue after becoming available.
>
> Agents who use the Skype for Business client aren't included in the call routing list when presence-based routing is enabled. If you have agents who use Skype for Business, don't enable presence-based call routing.

### Call agents can opt out of taking calls

You can specify whether call agents have the ability to opt out of taking calls or not.

We recommend turning on **Call agents can opt out of taking calls**.

### Agent alert time

**Agent alert time** specifies how long an agent's phone will ring before the queue redirects the call to the next agent.

> [!TIP]
> Setting the **Agent alert time** to a minimum **20 seconds** is the recommended setting.

Once you select your agent call routing options, select the **Next** button at the bottom of the **Add a Call queue** page.

## [Step 5: Exception Handling](#tab/call-exception-handling)

## Step 5: Exception handling

**Exception handling** determines how calls are handled when certain exceptions occur.

Each exception allows you to **disconnect** the call or **redirect** it to any of the call routing destinations.

For example, when **Overflow** occurs, you might send calls to a backup Call queue, but when **Timeout** or **No Agents** occurs, you might want the callers to leave a shared voicemail.

> [!NOTE]
> For external transfers, see [Prerequisites](./plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](./create-a-phone-system-auto-attendant.md?tabs=general-info#external-phone-number-transfers---technical-details) for number formatting.
> 
> Don't include any special characters in the greeting message when redirecting to **Voicemail (shared)**.
> 
> The Overflow, Call timeout and No Agents exception redirect options for **Person in organization** and **Voicemail personal** support additional prompting. For more information, see [Additional messaging](#additional-messaging)

### Overflow: Set how to handle call overflow

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time.

The default is 50, but it can range from 0 to 200.

When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

This limit applies only to calls that are waiting in queue to be answered.

> [!NOTE]
> If the maximum number of calls is set to 0, the greeting message can't play.

### Call timeout: Set how to handle call timeouts

**Call Timeout: maximum wait time** specifies the maximum time a call can be on hold in the queue before it's redirected or disconnected.

You can specify a value from 0 seconds to 45 minutes.

### No Agents Opted/Logged In: Set how to handle calls when no agents are opted/logged into the queue

This call exception handling option handles calls when no agents are opted into the queue or all agents are logged out of the queue.

**Apply to All or New Calls** controls whether or not the no agents call treatment applies to:

- ***All Calls*** (default) - calls already in queue and new calls arriving to the queue, or
- ***New Calls Only*** - only new calls that arrive once the No Agents condition occurs, existing calls in queue remain in queue

> [!NOTE]
> The **No Agents** handling exception occurs under the following conditions:
>
> - Presence based routing off: No agents are opted into the queue.
> - Presence based routing on: No agents logged in, or all agents are in *Appear Offline*.
>
> If agents are logged in or opted in, then calls will be queued.

Once you select your call overflow, call timeout, and no agents handling options, select the **Next** button at the bottom of the **Add a Call queue** page.

## [Step 6: Authorized users](#tab/authorized-users)

## Step 6: Authorized users

**Authorized users** specifies the users who are authorized to make changes to this Call queue.  The capabilities that the users have are based on the [Teams voice applications policy](./manage-voice-applications-policies.md) that's assigned to the user.

To **add a user** to the authorized users:

1. Select **Add**, search for the user, select **Add**, and then select **Add**.

> [!IMPORTANT]
> A user must have a policy assigned that enables at least one type of configuration change and must also be assigned as an authorized user to at least one Auto attendant or Call queue.
>
> A user can't make any configuration changes if:
>
> - The user has a policy assigned but isn't assigned as an authorized user to at least one Auto attendant or Call queue.
> - The user is assigned as an authorized user to at least one Auto attendant or Call queue but doesn't have a policy assigned.

> [!NOTE]
> A maximum of 15 authorized users can be assigned to the Call queue.

For more information, see [Set up authorized users](./aa-cq-authorized-users.md).

Once you select your authorized users, select the **Submit** button at the bottom of the **Add a Call queue** page.

---

## Summary of recommended Call queue settings

The following settings are recommended:

- **Conference mode** to **On**
  - This will be the only option available for call queues after June 2025
- **Routing method** to **Round robin** or **Longest idle**
- **Presence-based routing** to **On**
- **Agent alert time:** to a minimum of **20 seconds**

## Extra functionality available through PowerShell cmdlets

> [!CAUTION]
> These configuration options are currently only available through PowerShell cmdlets and they don't appear in Teams admin center. If these options are configured through PowerShell, any changes to the Call queue through Teams admin center will erase these settings.

### Additional messaging

The Overflow, Call timeout and No Agents exception redirect options for **Person in organization** and **Voicemail personal** support additional prompting just like the other redirect options. 

For more information, see:

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-OverflowRedirectPersonTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectPersonTextToSpeechPrompt)        | [-OverflowRedirectPersonTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectPersonTextToSpeechPrompt)        |
| [-OverflowRedirectPersonAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectPersonAudioFilePrompt)              | [-OverflowRedirectPersonAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectPersonAudioFilePrompt)              |
| [-OverflowRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectVoicemailTextToSpeechPrompt)  | [-OverflowRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectVoicemailTextToSpeechPrompt)  |
| [-OverflowRedirectVoicemailAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectVoicemailAudioFilePrompt)        | [-OverflowRedirectVoicemailAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectVoicemailAudioFilePrompt)        |
| [-TimeoutRedirectPersonTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectPersonTextToSpeechPrompt)          | [-TimeoutRedirectPersonTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectPersonTextToSpeechPrompt)          |
| [-TimeoutRedirectPersonAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectPersonAudioFilePrompt)                | [-TimeoutRedirectPersonAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectPersonAudioFilePrompt)                |
| [-TimeoutRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectVoicemailTextToSpeechPrompt)    | [-TimeoutRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectVoicemailTextToSpeechPrompt)    |
| [-TimeoutRedirectVoicemailAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectVoicemailAudioFilePrompt)          | [-TimeoutRedirectVoicemailAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectVoicemailAudioFilePrompt)          |
| [-NoAgentRedirectPersonTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectPersonTextToSpeechPrompt)          | [-NoAgentRedirectPersonTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectPersonTextToSpeechPrompt)          |
| [-NotAgentRedirectPersonAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectPersonAudioFilePrompt)               | [-NotAgentRedirectPersonAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectPersonAudioFilePrompt)               |
| [-NoAgentRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectVoicemailTextToSpeechPrompt)    | [-NoAgentRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectVoicemailTextToSpeechPrompt)    |
| [-NoAgentRedirectVoicemailAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectVoicemailAudioFilePrompt)          | [-NoAgentRedirectVoicemailAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectVoicemailAudioFilePrompt)          |

### Callback

Callback allows eligible callers waiting in queue to receive a callback to the number they are calling from when an agent becomes available.

A caller becomes *eligible* for callback based on any one of the following configured conditions coming true:

- Wait time in queue
  Once a caller in queue exceeds this configured wait time they become *eligible* for callback. This option applies to callers at the front of the queue.

- Number of calls in queue
  Once the number of callers in queue reaches this level, new callers arriving in the queue become *eligible* for callback. This option applies to callers arriving in the queue. Callers that arrived in the queue before this limit was reached aren't eligible for callback.

- Calls to agent ratio
  Once the number of callers waiting in queue exceeds the ratio, new callers arriving in the queue become *eligible* for callback. This option applies to callers arriving in the queue.

Additionally, for a call to become *eligble* for callback, it must have a valid inbound phone number in E.164 format and it must not be presenting to an agent.

*Eligible* callers will receive an option to request callback *after* the music on hold finishes playing.

You can also set the messaging a caller hears, the key they need to press, and an email address to be notified if the callback fails.

#### Callback and Call Queue Timeout Interplay

In order for an *eligible* call to be offered callback, the [Call timeout](#call-timeout-set-how-to-handle-call-timeouts) value must be set high enough to allow the call to become eligible for callback and for the music to finish playing after the call becomes eligible.

Consider the following call queue configuration:

- Callback wait time in queue: 60 seconds
- Call Queue Timeout: 120 seconds
- Call Queue Music: Default

The caller will become eligible for callback after waiting in the queue for 60 seconds however, as the default music is 2 minutes long, call queue timeout will occur and the caller will never be offered callback.

Once a caller has successfully requested a callback, the callback is also subject to the call queue timout configuration. If a callback times out the information about the caller will be sent to the configured email notification address.

**In order for a callback to be successful, the call queue timeout value must be high enough to allow for the call to become eligible, for the music to stop playing, for a caller to successfully request a callback and for the callback to be queued until an agent becomes available for and answers the call.**

> [!NOTE]
> Conference mode must be enabled on the call queue in order to configure callback.
> 
> In addition to the eligibility requirements already listed, for callers within the North American Numbering Plan, the inbound phone number must not start with any of the following digits in order to become eligible for callback:
>
> |Starting Digits                                   |
> |:-------------------------------------------------|
> | 1-242, 246, 264, 268, 284                        |
> | 1-340, 345                                       |
> | 1-441 , 473                                      |
> | 1-500                                            |
> | 1-600, 649, 658, 664, 670, 671, 684              |
> | 1-700, 721, 758, 767, 784, 787                   |
> | 1-800, 811, 822, 833, 844, 855, 866, 877, 888    |
> | 1-809, 829, 849, 868, 869, 876                   | 
> | 1-900, 939                                       |
> | 1-nnn-555-1212                                   |
> | 1-nnn-555,0100-0199                              |

For more information, see:

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-IsCallbackEnabled](/powershell/module/teams/new-cscallqueue#-IsCallbackEnabled) | [-IsCallbackEnabled](/powershell/module/teams/set-cscallqueue#-IsCallbackEnabled) |
| [-CallbackRequestDtmf](/powershell/module/teams/new-cscallqueue#-CallbackRequestDtmf) | [-CallbackRequestDtmf](/powershell/module/teams/set-cscallqueue#-CallbackRequestDtmf) |
| [-WaitTimeBeforeOfferingCallbackInSecond](/powershell/module/teams/new-cscallqueue#-WaitTimeBeforeOfferingCallbackInSecond) | [-WaitTimeBeforeOfferingCallbackInSecond](/powershell/module/teams/set-cscallqueue#-WaitTimeBeforeOfferingCallbackInSecond) |
| [-NumberOfCallsInQueueBeforeOfferingCallback](/powershell/module/teams/new-cscallqueue#-NumberOfCallsInQueueBeforeOfferingCallback) | [-NumberOfCallsInQueueBeforeOfferingCallback](/powershell/module/teams/set-cscallqueue#-NumberOfCallsInQueueBeforeOfferingCallback) |
| [-CallToAgentRatioThresholdBeforeOfferingCallback](/powershell/module/teams/new-cscallqueue#-CallToAgentRatioThresholdBeforeOfferingCallback) | [-CallToAgentRatioThresholdBeforeOfferingCallback](/powershell/module/teams/set-cscallqueue#-CallToAgentRatioThresholdBeforeOfferingCallback) |
| [-CallbackOfferAudioFilePromptResourceId](/powershell/module/teams/new-cscallqueue#-CallbackOfferAudioFilePromptResourceId) | [-CallbackOfferAudioFilePromptResourceId](/powershell/module/teams/set-cscallqueue#-CallbackOfferAudioFilePromptResourceId) |
| [-CallbackOfferTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-CallbackOfferTextToSpeechPrompt) | [-CallbackOfferTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-CallbackOfferTextToSpeechPrompt) |
| [-CallbackEmailNotificationTarget](/powershell/module/teams/new-cscallqueue#-CallbackEmailNotificationTarget) | [-CallbackEmailNotificationTarget](/powershell/module/teams/set-cscallqueue#-CallbackEmailNotificationTarget) |

#### PowerShell Examples

##### Calls become eligible after waiting 60 seconds

Create a new call queue:
````PowerShell
New-CsCallQueue -Name "Callback Eligible After 60 seconds" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -WaitTimeBeforeOfferingCallbackInSecond 60 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

Modify an existing call queue:
````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf
 “Tone1” -WaitTimeBeforeOfferingCallbackInSecond 60 -CallbackOfferTextToSpeechPrompt “If you would like to have a callback when an agent becomes available, press 1” -CallbackEmailNotificationTarget <Team or DL GUID>
````

##### Calls become eligible for callback when there are more than 50 calls in queue

Create a new call queue:
````PowerShell
New-CsCallQueue -Name "Callback Eligible After 50 calls" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

Modify an existing call queue:
````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf
 "Tone1" -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

##### Calls become eligible for callback when there 2 times more calls than agents

Create a new call queue:
````PowerShell
New-CsCallQueue -Name "Callback Eligible After 2x calls to agents" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -CallToAgentRatioThresholdBeforeOfferingCallback 2 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

Modify an existing call queue:
````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf
 "Tone1" -CallToAgentRatioThresholdBeforeOfferingCallback 2 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

##### Calls become eligible for callback after waiting 60 seconds or when there are more than 50 calls in queue

Create a new call queue:
````PowerShell
New-CsCallQueue -Name "Callback Eligible After 60s or 50 calls" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -WaitTimeBeforeOfferingCallbackInSecond 60 -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

Modify an existing call queue:
````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf
 "Tone1" -WaitTimeBeforeOfferingCallbackInSecond 60 -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

### Hiding authorized users

Hidden authorized users are authorized users who shouldn't appear on the list of supervisors for the agents who are members of a particular call queue.

Note that hidden authorized users aren't visible to Queues app users.

For more information, see:

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:-------------------|
| [-HideAuthorizedUsers](/powershell/module/teams/new-cscallqueue#-hideauthorizedusers) | [-HideAuthorizedUsers](/powershell/module/teams/set-cscallqueue#-hideauthorizedusers) |

## Resources for complex scenarios

### Call queue feature compatibility

|Feature                          |Teams Desktop<sup>1</sup> |Teams Web | Teams Mobile App<sup>2</sup> |Teams Phone Mobile<sup>3</sup> |Skype for Business |IP Phones | Standard Call Queues |Channel Based Call Queues | Comment      |
|:--------------------------------|:------------------------:|:--------:|:----------------------------:|:-----------------------------:|:-----------------:|:--------:|:--------------------:|:------------------------:|:-------------|
|**Agent Routing Methods**        |                          |          |                              |                               |                   |          |                      |                          |              |
|Attendant Routing                |Y                         |Y         |Y                             |Y                              |Y                  |Y         |Y                     |Y                         |*Default*     |
|Longest Idle<sup>4</sup>         |Y                         |Y         |Y                             |Y                              |N                  |Y         |Y                     |Y                         |*Recommended* |
|Round Robin                      |Y                         |Y         |Y                             |Y                              |Y                  |Y         |Y                     |Y                         |*Recommended* |
|Serial                           |Y                         |Y         |Y                             |Y                              |Y                  |Y         |Y<sup>5</sup>         |Y<sup>5</sup>             |              |
|**Agent Routing Options**        |                          |          |                              |                               |                   |          |                      |                          |              |
|Presence Based Routing<sup>4</sup>|Y                        |Y         |Y                             |Y<sup>11</sup>                 |N                  |Y         |Y                     |Y                         |*Default*     |
|Agents can opt out               |Y                         |Y         |Y                             |Y<sup>11</sup>                 |Y<sup>8</sup>      |Y<sup>8</sup>|Y                  |Y                         |*Default*     |
|**Transfer Modes**               |                          |          |                              |                               |                   |          |                      |                          |              |
|Conference Mode<sup>6</sup>      |Y                         |Y         |Y                             |Y                              |Y                  |Y         |Y                  |Y                         |*Default*     |
|Transfer Mode                    |Y                         |Y         |Y                             |Y                              |Y                  |Y         |Y                     |Y                         |              |
|**Collaborative Calling**        |                          |          |                              |                               |                   |          |                      |                          |              |
|Channel Based Queues             |Y                         |N         |N                             |N                              |N                  |N         |N/A                   |Y<sup>9</sup>             |Agents on non-supported devices can still answer calls however they won't have the collaborative calling user interface           |
|**Dynamic caller ID**            |                          |          |                              |                               |                   |          |                      |                          |              |
|Standard Call queue              |Y                         |Y         |Y                             |N                              |N                  |N         |Y                     |N/A                       |              |
|Channel based Call queue         |Y                         |N/A       |N/A                           |N/A                            |N/A                |N/A       |N/A                   |Y                         |              |
|**PSTN Connectivity Methods**    |                          |          |                              |                               |                   |          |                      |                          |See Note 10   |
|Calling Plans                    |Y                         |Y         |Y                             |Y                              |Y                  |Y         |Y                     |Y                         |              |
|Direct Routing                   |Y                         |Y         |Y                             |Y                              |N<sup>12</sup>     |Y         |Y<sup>7</sup>         |Y                         |              |
|Operator Connect                 |Y                         |Y         |Y                             |Y                              |N                  |Y         |Y<sup>7</sup>         |Y                         |              |
|**Miscellaneous**                |                          |          |                              |                               |                   |          |                      |                          |              |
|Call toast shows Resource Account Name |Y                   |N         |Y                             |N                              |Y                  |          |Y                     |Y                         |              |
|Click-to-call                    | Y                        |N         |N                             |N                              |N                  |N         |Y                     |Y                         |              |
|[Compliance recording](teams-recording-policy.md) |N/A      |N/A       |N/A                           |N/A                            |N/A                |N/A       |N/A                   |N/A                       |Not supported |
|[Location based routing](location-based-routing-plan.md#inbound-calls-through-auto-attendants)  |N/A                       |N/A       |N/A                           |N/A                            |N/A                |N/A       |N/A                   |N/A                       |Not supported |

#### Notes

1. Microsoft Teams Windows client, Microsoft Teams Mac Client, Microsoft Teams on Virtualized Desktop Infrastructure.
2. Microsoft Teams iPhone app, Microsoft Teams Android app.
3. Teams Phone Mobile Cellular Phone Dialer.
4. Selecting *Longest Idle* for the agent routing method automatically enables Presence based routing.
5. It's not possible to set the order the agents are presented with calls when using a group or channel for membership.
6. Conference mode isn't supported if phone calls are routed to the queue from a Direct Routing gateway that's enabled for Location-Based Routing.
    - Location based routing is not supported with Call queues, see [Voice apps (Auto Attendant or Call Queue)](location-based-routing-plan.md#inbound-calls-through-auto-attendants).
7. Microsoft Teams Phone only.
8. Through the User Settings Portal page at [https://aka.ms/vmsettings](https://aka.ms/vmsettings).
    - GCCH: [https://dialin.cpc.gov.teams.microsoft.us/usp](https://dialin.cpc.gov.teams.microsoft.us/usp)
    - DOD: [https://dialin.cpc.dod.teams.microsoft.us/usp](https://dialin.cpc.dod.teams.microsoft.us/usp)
9. Only standard channels are supported.
10. Transferring calls between PSTN connectivity methods isn't supported.
11. Performed through Team Phone Mobile app or see #8.
12. Call queues that are assigned a direct routing number don't support Skype for Business clients, Lync clients, or Skype for Business IP Phones as agents. The Teams client is only supported with a [co-existence mode of Teams Only](setting-your-coexistence-and-upgrade-settings.md).

### Supported clients

The following clients are supported for call agents in a Call queue:

- Skype for Business desktop client 2016 (32-bit and 64-bit versions)
- All IP phone models supported for Microsoft Teams.
- Mac Skype for Business Client (version 16.8.196 and later)
- Android Skype for Business Client (version 6.16.0.9 and later)
- iPhone Skype for Business Client (version 6.16.0 and later)
- iPad Skype for Business Client (version 6.16.0 and later)
- Microsoft Teams Windows client (32-bit and 64-bit versions)
- Microsoft Teams Mac client
- Microsoft Teams on [Virtualized Desktop Infrastructure](teams-for-vdi.md) (Windows Virtual Desktop, Citrix, and VMware)
- Microsoft Teams iPhone app
- Microsoft Teams Android app

### Call Queue Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate that a Call queue is able to receive calls:

1. Select **Run Tests**, which populates the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Call Queue](https://aka.ms/TeamsCallQueueDiag)

2. In the Run diagnostic pane, enter the Resource Account in the **Username or Email** field, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant, policy, and resource account configurations to validate that the Call queue is able to receive calls.

## Related articles

[Here's what you get with Microsoft Teams Phone](here-s-what-you-get-with-phone-system.md).

[Getting service phone numbers](getting-service-phone-numbers.md).

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).
