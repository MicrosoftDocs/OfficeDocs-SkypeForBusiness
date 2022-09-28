---
title: Overview of app policies to manage apps in Teams
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-apps
search.appverid: 
description: Learn about app permission policies, app setup policies, and custom app policies used to manage apps in Microsoft Teams.
audience: admin
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
---

# App policies used to manage access to and installation of apps

Microsoft Teams uses app policies to govern access and installation behavior of apps. App policies help Teams administrators control the following app behavior:

* Configure the access of apps for each individual user or for a group of users. It helps admin control the apps that are allowed for each end-user.

* Pin those apps for end-users that are relevant for your organization's needs. Also, admins can install apps for end-users without user intervention. It helps end-users easily get started with the relevant apps.

* Control which developers in your organization can submit custom apps for admin approval. It helps you control the access to custom apps upload functionality.

## App permission policies

With app permission policies, Teams admin control what apps are available to each user in their organization. You can allow a few apps for all users, you can allow a few apps for a specific group of users, or you can allow specific apps for specific users. App permission policies work in tandem with org-wide settings and allow or block status of each individual app.

The app permission policies apply to all the [types of apps available in Teams](deploy-apps-microsoft-teams-landing-page.md). Some example scenarios in which you use app permission policies are:

* Gradually roll out an app to some users initially and to all users eventually.
* Allow a custom recruiting and talent management app for only members of your HR department and block it for all other organization users.

:::image type="content" source="media/app-permission-policy-trimmed.png" alt-text="Screenshot of app permission policy." lightbox="media/app-permission-policy.png":::

To learn more, see [how to manage app permission policies](teams-app-permission-policies.md).

## App setup policies

App setup policies let you configure how and where are apps available for users in their Teams client. You choose the apps that you want to pin to the app bar in the Teams clients and define the order in which apps are displayed.

Pinning or installing apps helps drive awareness and adoption of the desired apps in your organization. The changes apply to web, desktop, and mobile Teams clients.

Some example scenarios in which you use app setup policies are:

* Pin a custom recruiting and talent management app for members of your HR team.
* Change the order of the pre-pinned core apps for your organization's users.

:::image type="content" source="media/app-setup-policy-trimmed.png" alt-text="Screenshot of app setup policy in Teams admin center." lightbox="media/app-setup-policy.png":::

To know more, see [how to manage app setup policies](teams-app-setup-policies.md).

## Custom app policy

Your organization may commission the creation of custom apps for org-specific requirements. Developers within your organization can build, test, and deploy custom apps for organization's internal users of Teams. You use app setup policy to control who in your organization can upload custom apps. You use org-wide settings to allow end-users to use custom apps. You use permission policies to allow only specific end-users to use a custom app.

:::image type="content" source="media/custom-app-policy-trimmed.png" alt-text="Screenshot that shows how to allow custom apps in your organization in the org-wide settings panel." lightbox="media/custom-app-policy.png":::

To know more, see [how to manage custom app policies and settings](teams-custom-app-policies-and-settings.md).

## Related articles

* [Manage Teams with policies](manage-teams-with-policies.md)
* [Manage app permission policies](teams-app-permission-policies.md)
* [Manage app setup policies](teams-app-setup-policies.md)
* [Manage custom app policies and settings](teams-custom-app-policies-and-settings.md)
