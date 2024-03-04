---
title: Set up Auto attendant and Call queue authorized users
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: admin
ms.date: 04/05/2023
ms.collection: 
- M365-voice
- m365initiative-voice
- Tier1
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.voiceapplications.overview
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to set up authorized users and what they can manage for Auto attendants and Call queues.
---

# Set up Auto attendant and Call queue authorized users

Before reading this article, be sure you've read [Plan for authorized users](aa-cq-authorized-users-plan.md), which describes licensing requirements and prerequisites for Auto attendant and Call queue authorized users.

An **authorized user** is a Teams user who has been authorized by a Teams admin center administrator to make configuration changes to Auto attendants and Call queues. The user doesn't need to have access to the Teams admin center portal nor be assigned any administrative roles.

The authorized user accesses these configuration items through their Teams desktop client.

For information on creating a Call queue or Auto attendant, see [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md) and [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md).

## Requirements for setting up authorized users

To create an authorized user, you must complete the following steps:

- Step 1 - Assign licenses and enable users for voice
- Step 2 - Assign phone numbers to your users
- Step 3 - Create a Teams voice applications policy
- Step 4 - Create an Auto attendant or Call queue
- Step 5 - Assign the voice applications policy to the user
- Step 6 - Assign authorized users to the relevant Auto attendant or Call queue

## Step 1: Assign licenses and enable users for voice

> [!NOTE]
> In order for your users to use the Queues App, they need to have a Teams Phone and Teams Premium license assigned to them. For a list of authorized user settings that require a Teams Premium license, see [Manage Teams voice applications policies](manage-voice-applications-policies.md).

To assign a Teams Phone and Teams Premium license, do the following steps:

1. Use the Microsoft 365 admin center and go to **Billing** > **Licenses**.
1. Select your Teams Phone license. On the product details page, select **Assign licenses** and assign the license to your users.
1. Select **Assign** once you're finished.
1. Repeat Steps 2 and 3 for a Teams Premium license.

## Step 2: Assign phone numbers to your users



## Step 3: Create a Teams voice applications policy

After assigning phone numbers to your users, you need to create a [Teams voice applications policy](manage-voice-applications-policies.md) that turns on the change functionality that the user needs and to assign that policy to the user.

## Step 4: Create an Auto attendant or Call queue

If you haven't already done so, you need to create an [Auto attendant](create-a-phone-system-auto-attendant.md) or [Call queue](create-a-phone-system-call-queue.md) that the user will be authorized to manage.

## Step 5: Assign the voice applications policy to the user

Once you’ve created your voice applications policy, you need to assign it to users. To do this, you can use the Teams admin center or [Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/grant-csteamsvoiceapplicationspolicy) cmdlet.

[!INCLUDE [assign-policy](includes/assign-policy.md)]

## Step 6: Assign authorized users to the relevant Auto attendant or Call queue

The second step is to assign the user as an Authorized user to at least one Auto attendant or Call queue. There's a maximum of 15 authorized users per each Auto attendant or Call queue.

> [!IMPORTANT]
> A user must have a policy assigned that enables at least one type of configuration change and must also be assigned as an authorized user to at least one Auto attendant or Call queue.
>
> A user won't be able to make any configuration changes if:
>
> - The user has a policy assigned but isn't assigned as an authorized user to at least one Auto attendant or Call queue.
> - The user is assigned as an authorized user to at least one Auto attendant or Call queue but doesn't have a policy assigned.

## Authorized user examples

[INCLUDE PS SCENARIO]

User 1 needs to be able to change Auto attendant business hours greetings and Call queue timeout shared voicemail greetings for *Auto attendant 1* and *Call queue 1*.

User 2 needs to be able to change Auto attendant after hours greetings for *Auto attendant 1*.

1. Create a *Teams voice applications policy* that enables the Auto attendant **Business Hours Greeting** and the Call queue **Timeout shared voicemail greeting**.

    :::image type="content" source="media/voiceapplications-policies-example-01.png" alt-text="Screenshot of voice applications policy that enables Auto attendant business hours greeting changes and Call queue timeout shared voicemail greeting changes.":::

1. Assign this policy to User 1.
1. Create another *Teams voice applications policy* that enables the Auto attendant **After Hours Greeting**.

    :::image type="content" source="media/voiceapplications-policies-example-02.png" alt-text="Screenshot of voice applications policy that enables Auto attendant after hours greeting changes.":::

1. Assign this policy to User 2.
1. Assign both User 1 and User 2 as *Authorized users* for *Auto attendant 1*.
1. Assign User 1 as an *Authorized User* for *Call queue 1*.

Both User 1 and User 2 are now fully authorized users and have new configuration options available to them in their Teams desktop client once they sign out and sign back in.

## Related articles

- [Manage Teams voice applications policies](manage-voice-applications-policies.md).
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md).
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md).
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/manage-your-call-queue-and-auto-attendant-greetings-in-microsoft-teams-52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
