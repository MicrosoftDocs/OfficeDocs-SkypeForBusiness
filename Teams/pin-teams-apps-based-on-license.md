---
title: Tailor Teams apps for your frontline workers
author: guptaashish
ms.author: guptaashish
ms.reviewer: aaglick
manager: prkosh
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to pin Teams apps for users in your organization based on license.
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Tailor your Teams apps based on license

> [!NOTE]
> Currently, this feature applies to F licenses. Therefore, this article focuses on the frontline worker experience. Other license types will be supported in the future.

## Overview

Teams provides an easy way to pin apps for frontline workers. <Add a blurb about FLW and link to the licensing marketing page>. When a user signs in to Teams with the tailored app experience enabled, the user gets an app experience that's tailored based on their license. This feature gives frontline workers the most relevant apps in Teams without any action needed from the admin.

## Tailored frontline app experience

Apps are pinned to the app bar, which is the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients (iOS and Android).

Apps pinned for users who have an F license:

- [Activity](https://support.microsoft.com/office/explore-the-activity-feed-in-teams-91c635a1-644a-4c60-9c98-233db3e13a56)
- [Chat](https://support.microsoft.com/office/get-started-with-chat-0b506ce2-eb6d-4fca-9668-e56980ba755e)
- [Teams](https://support.microsoft.com/office/teams-and-channels-in-microsoft-teams-c6d0e61d-a61e-44a6-a972-04f2a8fa4155)
- [Walkie Talkie](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c)
- [Tasks](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070)
- [Shifts](https://support.microsoft.com/office/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821)
- [Approvals](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3)

## Admin controls

> [!NOTE]
> User pinning must be turned on in the global (org-wide default) [app setup policy](teams-app-setup-policies.md) for this feature to take effect.

The tailored frontline app experience feature is controlled by the **Show tailored apps based on licenses** org-wide app setting on the [Manage apps](manage-apps.md#manage-org-wide-app-settings) page of the Teams admin center. If the feature is on, all users in your organization who have an F license will get the tailored app experience.

Keep in mind that any [custom app setup policies](teams-app-setup-policies.md) assigned to users take precedence. This means that if a user already has a custom app setup policy assigned to them, the user gets the configuration that's defined in the custom app setup policy. To learn more about how the feature works with existing app setup policies that you've applied in your organization, see the [Scenarios](#scenarios) section of this article.

This feature is on by default. However, if you don't want the tailored app experience provided by Microsoft, you can turn off the feature. To turn the feature off or on:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**, and then select **Org-wide app settings**.
2. Under **Tailored apps**, switch the **Show tailored apps based on licenses** toggle to **Off** or **On**.

## Scenarios

Use the information in this table to learn how the tailored app experience works in various scenarios, including when you've applied existing app setup policies.

|If...  |Then... |
|---------|---------|
The feature is turned off.   | The user gets the experience that's defined in the global app setup policy or custom app setup policy that's assigned to them.          |
|A user has the global app setup policy and the feature is on.     | The user gets the tailored app experience. The apps defined in the global app setup policy are pinned below the tailored app experience.      |
|A user has a custom app setup policy and the feature is on.    |The user gets the configuration that's defined in the custom app setup policy.          |
|The feature is on and you update the global app setup policy.     |The user gets the tailored app experience based on their license. The apps defined in the global app setup policy are pinned below the tailored app experience.         |
|A user has an E, A, or G license and the feature is on.   | The user doesn't get the tailored app experience. Currently, the tailored app experience applies only to users who have an F license.        |
|An app in the tailored app experience is blocked for a user or for your organization.      |The tailored app experience honors the app permission policy. If an app is blocked, users won't see the blocked app.           |
|An app in the tailored app experience is already defined in an app setup policy and the feature is on. |The app is pinned based on the order defined by the tailored app experience.        |

> [!NOTE]
> You can't change the apps or order of apps in the tailored app experience. For now, if you want to make changes, you can set up your own custom experience. To do this, first turn off the feature. Then, [create a custom app setup policy](teams-app-setup-policies.md), and [assign it to users or groups](assign-policies-users-and-groups.md).

## Related articles

- [Manage the Walkie Talkie app in Teams](walkie-talkie.md)
- [Manage the Tasks app in Teams](manage-tasks-app.md)
- [Manage the Shifts app in Teams](expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams.md)
- [Manage the Approvals app in Teams](approval-admin.md)
- [Manage app setup policies in Teams](teams-app-setup-policies.md)
- [Manage app permission policies in Teams](teams-app-permission-policies.md)
