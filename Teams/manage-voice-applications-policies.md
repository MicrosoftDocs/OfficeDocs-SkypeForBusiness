---
title: Manage voice applications policies for Microsoft Teams
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: admin
ms.date: 03/15/2023
ms.collection: 
- M365-voice
- tier1
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.voiceapplications.overview
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage voice applications policies for Microsoft Teams to allow authorized end users to perform configuration changes on Auto attendants and Call queues.
---

# Manage voice applications policies for Microsoft Teams

Voice applications policies allow you to create and assign voice applications policies to authorized users. Voice applications policies control what configuration changes an authorized user can make to the Auto attendants and Call queues they're authorized for.

Voice applications policies can be managed in the Microsoft Teams admin center.

1. Sign into the [Microsoft Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851).
1. Navigate to **Voice** > **Voice applications policies**.

Alternatively, the [PowerShell cmdlets](#voice-applications-policy-powershell-cmdlets) in this article may be used.

## Before creating and assigning voice applications policies

Before creating and assigning policies, read [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md). The [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md) article describes how to plan and assign users as authorized users for Auto attendants and Call queues.

### Choose the appropriate policy for authorized users

Users in your organization are automatically assigned the **Global, (Org-wide default)** policy unless you create and assign a custom policy. By default, the **Global, (Org-wide default)** policy turns off all configuration change capabilities for users. 

To allow authorized users to make configuration changes, you can either change the **Global (Org-wide default)** policy or create and assign custom policies.

We recommend you create custom policies that reflect the configuration changes you want to allow authorized users to make to Auto attendants and Call queues.

### Required steps to set up authorized users

Changing the global policy or creating a custom policy and assigning to user(s) is only one of two steps required to create authorized users.

In addition to having a voice applications policy assigned, users must also be assigned as an [Authorized user](aa-cq-authorized-users.md) to at least one Auto attendant or Call queue.

Assigning a policy to a user but not assigning them an authorized user to at least one Auto attendant or Call queue won't enable the user to perform the actions described in this article.

Similarly, assigning a user as an authorized user to at least one Auto attendant or Call queue but not assigning a policy won't enable the user to perform the actions described in this article.

## Create a custom voice applications policy

1. Sign into the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851).
1. Navigate to **Voice** > **Voice applications policies**.
1. Select **Add**.

    :::image type="content" source="media/voiceapplications-policies-add-policy.png" alt-text="Screenshot of voice applications policy page in the Microsoft Teams admin center.":::

1. Enter a name and description for the policy.
1. From here, choose the settings you want.
    1. Choose the policy name and description carefully as these can't be changed later.
1. Select **Save**.

## Edit a custom voice applications policy

You can edit the global policy or any custom policies you create.

1. Sign into the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851).

1. Navigate to **Voice** > **Voice applications policies**.

1. Select the policy by selecting to the left of the policy name, and then select **Edit**.

1. Change the settings you want.

1. Select **Save**.

> [!NOTE]
> It's not possible to change the name or description of the policy.

## Assign a custom voice applications policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Voice applications policy PowerShell cmdlets

- [Get-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/get-csteamsvoiceapplicationspolicy):
  - Retrieve Teams voice applications policy information.

- [Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/grant-csteamsvoiceapplicationspolicy):
  - Assign a Teams voice applications policy to one or more users.

- [New-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/new-csteamsvoiceapplicationspolicy):
  - Create a new Teams voice applications policy.

- [Remove-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/remove-csteamsvoiceapplicationspolicy):
  - Delete an existing Teams voice applications policy.

## Voice applications policy settings

> [!IMPORTANT]
> In addition to creating a `TeamsVoiceApplicationsPolicy` and assigning it to users, a user must also be assigned as an [Authorized users](aa-cq-authorized-users.md) to at least one Auto attendant or Call queue.

### Auto Attendant

#### Greetings

***Features are currently available to all customers.***

- **Business Hours Greeting**: Turn on this setting to allow authorized users to change the *business hours greeting* for the Auto attendants they're authorized for.

- **After Hours Greeting**: Turn on this setting to allow authorized users to change the *after hours greeting* for the Auto attendants they're authorized for.

- **Holiday Greeting**: Turn on this setting to allow authorized users to change the *holiday greeting* for the Auto attendants they're authorized for.

#### General

***Features are currently available to preview customers only.***

- **Time zone**: Turn on this setting to allow authorized users to change the *Auto attendant time zone* for the Auto attendants they're authorized for.

- **Language**: Turn on this setting to allow authorized users to change the *Auto attendant language* for the Auto attendants they're authorized for.

- **Business hours**: Turn on this setting to allow authorized users to change the *Auto attendant business hours schedule* for the Auto attendants they're authorized for.

- **Holiday dates and hours**: Turn on this setting to allow authorized users to change the *Auto attendant holiday schedules* for the Auto attendants they're authorized for.

  > [!WARNING]
  > Holiday sets may be shared across multiple auto attendants.  In order to successfully make a change to a holiday schedule that is shared across multiple auto attendants, the user must be configured as an authorized user for all the auto attendants that reference the holiday.

#### Call Flow Routing

***Features are currently available to preview customers only.***

- **Business hours call routing**: Turn on this setting to allow authorized users to change the *Auto attendant business hours call flow* for the Auto attendants they're authorized for.

- **After hours call routing**: Turn on this setting to allow authorized users to change the *Auto attendant after-hours call flow* for the Auto attendants they're authorized for.
  
- **Holiday call routing**: Turn on this setting to allow authorized users to change the *auto attendant holiday call flows* for the auto attendants they're authorized for.

