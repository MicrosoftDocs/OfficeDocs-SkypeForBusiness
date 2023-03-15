---
title: Manage voice applications policies in Microsoft Teams
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
description: Learn how to use and manage voice applications policies in Microsoft Teams to allow authorized end users to perform configuration changes on auto attendants and call queues.
---

# Manage voice applications policies in Microsoft Teams

Voice applications policies allow you to create and assign voice application policies to authorized users. Voice application policies control what configuration changes an authorized user can make to the auto attendants and call queues they're authorized for.

Before creating and assigning policies, read [Authorized users](aa-cq-authorized-users.md).

Manage voice applications policies by signing into the [Microsoft Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851) and navigating to **Voice** > **Voice applications policies**. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization automatically get the global policy unless you create and assign a custom policy.

Alternatively, the [PowerShell cmdlets](#powershell-cmdlets) listed below may also be used.

> [!TIP]
> Best practice is to create custom policies that reflect the configuration changes you want to allow authorized users to make to auto attendants and call queues.

> [!IMPORTANT]
> The global, org-wide default policy turns off all configuration change capabilities. Changing the global policy or creating a custom policy and assigning to user(s) is one of two steps required to create authorized users.
>
> In addition to having a Teams Voice Applications Policy assigned, users must also be assigned to an auto attendant or call queue [Authorized users](aa-cq-authorized-users.md).
>
> Having only a policy assigned or only being assigned as an authorized user results in the user not being able to make changes to auto attendant or call queue configurations.

## Create a custom voice applications policy

1. In the left navigation of the [Microsoft Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), go to **Voice** > **Voice applications policies**.
1. Select **Add**.

    :::image type="content" source="media/voiceapplications-policies-add-policy.png" alt-text="Screenshot of voice applications policy page in teams admin center.":::

1. Enter a name and description for the policy.
1. From here, choose the settings you want.

    > [!NOTE]
    > Choose the policy name and description carefully as these can't be changed later.

1. Select **Save**.

## Edit a custom voice applications policy

You can edit the global policy or any custom policies you create.

1. In the left navigation of the [Microsoft Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), go to **Voice** > **Voice applications policies**.
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

- Auto attendant:
  - **Business Hours Greeting**: Turn on this setting to allow authorized users to change the *Business Hours Greeting* on the auto attendants they're authorized for.
  - **After Hours Greeting**: Turn on this setting to allow authorized users to change the *After Hours Greeting* on the auto attendants they're authorized for.
  - **Holiday Greeting**: Turn on this setting to allow authorized users to change the *Holiday Greeting* on the auto attendants they're authorized for.

- Call queue:
  - **Welcome Greeting**: Turn on this setting to allow authorized users to change the *Welcome Greeting* on the call queues they're authorized for.
  - **Music on hold**: Turn on this setting to allow authorized users to change the *Music on hold* on the call queues they're authorized for.
  - **Overflow Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *Overflow Shared Voicemail Greeting* on the call queues they're authorized for.
  - **Timeout Shared Voicemail Greeting**: Turn on this setting to allow authorized users to change the *Timeout Shared Voicemail Greeting* on the call queues they're authorized for.
