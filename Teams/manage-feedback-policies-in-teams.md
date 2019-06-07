---
title: Manage feedback policies in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: msedliak
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to use feedback policies to control whether Teams users in your organization can submit feedback about Teams to Microsoft. 
---

# Manage feedback policies in Microsoft Teams

Users can send comments and suggestions about Teams to Microsoft by going to **Help** > **Give feedback** in the Teams clients. We're continually improving the Teams experience and we use this feedback to make Teams better.

<placeholder only, will replace with a better screen shot, when available><br>
![Screen shot of the Give feedback option in Teams](media/manage-feedback-policies-in-teams-give-feedback.png)

> [!NOTE]
> Data sent through **Give feedback** is considered as "Support Data" under your Office 365 agreement, including information that would otherwise be considered "Customer Data" or "Personal Data".

As an admin, you can use feedback policies in the Microsoft Teams admin center to control whether users in your organization can send feedback about Teams to Microsoft. By default, all users in your organization are automatically assigned the global (Org-wide default) policy. You can edit the global policy or create and assign a custom policy. If a user is assigned a custom policy, that policy applies to the user. If a user isn't assigned a custom policy, the global policy applies to the user.

<placeholder only, will replace with a better screen shot, when available><br>
![Screen shot of feedback policies in the admin center](media/manage-feedback-policies-in-teams-policy-setting.png)

Say, for example, you want to allow all users in your organization to send feedback except for new hires in training. In this scenario, you create a custom policy to turn off the feedback option and assign it to new hires and apply the global policy to turn on the feedback option for all other users in your organization.

## Create a custom feedback policy

After you create a custom policy, assign it to users for the changes to take effect. 

1. In the left navigation of the Microsoft Teams admin center, go to **Feedback policies**. 
2. Select **New policy**.
3. Enter a descriptive name for the policy.
4. Turn on or turn off **Users can send feedback to Microsoft**, and then click **Save**.

## Edit a feedback policy

You can edit the global policy or any custom policies that you create. 

1. In the left navigation of the Microsoft Teams admin center, go to **Feedback policies**. 
2. Select the policy you want to edit.
3. Turn on or turn off **Users can send feedback to Microsoft**, and then click **Save**.

## Related topics

- [Teams PowerShell Overview](teams-powershell-overview.md)