#### Reporting

***Features are currently available to preview customers only.***

- **Real Time Auto Attendant Metrics**: When set to **AuthorizedOnly** or **All**, this setting allows authorized users to access real-time auto attendant metrics.
   -  When set to **AuthorizedOnly**, an authorized user sees metrics for the auto attendants they're authorized for.
   -  When set to **All**, an authorized user sees metrics for all the auto attendants in the tenant.
     
- **Historical Auto Attendant Metrics**: When set to **Authorized** or **All**, this setting allows authorized users to access historical auto attendant metrics.
   -  When set to **AuthorizedOnly**, an authorized user sees metrics for the auto attendants they're authorized for.
   -  When set to **All**, an authorized user sees metrics for all the auto attendants in the tenant.


### Call Queue

#### Greetings

***Features are currently available to all customers.***

- **Welcome Greeting**: Turn on this setting to allow authorized users to change the *welcome greeting* for the Call queues they're authorized for.

- **Music on hold**: Turn on this setting to allow authorized users to change the *music on hold* for the Call queues they're authorized for.

- **Overflow Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *overflow shared voicemail greeting* for the Call queues they're authorized for.

- **Timeout Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *timeout shared voicemail greeting* for the Call queues they're authorized for.

- **No Agents Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *timeout shared voicemail greeting* for the Call queues they're authorized for.

#### General

***Features are currently available to preview customers only.***

- **Language**: Turn this setting on to allow authorized users to change the *Call queue language* for Call queues they're authorized for.

- **Membership**: Turn this setting on to allow authorized users to change the agents who are part of the Call queue.

- **Conference mode**: Turn this setting on to allow authorized users to change the *Call queue conference mode setting* for the Call queues they're authorized for.

  > [!WARNING]
  > **Conference mode** reduces the amount of time it takes for a caller and agent to be connected after the agent accepts the call.
  > 
  > Turning off **Conference Mode** will result in longer caller-to-agent connection times.

- **Agent routing method**: Turn this setting on to allow authorized users to change the *Call queue routing method* for the Call queues they're authorized for.

- **Presence-based routing**: Turn this setting on to allow authorized users to change the *Call queue presence-based routing option* for the Call queues they're authorized for.

- **Opt Out (Queue Configuration)**: Turn this setting on to allow authorized users to change the *Call queue opt-out setting* for the Call queues they're authorized for. This setting allows agents to opt-out of receiving calls from the Call queue.

- **Opt agent(s) in/out of queue**: Turn on this setting to allow authorized users to change an agent's opt-in status for the Call queues they're authorized for. 

#### Exception Handling

***Features are currently available to preview customers only.***

- **Routing for call overflow**: Turn this setting on to allow authorized users to change the *Call queue overflow handling properties* for the Call queues they're authorized for.

- **Routing for call timeout**: Turn this setting on to allow authorized users to change the *Call queue timeout handling properties* for the Call queues they're authorized for.

- **Routing for no agents**: Turn this setting on to allow authorized users to change the *call queue no-agent handling properties* for the call queues they're authorized for.

#### Monitor-Whisper-Barge-Takeover

***Features are not currently available.***

- **Agent monitor mode**: When set to **Monitor**, **Whisper**, **Barge**, or **Takeover**, this setting allows an authorized user to perform the following actions:
  - When set to **Monitor**, an authorized user can monitor an agent and listen to them while they are on an inbound call queue call.
  - When set to **Whisper**, an authorized user can monitor an agent and whisper to them while they are on an inbound call queue call. The caller won't hear the authorized user.
  - When set to **Barge**, an authorized user can monitor an agent, whisper to them, and barge in or join the inbound call queue call.
  - When set to **Takeover**, an authorized user can monitor an agent, whisper to them, barge in, and take over the inbound call queue call.

    > [!NOTE]
    > An agent may only be monitored by one authorized user at a time.
    >
    > An authorized user may only be in one monitor session at a time.

- **Agent monitor notification mode**: When set to *agent*, a call monitoring banner is presented to the agent who is being actively monitored by an authorized user.

#### Reporting

***Features are currently available to preview customers only.***

- **Real Time Call Queue Metrics**: When set to **AuthorizedOnly** or **All**, this setting allows authorized users to access real-time call queue metrics.
   -  When set to **AuthorizedOnly**, an authorized user sees metrics for the call queues they're authorized for.
   -  When set to **All**, an authorized user sees metrics for all the call queues in the tenant.

- **Real Time Agent Metrics**: When set to **AuthorizedOnly** or **All**, this setting allows authorized users to access real-time agent metrics.
   -  When set to **AuthorizedOnly**, an authorized user sees metrics for the agents associated with the call queues they're authorized for.
   -  When set to **All**, an authorized user sees metrics for all the agents in the tenant.

- **Historical Call Queue Metrics**: When set to **AuthorizedOnly** or **All**, this setting allows authorized users to access historical call queue metrics.
   -  When set to **AuthorizedOnly**, an authorized user sees metrics for the call queues they're authorized for.
   -  When set to **All**, an authorized user sees metrics for all the call queues in the tenant.

- **Historical Agent Metrics**: When set to **AuthorizedOnly** or **All**, this setting allows authorized users to access historical agent metrics.
   -  When set to **AuthorizedOnly**, an authorized user sees metrics for the agents associated with the call queues they're authorized for.
   -  When set to **All**, an authorized user sees metrics for all the agents in the tenant.


## Related articles

- [Authorized users](aa-cq-authorized-users.md).
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md).
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md).
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/manage-your-call-queue-and-auto-attendant-greetings-in-microsoft-teams-52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
