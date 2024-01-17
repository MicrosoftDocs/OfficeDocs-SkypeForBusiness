---
title: Manage voice applications policies for Microsoft Teams
author: mkbond007
ms.author: mabond
manager: pamgreen
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

Alternatively, the [PowerShell cmdlets](#voice-applications-policy-powershell-cmdlets) in this article can be used.

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

    :::image type="content" source="media/voiceapplications-policies-example-02.png" alt-text="Screenshot of voice applications policy page in the Microsoft Teams admin center.":::

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

- [Set-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/Set-CsTeamsVoiceApplicationsPolicy)
  - Change an existing Teams voice applications policy.

## Voice applications policy settings

> [!IMPORTANT]
> In addition to creating a `TeamsVoiceApplicationsPolicy` and assigning it to users, a user must also be assigned as an [Authorized users](aa-cq-authorized-users.md) to at least one Auto attendant or Call queue.

### Auto Attendant

#### Greetings

- **Business Hours Greeting**: Turn on this setting to allow authorized users to change the *business hours greeting* for the Auto attendants they're authorized for.

- **After Hours Greeting**: Turn on this setting to allow authorized users to change the *after hours greeting* for the Auto attendants they're authorized for.

- **Holiday Greeting**: Turn on this setting to allow authorized users to change the *holiday greeting* for the Auto attendants they're authorized for.

### Call Queue

#### Greetings

- **Welcome Greeting**: Turn on this setting to allow authorized users to change the *welcome greeting* for the Call queues they're authorized for.

- **Music on hold**: Turn on this setting to allow authorized users to change the *music on hold* for the Call queues they're authorized for.

- **Overflow Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *overflow shared voicemail greeting* for the Call queues they're authorized for.

- **Timeout Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *timeout shared voicemail greeting* for the Call queues they're authorized for.

- **No Agents Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *timeout shared voicemail greeting* for the Call queues they're authorized for.

## Related articles

- [Authorized users](aa-cq-authorized-users.md).
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md).
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md).
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/manage-your-call-queue-and-auto-attendant-greetings-in-microsoft-teams-52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
