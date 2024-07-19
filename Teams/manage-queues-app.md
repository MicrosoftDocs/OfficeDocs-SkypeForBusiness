---
title: Manage the Queues app for your organization
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.date: 07/16/2024
ms.topic: article
ms.reviewer: 
audience: admin
ms.service: msteams
description: Learn how to set up and manage the Queues app in Teams.
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-1p-app-admin
appliesto: 
  - Microsoft Teams
ms.custom:
  - M365-collaboration
search.appverid: MET150
---

# Manage the Queues app for your organization in Microsoft Teams

## Overview of Queues

[insert Queues overview text here]

## Licensing

Users must have a Teams Phone and a Teams Premium license to use Queues.

## Set up Queues

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
- [Assign policies to your users in Teams](../../policy-assignment-overview.md)
