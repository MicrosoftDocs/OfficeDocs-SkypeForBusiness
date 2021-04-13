---
title: "Create a call queue in Microsoft Teams"
ms.author: mikeplum
author: MikePlumleyMSFT
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
localization_priority: Normal
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
  - seo-marvel-apr2020
description: Learn how to set up Phone System for call queues with Microsoft Teams, which provides a greeting message, hold music, call redirecting, and other features.
---
# Create a call queue

Call queues provide a method of routing callers to people in your organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue (who are known as *agents*). 

Call queues provide:

- A greeting message.

- Music while people are waiting on hold in a queue.

- Call routing - in *First In, First Out* (FIFO) order - to agents.

- Handling options for queue overflow and timeout.

Be sure you have read [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and followed the [getting started steps](plan-auto-attendant-call-queue.md#getting-started) before you follow the procedures in this article.

To set up a call queue, in the Teams admin center, expand **Voice**, click **Call queues**, and then click **Add**.

## Resource account and language

![Screenshot of resource account and language settings](media/call-queue-name-language.png)

1. Type a name for the call queue.

2. Click **Add accounts**, search for the resource account that you want to use with this call queue, click **Add**, and then click **Add**. (Agents will see the resource account name when they receive an incoming call.)

3. Choose a [supported language](create-a-phone-system-call-queue-languages.md). This language will be used for system-generated voice prompts and voicemail transcription (if you enable them).

## Greetings and music on hold in queue

Specify if you want to play a greeting to callers when they arrive in the queue. You must upload an MP3, WAV, or WMA file containing the greeting that you want to play.

Teams provides default music to callers while they are on hold in a queue. If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file.

> [!NOTE]
> The uploaded recording can be no larger than 5 MB.
> The default music supplied in Teams call queues is free of any royalties payable by your organization. 

## Call agents

Review the [prerequisites for adding agents to a call queue](plan-auto-attendant-call-queue.md#prerequisites).

![Screenshot of users and groups settings for call queues](media/call-queue-users-groups.png)

##### Teams channel

You can add up to 200 agents via a Teams channel.

If you want to [use a Teams channel to manage the queue](https://support.microsoft.com/office/9f07dabe-91c6-4a9b-a545-8ffdddd2504e), select the **Choose a team** option and click **Add a channel**. Search for the team that you want to use, select it, and click **Add**. Select the channel that you want to use and click **Apply**.

##### Users and groups

You can add up to 20 agents individually and up to 200 agents via groups.

If you want to add individual users or groups to the queue, select the **Choose users and groups** option. 

To add a user to the queue, click **Add users**, search for the user, click **Add**, and then click **Add**.

To add a group to the queue, click **Add groups**, search for the group, click **Add**, and then click **Add**. You can use distribution lists, security groups, and Microsoft 365 groups or Microsoft Teams teams.

> [!NOTE]
> New users added to a group can take up to eight hours for their first call to arrive.

## Call routing

![Screenshot of conference mode and routing method settings](media/call-queue-conference-mode-routing-method.png)

**Conference mode** significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call. For conference mode to work, agents in the call queue must use one of the following clients:

  - The latest version of the Microsoft Teams desktop client, Android app, or iOS app
  - Microsoft Teams phone version 1449/1.0.94.2020051601 or later
  
Agents' Teams accounts need to be set to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list. We recommend enabling conference mode for your call queues if your agents are all using compatible clients.

**Routing method** determines the order in which agents receive calls from the queue. Choose from these options:

- **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

- **Serial routing** rings all call agents one by one in the order specified in the **Call agents** list. If an agent dismisses or does not pick up a call, the call will ring the next agent and will try all agents until it is picked up or times out.

- **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

- **Longest idle** routes each call to the agent who has been idle the longest time. An agent is considered idle if their presence state is Available or if their presence state has been Away for less than 10 minutes. Agents whose presence state has been Away for more than 10 minutes are not considered idle and will not be eligible to receive calls until they change their presence to Available. 

![Screenshot of routing, opt out, and alert time settings](media/call-queue-presence-agents-time.png)


**Presence-based routing** uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method. Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and won't receive calls until their availability status changes back to **Available**. 

You can enable presence-based call routing with any of the routing methods.

If an agent opts out of getting calls, they won't be included in the call routing list regardless of what their availability status is set to. 

> [!NOTE]
> Agents who use the Skype for Business client aren't included in the call routing list when presence-based routing is enabled. If you have agents who use Skype for Business, don't enable presence-based call routing.

**Agent alert time** specifies how long an agent's phone will ring before the queue redirects the call to the next agent.

The following settings are recommended:

- **Conference mode** to **Auto**
- **Routing method** to **Round robin** or **Longest idle**
- **Presence-based routing** to **On**
- **Agent alert time:** to **20 seconds**

> [!NOTE]
> If presence-based routing is not enabled and there are multiple calls in the queue, the system will present these calls simultaneously to the agents regardless of their presence status. This will result in multiple call notifications to agents, particularly if some agents don’t answer the initial call presented to them.

## Call overflow handling

![Screenshot of call overflow settings](media/call-queue-overflow-handling.png)

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time. The default is 50, but it can range from 0 to 200. When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

You can choose to disconnect the call or redirect it to any of the call routing destinations. For example, you might have the caller leave a voicemail for the agents in the queue. For external transfers, please refer to [Prerequisites](plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

> [!NOTE]
> If the maximum number of calls is set to 0 then the greeting message will not play.

## Call timeout handling

![Screenshot of call timeout settings](media/call-queue-timeout-handling.png)

**Call Timeout: maximum wait time** specifies the maximum time a call can be on hold in the queue before it is redirected or disconnected. You can specify a value from 0 seconds to 45 minutes.

You can choose to disconnect the call or redirect it to one of the call routing destinations. For example, you might have the caller leave a voicemail for the agents in the queue. For external transfers, please refer to [Prerequisites](plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

When you have selected your call timeout options, click **Save**.

## Caller ID for outbound calls

Since agents in a call queue may dial out to return a customer call, consider setting the caller ID for members of a call queue to the service number of an appropriate auto attendant. See [Manage caller ID policies in Microsoft Teams](caller-id-policies.md) for more information.

## Supported clients

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
  - Microsoft Teams iPhone app
  - Microsoft Teams Android app

    > [!NOTE]
    > Call queues that are assigned a direct routing number don't support Skype for Business clients, Lync clients, or Skype for Business IP Phones as agents.

## Call queue cmdlets

You can also use Windows PowerShell to create and set up call queues. Here are the cmdlets that you use to manage a call queue.

- [New-CsCallQueue](/powershell/module/skype/new-CsCallQueue)

- [Set-CsCallQueue](/powershell/module/skype/set-CsCallQueue)

- [Get-CsCallQueue](/powershell/module/skype/get-CsCallQueue)

- [Remove-CsCallQueue](/powershell/module/skype/remove-CsCallQueue)

## Related topics

[Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md)

[Getting service phone numbers](getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)

[New-CsOnlineApplicationInstance](/powershell/module/skype/new-csonlineapplicationinstance)

[An introduction to Windows PowerShell and Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)
