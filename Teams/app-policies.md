---
title: Overview of app policies to manage apps in Teams
author: guptaashish
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
ms.service: msteams
ms.reviewer: 
search.appverid: 
description: Learn about app permission policies, app setup policies, and custom app policies used to manage apps in Microsoft Teams.
audience: admin
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
---

# Overview of app policies used to manage access to apps

Microsoft Teams uses policies to govern access and installation behavior. Policies help Teams administrators control the following:

* Configure access of apps to the users at a granular level. It helps each end-user use only those apps that an admin has allowed for their use.

* Pin relevant apps for users that auto-install. It helps end-users get started easily and access the relevant apps quickly.

## App permission policies

To learn more, go to [Manage custom app policies and settings in Teams.](teams-custom-app-policies-and-settings.md)

With app permission policies, Teams admin can control what apps are available to which specific users in their organization. You can define exact access mapping between app and user or any combination of both. For example, you can allow a few apps for all users, you can allow a few apps for a specific group of users, or you can allow a specific app for a specific user.

The app permission policies apply to all the types of apps available in Teams. For example, you can use app permission policies to gradually roll-out a third-party app or a custom app, by allowing it for specific users. To learn more, read [how to manage app permission policies](teams-app-permission-policies.md).

:::image type="content" source="media/app-permission-policy-trimmed.png" alt-text="Screenshot of app permission policy." lightbox="media/app-permission-policy.png":::

## App setup policies

App setup policies let you customize the app experience for your users. You choose the apps that you want to pin to the app bar in the Teams clients and the order in which they appear, on web, desktop, and mobile clients.

Here's some examples of how you can use app setup policies:

* Drive awareness and adoption of apps. For example, pin a custom recruiting and talent management app for users on your HR team.
* Selectively pin core apps, such as Chat, Teams, and Calling.

To learn more, see [how to manage app setup policies in Teams.](teams-app-setup-policies.md).

:::image type="content" source="media/app-setup-policy.png" alt-text="Screenshot of app setup policy in Teams admin center." lightbox="media/app-setup-policy.png":::

To know more, see [how to manage app setup policies in Teams](teams-app-setup-policies.md).

## Custom app policies

Teams allows developers within your organization to build, test, and deploy custom apps for organization's internal users. Developers can submit their custom apps via Teams for approval from Teams admins. You can use app setup policies to control who in your organization can upload custom apps. Admins can allow their organization's end-users to use custom app and developers to upload custom apps, using the Org-wide app settings.

:::image type="content" source="media/custom-app-policy-trimmed.png" alt-text="Allow custom apps in your organization in the org-wide settings panel." lightbox="media/custom-app-policy.png":::

## Related articles

* [Manage custom app policies and settings in Teams](teams-custom-app-policies-and-settings.md)
* [Manage app setup policies in Teams](teams-app-setup-policies.md)
* [Manage app permission policies in Teams](teams-app-permission-policies.md)
* [Manage Teams with policies](manage-teams-with-policies.md)
