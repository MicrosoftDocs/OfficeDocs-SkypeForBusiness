---
title: Tailor your Teams apps based on license
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaglick
manager: samanro
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
> [!INCLUDE [new-feature-coming-soon-section](includes/new-feature-coming-soon-section.md)]

> [!NOTE]
> Currently, this feature applies to F licenses. Therefore, this article focuses on the frontline worker experience. Other license types will be supported in the future.

## Overview

Teams provides a way to pin apps based on license. When a user signs in to Teams with the tailored app experience enabled, the user gets an app experience that's tailored based on their license.

This feature gives users the most relevant apps in Teams without any action needed from the admin.

## Tailored app experience

Apps are pinned to the app bar, which is the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients (iOS and Android).

Apps pinned for users who have an F license:

- Activity
- Chat
- Teams
- Shifts
- Tasks
- Walkie Talkie

## Admin controls

> [!NOTE]
> User pinning must be turned on in the global (org-wide default) app setup policy for this feature to take effect. To learn more, see [Manage app setup policies in Teams](teams-app-setup-policies.md).

The tailored app experience feature is controlled by the **Show tailored apps based on licenses** org-wide app setting on the [Manage apps](manage-apps.md#manage-org-wide-app-settings) page of the Teams admin center. If the feature is on, all users in your organization who have an F license will get the tailored app experience.

:::image type="content" source="media/pin-teams-apps-based-on-license.png" alt-text="Screenshot of the Show tailored apps based on license org-wide app setting":::

This feature is on by default. However, if you don't want the tailored app experience provided by Microsoft, you can turn off the setting on the [Manage apps](manage-apps.md#manage-org-wide-app-settings) page.

Keep in mind that any custom app setup policies assigned to users take precedence. This means that if a user already has a custom app setup policy assigned to them, the user gets the configuration that's defined in the custom app setup policy. To learn more about how the feature works with existing app setup policies that you've applied in your organization, see the [Scenarios](#scenarios) section of this article.

## Scenarios

Use the information in this table to learn how the tailored app experience feature works in various scenarios, including when you've applied existing app setup policies.

|If...  |Then... |
|---------|---------|
|A user has the global app setup policy and the feature is on.     | The user gets the tailored app experience.        |
|A user has a custom app setup policy and the feature is on.    |The user gets the configuration that's defined in the custom app setup policy.          |
|The feature is on and you update the global app setup policy.     |The user gets the tailored app experience based on their license. The apps defined in the global app setup policy are still pinned and appear further down in the list of   pinned apps.          |
|The feature is turned off.   | The user gets the experience that's defined in the global app setup policy or custom app setup policy that's assigned to them.          |
|A user has an E, A, or G license and the feature is on.   | The user doesn't get the tailored app experience. Currently, the tailored app experience applies only to users who have an F license.        |
|An app in the tailored app experience is blocked for a user or for your organization.      |The tailored app experience honors the app permission policy. If an app is blocked, users won't see the blocked app.           |
|An app in the tailored app experience is already defined in an app setup policy and the feature is on. |The app is pinned based on the order defined by the tailored app experience.        |

> [!NOTE]
> You can't change the apps or order of apps in the tailored app experience. For now, if you want to make changes, you can set up your own custom experience. To do this, first turn off the feature. Then, [create a custom app setup policy](teams-app-setup-policies.md), and [assign it to users or groups](assign-policies-users-and-groups.md).

## Related articles

- [Manage app setup policies in Teams](teams-app-setup-policies.md)
- [Manage app permission policies in Teams](teams-app-permission-policies.md)
