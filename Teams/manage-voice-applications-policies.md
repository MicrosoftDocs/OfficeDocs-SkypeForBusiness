---
title: Manage voice applications policies in Microsoft Teams
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: admin
ms.date: 03/13/2024
ms.collection: 
- M365-voice
- m365initiative-voice
- tier1
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.voiceapplications.overview
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage voice applications policies in Microsoft Teams to allow authorized end users to perform configuration changes on auto attendants and call queues.
---

# Manage voice applications policies in Microsoft Teams

> [!IMPORTANT]
> The Voice applications policy and Authorized user configuration options are available to all customers however any Voice applications policy items marked as `Preview` are currently only available as part of a Public Preview.
>
> General availability for all customers is scheduled for the second half of 2024. Licensing requirements TBD.

Voice applications policies allow you to create and assign voice application policies to authorized users. Voice application policies control what configuration changes an authorized user can make to the auto attendants and call queues they're authorized for.

Before creating and assigning policies, read [Authorized users](aa-cq-authorized-users.md).

Manage voice applications policies by signing into the [Microsoft Teams admin center](https://admin.microsoft.com/) and navigating to **Voice** > **Voice applications policies**. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization automatically get the global policy unless you create and assign a custom policy.

Alternatively, the [PowerShell cmdlets](#powershell-cmdlets) listed below may also be used.

> [!TIP]
> Best practice is to create custom policies that reflect the configuration changes you want to allow authorized users to make to auto attendants and call queues.

> [!IMPORTANT]
> The global, org-wide default policy turns off all configuration change capabilities. Changing the global policy or creating a custom policy and assigning to user(s) is one of two steps required to create authorized users.
>
> In addition to having a Teams Voice Applications Policy assigned, users must also be assigned as an [Authorized users](aa-cq-authorized-users.md) to at least one auto attendant or call queue.
>
> Having only a policy assigned and not being assigned as an authorized user to at least one auto attendant or call queue will not enable the user to perform the actions described below.
> Having only been assigned as an authorized user to at least one auto attendant or call queue but not being assigned a policy will not enable the user to perform the actions described below.

## Create a custom voice applications policy

1. In the left navigation of the [Microsoft Teams admin center](https://admin.microsoft.com/), go to **Voice** > **Voice applications policies**.
1. Select **Add**.

    :::image type="content" source="media/voiceapplications-policies-add-policy.png" alt-text="Screenshot of voice applications policy page in the Microsoft Teams admin center.":::

1. Enter a name and description for the policy.
1. From here, choose the settings you want.

    > [!NOTE]
    > Choose the policy name and description carefully as these can't be changed later.

1. Select **Save**.

## Edit a custom voice applications policy

You can edit the global policy or any custom policies you create.

1. In the left navigation of the [Microsoft Teams admin center](https://admin.microsoft.com/), go to **Voice** > **Voice applications policies**.
1. Select the policy by selecting to the left of the policy name, and then select **Edit**.
1. Change the settings you want.
1. Select **Save**.

> [!NOTE]
> It's not possible to change the name or description of the policy.

## Assign a custom voice applications policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## PowerShell cmdlets

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
> In addition to creating a TeamsVoiceApplicationsPolicy and assigning it to users, a user must also be assigned as an [Authorized users](aa-cq-authorized-users.md) to at least one auto attendant or call queue.

- Auto attendant configuration:
  - **Business Hours Greeting**: Turn on this setting to allow authorized users to change the *Business Hours Greeting* for the auto attendants they're authorized for.
  - **After Hours Greeting**: Turn on this setting to allow authorized users to change the *After Hours Greeting* for the auto attendants they're authorized for.
  - **Holiday Greeting**: Turn on this setting to allow authorized users to change the *Holiday Greeting* for the auto attendants they're authorized for.

- Call queue configuration:
  - **Welcome Greeting**: Turn on this setting to allow authorized users to change the *Welcome Greeting* for the call queues they're authorized for.
  - **Music on hold**: Turn on this setting to allow authorized users to change the *Music on hold* for the call queues they're authorized for.
  - **Overflow Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *Overflow Shared Voicemail Greeting* for the call queues they're authorized for.
  - **Timeout Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *Timeout Shared Voicemail Greeting* for the call queues they're authorized for.

## Voice applications policy settings - Preview

The following policy settings are referenced in the [PowerShell cmdlets](#powershell-cmdlets) however they are not generally available at this time and are not shown in Teams Admin Center.  Changing these policy keys via the cmdlet will not enable authorized users to perform these functions.  

- Auto attendant configuration
  - **AllowAutoAttendantBusinessHoursChange**: Turn on this setting to allow authorized users to change the *auto attendant business hours schedule* for the auto attendants they're authorized for.
  - **AllowAutoAttendantBusinessHoursRoutingChange**: Turn on this setting to allow authorized users to change the *auto attendant business hours call flow* for the auto attendants they're authorized for.
  - **AllowAutoAttendantAfterHoursRoutingChange**: Turn on this setting to allow authorized users to change the *auto attendant after-hours call flow* for the auto attendants they're authorized for.
  - **AllowAutoAttendantHolidaysChange**: Turn on this setting to allow authorized users to change the *auto attendant holiday schedules* for the auto attendants they're authorized for.
  - **AllowAutoAttendantHolidayRoutingChange**: Turn on this setting to allow authorized users to change the *auto attendant holiday call flows* for the auto attendants they're authorized for.
  - **AllowAutoAttendantLanguageChange**: Turn on this setting to allow authorized users to change the *auto attendant language* for the auto attendants they're authorized for.
  - **AllowAutoAttendantTimeZoneChange**: Turn on this setting to allow authorized users to change the *auto attendant time zone* for the auto attendants they're authorized for.

- Call Queue configuration
  - **AllowCallQueueOptOutChange**: Turn this setting on to allow authorized users to change the *call queue opt-out setting* for the call queues they're authorized for.  This setting allows agents to opt-out of receiving calls from the call queue.
  - **AllowCallQueueConferenceModeChange**: Turn this setting on to allow authorized users to change the *call queue conference mode setting* for the call queues they're authorized for.

    > [!WARNING]
    > **Conference mode** reduces the amount of time it takes for a caller and agent to be connected after the agent accepts the call.
    > .
    > Turning off **Conference Mode** will result in longer caller-to-agent connection times.

  - **AllowCallQueueLanguageChange**: Turn this setting on to allow authorized users to change the *call queue language* for call queues they're authorized for.
  - **AllowCallQueueMembershipChange**: Turn this setting on to allow authorized users to change the agents who are part of the call queue.
  - **AllowCallQueueMusicOnHoldChange**: Turn this setting on to allow authorized users to change the *call queue music on hold* for the call queues they're authorized for.
  - **AllowCallQueueNoAgentsRoutingChange**: Turn this setting on to allow authorized users to change the *call queue no-agent handling properties* for the call queues they're authorized for.
  - **AllowCallQueueOverflowRoutingChange**: Turn this setting on to allow authorized users to change the *call queue overflow handling properties* for the call queues they're authorized for.
  - **AllowCallQueuePresenceBasedRoutingChange**: Turn this setting on to allow authorized users to change the *call queue presence-based routing option* for the call queues they're authorized for.
  - **AllowCallQueueRoutingMethodChange**: Turn this setting on to allow authorized users to change the *call queue routing method* for the call queues they're authorized for.
  - **AllowCallQueueTimeoutRoutingChange**: Turn this setting on to allow authorized users to change the *call queue timeout handling properties* for the call queues they're authorized for.

- Call Queue - Agent opt-in status
  - **AllowCallQueueAgentOptChange**: Turn on this setting to allow authorized users to change an agent's opt-in status for the call queues they're authorized for.

- Call Queue - Monitor, whisper, barge, takeover  --- not currently available - this will be visible in the policy - leave out?
  - **CallQueueAgentMonitorMode**: When set to Monitor, Whisper, Barge or Takeover this setting allows an authorized user to perform the following actions:
    - When set to Monitor, an authorized user will be able to monitor an agent and listen to them while they are on an inbound call queue call.
    - When set to Whisper, an authorized user will be able to monitor an agent and whisper to them while they are on an inbound call queue call - the caller won't hear the authorized user.
    - When set to Barge, an authorized user will be able to monitor an agent, whisper to them and barge-in or join their inbound call queue call.
    - When set to Takeover, an authorized user will be able to monitor an agent, whisper to them, barge-in and take over the inbound call queue.

    > [!NOTE]
    > An agent may only be monitored by one authorized user at a time.
    > An authorized user may only be in one monitor session at a time.

  - **CallQueueAgentMonitorNotificationMode**: When set to *agent*, a call monitoring banner will be presented to an agent who is being actively monitored by an authorized user.

- Real-time and historical reporting

  - Real Time
    - **RealTimeAutoAttendantMetricsPermission**: Controls access to real-time auto attendant metrics - see below for values.
    - **RealTimeQueueMetricsPermission**: Controls access to real-time call queue metrics - see below for values.
    - **RealTimeAgentMetricsPermission**: Controls access to real-time agent metrics - see below for values.

  - Historical
    - **HistoricalAutoAttendantMetricsPermission**: Controls access to historical auto attendant metrics - see below for values.
    - **HistoricalQueueMetricsPermission**: Controls access to historical call queue metrics - see below for values.
    - **HistoricalAgentMetricsPermission**: Controls access to historical agent metrics - see below for values.

    Values:
    - None - no access to any metrics.
    - Authorized - the authorized user only sees metrics for the auto attendants and call queues (and associated agents) they're authorized for.
    - All - the authorized user sees metrics for all auto attendants and call queues (and associated agents) configured in the tenant.

## Related articles

- [Authorized users](aa-cq-authorized-users.md).
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md).
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md)
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
