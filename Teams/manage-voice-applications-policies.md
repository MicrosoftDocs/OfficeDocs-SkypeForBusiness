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
ms.date: 09/16/2024
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

A user must be an Authorized user to at least one auto attendant or call queue, and must have a voice applications policy assigned to perform the actions described in [Voice applications policy settings](#voice-applications-policy-settings). 

To learn more about the different ways that you can assign policies to users, see [Assign policies to your users in Teams](policy-assignment-overview.md).

## Voice applications policy settings

Voice applications policies control the configuration changes and actions an authorized user can make to the auto attendants and call queues they're authorized for. In addition, they also control which real-time and historical reports authorized users have access to. The following settings are available:

### Auto attendants - Features

|Teams voice applications policy setting|Description                                                                        |PowerShell parameter                |Teams Premium required<sup>1</sup>|
|---------------------------|-----------------------------------------------------------------------------------------------|----------------------------------------------|------------------------|
|Business hours greeting    |This setting allows authorized users to change the Business Hours Greeting.                    |AllowAutoAttendantBusinessHoursGreetingChange |No, Generally Available |
|After hours greeting       |This setting allows authorized users to change the After Hours Greeting.                       |AllowAutoAttendantAfterHoursGreetingChange    |No, Generally Available |
|Holiday greeting           |This setting allows authorized users to change the Holiday Greeting.                           |AllowAutoAttendantHolidayGreetingChange       |No, Generally Available |
|Time zone                  |This setting allows authorized users to change the Time zone.                                  |AllowAutoAttendantTimeZoneChange              |Yes<sup>3</sup>         |
|Language                   |This setting allows authorized users to change the Lanugage.                                   |AllowAutoAttendantLanguageChange              |Yes<sup>3</sup>         |
|Business hours             |This setting allows authorized users to change the auto attendant business hours schedule.     |AllowAutoAttendantBusinessHoursChange         |Yes                     |
|Holiday dates and hours    |This setting allows authorized users to change the auto attendant holiday schedule.<sup>2</sup>|AllowAutoAttendantHolidaysChange              |Yes                     |
|Business hours call routing|This setting allows authorized users to change the auto attendant business hours call flow.    |AllowAutoAttendantBusinessHoursRoutingChange  |Yes                     |
|After hours call routing|This setting allows authorized users to change the auto attendant after hours call flow.          |AllowAutoAttendantAfterHoursRoutingChange     |Yes                     |
|Holiday hours call routing|This setting allows authorized users to change the auto attendant holiday call flow.            |AllowAutoAttendantHolidayRoutingChange        |Yes                     |

Notes

1. The authorized user requires a Teams Premium license and Queues app to access this functionality.
1. In order to change the holiday schedule, the authorized user must be authorized for all auto attendants that reference the holiday.
1. This option is not currently available for authorized users.
   
### Auto attendant - Reporting

|Teams voice applications policy setting  |Description                                                                      |PowerShell parameter           |Teams Premium required<sup>1</sup>|
|-----------------------------------------|---------------------------------------------------------------------------------|------------------------------------------|-----------------------|
|Real-time auto attendant metrics         |This setting allows authorized users to access real-time auto attendant metrics. |RealTimeAutoAttendantMetricsPermission    |Yes                    |
|Historical auto attendant metrics        |This setting allows authorized users to access historical auto attendant metrics in Power BI and Queues App.|HistoricalAutoAttendantMetricsPermission  |Power BI - No, Generally Available<br>Queues App - Yes|

Reporting values:

- **None** - no access to any metrics.
- **AuthorizedOnly** - the authorized user only sees metrics for the auto attendants and call queues (and associated agents) they're authorized for.
- **All** - the authorized user sees metrics for all auto attendants and call queues (and associated agents) configured in the tenant.

> [!IMPORTANT]
> The **All** value for real-time auto attendant metrics is no longer supported.

Notes

1. The authorized user requires a Teams Premium license and Queues app to access this functionality.

### Call queues - Features

|Teams voice applications policy setting|Description                                                                                |PowerShell parameter          |Teams Premium required<sup>1</sup>|
|------------------------------|----------------------------------------------------------------------------------------------------|-----------------------------------------|-----------------------|
|Welcome greeting              |This setting allows authorized users to change the Welcome Greeting.                                |AllowCallQueueWelcomeGreetingChange      |No, Generally Available|
|Music on Hold                 |This setting allows authorized users to change the Music on Hold.                                   |AllowCallQueueMusicOnHoldChange          |No, Generally Available|
|Shared voicemail greeting for call overflow|This setting allows authorized users to change the Overflow Shared Voicemail Greeting. |AllowCallQueueOverflowSharedVoicemailGreetingChange|No, Generally Available|
|Shared voicemail greeting for call timeout|This setting allows authorized users to change the Timeout Shared Voicemail Greeting.   |AllowCallQueueTimeoutSharedVoicemailGreetingChange|No, Generally Available|
|Shared voicemail greeting for no agents|This setting allows authorized users to change the No Agents Shared Voicemail Greeting.    |AllowCallQueueNoAgentSharedVoicemailGreetingChange|No<sup>3</sup>|
|Language                      |This setting allows authorized users to change the Language.                                        |AllowCallQueueLanguageChange             |Yes<sup>3</sup> |
|Membership                    |This setting allows authorized users to change the agents who are part of the call queue.           |AllowCallQueueMembershipChange           |Yes<br>See note 2|
|Conference mode               |This setting allows authorized users to change the call queue conference mode setting.              |AllowCallQueueConferenceModeChange       |Yes |
|Agent routing method          |This setting allows authorized users to change the call queue agent routing (selection) method.     |AllowCallQueueRoutingMethodChange        |Yes |
|Presence-based routing        |This setting allows authorized users to change the call queue presence-based routing setting.       |AllowCallQueuePresenceBasedRoutingChange |Yes |
|Opt out (queue configuration) |This setting allows authorized users to change the call queue opt-out setting.                      |AllowCallQueueOptOutChange               |Yes |
|Routing for call overflow     |This setting allows authorized users to change the call queue overflow handling.                    |AllowCallQueueOverflowRoutingChange      |Yes |
|Routing for call timeout      |This setting allows authorized users to change the call queue timeout handling.                     |AllowCallQueueTimeoutRoutingChange       |Yes |
|Routing for no agents         |This setting allows authorized users to change the call queue no agents handling.                   |AllowCallQueueNoAgentsRoutingChange      |Yes |

Notes

1. The authorized user requires a Teams Premium license and Queues app to access this functionality.
1. If the Call queue uses a distribution list, security group, Microsoft 365 group or a Microsoft Teams channel the owner of these can add or remove agents without a Teams Premium license or Queues app.
1. This option is not currently available for authorized users.

### Call queues - Agent actions

|Teams voice applications policy setting|Description                                                      |PowerShell parameter     |Teams Premium required<sup>1</sup>|
|--------------------------------|------------------------------------------------------------------------|--------------------------------------|---------------------|
|Opt agent in/out of queue       |This setting allows authorized users to change an agent's opt-in status.|AllowCallQueueAgentOptChange          |Yes                  | 
|Agent monitor mode              |This setting is not currently available for authorized users.           |CallQueueAgentMonitorMode             |Yes<sup>2</sup>      |
|Agent monitor notification mode |This setting is not currently available for authorized users.           |CallQueueAgentMonitorNotificationMode |Yes<sup>2</sup>      |

Notes

1. The authorized user requires a Teams Premium license and Queues app to access this functionality.
1. This option is not currently available for authorized users.
   
### Call queues - Reporting

|Teams voice applications policy setting|Description|PowerShell parameter|Teams Premium required<sup>1</sup>|
|------------------------------------------------|--------------------------------|---------------------|---------------------|
|Real-time call queue metrics   |This setting allows authorized users to access real-time call queue metrics.                            |RealTimeQueueMetricsPermission|Yes |
|Real-time agent metrics        |This setting allows authorized users to access real-time call queue agent metrics.                      |RealTimeAgentMetricsPermission|Yes |
|Historical call queue metrics  |This setting allows authorized users to access historical call queue metrics in Power BI and Queues App.|HistoricalQueueMetricsPermission|Power BI - No, Generally Available<br>Queues App - Yes |
|Historical agent metrics       |This setting allows authorized users to access historical call queue agent metrics in Power BI and Queues App.|HistoricalAgentMetricsPermission|Power BI - No, Generally Available<br>Queues App - Yes1. This option is not currently available for authorized users.|

Reporting values:

- **None** - no access to any metrics.
- **AuthorizedOnly** - the authorized user only sees metrics for the auto attendants and call queues (and associated agents) they're authorized for.
- **All** - the authorized user sees metrics for all auto attendants and call queues (and associated agents) configured in the tenant.

> [!IMPORTANT]
> The **All** value for real-time call queue and real-time agent metrics is no longer supported.

Notes

1. The authorized user requires a Teams Premium license and Queues app to access this functionality.

## Related articles

- [Set up Authorized users](aa-cq-authorized-users.md)
- [Plan for Authorized users](aa-cq-authorized-users-plan.md)
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md)
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md)
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
