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

This article is for IT Pros and administrators who want to manage certain Auto attendant or Call queue configuration capabilities to users in their organization through voice application policies.  

Voice applications policies allow you to create and assign voice application policies to authorized users. Voice application policies control what configuration changes an authorized user can make to the auto attendants and call queues they're authorized for.

Before creating and assigning policies, read [Plan for authorized users](aa-cq-authorized-users-plan) for licensing information and [Set up authorized users](aa-cq-authorized-users.md). Some configuration capabilities require a Teams Premium license.

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
> The global, org-wide default policy turns off all configuration change capabilities. You must create and assign custom policies to allow authorized users to make configuration changes to auto attendants and call queues.

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

To learn more about the different ways that you can assign policies to users, see [Assign policies to your users in Teams](../policy-assignment-overview.md).

## Voice applications policy settings

Voice applications policies control what configuration changes an authorized user can make to the auto attendants and call queues they're authorized for. The following settings are available:



Reporting values:

- *None* - no access to any metrics.
- *Authorized* - the authorized user only sees metrics for the auto attendants and call queues (and associated agents) they're authorized for.
- *All* - the authorized user sees metrics for all auto attendants and call queues (and associated agents) configured in the tenant.

## Related articles

- [Set up Authorized users](aa-cq-authorized-users.md)
- [Plan for Authorized users](aa-cq-authorized-users-plan.md)
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md)
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md)
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
