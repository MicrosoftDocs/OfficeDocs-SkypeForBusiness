---
title: Create a call queue in Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
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
    - seo-marvel-apr2020
description: Learn how to set up call queues in Microsoft Teams. Call queues provide a greeting message, hold music, call redirecting, and other features.
---

# Create a call queue

Call queues route callers to people in your organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue, who are known as *agents*.

Call queues provide:

- A greeting message.
- Music while people are waiting on hold in a queue.
- Call routing - in *First In, First Out* (FIFO) order - to agents.
- Handling options for queue overflow and timeout.

Before you follow the procedures in this article, be sure you have read [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and followed the [getting started steps](plan-auto-attendant-call-queue.md#getting-started).

## What's new in call queue in the past 6 months

- August 99 - **Add a greeting message** (Text to Speech (TTS)) is now supported for the call queue main greeting
- August 99 - **Skip voicemail system message** controls are now exposed when routing to shared voicemail and now also apply to **Add a greeting message** prompts

## Steps to create a call queue

The steps to set up a call queue includes:

1. Set up general information
1. Set the greeting and music
1. Set up call answering
1. Choose and assign agents
1. Set call overflow handling
1. Set call timeout handling

The steps outlined in the article create call queues using the Teams admin center. For instructions to create call queues using PowerShell, see [Creating call queues with PowerShell cmdlets](create-a-phone-system-call-queue-via-cmdlets.md).

## Follow these steps to set up your call queue

# [Step 1: General info](#tab/general-info)

## Step 1: Set up general information

To set up a call queue, in the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), expand **Voice**, select **Call queues**, and then select **Add**.

Type a name for the call queue in the box at the top.

### Add a resource account

To add an existing resource account:

1. Under **Resource accounts**, click the **Add** button to add a resource account for this call queue.
1. On the **Add accounts** pane, search for the resource account to add.
1. Select the **Add** button next to the resource account you want to assign to this call queue.
1. At the bottom of the pane, select the **Add** button.

If you need to create a resource account:

1. Under **Resource accounts**, click the **Add** button to add a resource account for this call queue.
1. On the **Add accounts** pane, search for any set of letters to pull up the results dropdown.
1. Select the **+ Add a resource account** button at the bottom of the results.
1. On the **Add resource account** pane:
    1. Type in a descriptive **Display name**, which will be visible to agents.
    1. Type in a descriptive **Username** for the resource account.
    1. Select the **Resource account type** dropdown and select **Call queue**.
1. At the bottom of the pane, select the **Save** button.
1. On the **Resource accounts** pane, select the **Add** button.

Agents will see the resource account name when they receive an incoming call.

For more information, see [Manage Teams resource accounts](manage-resource-accounts.md).

### Assign a calling ID (optional)

**Available for Teams channel/collaborative calling desktop users and Teams mobile client users with standard call queues.**

You can assign outbound caller ID numbers for the agents by specifying one or more resource accounts with a phone number. Agents can select which outbound caller ID number to use with each outbound call they make. Within the Calls App, agents can use their Call Queue (CQ) / Auto Attendant (AA) number or their own personal Direct InWard Dial (DID).

> [!NOTE]
> The resource account used for calling ID purposes must have a **Microsoft Teams Phone Resource Account** license and one of the following assigned:
>
> - A Calling Plan license and a phone number assigned
> - An Operator Connect phone number assigned
> - An online voice routing policy (phone number assignment is optional when using Direct Routing)

1. Under **Assign calling ID**, select the **Add** button.
1. On the **Add accounts** pane, search for the resource account(s) you want to allow agents to use for outbound caller ID purposes.
1. Select the **Add** button next to the resource account with an assigned phone number.
1. Select the **Add** button at the bottom of the pane.

If you don't have a resource account with an assigned phone number:

1. Under **Resource accounts**, click the **Add** button to add a resource account.
1. On the **Add accounts** pane, search for any set of letters to pull up the results dropdown.
1. Select the **+ Add a resource account** button at the bottom of the results.
1. On the **Add resource account** pane:
    1. Type in a descriptive **Display name**, which will be visible to call recipients.
    1. Type in a descriptive **Username** for the resource account.
    1. Select the **Resource account type** dropdown and select **Call queue**.
1. At the bottom of the pane, select the **Save** button.
1. On the **Resource accounts** pane, select the **Add** button.

After you've created this new resource account for calling ID, you'll still need to:

- Assign a [Teams Phone Resource Account license](manage-resource-accounts.md#assign-a-license)
- Assign a Microsoft Calling Plan license, assign an Operator Connect phone number, or assign an online voice routing policy for Direct Routing
- Assign the [service phone number to the resource account](manage-resource-accounts.md#assign-a-service-number), if you're using Microsoft Calling Plan

### Set the call queue language

Choose a [supported language](create-a-phone-system-call-queue-languages.md).

This language will be used for system-generated voice prompts and voicemail transcription, if you enable them.

Once you've selected a language, select the **Next** button at the bottom of the **Add a call queue** page.

# [Step 2: Greeting and music](#tab/greeting-music)

## Step 2: Add a greeting and on-hold music

*New - **Add a greeting message** (Text to Speech (TTS)) is now supported for the call queue main greeting*

Specify if you want to play a *greeting* to callers when they arrive in the queue.

- If you select **Play an audio file**, you must upload an MP3, WAV, or WMA file containing the greeting that you want to play. The uploaded recording can be no larger than 5 MB.

- If you select **Type a greeting message**, the system will read the text that you type (up to 1000 characters) when the call queue answers a call.

Teams provides default music to callers while they are *on hold in a queue*.

- The default music supplied in Teams call queues is free of any royalties payable by your organization.
- If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file.

> [!NOTE]
> You are responsible for independently clearing and securing all necessary rights and permissions to use any music or audio file with your Microsoft Teams service, which may include intellectual property and other rights in any music, sound effects, audio, brands, names, and other content in the audio file from all relevant rights holders, which may include artists, actors, performers, musicians, songwriters, composers, record labels, music publishers, unions, guilds, rights societies, collective management organizations and any other parties who own, control or license the music copyrights, sound effects, audio and other intellectual property rights.

Once you've selected a greeting and on-hold music, select the **Next** button at the bottom of the **Add a call queue** page.

# [Step 3: Call answering](#tab/call-answering)

## Step 3: Set up who will answer incoming calls

Review the [prerequisites for adding agents to a call queue](plan-auto-attendant-call-queue.md#prerequisites).

### Teams channel

You can add up to 200 agents via a Teams channel. You must be a member of the team or the creator or owner of the channel to add a channel to the queue.

If you want to [use a Teams channel to manage the queue](https://support.microsoft.com/office/9f07dabe-91c6-4a9b-a545-8ffdddd2504e):

1. Select the **Choose a team** radio button and select **Add a channel**.
1. Search for the team that you want to use, select it, and select **Add**.
1. Select the channel that you want to use (only standard channels are supported) and select **Apply**.

The following clients are supported when using a Teams channel for call queues:

- Microsoft Teams Windows client
- Microsoft Teams Mac client

> [!NOTE]
> If you use this option, it can take up to 24 hours for the call queue to be fully operational.
>
> If there are more than 200 members in the team, only the first 200 members, in alphabetical order, will be added as agents to the call queue.

### Users and groups

You can add up to 20 agents individually and up to 200 agents via groups.

If you want to add individual users or groups to the queue:

1. Select the **Choose users and groups** radio button.

To **add a user** to the queue:

1. Select **Add users**, search for the user, click **Add**, and then click **Add**.

To **add a group** to the queue:

1. Select **Add groups**, search for the group, click **Add**, and then click **Add**. 
    1. You can use distribution lists, security groups, and Microsoft 365 groups or Microsoft Teams teams.

> [!NOTE]
> New users added to a group can take up to eight hours for their first call to arrive.
>
> If there are more than 200 members in the group, only the first 200 members, in alphabetical order, will be added as agents to the call queue.

### Conference mode

**Conference mode** reduces the amount of time it takes for a caller to be connected to an agent after the agent accepts the call. For conference mode to work, agents in the call queue must use one of the following clients:

- The latest version of the Microsoft Teams desktop client, Android app, or iOS app
- Microsoft Teams Phone version 1449/1.0.94.2020051601 or later
  
Agents' Teams accounts must be set to TeamsOnly mode. Agents who don't meet the requirements aren't included in the call routing list. We recommend enabling conference mode for your call queues if your agents are using compatible clients.

> [!NOTE]
> Conference mode isn't supported if phone calls are routed to the queue from a Direct Routing gateway that is enabled for Location Based Routing.
>
> Conference mode isn't supported if phone calls are routed to the queue from Skype for Business Server.
> 
> Conference mode is required if Teams users need to consult/transfer calls with call queues.
>
> Agents may hear the configured music on hold in queue for up to 2 seconds when first joining the call.


> [!TIP]
> Setting **Conference mode** to **On** is the recommended setting.

Once you've selected your call answering options, select the **Next** button at the bottom of the **Add a call queue** page.

# [Step 4: Agent routing](#tab/agent-routing)

## Step 4: Select your agent routing options

**Routing method** determines the order in which agents receive calls from the queue.

Choose from these options:

- **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

- **Serial routing** rings all call agents one by one in the order specified in the **Call agents** list. If an agent dismisses or doesn't pick up a call, the call will ring the next agent. This will repeat until the call is picked up or times out.

- **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This routing method may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

- **Longest idle** routes each call to the agent who has been idle the longest time. An agent is considered idle if their presence state is Available. Agents whose presence state isn't Available won't be eligible to receive calls until they change their presence to Available.

We recommend setting your **Routing Method** to either **Round robin** or **Longest idle**.

> [!NOTE]
> If [Compliance recording](teams-recording-policy.md) is enabled on the agents, the combination of **Conference mode** and **Attendant routing** isn't supported. If you need to use **Conference mode**, select **Serial Routing**, **Round robin**, or **Longest idle** as the **Routing method**. If you need to use **Attendant routing**, set **Conference mode** to **Off**.
>
> When using **Longest idle** and when there are less calls in queue than available agents, only the first two longest idle agents will be presented with calls from the queue.
>
> When using **Longest idle**, there may be times when an agent receives a call from the queue shortly after becoming unavailable, or a short delay in receiving a call from the queue after becoming available.
>
> Call Queue call presentation to agents may conflict with Location Based Routing restrictions. In this case, the agent will receive a call toast but won't be able to answer the call. This condition will continue until another agent is available to answer the call, the caller hangs up or the call queue timeout condition occurs.  

### Presence-based call routing

**Presence-based call routing** uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method.

Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and won't receive calls until their availability status changes back to **Available**.

You can enable **presence-based call routing** with any of the routing methods.

If an agent opts out of getting calls, they won't be included in the call routing list regardless of what their availability status is set to.

We recommend turning on **Presence-based routing**.

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

We recommend setting the **Agent alert time** to **20 seconds**.

Once you've selected your agent call routing options, select the **Next** button at the bottom of the **Add a call queue** page.

# [Step 5: Call overflow](#tab/call-overflow)

## Step 5: Set how to handle call overflow

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time.

The default is 50, but it can range from 0 to 200.

When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

You can choose to **disconnect** the call or **redirect** it to any of the call routing destinations.

For example, you might have the caller leave a voicemail for the agents in the queue.

*New - **Skip voicemail system message** controls are now exposed when routing to shared voicemail and now also apply to **Add a greeting message** prompts*

For external transfers, see [Prerequisites](./plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](create-a-phone-system-auto-attendant.md?tabs=additional-resources) for number formatting.

> [!NOTE]
> If the maximum number of calls is set to 0 then the greeting message won't play.

Once you've selected your call overflow handling options, select the **Next** button at the bottom of the **Add a call queue** page.

# [Step 6: Call timeout](#tab/call-timeout)

## Step 6: Set how to handle call timeouts

**Call Timeout: maximum wait time** specifies the maximum time a call can be on hold in the queue before it is redirected or disconnected.

You can specify a value from 0 seconds to 45 minutes.

You can choose to **disconnect** the call or **redirect** it to one of the call routing destinations.

For example, you might have the caller leave a voicemail for the agents in the queue.

*New - **Skip voicemail system message** controls are now exposed when routing to shared voicemail and now also apply to **Add a greeting message** prompts*

For external transfers, see [Prerequisites](./plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](create-a-phone-system-auto-attendant.md?tabs=additional-resources) for number formatting.

Once you've selected your call timeout handling options, select the **Submit** button at the bottom of the **Add a call queue** page.

---

## Resources for complex scenarios

### Summary of recommended call queue settings

The following settings are recommended:

- **Conference mode** to **On**
- **Routing method** to **Round robin** or **Longest idle**
- **Presence-based routing** to **On**
- **Agent alert time:** to **20 seconds**

### Call queue feature compatibility

|Feature                          |Teams Desktop<sup>1</sup> |Teams Web | Teams Mobile<sup>2</sup> |Lync |IP Phones | Standard Call Queues |Channel Based Call Queues | Comment |
|:--------------------------------|:------------------------:|:--------:|:--------------:|:---:|:--------:|:--------------------:|:------------------------:|:--------|
|**Agent Routing Methods**        |                          |          |                |     |          |                      |                          |   |
|`Attendant Routing`              |Y                         |Y         |Y               |Y    |Y         |Y                     |Y                         |*Default*     |
|`Longest Idle`<sup>3</sup>       |Y                         |Y         |Y               |N    |Y         |Y                     |Y                         |*Recommended* |
|`Round Robin`                    |Y                         |Y         |Y               |Y    |Y         |Y                     |Y                         |*Recommended* |
|`Serial`                         |Y                         |Y         |Y               |Y    |Y         |Y<sup>4</sup>         |Y<sup>4</sup>             |   |
|**Agent Routing Options**        |                          |          |                |     |          |                      |                          |   |
|`Presence Based Routing`<sup>3</sup>|Y                      |Y         |Y               |N    |Y         |Y                     |Y                         |*Recommended* |
|`Agents can Opt-out`               |Y                       |Y         |Y               |Y<sup>7</sup>|Y<sup>7</sup>|Y          |Y                         |*Default*     |
|**Transfer Modes**               |                          |          |                |     |          |                      |                          |   |
|`Conference Mode`<sup>5</sup>    |Y                         |Y         |Y               |N    |Y<sup>6</sup>|Y                  |Y                         |*Recommended* |
|`Transfer Mode`                  |Y                         |Y         |Y               |Y    |Y         |Y                     |Y                         |*Default*              |
|**Collaborative Calling**        |                          |          |                |     |          |                      |                          |   |
|`Channel Based Queues`             |Y                       |N         |N               |N    |N         |n/a                   |Y<sup>8</sup>             |   |
|**Dynamic caller ID**            |                          |          |                |     |          |                      |                          |   |
|`Standard call queue`            |Y                         |Y         |Y               |N    |N         |Y                     |n/a                       |   |
|`Channel based call queue`       |Y                         |n/a       |n/a             |n/a  |n/a       |n/a                   |Y                         |   |
|**PSTN Connectivity Methods**    |                          |          |                |     |          |                      |                          |See Note 9   |
|`Calling Plans`                  |Y                         |Y         |Y               |Y    |Y         |Y                     |Y                         |   |
|`Direct Routing`                 |Y                         |Y         |Y               |N    |N         |Y                     |Y                         |   |
|`Operator Connect`               |Y                         |Y         |Y               |     |          |Y                     |Y                         |   |
|**Miscellaneous**                |                          |          |                |     |          |                      |                          |   |
|`Call toast shows Resource Account Name` |Y                 |N         |Y               |Y    |          |Y                     |Y                         |              |

#### Notes

1. Microsoft Teams Windows client, Microsoft Teams Mac Client, Microsoft Teams on Virtualized Desktop Infrastructure.
2. Microsoft Teams iPhone app, Microsoft Teams Android app.
3. Selecting Longest Idle for the agent routing method will automatically enable Presence based routing.
4. Can only set the order when adding individual users as part of standard call queues. When a distribution list or Teams Channel is used order will be alphabetical.
5. Conference mode isn't supported if phone calls are routed to the queue from a Direct Routing gateway that is enabled for Location Based Routing.
6. Microsoft Teams Phone only.
7. Through the User Settings Portal page at [https://aka.ms/vmsettings](https://aka.ms/vmsettings).
8. Only public channels are supported.
9. Auto Attendants and Call Queues cannot transfer calls between PSTN connectivity methods.

### Supported clients

The following clients are supported for call agents in a call queue:

- Skype for Business desktop client 2016 (32-bit and 64-bit versions)
- Lync desktop client 2013 (32-bit and 64-bit versions)
- All IP phone models supported for Microsoft Teams. See [Getting phones for Skype for Business Online](/skypeforbusiness/what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/getting-phones-for-skype-for-business-online).
- Mac Skype for Business Client (version 16.8.196 and later)
- Android Skype for Business Client (version 6.16.0.9 and later)
- iPhone Skype for Business Client (version 6.16.0 and later)
- iPad Skype for Business Client (version 6.16.0 and later)
- Microsoft Teams Windows client (32-bit and 64-bit versions)
- Microsoft Teams Mac client
- Microsoft Teams on [Virtualized Desktop Infrastructure](teams-for-vdi.md) (Windows Virtual Desktop, Citrix, and VMware)
- Microsoft Teams iPhone app
- Microsoft Teams Android app

  > [!NOTE]
  > Call queues that are assigned a direct routing number don't support Skype for Business clients, Lync clients, or Skype for Business IP Phones as agents. The Teams client is only supported with a [co-existence mode of Teams Only](setting-your-coexistence-and-upgrade-settings.md).

### Call Queue Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate that a call queue is able to receive calls:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Call Queue](https://aka.ms/TeamsCallQueueDiag)

2. In the Run diagnostic pane, enter the Resource Account in the **Username or Email** field, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant, policy, and resource account configurations to validate that the call queue is able to receive calls.

### Related topics

[Here's what you get with Microsoft Teams Phone](here-s-what-you-get-with-phone-system.md)

[Getting service phone numbers](getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
