---
title: Manage the Queues app for your organization
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.date: 07/16/2024
ms.topic: article
ms.reviewer: colongma, emkirby
audience: admin
ms.service: msteams
description: Learn how to set up and manage the Queues app in Teams.
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-voice
  - tier1
  - teams-1p-app-admin
appliesto: 
  - Microsoft Teams
search.appverid: MET150
---

# Manage the Queues app for your organization in Microsoft Teams

> [!NOTE]
> Queues app is in limited public preview. For more information, contact your Microsoft customer success manager. Information in this article is subject to change.

The Queues app is a Teams-native solution designed to empower organizations to manage customer engagements efficiently, starting with call queue calls. It leverages Teams Phone to enable your users to make and receive customer calls without leaving Teams, offering tailored experiences for users and leads that are designed for efficiency in call handling and resolution.

To learn more about call queues, see [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md).

## Overview of Queues

As an IT admin, you can enable Queues for your organization, manage the app settings, and designate authorized users to perform various actions such as adding and removing queue members, changing call handling flows, configuring auto-attendant greetings, and more. For a complete list of actions authorized users can make, see [Manage voice applications policies in Microsoft Teams](manage-voice-applications-policies.md).

## Licensing

Users must have a Teams Phone and a Teams Premium license to use Queues.

## Set up Queues

Before your users can use Queues, you need to enable the app for your organization and assign the appropriate licenses to your authorized users. You can also pin the Queues app to the Teams client for easy access.

For information on authorized users, see the following articles:

- [Plan for Auto attendant and Call queue authorized users](aa-cq-authorized-users-plan.md)
- [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md)
- [Manage voice applications policies in Teams](manage-voice-applications-policies.md)

Your users can find information on using the Queues app with [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9).

### Enable Queues in your organization

Queues is enabled by default for all Teams users in your organization who have been assigned a Teams Premium and Teams Phone license and who have been voice enabled. These users must be Authorized users. For more information, see [Steps for setting up Authorized users](aa-cq-authorized-users.md).

You can turn off or turn on the Queues app at the organization level on the [Manage apps](manage-apps.md) page in the Teams admin center:

1. In the Teams admin center, go to **Teams apps** >  **Manage apps**.
1. In the list of apps, search for **Queues**, select the app, and then switch the **Status** toggle to **Allowed**.

### Enable Queues for specific users in your organization

To allow or block specific users in your organization from using Queues, make sure Queues is turned on for your organization on the Manage apps page. Then, create a custom policy for app permissions and assign it to those users. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

### Pin Queues to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps you set in a policy are pinned to the app bar—the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

Authorized users with a Teams Phone and Teams Premium license have access to Queues and can pin the app on their Teams client. If the app isn't pinned by you via an app setup policy, Authorized users can still view Queues in the app bar flyout.

To automatically pin the Queues app in the Teams client for your users, do the following:

1. In the Teams admin center, go to **Teams apps** > **Setup policies**.
1. Select an existing policy or select **Add** to create a new policy.
1. Turn on **User pinning** so that your users can choose to pin the app for convenient access.
1. Under **Pinned apps**, select **Add apps**.
1. Search for **Queues** and select **Add**.
1. Select **Add** and then **Save**.

## Give feedback or report an issue

To send feedback or report an issue, select **Settings and more** (**…**) in Teams, and then choose **Help** > **Give feedback**. Enter your feedback or details about the issue you're experiencing. Indicate at the beginning of your feedback report that you're sending feedback about Queues so we can easily identify Queues issues.

## Related articles

- [Plan for Auto attendant and Call queue authorized users](aa-cq-authorized-users-plan.md)
- [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md)
- [Manage voice applications policies in Teams](manage-voice-applications-policies.md)
- [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Teams Premium licensing](/teams-add-on-licensing/licensing-enhance-teams)
