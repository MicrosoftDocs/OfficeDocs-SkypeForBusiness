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
ms.date: 07/31/2024
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

> [!NOTE]
> Some of these features are in limited private preview. For more information, contact your Microsoft customer success manager. Information in this article is subject to change.

This article is for IT Pros and administrators who want to delegate Auto attendant and Call queue change capabilities to users in their organization.

Voice applications policies allow you to create and assign voice application policies to authorized users. Voice application policies control what configuration changes an authorized user can make to the auto attendants and call queues they're authorized for.

Before creating and assigning policies, read [Plan for authorized users](aa-cq-authorized-users-plan.md) for licensing information and [Set up authorized users](aa-cq-authorized-users.md). Some configuration capabilities require a Teams Premium license.

You can manage voice applications policies by using the [Microsoft Teams admin center](https://admin.microsoft.com/) or with PowerShell to create and assign custom policies. Users in your organization automatically get the global policy unless you create and assign a custom policy.

To manage voice applications policies with PowerShell, use the following PowerShell cmdlets:

- [Set-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/set-csteamsvoiceapplicationspolicy):
  - Update Teams voice applications policy settings.
- [Get-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/get-csteamsvoiceapplicationspolicy):
  - Retrieve Teams voice applications policy information.
- [Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/grant-csteamsvoiceapplicationspolicy):
  - Assign a Teams voice applications policy to one or more users.
- [New-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/new-csteamsvoiceapplicationspolicy):
  - Create a new Teams voice applications policy.
- [Remove-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/remove-csteamsvoiceapplicationspolicy):
  - Delete an existing Teams voice applications policy.

> [!IMPORTANT]
> The global, org-wide default policy disables all configuration change capabilities for all users. This policy should not be changed.
>
> You must create and assign custom policies to allow authorized users to make configuration changes to auto attendants and call queues.
>
> Best practice: The custom policy assigned to a user should provide the minimum levels of permissions the user needs to perform their job.

## Create a custom voice applications policy

Create custom policies that reflect the configuration changes you want to allow authorized users to make to auto attendants and call queues.

1. In the left navigation of the [Microsoft Teams admin center](https://admin.microsoft.com/), go to **Voice** > **Voice applications policies**.
1. Select **Add**.
1. Enter a name and description for the policy.
1. From here, choose the settings you want  to allow your authorized users to configure.

    > [!NOTE]
    > Choose the policy name and description carefully as these can't be changed later.

1. Select **Save**.

## Edit a custom voice applications policy

You can edit any custom voice applications policies you create.

1. In the left navigation of the [Microsoft Teams admin center](https://admin.microsoft.com/), go to **Voice** > **Voice applications policies**.
1. Select the policy by selecting to the left of the policy name, and then select **Edit**.
1. Change the settings you want to allow your authorized users to configure.
1. Select **Save**.

> [!NOTE]
> It's not possible to change the name or description of the policy.

## Assign a custom voice applications policy to users

To individually assign a custom voice application policy to users, you can use the Teams admin center or [Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/grant-csteamsvoiceapplicationspolicy) cmdlet.

In addition to creating a TeamsVoiceApplicationsPolicy and assigning it to users, a user must also be assigned as an [Authorized user](aa-cq-authorized-users.md) to at least one auto attendant or call queue.

If you only assign a voice application policy to a user and don't assign them as an authorized user to at least one auto attendant or call queue, the user can't perform the actions described in [Voice applications policy settings](#voice-applications-policy-settings). The reverse is also true - if you only assign a user as an Authorized user to at least one auto attendant or call queue but you don't assign them a voice applications policy, the user can't perform the actions you delegate.

To learn more about the different ways that you can assign policies to users, see [Assign policies to your users in Teams](policy-assignment-overview.md).

## Voice applications policy settings

Voice applications policies control what configuration changes and actions an authorized user can make to the auto attendants and call queues they're authorized for and what reports authorized users have access to. The following settings are available:

### Auto attendants - Features

|Teams voice applications policy setting|Description|PowerShell parameter|Teams Premium required<sup>1</sup>|
|-----------------------|--------------------------------|---------------------|---------------------|
|Business hours greeting|This setting allows authorized users to change the Business Hours Greeting.|AllowAutoAttendantBusinessHoursGreetingChange|No|
|After hours greeting|This setting allows authorized users to change the After Hours Greeting.|AllowAutoAttendantAfterHoursGreetingChange|No|
|Holiday greeting|This setting allows authorized users to change the Holiday Greeting.|AllowAutoAttendantHolidayGreetingChange|No|
|Business hours|This setting allows authorized users to change the auto attendant business hours schedule.|AllowAutoAttendantBusinessHoursChange|Yes, Private Preview|
|Business hours call routing|This setting allows authorized users to change the auto attendant business hours call flow.|AllowAutoAttendantBusinessHoursRoutingChange|Yes, Private Preview|
|After hours call routing|This setting allows authorized users to change the auto attendant after hours call flow.|AllowAutoAttendantAfterHoursRoutingChange|Yes, Private Preview|
|Holiday hours dates and hours |This setting allows authorized users to change the auto attendant holiday schedules.|AllowAutoAttendantHolidaysChange|Yes, Private Preview|
|Holiday hours call routing|This setting allows authorized users to change the auto attendant holiday call flow.|AllowAutoAttendantHolidayRoutingChange|Yes, Private Preview|

Notes

1. The user requires a Teams Premium license and Queues app to access this functionality.
   
### Auto attendant - Reporting

|Teams voice applications policy setting|Description|PowerShell parameter|Teams Premium required<sup>1</sup>|
|-----------------------|--------------------------------|---------------------|---------------------|
|Real-time auto attendant metrics|This setting allows authorized users to access real-time auto attendant metrics. |RealTimeAutoAttendantMetricsPermission |Yes, Private Preview|
|Historical auto attendant metrics using Power BI|This setting allows authorized users to access historical auto attendant metrics.|HistoricalAutoAttendantMetricsPermission|No|
|Historical auto attendants metrics using Queues app|This setting allows authorized users to access historical auto attendant metrics.|HistoricalAutoAttendantMetricsPermission|Yes, Private Preview|

Reporting values:

- **None** - no access to any metrics.
- **AuthorizedOnly** - the authorized user only sees metrics for the auto attendants and call queues (and associated agents) they're authorized for.
- **All** - the authorized user sees metrics for all auto attendants and call queues (and associated agents) configured in the tenant.

> [!IMPORTANT]
> The **All** value for real-time auto attendant metrics is no longer supported.

Notes

1. The user requires a Teams Premium license and Queues app to access this functionality.

### Call queues - Features

|Teams voice applications policy setting|Description|PowerShell parameter|Teams Premium required<sup>1</sup>|
|-----------------------|--------------------------------|---------------------|---------------------|
|Welcome greeting|This setting allows authorized users to change the Welcome Greeting.|AllowCallQueueWelcomeGreetingChange|No|
|Music on Hold|This setting allows authorized users to change the Music on Hold.|AllowCallQueueMusicOnHoldChange|No|
|Shared voicemail greeting for call overflow|This setting allows authorized users to change the Overflow Shared Voicemail Greeting.|AllowCallQueueOverflowSharedVoicemailGreetingChange|No|
|Shared voicemail greeting for call timeout|This setting allows authorized users to change the Timeout Shared Voicemail Greeting.|AllowCallQueueTimeoutSharedVoicemailGreetingChange|No|
|Shared voicemail greeting for no agents|This setting allows authorized users to change the No Agents Shared Voicemail Greeting.|AllowCallQueueNoAgentSharedVoicemailGreetingChange|No|
|Membership|This setting allows authorized users to change the agents who are part of the call queue.|AllowCallQueueMembershipChange|Yes, Private Preview<br>See note 2|
|Conference mode|This setting allows authorized users to change the call queue conference mode setting.|AllowCallQueueConferenceModeChange|Yes, Private Preview|
|Agent routing method|This setting allows authorized users to change the call queue agent routing (selection) method.|AllowCallQueueRoutingMethodChange|Yes, Private Preview|
|Presence-based routing|This setting allows authorized users to change the call queue presence-based routing setting.|AllowCallQueuePresenceBasedRoutingChange|Yes, Private Preview|
|Opt out (queue configuration)|This setting allows authorized users to change the call queue opt-out setting.|AllowCallQueueOptOutChange|Yes, Private Preview|
|Routing for call overflow|This setting allows authorized users to change the call queue overflow handling.|AllowCallQueueOverflowRoutingChange|Yes, Private Preview|
|Routing for call timeout|This setting allows authorized users to change the call queue timeout handling.|AllowCallQueueTimeoutRoutingChange|Yes, Private Preview|
|Routing for no agents|This setting allows authorized users to change the call queue no agents handling.|AllowCallQueueNoAgentsRoutingChange|Yes, Private Preview|

Notes

1. The user requires a Teams Premium license and Queues app to access this functionality.
1. If the Call queue uses a distribution list, security group, Microsoft 365 group or a Microsoft Teams channel the owner of these can add or remove agents without a Teams Premium license or Queues app.

### Call queues - Agent actions

|Teams voice applications policy setting|Description|PowerShell parameter|Teams Premium required<sup>1</sup>|
|-----------------------|--------------------------------|---------------------|---------------------|
|Opt agent in/out of queue|This setting allows authorized users to change an agent's opt-in status.|AllowCallQueueAgentOptChange|Yes, Private Preview|

Notes

1. The user requires a Teams Premium license and Queues app to access this functionality.
   
### Call queues - Reporting

|Teams voice applications policy setting|Description|PowerShell parameter|Teams Premium required<sup>1</sup>|
|-----------------------|--------------------------------|---------------------|---------------------|
|Real-time call queue metrics|This setting allows authorized users to access real-time call queue metrics.|RealTimeQueueMetricsPermission|Yes, Private Preview|
|Real-time agent metrics|This setting allows authorized users to access real-time call queue agent metrics.|RealTimeAgentMetricsPermission|Yes, Private Preview|
|Historical call queue metrics using Power BI|This setting allows authorized users to access historical call queue metrics in Power BI.|HistoricalQueueMetricsPermission|No|
|Historical agent metrics using Power BI|This setting allows authorized users to access historical call queue agent metrics in Power BI.|HistoricalAgentMetricsPermission|No|
|Historical call queue metrics using Queues app|This setting allows authorized users to access historical call queue metrics in the Queues app.|HistoricalQueueMetricsPermission|Yes, Private Preview|
|Historical agent metrics using Queues app|This setting allows authorized users to access historical call queue agent metrics in the Queues app.|HistoricalAgentMetricsPermission|Yes, Private Preview|

Reporting values:

- **None** - no access to any metrics.
- **AuthorizedOnly** - the authorized user only sees metrics for the auto attendants and call queues (and associated agents) they're authorized for.
- **All** - the authorized user sees metrics for all auto attendants and call queues (and associated agents) configured in the tenant.

> [!IMPORTANT]
> The **All** value for real-time call queue and real-time agent metrics is no longer supported.

Notes

1. The user requires a Teams Premium license and Queues app to access this functionality.

## Related articles

- [Set up Authorized users](aa-cq-authorized-users.md)
- [Plan for Authorized users](aa-cq-authorized-users-plan.md)
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md)
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md)
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
