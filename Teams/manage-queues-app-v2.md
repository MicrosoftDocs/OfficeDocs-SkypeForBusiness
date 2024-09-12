---
title: Manage Queues app for Microsoft Teams  
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.date: 09/05/2024
ms.topic: article
ms.reviewer: colongma, emkirby
audience: admin
ms.service: msteams
description: Learn how to configure the Queues app in Teams.
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-voice
  - tier1
  - teams-1p-app-admin
appliesto: 
  - Microsoft Teams
search.appverid: MET150
---

# Manage Queues app for Microsoft Teams in your organization  

## Overview of Queues app

> [!NOTE]
> Queues app is currently in limited private preview. Once generally available, it will be included in Teams Premium. For more information, contact your Microsoft customer success manager. Information in this article is subject to change.

The Queues app is a Teams-native solution designed to empower organizations to manage customer engagements efficiently, unlocking a set of advanced call functionalities for Teams Phone Call queues and Auto attendants, such as:

- **Call queue management**: Admins can now delegate authorized users, also known as leads or supervisors, to manage and configure Call queues and Auto attendants directly from the Teams client. Authorized users can configure Call queues and Auto attendants from Call settings and they can opt agents into and out of the queue from Queues app. For more information, see [Configure Queues app](#configure-users-for-queues-app).

- **Real-time metrics**: The number of waiting calls, average wait time, longest call waiting time metrics, and more are included in real-time metrics within the Queues app. During public preview, the analytics report will show activity made in the queue from 12:00 AM local time of the signed in user.

- **Historical reporting**: View historical metrics for call queues, and auto attendants, and agent queue actions. Historical metrics report up to the past 27 days.

Queues app is designed to enhance call queue handling capabilities within Teams for your users who utilize or plan to utilize call queues and auto attendants.

Keep the following in mind:

- Queues app is currently only supported on Teams desktop and Mac client, not on the web or Virtualized Desktop Infrastructure (VDI).
- Queues app is available in all regions where Teams Phone is supported. For more information, see [Country/region availability for Teams Phone](calling-plan-overview.md).
- Queues app is currently only available in public clouds, including GCC.

To learn more about Call queues and Auto attendants, see [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md).

Your users can find information on using the Queues app with [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9).

## Configure users for Queues app

### Licensing

Users must have a Teams Phone and a Teams Premium license to use Queues app. Once a user is licensed for Teams Premium, it can take up to 48 hours for Queues app to be available in the Teams client.

For more information on Teams Phone, see [What is Teams Phone](what-is-phone-system-in-office-365.md). For more information on Teams Premium, see [Microsoft Teams Premium – Overview for admins](enhanced-teams-experience.md) and [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams.md).

### Prerequisites

Queues app is enabled by default for all Teams users in your organization who are assigned both a Teams Premium and Teams Phone license who and are voice enabled.

As an IT admin, you can manage Queues app settings and designate *authorized users* to perform various actions such as adding and removing queue members, changing call handling flows, configuring auto attendant greetings, and more. For users who need additional capabilities to manage day-to-day operational changes, such as team leads, you must set up a voice applications policy and assign this policy to authorized users. You can allow authorized users to control call queue membership, greetings, call routing rules, and hours of operation.

By utilizing multiple voice application policies, you can assign different levels of permissions that reflect the configuration changes you want to allow authorized users to make to auto attendants and call queues. For example, you could have one voice application policy that allows the "team supervisor" to have access to both real-time and historical reporting and another policy for "shift leads" that allows access to real-time reporting and the ability to opt agents in and out of call queues.

For information on authorized users, see the following articles:

- [Plan for Auto attendant and Call queue authorized users](aa-cq-authorized-users-plan.md)
- [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md)
- [Manage voice applications policies in Teams](manage-voice-applications-policies.md)

For a list of all the Teams voice applications policy configuration and reporting settings, including their definitions, their PowerShell parameters, and their licensing requirements, see [Manage voice applications policies in Teams](manage-voice-applications-policies.md).

Your users, both queue members and leads, can find information on using the Queues app with [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9).

## Set up Queues app

> [!NOTE]
> You can turn off Queues app via the the Teams admin center. However, doing so also turns off other Microsoft apps like Insights and Tasks. Navigate to **Teams apps** > **Manage apps**. Select **Actions** > **Org-wide app settings** > **Microsoft apps**. Select **Off** and **Save**.

### Step 1: Assign licenses to users in your organization

Queues is enabled by default for all Teams users in your organization who are assigned both a Teams Premium and Teams Phone license and who are voice enabled.

### Step 2: Assign users to a call queue

In order to use Queues app, your users must be in at least one Call     queue. For information on configuring Call queues, see [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md). For more information on how to add users to a Call queue, see [Create a Call queue](create-a-phone-system-call-queue.md).

### Step 3: Pin Queues app to Teams (optional)

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps you set in a policy are pinned to the app bar—the bar on the left side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

Any user with a Teams Phone and Teams Premium license has access to Queues app and can pin the app on their Teams client. If the app isn’t pinned by you via an app setup policy, your users can still view Queues app in the app bar flyout under **View more apps**.

To automatically pin the Queues app in the Teams client for your users, do the following:

1. In the Teams admin center, go to **Teams apps** > **Setup policies**.
1. Select an existing policy or select **Add** to create a new policy.
1. Turn on **User pinning** so that your users can choose to pin the app for convenient access.
1. Under **Pinned apps**, select **Add apps**.
1. Search for **Queues** and select **Add**.
1. Select **Add** and then **Save**.

## Give feedback or report an issue

To send feedback or report an issue, select **Settings and more** (**…**) in Teams, and then choose **Help** > **Give feedback**. Enter your feedback or details about the issue you're experiencing. Indicate at the beginning of your feedback report that you're sending feedback about Queues app so we can easily identify Queues app-related issues.

## Related articles

- [Plan for Auto attendant and Call queue authorized users](aa-cq-authorized-users-plan.md)
- [Set up Auto attendant and Call queue authorized users](aa-cq-authorized-users.md)
- [Manage voice applications policies in Teams](manage-voice-applications-policies.md)
- [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams.md)
