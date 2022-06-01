---
title: "Create a call queue in Microsoft Teams"
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
description: Learn how to set up call queues for large organizations in Microsoft Teams, which provides a greeting message, hold music, call redirecting, and other features.
---
# Create a call queue

Call queues provide a method of routing callers to people in your organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue (who are known as *agents*).

Call queues provide:

- A greeting message.
- Music while people are waiting on hold in a queue.
- Call routing - in *First In, First Out* (FIFO) order - to agents.
- Handling options for queue overflow and timeout.

Be sure you have read [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and followed the [getting started steps](plan-auto-attendant-call-queue.md#getting-started) before you follow the procedures in this article.

**See the [Call Queue Feature Compatibility](#call-queue-feature-compatibility) matrix below for more information.**

The steps to set up a call queue includes:

1. [Create the call queue](?tabs=create-queue)
1. [Add resource accounts](?tabs=resource-account)
1. [Set up dynamic caller ID](?tabs=dynamic-caller-id)
1. [Choose languages](?tabs=language)
1. [Choose greetings and music](?tabs=greetings)
1. [Select call agents](?tabs=call-agents)
1. [Map call routing](?tabs=call-routing)
1. [Handle call overflow](?tabs=call-overflow)
1. [Handle call timeout](?tabs=call-timeout)

## Video demonstration

This video shows a basic example of how to create a call queue in Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWCF23?autoplay=false]

## How to set up your call queue

### [Step 1: Call queue](#tab/create-queue)

## Step 1: Create the call queue

To set up a call queue, in the Teams admin center, expand **Voice**, click **Call queues**, and then click **Add**.

Type a name for the call queue.

### [Step 2 - Resource accounts](#tab/resource-account)

## Step 2: Add resource accounts

![Screenshot of resource account settings.](./media/call-queue-name-language.png)

Click **Add accounts**, search for the resource account that you want to use with this call queue, click **Add**, and then click **Add**.

Agents will see the resource account name when they receive an incoming call.

For more information, see [Manage Teams resource accounts](./manage-resource-accounts.md).

### [Step 3 - Dynamic Caller ID](#tab/dynamic-caller-id)

## Step 3: Set up dynamic caller ID

![Screenshot of calling ID settings.](./media/call-queue-assign-calling-id.png)

**Available for Teams channel/collaborative calling desktop users and Teams mobile client users with standard call queues**

You can assign outbound caller ID numbers for the agents by specifying one or more resource accounts with a phone number. Agents can select which outbound caller ID number to use with each outbound call they make.

Click **Add**, search for the resource accounts that you want to allow agents to use for caller ID purposes when making outbound calls, click **Add**, and then click **Add**.

### Standard Call Queues

For Teams desktop users and standard call queues consider directly setting the caller ID for members of the call queue to the service number of the call queue or appropriate auto attendant. For more information, see [Manage caller ID policies in Microsoft Teams](./caller-id-policies.md).

> [!NOTE]
> The resource account used for calling ID purposes must have a Microsoft Teams Phone System Virtual User license and one of the following assigned:
>
> - A Calling Plan license and a phone number assigned
> - An Operator Connect phone number assigned
> - An online voice routing policy (phone number assignment is optional when using Direct Routing)

### [Step 4 - Language](#tab/language)

## Step 4: Choose a language

![Screenshot of language settings.](./media/call-queue-language.png)

Choose a [supported language](./create-a-phone-system-call-queue-languages.md).

This language will be used for system-generated voice prompts and voicemail transcription (if you enable them).

### [Step 5 - Greetings and music](#tab/greetings)

## Step 5: Greetings and music on hold in queue

![Screenshot of greetings and music on hold in queue settings.](./media/call-queue-greetings-music.png)

Specify if you want to play a greeting to callers when they arrive in the queue. You must upload an MP3, WAV, or WMA file containing the greeting that you want to play. The uploaded recording can be no larger than 5 MB.

Teams provides default music to callers while they are on hold in a queue. The default music supplied in Teams call queues is free of any royalties payable by your organization. If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file.

> [!NOTE]
> You are responsible for independently clearing and securing all necessary rights and permissions to use any music or audio file with your Microsoft Teams service, which may include intellectual property and other rights in any music, sound effects, audio, brands, names, and other content in the audio file from all relevant rights holders, which may include artists, actors, performers, musicians, songwriters, composers, record labels, music publishers, unions, guilds, rights societies, collective management organizations and any other parties who own, control or license the music copyrights, sound effects, audio and other intellectual property rights.

### [Step 6 - Call agents](#tab/call-agents)

## Step 6: Call agents

Review the [prerequisites for adding agents to a call queue](./plan-auto-attendant-call-queue.md#prerequisites).

![Screenshot of users and groups settings for call queues.](./media/call-queue-users-groups.png)

### Teams channel

You can add up to 200 agents via a Teams channel. You must be a member of the team or the creator or an owner of the channel to add a channel to the queue.

If you want to [use a Teams channel to manage the queue](https://support.microsoft.com/office/9f07dabe-91c6-4a9b-a545-8ffdddd2504e), select the **Choose a team** option and click **Add a channel**. Search for the team that you want to use, select it, and click **Add**. Select the channel that you want to use (only standard channels are supported) and click **Apply**.

The following clients are supported when using a Teams channel for call queues:

- Microsoft Teams Windows client
- Microsoft Teams Mac client

> [!NOTE]
> If you use this option, it can take up to 24 hours for the call queue to be fully operational.

### Users and groups

You can add up to 20 agents individually and up to 200 agents via groups.

If you want to add individual users or groups to the queue, select the **Choose users and groups** option.

To add a user to the queue, click **Add users**, search for the user, click **Add**, and then click **Add**.

To add a group to the queue, click **Add groups**, search for the group, click **Add**, and then click **Add**. You can use distribution lists, security groups, and Microsoft 365 groups or Microsoft Teams teams.

> [!NOTE]
> New users added to a group can take up to eight hours for their first call to arrive.

### [Step 7 - Call routing](#tab/call-routing)

## Step 7: Call routing

![Screenshot of conference mode and routing method settings.](./media/call-queue-conference-mode-routing-method.png)

**Conference mode** significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call. For conference mode to work, agents in the call queue must use one of the following clients:

- The latest version of the Microsoft Teams desktop client, Android app, or iOS app
- Microsoft Teams Phone version 1449/1.0.94.2020051601 or later
  
Agents' Teams accounts must be set to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list. We recommend enabling conference mode for your call queues if your agents are all using compatible clients.

> [!NOTE]
> Conference mode is not supported if phone calls are routed to the queue from a Direct Routing gateway that is enabled for Location Based Routing.

> [!TIP]
> Setting **Conference mode** to **On** is the recommended setting.

**Routing method** determines the order in which agents receive calls from the queue. Choose from these options:

- **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

- **Serial routing** rings all call agents one by one in the order specified in the **Call agents** list. If an agent dismisses or does not pick up a call, the call will ring the next agent. This will repeat until the call is picked up or times out.

- **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This routing method may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

- **Longest idle** routes each call to the agent who has been idle the longest time. An agent is considered idle if their presence state is Available. Agents whose presence state is not Available will not be eligible to receive calls until they change their presence to Available.

> [!TIP]
> Setting **Routing Method** to **Round robin** or **Longest idle** is the recommended setting.

> [!NOTE]
> If [Compliance recording](./teams-recording-policy.md) is enabled on the agents, the combination of **Conference mode** and **Attendant routing** is not supported. If you need to use **Conference mode**, select **Serial Routing**, **Round robin**, or **Longest idle** as the **Routing method**. If you need to use **Attendant routing**, set **Conference mode** to **Off**.
>
> When using **Longest idle** and when there are less calls in queue than available agents, only the first two longest idle agents will be presented with calls from the queue.
>
> When using **Longest idle** there may be times when an agent receives a call from the queue shortly after becoming unavailable or a short delay in receiving a call from the queue after becoming available.
>
> Call Queue call presentation to agents may conflict with Location Based Routing restrictions. In this case, the agent will receive a call toast but will not be able to answer the call. This condition will continue until another agent is available to answer the call, the caller hangs up or the call queue timeout condition occurs.  

![Screenshot of routing, opt out, and alert time settings.](./media/call-queue-presence-agents-time.png)

**Presence-based routing** uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method. Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and won't receive calls until their availability status changes back to **Available**.

You can enable presence-based call routing with any of the routing methods.

If an agent opts out of getting calls, they won't be included in the call routing list regardless of what their availability status is set to.

> [!NOTE]
> When **Longest idle** is selected as the routing method, presence-based routing is required and automatically enabled even though the Presence-based routing toggle will be **Off** and grayed out.
>
> If presence-based routing is not enabled and there are multiple calls in the queue, the system will present these calls simultaneously to the agents regardless of their presence status. This will result in multiple call notifications to agents, particularly if some agents don’t answer the initial call presented to them.
>
> When using **Presence-based routing** there may be times when an agent receives a call from the queue shortly after becoming unavailable or a short delay in receiving a call from the queue after becoming available.
>
> Agents who use the Skype for Business client aren't included in the call routing list when presence-based routing is enabled. If you have agents who use Skype for Business, don't enable presence-based call routing.

> [!TIP]
> Setting **Presence-based routing** to **On** is the recommended setting.

**Agent alert time** specifies how long an agent's phone will ring before the queue redirects the call to the next agent.

> [!TIP]
> Setting **Agent alert time** to **20 seconds** is the recommended setting.

### [Step 8 - Call overflow](#tab/call-overflow)

## Step 8: Call overflow handling

![Screenshot of call overflow settings.](./media/call-queue-overflow-handling.png)

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time. The default is 50, but it can range from 0 to 200. When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

You can choose to disconnect the call or redirect it to any of the call routing destinations. For example, you might have the caller leave a voicemail for the agents in the queue. For external transfers, see [Prerequisites](./plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](./create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

> [!NOTE]
> If the maximum number of calls is set to 0 then the greeting message will not play.

### [Step 9 - Call timeout](#tab/call-timeout)

## Step 9: Call timeout handling

![Screenshot of call timeout settings.](./media/call-queue-timeout-handling.png)

**Call Timeout: maximum wait time** specifies the maximum time a call can be on hold in the queue before it is redirected or disconnected. You can specify a value from 0 seconds to 45 minutes.

You can choose to disconnect the call or redirect it to one of the call routing destinations. For example, you might have the caller leave a voicemail for the agents in the queue. For external transfers, refer to [Prerequisites](./plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](./create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details) for number formatting.

When you have selected your call timeout options, click **Save**.

---

## Summary of recommended call queue settings

The following settings are recommended:

- **Conference mode** to **On**
- **Routing method** to **Round robin** or **Longest idle**
- **Presence-based routing** to **On**
- **Agent alert time:** to **20 seconds**

## Call queue feature compatibility

|Feature                          |Teams Desktop<sup>1</sup> |Teams Mobile<sup>2</sup> |Lync |IP Phones | Standard Call Queues |Channel Based Call Queues | Comment |
|:--------------------------------|:------------------------:|:-----------------------:|:---:|:--------:|:--------------------:|:------------------------:|:-------------|
|**Agent Routing Methods**        |                          |                         |     |          |                      |                          |              |
|`Attendant Routing`              |Y                         |Y                        |Y    |Y         |Y                     |Y                         |*Default*     |
|`Longest Idle`<sup>3</sup>       |Y                         |Y                        |N    |Y         |Y                     |Y                         |*Recommended* |
|`Round Robin`                    |Y                         |Y                        |Y    |Y         |Y                     |Y                         |*Recommended* |
|`Serial`                         |Y                         |Y                        |Y    |Y         |Y<sup>4</sup>         |Y<sup>4</sup>             |              |
|**Transfer Modes**               |                          |                         |     |          |                      |                          |              |
|`Conference Mode`<sup>5</sup>    |Y                         |Y                        |N    |Y<sup>6</sup>|Y                  |Y                         |*Recommended* |
|`Transfer Mode`                  |Y                         |Y                        |Y    |Y         |Y                     |Y                         |              |
|Presence Based Routing<sup>3</sup>|Y                        |Y                        |N    |Y         |Y                     |Y                         |*Recommended* |
|Agents can Opt-out               |Y                         |Y                        |Y<sup>7</sup>|Y<sup>7</sup>|Y          |Y                         |*Default*     |
|Channel Based Queues             |Y                         |N                        |N    |N         |n/a                   |Y<sup>8</sup>             |              |
|Call toast shows Resource Account Name |Y<sup>9</sup>       |Y                        |Y    |          |Y                     |Y                         |              |
|**Dynamic caller ID**            |                          |                         |     |          |                      |                          |              |
|`Standard call queue`            |N                         |Y                        |N    |N         |Y                     |n/a                       |              |
|`Channel based call queue`       |Y                         |n/a                      |n/a  |n/a       |n/a                   |Y                         |              |
|**PSTN Connectivity Methods**    |                          |                         |     |          |                      |                          |See Note 10   |
|`Calling Plans`                  |Y                         |Y                        |Y    |Y         |Y                     |Y                         |              |
|`Direct Routing`                 |Y                         |Y                        |N    |N         |Y                     |Y                         |              |
|`Operator Connect`               |Y                         |Y                        |     |          |Y                     |Y                         |              |

Notes:

1. Microsoft Teams Windows client, Microsoft Teams Mac Client, Microsoft Teams on Virtualized Desktop Infrastructure, Microsoft Teams Web client.
2. Microsoft Teams iPhone app, Microsoft Teams Android app.
3. Selecting Longest Idle for the agent routing method will automatically enable Presence based routing.
4. Can only set the order when adding individual users as part of standard call queues. When a distribution list or Teams Channel is used order will be alphabetical.
5. Conference mode is not supported if phone calls are routed to the queue from a Direct Routing gateway that is enabled for Location Based Routing.
6. Microsoft Teams phone only.
7. Via the User Settings Portal page at [https://aka.ms/vmsettings](https://aka.ms/vmsettings).
8. Only public channels are supported.
9. Excluding Teams Web client.
10. Auto Attendants and Call Queues cannot transfer calls between PSTN connectivity methods.

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
- Microsoft Teams on [Virtualized Desktop Infrastructure](/microsoftteams/teams-for-vdi) (Windows Virtual Desktop, Citrix, and VMware)
- Microsoft Teams iPhone app
- Microsoft Teams Android app

  > [!NOTE]
  > Call queues that are assigned a direct routing number don't support Skype for Business clients, Lync clients, or Skype for Business IP Phones as agents. The Teams client is only supported with a [co-existence mode of Teams Only](/microsoftteams/setting-your-coexistence-and-upgrade-settings).

## Call queue cmdlets

Windows PowerShell allows you to create and manage call queues via the command line in a batch or programmatic manner.

The following cmdlets allow you to manage a call queue:

- [New-CsCallQueue](/powershell/module/skype/New-CsCallQueue)
- [Get-CsCallQueue](/powershell/module/skype/Get-CsCallQueue)
- [Set-CsCallQueue](/powershell/module/skype/Set-CsCallQueue)
- [Remove-CsCallQueue](/powershell/module/skype/Remove-CsCallQueue)

The following additional cmdlets are also required to manage the users, resource accounts, Microsoft Teams Phone licenses, phone numbers, audio files, and supported language that will be used with call queues:

Users/Teams

- Users
  - [Get-CsOnlineUser](/powershell/module/skype/Get-CsOnlineUser)

- Teams:
  - [Get-Team](/powershell/module/teams/Get-Team)
  - [Get-TeamChannel](/powershell/module/teams/Get-TeamChannel)

Resource accounts:

- [New-CsOnlineApplicationInstance](/powershell/module/skype/New-CsOnlineApplicationInstance)
- [Find-CsOnlineApplicationInstance](/powershell/module/skype/Find-CsOnlineApplicationInstance)
- [Get-CsOnlineApplicationInstance](/powershell/module/skype/Get-CsOnlineApplicationInstance)
- [Set-CsOnlineApplicationInstance](/powershell/module/skype/Set-CsOnlineApplicationInstance)
- [New-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/New-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/Get-CsOnlineApplicationInstanceAssociation)
- [Remove-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/Remove-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociationStatus](/powershell/module/skype/Get-CsOnlineApplicationInstanceAssociationStatus)

Virtual Teams Phone licenses:

- [Get-MsolAccountSku](/powershell/module/msonline/get-msolaccountsku)
- [Set-MsolUserLicense](/powershell/module/msonline/set-msoluserlicense)

Phone number assignment:

- [Get-CsOnlineTelephoneNumber](/powershell/module/skype/Get-CsOnlineTelephoneNumber)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/Set-csphonenumberassignment)

Audio Files

- [Get-CsOnlineAudioFile](/powershell/module/skype/Get-CsOnlineAudioFile)
- [Import-CsOnlineAudioFile](/powershell/module/skype/Import-CsOnlineAudioFile)
- [Export-CsOnlineAudioFile](/powershell/module/skype/Export-CsOnlineAudioFile)
- [Remove-CsOnlineAudioFile](/powershell/module/skype/Remove-CsOnlineAudioFile)

Support Language Lists

- [Get-CsAutoAttendantSupportedLanguage](/powershell/module/skype/Get-CsAutoAttendantSupportedLanguage)

For a step-by-step guide to creating call queues with PowerShell, see [Creating Call Queues with PowerShell cmdlets](create-a-phone-system-call-queue-via-cmdlets.md)

## Call Queue Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate that a call queue is able to receive calls:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Call Queue](https://aka.ms/TeamsCallQueueDiag)

2. In the Run diagnostic pane, enter the Resource Account in the **Username or Email** field, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant, policy, and resource account configurations to validate that the call queue is able to receive calls.

## Related topics

[Here's what you get with Microsoft Teams Phone](here-s-what-you-get-with-phone-system.md)

[Getting service phone numbers](getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
