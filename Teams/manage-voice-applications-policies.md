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
description: Learn how to use and manage voice application policies in Microsoft Teams to enable end users to perform configuration changes on autho attendants and call queues.
---

# Manage voice applications policies in Microsoft Teams

***** INSERT STUFF HERE *****

You manage voice applications policies by going to **Voice** > **Voice applications policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

Note: Best practice is to create custom policies...... 

## Create a custom voice applications policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Voice applications policies**.
2. Click **Add**. <br>
![Screenshot of new voice applications policy page in the admin center.](media/caller-id-policies-add-policy.png)
3. Enter a name and description for the policy.
4. From here, choose the settings that you want:
- Auto Attendant
    - **Business Hours Greeting**: Turn on this setting to block the caller ID of incoming calls from being displayed.
    - **After Hours Greeting**: Turn on this setting to let users override the settings in the policy regarding displaying their number to callees or not. This means that users can choose whether to display their caller ID. For more information, see [End user control of outbound caller ID](./how-can-caller-id-be-used-in-your-organization.md#end-user-control-of-outbound-caller-id).
    - **Holiday Greeting**: Set the caller ID to be displayed for users by selecting one of the following:

- Call Queue
    - **Welcome greeting**: Turn on this setting to block the caller ID of incoming calls from being displayed.
    - **Music on hold**: Turn on this setting to let users override the settings in the policy regarding displaying their number to callees or not. This means that users can choose whether to display their caller ID. For more information, see [End user control of outbound caller ID](./how-can-caller-id-be-used-in-your-organization.md#end-user-control-of-outbound-caller-id).
    - **Overflow shared voicemail greeting**: Set the caller ID to be displayed for users by selecting one of the following:
    - **Timeout shared voicemail greeting**: Set the caller ID to be displayed for users by selecting one of the following:

NOTE: Choose name and description carefully as these can't be changed later.

5. Click **Save**.

## Edit a custom voice applications policy

You can edit the global policy or any custom policies that you create. 

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Voice applications policies**.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Change the settings that you want, and then click **Save**.

NOTE: It's not possible to change the name or description of the policy.

## Assign a custom voice applications policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Related topics

[Get-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/get-csteamsvoiceapplicationspolicy)

[Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/grant-csteamsvoiceapplicationspolicy)

[New-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/new-csteamsvoiceapplicationspolicy)

[Remove-CsTeamsVoiceApplicationsPolicy](/powershell/module/skype/remove-csteamsvoiceapplicationspolicy)

[Assign policies to your users in Teams](policy-assignment-overview.md)
