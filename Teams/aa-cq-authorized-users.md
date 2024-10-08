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
ms.date: 03/25/2024
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

This article is for IT Pros and administrators who want to delegate Auto attendant and Call queue change capabilities to users in their organization. This article describes the necessary steps to create an Authorized user.

Before reading this article, be sure you've read [Plan for authorized users](aa-cq-authorized-users-plan.md), which describes licensing requirements and prerequisites for Auto attendant and Call queue authorized users.

An **authorized user** is a Teams user who has been authorized by a Teams admin center administrator to make configuration changes to Auto attendants and Call queues. The user doesn't need to have access to the Teams admin center portal nor be assigned any administrative roles.

With the Queues app in Microsoft Teams, you can delegate even more capabilities to your authorized users, such as configuring business, after hours, and holiday call routing and they can view real-time and historical metrics for Auto attendants and Call queues. To enable access to Queues, you must assign each user a Teams Premium and Teams Phone license. For more information, see [Set up Queues app for authorized users](#step-7-set-up-queues-app-for-authorized-users-optional).

The authorized user can access these change configuration items through their Teams desktop client or Queues. For end user documentation, see [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/52c741c6-8577-4faf-aa5a-c7853e0ab8f8).

For information on creating a Call queue or Auto attendant, see [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md) and [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md).

## Steps for setting up authorized users

To create an authorized user, you must complete the following steps:

- [Step 1 - Assign licenses and enable users for voice](#step-1-assign-licenses-and-enable-users-for-voice)
- [Step 2 - Assign phone numbers to your users](#step-2-assign-phone-numbers-to-your-users)
- [Step 3 - Create a Teams voice applications policy](#step-3-create-a-teams-voice-applications-policy)
- [Step 4 - Assign the voice applications policy to the user](#step-4-assign-the-voice-applications-policy-to-the-user)
- [Step 5 - Create an Auto attendant or Call queue and assign licensed resource accounts](#step-5-create-an-auto-attendant-or-call-queue-and-assign-licensed-resource-accounts)
- [Step 6 - Assign authorized users to the relevant Auto attendant or Call queue](#step-6-assign-authorized-users-to-the-relevant-auto-attendant-or-call-queue)
- [Step 7 – Set up Queues app for authorized users (optional)](#step-7-set-up-queues-app-for-authorized-users-optional)

## Step 1: Assign licenses and enable users for voice

> [!NOTE]
> In order for your users to use the Microsoft Teams Queues app, they need to have a Teams Phone and Teams Premium license assigned to them. For a complete list of authorized user settings that require a Teams Premium license, see [Manage Teams voice applications policies](manage-voice-applications-policies.md).

To assign a Teams Phone and Teams Premium license, do the following steps:

1. Use the Microsoft 365 admin center and go to **Billing** > **Licenses**.
1. Select your Teams Phone license. On the product details page, select **Assign licenses** and assign the license to your users.
1. Select **Assign** once you're finished.
1. Repeat Steps 2 and 3 for a Teams Premium license.

## Step 2: Assign phone numbers to your users

If you haven't already done so, assign user phone numbers to your users. For more information, see [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md).

## Step 3: Create a Teams voice applications policy

After assigning phone numbers to your users, you need to create a [Teams voice applications policy](manage-voice-applications-policies.md) that turns on the change functionality that the user needs and to assign that policy to the user.

## Step 4: Assign the voice applications policy to the user

Once you create your Teams voice applications policy, you need to individually assign it to users. To do this, you can use the Teams admin center or [Grant-CsTeamsVoiceApplicationsPolicy](/powershell/module/teams/grant-csteamsvoiceapplicationspolicy) cmdlet.

To learn about the different ways that you can assign policies to users, see [Assign policies to your users in Teams](policy-assignment-overview.md).

## Step 5: Create an Auto attendant or Call queue and assign licensed resource accounts

After assigning the voice applications policy to your users, if you haven’t already done so, you need to create Auto attendants or Call queues that the user will be authorized to manage.

For more information, see [Set up Auto attendants]( create-a-phone-system-auto-attendant.md) and [Set up Call queues](create-a-phone-system-call-queue.md).

## Step 6: Assign authorized users to the relevant Auto attendant or Call queue

The next step is assigning the user as an Authorized user to at least one Auto attendant or Call queue. There’s a maximum of 15 authorized users per each Auto attendant or Call queue.

## Step 7: Set up Queues app for Authorized users (optional)

With Queues in Microsoft Teams, authorized users can access more configuration features and reports for Auto attendants and Call queues, such as call flow configuration for business hours, after hours, holidays, and real-time call queue and agent metrics. Queues in Microsoft Teams is available to authorized users with a Teams Premium and Teams Phone license.

For a complete list of features and licensing required for each, see [Manage voice applications policies](manage-voice-applications-policies.md).

For information on how to manage the Queues app, see [Manage the Queues app in Microsoft Teams](manage-queues-app.md).

## Authorized user examples

User 1 needs to be able to change Auto attendant business hours greetings and Call queue timeout shared voicemail greetings for *Auto attendant 1* and *Call queue 1*.

User 2 needs to be able to change Auto attendant after hours greetings for *Auto attendant 1*.

1. Create a *Teams voice applications policy* that enables the Auto attendant **Business Hours Greeting** and the Call queue **Timeout shared voicemail greeting**.
1. Assign this policy to User 1.
1. Create another *Teams voice applications policy* that enables the Auto attendant **After Hours Greeting**.
1. Assign this policy to User 2.
1. Assign both User 1 and User 2 as *Authorized users* for *Auto attendant 1*.
1. Assign User 1 as an *Authorized User* for *Call queue 1*.

Both User 1 and User 2 are now fully authorized users and have new configuration options available to them in their Teams desktop client once they sign out and sign back in.

## Related articles

- [Manage Teams voice applications policies](manage-voice-applications-policies.md)
- [Plan for Auto attendant and Call queue authorized users](aa-cq-authorized-users-plan.md)
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md)
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md)
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
