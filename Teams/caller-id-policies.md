---
title: Manage caller ID policies in Microsoft Teams
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: roykuntz; jens
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.callinglineid.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage caller ID policies in Microsoft Teams to change or block the caller ID of Teams users in your organization.
---

# Manage caller ID policies in Microsoft Teams

> [!NOTE]
> To set the caller ID to a resource account phone number and to set the calling party name, use the PowerShell cmdlets New-CsCallingLineIdentity or Set-CsCallingLineIdentity in the Teams PowerShell module 2.3.1 or later. (These options are not currently available in the Microsoft Teams admin center.) 

By default, when a Teams user makes a call to a PSTN phone, the phone number of the Teams user is visible. Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible.

As an administrator, you can use caller ID policies to change or block the caller ID (also known as calling line ID). You can use caller ID policies to display an alternate phone number for Teams users in your organization, block the outbound phone number, block an incoming number from being displayed, or set the Calling Party Name (CNAM). For example, when a user makes a call, you can change the caller ID to display your organization's main phone number and company name instead of the user's phone number.

You manage caller ID policies by going to **Voice** > **Caller ID policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

## Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.
2. Click **Add**. <br>
![Screenshot of new caller ID policy page in the admin center.](media/caller-id-policies-add-policy.png)
3. Enter a name and description for the policy.
4. From here, choose the settings that you want:

    - **Block incoming caller ID**: Turn on this setting to block the caller ID of incoming calls from being displayed.
    - **Override the caller ID policy**: Turn on this setting to let users override the settings in the policy regarding displaying their number to callees or not. This means that users can choose whether to display their caller ID. For more information, see [End user control of outbound caller ID](./how-can-caller-id-be-used-in-your-organization.md#end-user-control-of-outbound-caller-id).
    - **Replace the caller ID with**: Set the caller ID to be displayed for users by selecting one of the following:

        - **User's number**: Displays the user's number. 
        - **Service number**: Lets you set a service phone number to display as the caller ID.
        - **Anonymous**: Displays the caller ID as Anonymous.

    - **Replace the caller ID with this service number**: Choose a service number to replace the caller ID of users. This option is available if you selected **Service number** in **Replace the caller ID with**.

5. Click **Save**.

## Edit a caller ID policy

You can edit the global policy or any custom policies that you create. 

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Change the settings that you want, and then click **Save**.

## Assign a custom caller ID policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Related topics

[New-CsCallingLineIdentity](/powershell/module/skype/new-cscallinglineidentity)

[Set-CsCallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity)

[Assign policies to your users in Teams](policy-assignment-overview.md)