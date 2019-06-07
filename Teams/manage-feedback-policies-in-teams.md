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

Users can send comments and suggestions about Teams to Microsoft by going to **Help** > **Give feedback** in the Teams clients. We value feedback from customers and use it to improve Teams.

The information that's sent through **Give feedback** is considered as "Support Data" under your Office 365 agreement, including information that would otherwise be considered "Customer Data" or "Personal Data". 

As an admin, you can use feedback policies in the Microsoft Teams admin center to control whether Teams users in your organization can send feedback about Teams to Microsoft. By default, all users in your organization are automatically assigned the global (Org-wide default) policy. You can make changes to the global policy or create and assign one or more custom policies. 

If a user is assigned a custom policy, that policy applies to the user. If a user isn't assigned a custom policy, the global policy applies to the user.

Say, for example, you want to allow all users in your organization to send feedback except for new hires in training. In this scenario, you create a custom feedback policy with the setting turned off and assign it to new hires in training.

## Create a custom feedback policy

1. In the left navigation, go to **Feedback policies**. 
2. Select **New policy**.
3. Enter a descriptive name for the policy.
4. Turn on or turn off **Users can send feedback to Microsoft**, and then click **Save**.

## Related topics

- [Teams PowerShell Overview](teams-powershell-overview.md)