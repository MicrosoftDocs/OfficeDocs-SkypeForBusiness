---
title: Manage voice applications policies in Microsoft Teams
ms.author: 
author: 
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.voiceapplications.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage voice applications policies in Microsoft Teams to enable authorized end users to perform configuration changes on auto attendants and call queues.
---

# Manage voice applications policies in Microsoft Teams

Voice applications policies allow you to create and assign voice application policies to authorized users.  Voice application policies control what configuration changes an authorized user can make to the auto attendants and call queues they're authorized for.

Before creating and assigning policies, read [Authorized users](./aa-cq-authorized-users).

You manage voice applications policies by going to **Voice** > **Voice applications policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

Alternatively, the [PowerShell cmdlets](./manage-voice-applications-policies.md#powershell-cmdlets) listed below may also be used.

[!TIP]
> Best practice is to create custom policies based on needs of the user(s).

## Create a custom voice applications policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Voice applications policies**.
2. Click **Add**. <br>
![Screenshot of new voice applications policy page in the admin center.](media/caller-id-policies-add-policy.png)
3. Enter a name and description for the policy.
4. From here, choose the settings that you want:
- Auto Attendant
    - **Business Hours Greeting**: Turn on this setting to allow authorized users to change the Business Hours Greeting on the auto attendants they're authorized for.
    - **After Hours Greeting**: Turn on this setting to allow authorized users to change the After Hours Greeting on the auto attendants they're authorized for.
    - **Holiday Greeting**: Turn on this setting to allow authorized users to change the Holiday Greeting on the auto attendants they're authorized for.

- Call Queue
    - **Welcome greeting**: Turn on this setting to allow users to change the Welcome greeting on the call queues they're authorized for.
    - **Music on hold**: Turn on this setting to allow users to change the Music on hold on the call queues they're authorized for.
    - **Overflow shared voicemail greeting**: Turn on this setting to allow users to change the Overflow shared voicemail greeting on the call queues they're authorized for.
    - **Timeout shared voicemail greeting**: Turn on this setting to allow users to change the Timeout shared voicemail greeting on the call queues they're authorized for.

[!NOTE}
> Choose the policy name and description carefully as these can't be changed later.

5. Click **Save**.

## Edit a custom voice applications policy

You can edit the global policy or any custom policies that you create. 

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Voice applications policies**.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Change the settings that you want, and then click **Save**.

NOTE: It's not possible to change the name or description of the policy.

## Assign a custom voice applications policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

[!IMPORTANT]
> In addition to assigning the policy to users, the users must also be configured as Auto attendant or Call Queue [Authorized users](./aa-cq-authorized-users)

## PowerShell cmdlets

[Get-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/get-csteamsvoiceapplicationspolicy)

[Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/grant-csteamsvoiceapplicationspolicy)

[New-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/new-csteamsvoiceapplicationspolicy)

[Remove-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/remove-csteamsvoiceapplicationspolicy)
