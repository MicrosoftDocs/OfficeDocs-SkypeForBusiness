---
title: "Create a call queue in Microsoft Teams - small business tutorial"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: colongma
ms.topic: article
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
localization_priority: Normal
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
description: Learn how to set up Phone System for call queues with Microsoft Teams, which provide a greeting message, hold music, call redirecting, and other features.
---
# Create a call queue - small business tutorial

Call queues provide a method of routing callers to people in your organization who can help with with a particular issue or question. Calls are distributed one at a time to the people in the queue (who are known as *agents*). 

Call queues provide:

- A greeting message.

- Music while people are waiting on hold in a queue.

- Call routing - in *First In, First Out* (FIFO) order - to agents.

- Handling options for queue overflow and timeout.

Be sure you have read [Plan for Teams auto attendants and call queues](../plan-auto-attendant-call-queue.md) and followed the [getting started steps](../plan-auto-attendant-call-queue.md#getting-started) before you follow the procedures in this articles.

get licenses

## Before you begin

Get some [Phone System - Virtual User licenses](teams-add-on-licensing/virtual-user.md) if you don't already have them. Get one for each call queue and auto attendant that you plan to set up. These licenses are free, so we suggest getting a few extra in case you decide to make changes to your setup in the future.

<a name="steps"></a>

# [Step 1<br>Create a team](#tab/create-team)

Create a team in Microsoft Teams.

> [!div class="nextstepaction"]
> [Step 2 - Resource accounts >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=resource-account#steps)

# [Step 2<br>Resource accounts](#tab/resource-account)

create resource account
assign license


To set up a call queue, in the Teams admin center, expand **Voice**, click **Call queues**, and then click **Add**.

## Resource account and language

![Screenshot of resource account and language settings](../media/call-queue-name-language.png)

1. Type a name for the call queue. Agents will see this name when they receive an incoming call from the queue.

2. Click **Add accounts**, search for the resource account that you want to use with this call queue, click **Add**, and then click **Add**.

3. Choose a language. This language will be used for system-generated voice prompts and voicemail transcription (if you enable them).

## Greetings and music on hold in queue

Specify if you want to play a greeting to callers when they arrive in the queue. You must upload an MP3, WAV, or WMA file containing the greeting that you want to play.

Teams provides default music to callers while they are on hold in a queue. If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file.

> [!NOTE]
> The uploaded recording can be no larger than 5 MB.
> The default music supplied in Teams call queues is free of any royalties payable by your organization. 

> [!div class="nextstepaction"]
> [Step 3 - Call agents >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-agents#steps)

# [Step 3<br>Call agents](#tab/call-agents)

## Call agents

Please refer to the [Prerequisites](../plan-auto-attendant-call-queue.md#prerequisites) in order to be able to add agents to a call queue.

![Screenshot of users and groups settings for call queues](../media/call-queue-users-groups.png)

You can add up to 20 agents individually and up to 200 agents via groups.

To add a user to the queue, click **Add users**, search for the user, click **Add**, and then click **Add**.

To add a group to the queue, click **Add groups**, search for the group, click **Add**, and then click **Add**. You can use distribution lists, security groups, and Microsoft 365 groups or Microsoft Teams teams.

> [!NOTE]
> New users added to a group can take up to eight hours for their first call to arrive.

> [!div class="nextstepaction"]
> [Step 4 - Resource accounts >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-routing#steps)

# [Step 4<br>Call routing](#tab/call-routing)

## Call routing

![Screenshot of conference mode and routing method settings](../media/call-queue-conference-mode-routing-method.png)

**Conference mode** significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call. For conference mode to work, agents in the call queue must use one of the following clients:

  - The latest version of the Microsoft Teams desktop client, Android app, or iOS app
  - Microsoft Teams phone version 1449/1.0.94.2020051601 or later
  
Agents' Teams accounts need to be set to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list. We recommend enabling conference mode for your call queues if your agents are all using compatible clients.

> [!NOTE]
> Busy on Busy is not supported by conference mode. Agents on non-call queue calls may still be presented with a call queue call if presence-based routing is not enabled.

**Routing method** determines the order in which agents receive calls from the queue. Choose from these options:

- **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

- **Serial routing** rings all call agents one by one in the order specified in the **Call agents** list. If an agent dismisses or does not pick up a call, the call will ring the next agent and will try all agents until it is picked up or times out.

- **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

- **Longest idle** routes each call to the agent who has been idle the longest time. An agent is considered idle if their presence state is Available or if their presence state has been Away for less than 10 minutes. Agents whose presence state has been Away for more than 10 minutes are not considered idle and will not be eligible to receive calls until they change their presence to Available. 

![Screenshot of routing, opt out, and alert time settings](../media/call-queue-presence-agents-time.png)


**Presence-based routing** uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method. Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and won't receive calls until their availability status changes back to **Available**. 

You can enable presence-based call routing with any of the routing methods.

If an agent opts out of getting calls, they won't be included in the call routing list regardless of what their availability status is set to. 

> [!NOTE]
> Agents who use the Skype for Business client aren't included in the call routing list when presence-based routing is enabled. If you have agents who use Skype for Business, don't enable presence-based call routing.

**Agent alert time** specifies how long an agent's phone will ring before the queue redirects the call to the next agent.

For high volume queues, we recommend the following settings:

- **Conference mode** to **Auto**
- **Routing method** to **Attendant routing**
- **Presence-based routing** to **On**
- **Agent alert time:** to **20 seconds**

> [!div class="nextstepaction"]
> [Step 5 - Resource accounts >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-overflow#steps)

# [Step 5<br>Call overflow](#tab/call-overflow)

## Call overflow handling

![Screenshot of call overflow settings](../media/call-queue-overflow-handling.png)

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time. The default is 50, but it can range from 0 to 200. When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

You can choose to disconnect the call or redirect it to any of the call routing destinations. For example, you might have the caller leave a voicemail for the agents in the queue. For external transfers, please refer to [Prerequisites](../plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](../create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

> [!NOTE]
> If the maximum number of calls is set to 0 then the greeting message will not play.

> [!div class="nextstepaction"]
> [Step 6 - Resource accounts >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-call-queue-smb?branch=mikeplum-smb-voice&tabs=call-timeout#steps)

# [Step 6<br>Call timeout](#tab/call-timeout)

## Call timeout handling

![Screenshot of call timeout settings](../media/call-queue-timeout-handling.png)

**Call Timeout: maximum wait time** specifies the maximum time a call can be on hold in the queue before it is redirected or disconnected. You can specify a value from 0 seconds to 45 minutes.

You can choose to disconnect the call or redirect it to one of the call routing destinations. For example, you might have the caller leave a voicemail for the agents in the queue. For external transfers, please refer to [Prerequisites](../plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](../create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

When you have selected your call timeout options, click **Save**.

---

## Caller ID for outbound calls

Since agents in a call queue may dial out to return a customer call, consider setting the caller ID for members of a call queue to the service number of an appropriate auto attendant. See [Manage caller ID policies in Microsoft Teams](../caller-id-policies.md) for more information.

